


# Landbase Definition

The Analysis Forest Landbase (AFLB) refers to the forested area of the TSA that the provincial government manages for a variety of natural resource values.  This excludes non-forested areas (e.g., water, rock and ice), non-productive forest (e.g., alpine areas, areas with very low productivity, roads),non-commercial forest (e.g., brush areas), and areas excluded from the TSA for analysis purpose (Area-based tenures, private land).  The analysis forest does include federally-protected areas because of their contribution to biodiversity. 

The Timber Harvesting Landbase (THLB) is an estimate of the land where timber harvesting is considered both acceptable and economically feasible, given the objectives for all relevant forest values, existing timber quality, market values and applicable technology. The THLB is derived from the data, forest management practices and assumptions described in the data package.  It is a theoretical, strategic level estimate used for timber supply analysis and could include areas that may never be harvested or may exclude areas that will be harvested.

AFLB and THLB derivation is detailed in the [Mackenzie Timber supply Review Data Package](https://www2.gov.bc.ca/assets/gov/farming-natural-resources-and-industry/forestry/stewardship/forest-analysis-inventory/tsr-annual-allowable-cut/16ts_dp_2020_november.pdf). 

The following SQL script implements the Mackenzie TSA netdown:


```sql
--Netdown

----\set tsa16_netdown2022 

\echo --------------------------------------------
\echo tsa16_netdown2022
\echo --------------------------------------------
\echo creating source table 
drop table tsa16_netdown2022;

create table tsa16_netdown2022 as (
select a.*,
  b.feature_id,
  b.bclcs_lv_1,
  b.bclcs_lv_2,
  b.bclcs_lv_3,
  b.bclcs_lv_4,
  b.bclcs_lv_5,
  b.wetland_type,
  b.site_index,
  b.spec_cd_1,
  b.np_desc,
  b.cutblocks2019_fid,
  b.cc_harvest_year,
  b.lu_name,
  b.bgc_label,
  b.ogma_provid,
  b.rmp_l_name,
  b.uwr_no_harv_code,
  b.wha_no_harv_code,
  b.fisher_no_harv,
  b.dmk_id,
  b.unit_type,
  b.arch_grid,
  c.area_lineal,
  d.slope,
  d.elevation,
  d.ctime,
  d.instability,
  d.econ_neighborhood,
  d.patch_id,
  d.size,
  d.nndist,
  d.isolated,
  e.max_vol2020,
  b.isolation_mask_id,
  b.wolv0315_no_harv
from tsa16_ownership a join tsa16_tmp_res b using (ogc_fid) join tsa16_netdown c using(ogc_fid) join tsa16_op_wrk d using(ogc_fid)
join tsa16_maxvol2020 e using(ogc_fid)
where b.included > 0);

\echo ----------------------------------
\echo add included field
\echo -----------------------------------

alter table tsa16_netdown2022 add column included int default 1;

\echo ----------------------------------
\echo add tracking fields in source table
\echo ------------------------------------

alter table tsa16_netdown2022 add column cflb_fact numeric default 1.0,
 add column thlb_fact numeric default 1.0,
 add column thlb_net numeric default 1.0,
 add column n01_ownership text,
 add column n02_nonfor text,
 add column p03_lineal_features numeric default 1.0,
 add column n04_park text,
 add column n05_uwr text,
 add column n06_wha text,
 add column n07_ogma text,
 add column n08_rmp text,
 add column n09_ch text,
 add column n10_inoperable text,
 add column n11_nonmerchantable text,
 add column n12_inaccessible text,
 add column p13_retention numeric default 1.0;
 

\echo ---------------------------
\echo create summary table
\echo ----------------------------


drop table tsa16_netdown_summary2022;
create table tsa16_netdown_summary2022 (
  landclass text,
  total numeric,
  percent numeric,
  excluded numeric
);

\echo ------------------------
\echo calculate total area
\echo ------------------------

insert into tsa16_netdown_summary2022 (landclass, total) select 'TSA boundary', sum(included) from tsa16_netdown2022;

\echo ---------------------------
\echo set ownership null to 91U
\echo ----------------------------

\echo -----------------------------
\echo assign labels to ownership tracker
\echo new FNWL has been remove: 100N - use new_lbl for ownership
\echo -----------------------------

update tsa16_netdown2022 set n01_ownership = case
    when new_lbl = '40N' then description
    when new_lbl = '100N' then description
    when new_lbl = '80N' then description
    when new_lbl = '52N' then description
    when new_lbl = '54N' then description
    when new_lbl = '79B' then description
    when new_lbl = '77B' then description
    when new_lbl = '72B' then description
  end;

\echo ---------------------------------------
\echo calculate area for non provincial lands
\echo --------------------------------------

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Non_provincial_Crown_Lands', sum(included), round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n01_ownership is not null;
\echo ----------------------
\echo update thlb area
\echo ----------------------
update tsa16_netdown2022 set thlb_net = 0 where n01_ownership is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo calculate area for non-forest,non-productive
\echo --------------------------------------

update tsa16_netdown2022 set n02_nonfor = case
  	when bclcs_lv_1 = 'N' AND bclcs_lv_3 = 'A' then 'non_vegetated_alpine_lcs'
  	when bclcs_lv_2 = 'N' AND bclcs_lv_3 = 'A' then 'non_treed_alpine_lcs'
  	when bgc_label = 'BAFAun' then 'alpine_bec'
  	when bclcs_lv_1 = 'N' AND bclcs_lv_5 = 'LA' then 'lake_lcs'
  	when bclcs_lv_1 = 'N' AND bclcs_lv_5 = 'RE' then 'reservoir_lcs'
  	when bclcs_lv_1 = 'N' AND bclcs_lv_5 = 'RI' then 'riparian_lcs'
  	when bclcs_lv_2 = 'T' AND bclcs_lv_3 = 'W' then 'treed_wetland_lcs'
  	when  bclcs_lv_2 = 'N' AND bclcs_lv_3 = 'W' then 'non_treed_wetland_lcs'
  	when bclcs_lv_3 = 'W' then 'wetlands_lcs'
  	when wetland_type = 'W' then 'wetland_fwa'
  	when bclcs_lv_1 = 'N' and cc_harvest_year is null then 'non_vegetated_lcs'
  	when bclcs_lv_2 = 'N' and bclcs_lv_4 not in ('ST', 'SL') and cc_harvest_year is null then 'non_treed_herb_lcs'
  	when bclcs_lv_4 in ('ST', 'SL') and cc_harvest_year is null then 'non_treed_shrub_lcs'
  	when (coalesce(site_index, 0) < 5) and cc_harvest_year is null then 'non_productive_si_vri'
  	when np_desc is not null and cc_harvest_year is null then 'FC1_' || np_desc
  	when bclcs_lv_1||bclcs_lv_2 ='VT' AND spec_cd_1 is NULL then 'no_spec_cd_1'
  	when bclcs_lv_1 = 'U' or bclcs_lv_1 is null then 'unclassified'	
  end;
  
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Non_Forest_and_Non_Productive_Forest', sum(included), round(sum(included)/64106.430,2),sum(thlb_net) 
	from tsa16_netdown2022
	where n02_nonfor is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n02_nonfor is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ----------------------------------------n----------
\echo add lineal features
\echo -------------------------------------------------

update tsa16_netdown2022 set
  p03_lineal_features  = 1- round(area_lineal,3);


\echo ---------------------------------------
\echo calculate area for lineal features
\echo --------------------------------------

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Lineal_Features', sum(included*(1-p03_lineal_features )),
	round(sum(included*(1-p03_lineal_features ))/64106.430,2), sum(thlb_net*(1-p03_lineal_features )) 
	from tsa16_netdown2022;

update tsa16_netdown2022 set thlb_net = thlb_net*p03_lineal_features ;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo calculate area for crown forest
\echo --------------------------------------

update tsa16_netdown2022 set
  cflb_fact = 
    (n01_ownership is null)::int *
    (n02_nonfor is null)::int *
    p03_lineal_features;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add crown forest arua to netdowntable_blks
\echo --------------------------------------
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Crown_forest_management_land_base', sum(thlb_net), round(sum(thlb_net)/64106.430,2), NULL 
	from tsa16_netdown2022;
	
\echo ---------------------------------------
\echo add Provincial parks and mic.reserves
\echo --------------------------------------

update tsa16_netdown2022 set 
  n04_park = case
    when new_lbl = '60N' then 'Conservancy_Ecological_Reserve_Protected_Area_Provincial_Park'
    when own_lbl = '81U'  then 'Local_Region_Park'
  end;

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Provincial_Parks_and_Miscellaneous_Reserves', sum(included), round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n04_park is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n04_park is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add UWR No Harvest Zones
\echo --------------------------------------

update tsa16_netdown2022 set
  n05_uwr = 'No_Harvest'
where 
  uwr_no_harv_code = 'NO HARVEST ZONE' or unit_type ='core';

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Ungulate_Winter_Range', sum(included), round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n05_uwr is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n05_uwr is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add WHA No Harvest Zones
\echo --------------------------------------

update tsa16_netdown2022 set
  n06_wha = 'WildLife_Habitat_Area'
where 
  wha_no_harv_code = 'NO HARVEST ZONE' or wolv0315_no_harv > 0 or fisher_no_harv is not null;

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Wildlife_Habitat_Areas', sum(included), round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n06_wha is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n06_wha is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add OGMAs
\echo --------------------------------------

update tsa16_netdown2022 set
  n07_ogma = 'OGMA'
where 
  ogma_provid is not null;

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Old_Growth_Management_Areas', sum(included),round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n07_ogma is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n07_ogma is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add RMP:Mugaha Marsh Sensitive Area Plan
\echo --------------------------------------

update tsa16_netdown2022 set
  n08_rmp = 'Mugaha_Marsh_Sensitive_Area_Plan'
where 
  rmp_l_name is not null;

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Mugaha_Marsh_Sensitive_Area_Plan', sum(included),round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n08_rmp is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n08_rmp is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add Cultural Heritage Values
\echo --------------------------------------

update tsa16_netdown2022 set
  n09_ch = 'Cultural Heritage Sites'
where 
  arch_grid is not null;

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Cultural Heritage Sites', sum(included),round(sum(included)/64106.430,2), sum(thlb_net) 
	from tsa16_netdown2022
	where n09_ch is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n09_ch is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo add gthlb to netdowntable_blks
\echo --------------------------------------
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Gross_Timber_Harvesting_Landbase', sum(thlb_net), round(sum(thlb_net)/64106.430,2), NULL 
	from tsa16_netdown2022;
	
\echo --------------------------------------
\echo add inoperable categories-------------
\echo --------------------------------------

update tsa16_netdown2022 set n10_inoperable = case
  	when slope > 46.7 AND econ_neighborhood < 1 and cc_harvest_year is null then 'inoperable_slope'
  	when elevation > 1332 AND econ_neighborhood < 1 and cc_harvest_year is null then 'inoperable_elevation'
  	when ctime > 1622 AND econ_neighborhood < 1 and cc_harvest_year is null then 'inoperable_distance'
  	when instability > 0 AND econ_neighborhood < 1 and cc_harvest_year is null then 'inoperable_instability'
  end;
  
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Inoperable_Forest', sum(included), round(sum(included)/64106.430,2),sum(thlb_net) 
	from tsa16_netdown2022
	where n10_inoperable is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n10_inoperable is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;


\echo --------------------------------------
\echo add non-merchantable area-------------
\echo --------------------------------------

update tsa16_netdown2022 set n11_nonmerchantable = case
		when max_vol2020 <  125.1 AND econ_neighborhood < 1 and cc_harvest_year is null then 'non-Merchantable'
 		when spec_cd_1 in ('Z','W','EP','AC','ACT') and cc_harvest_year is null then 'non-Commercial'
	end;
  
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Non-Merchantable_Forest', sum(included), round(sum(included)/64106.430,2),sum(thlb_net) 
	from tsa16_netdown2022
	where n11_nonmerchantable is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n11_nonmerchantable is not null;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo --------------------------------------
\echo add inaccessible categories-------------
\echo --------------------------------------

update tsa16_netdown2022 set n12_inaccessible= case
  	when size < 5 and ctime > 300 then 'inaccessible_patch_size'
  	when isolation_mask_id is not null then 'inaccesible_isolated'
  end;
  
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Inaccessible_Forest', sum(included), round(sum(included)/64106.430,2),sum(thlb_net) 
	from tsa16_netdown2022
	where n12_inaccessible is not null;	

update tsa16_netdown2022 set thlb_net = 0 where n12_inaccessible is not null;

\echo --------------------------------------
\echo add retention-------------
\echo --------------------------------------

update tsa16_netdown2022 set p13_retention = case 
  	when thlb_net > 0 then 0.913
	end;
  
insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Retention', sum(included*0.087),
	round(sum(included *0.087)/64106.430,2), sum(thlb_net *0.087) 
	from tsa16_netdown2022;

update tsa16_netdown2022 set thlb_net = thlb_net*p13_retention ;

vacuum tsa16_netdown2022;
analyze verbose tsa16_netdown2022;

\echo ---------------------------------------
\echo calculate THLB
\echo The area of CFLB was calculated by multiplying the netdown factors. Complete removals were evaluated as a value of zero 
\echo when a netdown label was present (the 'is null' boolean returns 'FALSE' and is then cast to the integer zero).
\echo --------------------------------------

update tsa16_netdown2022 set
  thlb_fact = 
   	(n04_park is null)::int *
		(n05_uwr is null)::int *
		(n06_wha is null)::int  *
		(n07_ogma is null)::int *
		(n08_rmp is null)::int *
		(n09_ch is null)::int *
		(n10_inoperable is null)::int *
		(n11_nonmerchantable is null)::int*
		(n12_inaccessible is null)::int*
		p13_retention*
		p03_lineal_features;
		

insert into tsa16_netdown_summary2022 (landclass, total, percent, excluded)
	select 'Timber harvesting land base', sum(thlb_net), round(sum(thlb_net)/64106.430,2), NULL 
	from tsa16_netdown2022;
```


