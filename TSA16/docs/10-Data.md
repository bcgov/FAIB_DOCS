



# Data

The resultant datasets from the Mackenzie TSR were assembled using [PostgreSQL](https://www.postgresql.org/) and archived as as series of [pg_dump files](https://www.postgresql.org/docs/current/app-pgdump.html) located on the MOF [FTP server](https://www.for.gov.bc.ca/ftp/HTS/external/!publish/Timber_Supply_Review/TSA/Mackenzie_16/TSR_2019/resultant/).

The following details each of the postgres tables that form the resutant dataset

## Unique Identifiers and Geometry

The tsa16_skey.sql.7z file contains the tsa16_skey which has been extracted from the bc_gr_skey. The bc_gr_skey is a one hectare int32 GEOTIFF raster of the entire province buffered by 100 km. The dimensions of the tsa16_skey are based on the extents (bounding box) of the TSA boundary with postive skey values within the boundary and negative skey values external to the boundary. The tsa16_skey containts the ogc_fid which provides a unique identifier for every hectare within the extents of the TSA. The ogc_fid is the primary/foriegn key for all tables in the resultant suite.

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table27) tsa16_skey</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> field </th>
   <th style="text-align:left;"> type </th>
   <th style="text-align:left;"> description </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> skey </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> provincial unique identifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ogc_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> gdal unique identifier: foreign key </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wkb_geometry </td>
   <td style="text-align:left;"> geometry </td>
   <td style="text-align:left;"> grided geometry at 1 ha resoltion </td>
  </tr>
</tbody>
</table>

## Netdown Table

The tsa16_netdown2022.7z contains the tsa16_netdown table which provides a classification label, proportion AFLB and proportion THLB for every hectare in the TSA. It identifies all spatial layers used in the construction of the timber harvesting landbase (for the full netdown script see Chapter \@ref(netdown).)

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table28) tsa16_netdown2022</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> field </th>
   <th style="text-align:left;"> type </th>
   <th style="text-align:left;"> description </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> ogc_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> gdal unique identifier: foreign key </td>
  </tr>
  <tr>
   <td style="text-align:left;"> own_lbl </td>
   <td style="text-align:left;"> character varying </td>
   <td style="text-align:left;"> ownership label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> description </td>
   <td style="text-align:left;"> character varying </td>
   <td style="text-align:left;"> ownership description </td>
  </tr>
  <tr>
   <td style="text-align:left;"> forest_fil </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> N2T </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mus_labl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Muskwa-Kechika </td>
  </tr>
  <tr>
   <td style="text-align:left;"> new_lbl </td>
   <td style="text-align:left;"> character varying </td>
   <td style="text-align:left;"> updated ownership label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> feature_id from VRI (ar2018_inc table) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bclcs_lv_1 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> bc land classification level 1 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bclcs_lv_2 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> bc land classification level 2 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bclcs_lv_3 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> bc land classification level 3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bclcs_lv_4 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> bc land classification level 4 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bclcs_lv_5 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> bc land classification level 5 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wetland_type </td>
   <td style="text-align:left;"> character varying(1) </td>
   <td style="text-align:left;"> wetlands from FWA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> site_index </td>
   <td style="text-align:left;"> real </td>
   <td style="text-align:left;"> VRI Site Index </td>
  </tr>
  <tr>
   <td style="text-align:left;"> spec_cd_1 </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> VRI Leading Species </td>
  </tr>
  <tr>
   <td style="text-align:left;"> np_desc </td>
   <td style="text-align:left;"> character varying(5) </td>
   <td style="text-align:left;"> non=productive description </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cutblocks2019_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2019 consolidated cutblocks harvest year </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cc_harvest_year </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2020 consolidated cutblocks feature id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lu_name </td>
   <td style="text-align:left;"> character varying(80) </td>
   <td style="text-align:left;"> Landscape Unit Label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bgc_label </td>
   <td style="text-align:left;"> character varying(27) </td>
   <td style="text-align:left;"> BEC Label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ogma_provid </td>
   <td style="text-align:left;"> character varying(20) </td>
   <td style="text-align:left;"> OGMA Label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rmp_l_name </td>
   <td style="text-align:left;"> character varying(100) </td>
   <td style="text-align:left;"> Resource Management Plan Label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_no_harv_code </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> UWR no harvest flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wha_no_harv_code </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> WHA no harvest flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fisher_no_harv </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Fisher no harvest flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> dmk_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Wolverine Herd Unit Numbers </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unit_type </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Moose Core </td>
  </tr>
  <tr>
   <td style="text-align:left;"> arch_grid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Archeological site </td>
  </tr>
  <tr>
   <td style="text-align:left;"> area_lineal </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> lineal feature proportion (roads etc) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> slope </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Slope % </td>
  </tr>
  <tr>
   <td style="text-align:left;"> elevation </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Elevation (m) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ctime </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Modeled cycletime (spatial index) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> instability </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> terrain stability mapping </td>
  </tr>
  <tr>
   <td style="text-align:left;"> econ_neighborhood </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> economic neighborhood adjustment for operability </td>
  </tr>
  <tr>
   <td style="text-align:left;"> patch_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> operable patch id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> size </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> operable patch size </td>
  </tr>
  <tr>
   <td style="text-align:left;"> nndist </td>
   <td style="text-align:left;"> real </td>
   <td style="text-align:left;"> operable patch nearest neighbor distance </td>
  </tr>
  <tr>
   <td style="text-align:left;"> isolated </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> isolated area flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> max_vol2020 </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> maximium volume per ha </td>
  </tr>
  <tr>
   <td style="text-align:left;"> isolation_mask_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> isolated area adjustment </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wolv0315_no_harv </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Wolverine Herd No Harvest Flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> included </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> TSA Boundary flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cflb_fact </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> CFLB inclusion factor (* 10000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> thlb_fact </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> THLB inclusion factor (*10000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> thlb_net </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> THLB inclusion factor </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n01_ownership </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> ownership exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n02_nonfor </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> non-productive forest exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> p03_lineal_features </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> lineal feature exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n04_park </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> park exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n05_uwr </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> UWR exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n06_wha </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> WHA exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n07_ogma </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> OGMA exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n08_rmp </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Resource Management Plan exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n09_ch </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Cultural Heritage exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n10_inoperable </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Operability exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n11_nonmerchantable </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Merchantibility exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n12_inaccessible </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Accessibility exclusion flag </td>
  </tr>
  <tr>
   <td style="text-align:left;"> p13_retention </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> Retention exclusion flag </td>
  </tr>
</tbody>
</table>

## Transitions/Volumes/Landbase

The tsa16_cur_trans230206.7z file contains the resultant landbase proportion (AFLB/THLB) along with the unique analysis unit identifier and corresponding transition unit number, various model parameters along with current total volume, green and dead volumes per hectare for each hectare in the TSA. The yield table (tsa16_yield_curves221205.7z) joins the transition table on the corresponding au fields.

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table29) tsa16_transitions (auinfo table)</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> field </th>
   <th style="text-align:left;"> type </th>
   <th style="text-align:left;"> description </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> ogc_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> gdal unique identifier: foreign key </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cur_au2021sp </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> current analysis unit id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> au </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> current analysis unit id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> auid </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> current analysis unit id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> regen_delay </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> regeneration delay value </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mha </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> minimum harvest volume threshold </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mhv </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> minimum harvest age threshold </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cmaiage </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> culmination age threshold (not used) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaf1 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> operational adjustment factor to yield </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaf2 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> incremental operational adjustment factor to yield (value at yr100) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> standtype </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> stand type label (old, thrifty, managed) for reporting </td>
  </tr>
  <tr>
   <td style="text-align:left;"> leadspp1 </td>
   <td style="text-align:left;"> text </td>
   <td style="text-align:left;"> Leading species label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> pplantedau1 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> Proportion planted </td>
  </tr>
  <tr>
   <td style="text-align:left;"> plantedau1 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> transition analysis unit 1 (planted) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> plantedau2 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> transtion analysis unit 2 (natural) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unmanagedau </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> NYST analysis unit for transition post natural disturbance </td>
  </tr>
  <tr>
   <td style="text-align:left;"> pctpriority </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> priority proportion for reporting (managed pine proportion) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> feature id from VRI </td>
  </tr>
  <tr>
   <td style="text-align:left;"> aflb_net </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> 2022 AFLB inclusion factor </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cur_vph </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> current volume per ha (unadjusted for Sx/Ba mortality) *100 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cur_tvph </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> current volume per ha (adjusted for Sx/Ba mortality) *100 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> dead_vol </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> total dead volume (Pl/Sx/Ba)*100 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> thlb_net </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> 2022 THLB inclusion factor </td>
  </tr>
</tbody>
</table>

## Analysis Ready Dataset

The tsa16_ar_table.sql.7z contains the 2021 vri and standard layers that make-up the FAIB analysis ready dataset produced annually for every TSA in the Province.The Analysis Ready datasets are pre-compiled base data used as the analytical starting point for all Timber Supply Reviews.

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table30) tsa16_ar2021</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> dataset </th>
   <th style="text-align:left;"> SrcFeatureClass </th>
   <th style="text-align:left;"> fieldName </th>
   <th style="text-align:left;"> wrkFeatureClass </th>
   <th style="text-align:left;"> longName </th>
   <th style="text-align:left;"> wrkName </th>
   <th style="text-align:left;"> IsNullable </th>
   <th style="text-align:left;"> Editable </th>
   <th style="text-align:left;"> Required </th>
   <th style="text-align:right;"> Length </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:right;"> Precision </th>
   <th style="text-align:right;"> Scale </th>
   <th style="text-align:left;"> Domain </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> ZONE </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> zone </td>
   <td style="text-align:left;"> bec_zone </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 12 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> SUBZONE </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> subzone </td>
   <td style="text-align:left;"> bec_subzone </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> VARIANT </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> variant </td>
   <td style="text-align:left;"> bec_variant </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> PHASE </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> phase </td>
   <td style="text-align:left;"> bec_phase </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> NATURAL_DISTURBANCE </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> natural_disturbance </td>
   <td style="text-align:left;"> bec_ndt </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 12 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> BEC_BIOGEOCLIMATIC_POLY </td>
   <td style="text-align:left;"> BGC_LABEL </td>
   <td style="text-align:left;"> bec </td>
   <td style="text-align:left;"> bgc_label </td>
   <td style="text-align:left;"> bgc_label </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 27 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> F_OWN </td>
   <td style="text-align:left;"> OWN </td>
   <td style="text-align:left;"> own </td>
   <td style="text-align:left;"> own </td>
   <td style="text-align:left;"> f_own_code </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> F_OWN </td>
   <td style="text-align:left;"> SCHEDULE </td>
   <td style="text-align:left;"> own </td>
   <td style="text-align:left;"> schedule </td>
   <td style="text-align:left;"> f_own_schedule </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> F_OWN </td>
   <td style="text-align:left;"> OWNERSHIP_DESCRIPTION </td>
   <td style="text-align:left;"> own </td>
   <td style="text-align:left;"> f_own_desc </td>
   <td style="text-align:left;"> f_own_desc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 100 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FADM_DESIGNATED_AREAS </td>
   <td style="text-align:left;"> DESIGNATED_AREA_NAME </td>
   <td style="text-align:left;"> desig_area </td>
   <td style="text-align:left;"> designated_area_name </td>
   <td style="text-align:left;"> desig_area_name </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FADM_DESIGNATED_AREAS </td>
   <td style="text-align:left;"> DESIGNATED_AREA_TYPE </td>
   <td style="text-align:left;"> desig_area </td>
   <td style="text-align:left;"> designated_area_type </td>
   <td style="text-align:left;"> desig_area_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FADM_TSA </td>
   <td style="text-align:left;"> TSA_NUMBER </td>
   <td style="text-align:left;"> tsa </td>
   <td style="text-align:left;"> tsa_number </td>
   <td style="text-align:left;"> tsa_number </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FADM_TSA </td>
   <td style="text-align:left;"> TSB_NUMBER </td>
   <td style="text-align:left;"> tsa </td>
   <td style="text-align:left;"> tsb_number </td>
   <td style="text-align:left;"> tsb_number </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FTEN_RECREATION_POLY_SVW </td>
   <td style="text-align:left;"> PROJECT_TYPE </td>
   <td style="text-align:left;"> rec </td>
   <td style="text-align:left;"> project_type </td>
   <td style="text-align:left;"> rec_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FTEN_RECREATION_POLY_SVW </td>
   <td style="text-align:left;"> RETIREMENT_DATE </td>
   <td style="text-align:left;"> rec </td>
   <td style="text-align:left;"> retirement_date </td>
   <td style="text-align:left;"> rec_retire </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FTEN_RECREATION_POLY_SVW </td>
   <td style="text-align:left;"> LIFE_CYCLE_STATUS_CODE </td>
   <td style="text-align:left;"> rec </td>
   <td style="text-align:left;"> life_cycle_status_code </td>
   <td style="text-align:left;"> rec_status </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FWA_ASSESSMENT_WATERSHEDS_POLY </td>
   <td style="text-align:left;"> WATERSHED_FEATURE_ID </td>
   <td style="text-align:left;"> fwa_aws </td>
   <td style="text-align:left;"> watershed_feature_id </td>
   <td style="text-align:left;"> fwa_id </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FWA_ASSESSMENT_WATERSHEDS_POLY </td>
   <td style="text-align:left;"> WATERSHED_TYPE </td>
   <td style="text-align:left;"> fwa_aws </td>
   <td style="text-align:left;"> watershed_type </td>
   <td style="text-align:left;"> fwa_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FWA_ASSESSMENT_WATERSHEDS_POLY </td>
   <td style="text-align:left;"> WATERSHED_ORDER </td>
   <td style="text-align:left;"> fwa_aws </td>
   <td style="text-align:left;"> watershed_order </td>
   <td style="text-align:left;"> fwa_order </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FWA_WETLANDS_POLY </td>
   <td style="text-align:left;"> WATERBODY_POLY_ID </td>
   <td style="text-align:left;"> fwa_wetlands </td>
   <td style="text-align:left;"> waterbody_poly_id </td>
   <td style="text-align:left;"> wetland_id </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> FWA_WETLANDS_POLY </td>
   <td style="text-align:left;"> WATERBODY_TYPE </td>
   <td style="text-align:left;"> fwa_wetlands </td>
   <td style="text-align:left;"> waterbody_type </td>
   <td style="text-align:left;"> wetland_type </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> gry_psp_status_active </td>
   <td style="text-align:left;"> SAMPLE_REFERENCE_NUMBER </td>
   <td style="text-align:left;"> psps </td>
   <td style="text-align:left;"> psp_ref_num </td>
   <td style="text-align:left;"> psp_ref_num </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> gry_psp_status_active </td>
   <td style="text-align:left;"> ESTABLISHMENT_YEAR </td>
   <td style="text-align:left;"> psps </td>
   <td style="text-align:left;"> psp_estab_year </td>
   <td style="text-align:left;"> psp_estab_year </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Short </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> gry_psp_status_active </td>
   <td style="text-align:left;"> ACTIVE_INDICATOR </td>
   <td style="text-align:left;"> psps </td>
   <td style="text-align:left;"> psp_active_ind </td>
   <td style="text-align:left;"> psp_active_ind </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> MTA_SITE_SP </td>
   <td style="text-align:left;"> MTA_SITE_ORDER_RESTR_CODE </td>
   <td style="text-align:left;"> mta </td>
   <td style="text-align:left;"> mta_site_order_restr_code </td>
   <td style="text-align:left;"> mta_restr_code </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> MTA_SITE_SP </td>
   <td style="text-align:left;"> MTA_SITE_REASON_CODE </td>
   <td style="text-align:left;"> mta </td>
   <td style="text-align:left;"> mta_site_reason_code </td>
   <td style="text-align:left;"> mta_reason </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> PROT_HISTORICAL_FIRE_POLYS_SP </td>
   <td style="text-align:left;"> FIRE_YEAR </td>
   <td style="text-align:left;"> hist_fires </td>
   <td style="text-align:left;"> fire_year </td>
   <td style="text-align:left;"> fire_year </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Short </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> VLI_POLYGON_NO </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> vli_polygon_no </td>
   <td style="text-align:left;"> vli_poly </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> VSU_NUMBER </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> vsu_number </td>
   <td style="text-align:left;"> vli_vsu_number </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_MADE_KNOWN_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_made_known_code </td>
   <td style="text-align:left;"> vli_made_known </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_EVC_FINAL_VALUE_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_evc_final_value_code </td>
   <td style="text-align:left;"> vli_evc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_VC_FINAL_VALUE_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_vc_final_value_code </td>
   <td style="text-align:left;"> vli_vc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_VAC_FINAL_VALUE_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_vac_final_value_code </td>
   <td style="text-align:left;"> vli_vac </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> VLI_POLYGON_ID </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> vli_polygon_id </td>
   <td style="text-align:left;"> vli_id </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_RVQC_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_rvqc_code </td>
   <td style="text-align:left;"> vli_rvqc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> REC_VISUAL_LANDSCAPE_INVENTORY </td>
   <td style="text-align:left;"> REC_EVQO_CODE </td>
   <td style="text-align:left;"> vli </td>
   <td style="text-align:left;"> rec_evqo_code </td>
   <td style="text-align:left;"> vli_evqo </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RESPROJ_RSRCH_INSTLTNS_GOV_SVW </td>
   <td style="text-align:left;"> STUDY_SITE </td>
   <td style="text-align:left;"> rsrch_intstl </td>
   <td style="text-align:left;"> rsrch_inst_study_site </td>
   <td style="text-align:left;"> rsrch_study_site </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RESPROJ_RSRCH_INSTLTNS_GOV_SVW </td>
   <td style="text-align:left;"> RESEARCH_INST_STATUS_DESC </td>
   <td style="text-align:left;"> rsrch_intstl </td>
   <td style="text-align:left;"> rsrch_inst_status </td>
   <td style="text-align:left;"> rsrch_inst_status </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_LANDSCAPE_UNIT_SVW_NO_MULTIPLES </td>
   <td style="text-align:left;"> LANDSCAPE_UNIT_ID </td>
   <td style="text-align:left;"> lu </td>
   <td style="text-align:left;"> landscape_unit_id </td>
   <td style="text-align:left;"> lu_unit_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_LANDSCAPE_UNIT_SVW_NO_MULTIPLES </td>
   <td style="text-align:left;"> LANDSCAPE_UNIT_PROVID </td>
   <td style="text-align:left;"> lu </td>
   <td style="text-align:left;"> landscape_unit_provid </td>
   <td style="text-align:left;"> lu_provid </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_LANDSCAPE_UNIT_SVW_NO_MULTIPLES </td>
   <td style="text-align:left;"> LANDSCAPE_UNIT_NAME </td>
   <td style="text-align:left;"> lu </td>
   <td style="text-align:left;"> landscape_unit_name </td>
   <td style="text-align:left;"> lu_name </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_LANDSCAPE_UNIT_SVW_NO_MULTIPLES </td>
   <td style="text-align:left;"> BIODIVERSITY_EMPHASIS_OPTION </td>
   <td style="text-align:left;"> lu </td>
   <td style="text-align:left;"> biodiversity_emphasis_option </td>
   <td style="text-align:left;"> lu_beo </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_OGMA_LEGAL_CURRENT_SVW </td>
   <td style="text-align:left;"> LEGAL_OGMA_PROVID </td>
   <td style="text-align:left;"> ogma </td>
   <td style="text-align:left;"> legal_ogma_provid </td>
   <td style="text-align:left;"> ogma_provid </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_OGMA_LEGAL_CURRENT_SVW </td>
   <td style="text-align:left;"> OGMA_TYPE </td>
   <td style="text-align:left;"> ogma </td>
   <td style="text-align:left;"> ogma_type </td>
   <td style="text-align:left;"> ogma_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_OGMA_NON_LEGAL_CURRENT_SVW </td>
   <td style="text-align:left;"> NON_LEGAL_OGMA_PROVID </td>
   <td style="text-align:left;"> ogma_nl </td>
   <td style="text-align:left;"> non_legal_ogma_provid </td>
   <td style="text-align:left;"> ogma_nl_provid </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_OGMA_NON_LEGAL_CURRENT_SVW </td>
   <td style="text-align:left;"> OGMA_TYPE </td>
   <td style="text-align:left;"> ogma_nl </td>
   <td style="text-align:left;"> ogma_type </td>
   <td style="text-align:left;"> ogma_nl_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_PLAN_LEGAL_POLY_SVW </td>
   <td style="text-align:left;"> STRGC_LAND_RSRCE_PLAN_NAME </td>
   <td style="text-align:left;"> rmp_legal </td>
   <td style="text-align:left;"> strgc_land_rsrce_plan_name </td>
   <td style="text-align:left;"> rmp_l_name </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_PLAN_LEGAL_POLY_SVW </td>
   <td style="text-align:left;"> LEGAL_FEAT_OBJECTIVE </td>
   <td style="text-align:left;"> rmp_legal </td>
   <td style="text-align:left;"> legal_feat_objective </td>
   <td style="text-align:left;"> rmp_l_obj </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_PLAN_NON_LEGAL_POLY_SVW </td>
   <td style="text-align:left;"> STRGC_LAND_RSRCE_PLAN_NAME </td>
   <td style="text-align:left;"> rmp_nonlegal </td>
   <td style="text-align:left;"> strgc_land_rsrce_plan_name </td>
   <td style="text-align:left;"> rmp_nl_name </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_PLAN_NON_LEGAL_POLY_SVW </td>
   <td style="text-align:left;"> NON_LEGAL_FEAT_OBJECTIVE </td>
   <td style="text-align:left;"> rmp_nonlegal </td>
   <td style="text-align:left;"> non_legal_feat_objective </td>
   <td style="text-align:left;"> rmp_nl_obj </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_STRGC_LAND_RSRCE_PLAN_SVW </td>
   <td style="text-align:left;"> STRGC_LAND_RSRCE_PLAN_PROVID </td>
   <td style="text-align:left;"> rmp_slrp </td>
   <td style="text-align:left;"> strgc_land_rsrce_plan_provid </td>
   <td style="text-align:left;"> rmp_strgc_provid </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_STRGC_LAND_RSRCE_PLAN_SVW </td>
   <td style="text-align:left;"> STRGC_LAND_RSRCE_PLAN_NAME </td>
   <td style="text-align:left;"> rmp_slrp </td>
   <td style="text-align:left;"> strgc_land_rsrce_plan_name </td>
   <td style="text-align:left;"> rmp_strgc_name </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 100 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_STRGC_LAND_RSRCE_PLAN_SVW </td>
   <td style="text-align:left;"> PLAN_TYPE </td>
   <td style="text-align:left;"> rmp_slrp </td>
   <td style="text-align:left;"> plan_type </td>
   <td style="text-align:left;"> rmp_strgc_type </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> RMP_STRGC_LAND_RSRCE_PLAN_SVW </td>
   <td style="text-align:left;"> PLAN_STATUS </td>
   <td style="text-align:left;"> rmp_slrp </td>
   <td style="text-align:left;"> plan_status </td>
   <td style="text-align:left;"> rmp_strgc_status </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> STE_TER_STABILITY_POLYS_SVW </td>
   <td style="text-align:left;"> SLOPE_STABILITY_CLASS_TXT </td>
   <td style="text-align:left;"> tsp </td>
   <td style="text-align:left;"> slope_stability_class_txt </td>
   <td style="text-align:left;"> slp_stab_cls </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> STE_TER_STABILITY_POLYS_SVW </td>
   <td style="text-align:left;"> SURFACE_EROSION_POT_CLASS_TXT </td>
   <td style="text-align:left;"> tsp </td>
   <td style="text-align:left;"> surface_erosion_pot_class_txt </td>
   <td style="text-align:left;"> surf_erosion_pot_cls </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> TA_WILDLIFE_MGMT_AREAS_SVW </td>
   <td style="text-align:left;"> WILDLIFE_MANAGEMENT_AREA_NAME </td>
   <td style="text-align:left;"> wma </td>
   <td style="text-align:left;"> wildlife_management_area_name </td>
   <td style="text-align:left;"> wma_name </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> thlb_2021 </td>
   <td style="text-align:left;"> thlb_fact </td>
   <td style="text-align:left;"> thlb </td>
   <td style="text-align:left;"> thlb_fact </td>
   <td style="text-align:left;"> thlb_fact </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> thlb_2021 </td>
   <td style="text-align:left;"> cfmlb_fact </td>
   <td style="text-align:left;"> thlb </td>
   <td style="text-align:left;"> cfmlb_fact </td>
   <td style="text-align:left;"> cfmlb_fact </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> map_id </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> map_id </td>
   <td style="text-align:left;"> map_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> polygon_id </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> polygon_id </td>
   <td style="text-align:left;"> poly_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> alpine_designation </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> alpine_designation </td>
   <td style="text-align:left;"> alpn_desig </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BASAL_AREA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> basal_area </td>
   <td style="text-align:left;"> basal_area </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BCLCS_LEVEL_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bclcs_level_1 </td>
   <td style="text-align:left;"> bclcs_lv_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BCLCS_LEVEL_2 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bclcs_level_2 </td>
   <td style="text-align:left;"> bclcs_lv_2 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BCLCS_LEVEL_3 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bclcs_level_3 </td>
   <td style="text-align:left;"> bclcs_lv_3 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BCLCS_LEVEL_4 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bclcs_level_4 </td>
   <td style="text-align:left;"> bclcs_lv_4 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BCLCS_LEVEL_5 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bclcs_level_5 </td>
   <td style="text-align:left;"> bclcs_lv_5 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> COAST_INTERIOR_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> coast_interior_cd </td>
   <td style="text-align:left;"> c_i_code </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> CROWN_CLOSURE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> crown_closure </td>
   <td style="text-align:left;"> cr_closure </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_STAND_VOLUME_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_stand_volume_125 </td>
   <td style="text-align:left;"> dvltot_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_STAND_VOLUME_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_stand_volume_175 </td>
   <td style="text-align:left;"> dvltot_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP1_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp1_125 </td>
   <td style="text-align:left;"> dvlsp1_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP1_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp1_175 </td>
   <td style="text-align:left;"> dvlsp1_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP2_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp2_125 </td>
   <td style="text-align:left;"> dvlsp2_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP2_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp2_175 </td>
   <td style="text-align:left;"> dvlsp2_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP3_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp3_125 </td>
   <td style="text-align:left;"> dvlsp3_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP3_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp3_175 </td>
   <td style="text-align:left;"> dvlsp3_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP4_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp4_125 </td>
   <td style="text-align:left;"> dvlsp4_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP4_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp4_175 </td>
   <td style="text-align:left;"> dvlsp4_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP5_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp5_125 </td>
   <td style="text-align:left;"> dvlsp5_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP5_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp5_175 </td>
   <td style="text-align:left;"> dvlsp5_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP6_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp6_125 </td>
   <td style="text-align:left;"> dvlsp6_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> DEAD_VOL_PER_HA_SPP6_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> dead_vol_per_ha_spp6_175 </td>
   <td style="text-align:left;"> dvlsp6_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> EARLIEST_NONLOGGING_DIST_DATE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> earliest_nonlogging_dist_date </td>
   <td style="text-align:left;"> n_log_date </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> earliest_nonlogging_dist_type </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> earliest_nonlogging_dist_type </td>
   <td style="text-align:left;"> n_log_dist </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> EST_SITE_INDEX </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> est_site_index </td>
   <td style="text-align:left;"> est_si </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> EST_SITE_INDEX_SPECIES_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> est_site_index_species_cd </td>
   <td style="text-align:left;"> est_si_spc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> FIZ_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> fiz_cd </td>
   <td style="text-align:left;"> fiz_cd </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> FOR_COVER_RANK_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> for_cover_rank_cd </td>
   <td style="text-align:left;"> rank_cd </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> FOR_MGMT_LAND_BASE_IND </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> for_mgmt_land_base_ind </td>
   <td style="text-align:left;"> fmlb </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> free_to_grow_ind </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> free_to_grow_ind </td>
   <td style="text-align:left;"> ftg_ind </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> HARVEST_DATE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> harvest_date </td>
   <td style="text-align:left;"> hrvstdt </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> INPUT_DATE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> input_date </td>
   <td style="text-align:left;"> input_date </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> INTERPRETATION_DATE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> interpretation_date </td>
   <td style="text-align:left;"> intrp_date </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> INTERPRETED_DATA_SRC_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> interpreted_data_src_cd </td>
   <td style="text-align:left;"> interp_cd </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> INVENTORY_STANDARD_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> inventory_standard_cd </td>
   <td style="text-align:left;"> inv_std_cd </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LAND_COVER_CLASS_CD_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> land_cover_class_cd_1 </td>
   <td style="text-align:left;"> land_cd_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LAND_COVER_CLASS_CD_2 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> land_cover_class_cd_2 </td>
   <td style="text-align:left;"> land_cd_2 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LAND_COVER_CLASS_CD_3 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> land_cover_class_cd_3 </td>
   <td style="text-align:left;"> land_cd_3 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LAYER_ID </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> layer_id </td>
   <td style="text-align:left;"> layer_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_STAND_VOLUME_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_stand_volume_125 </td>
   <td style="text-align:left;"> lvltot_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_STAND_VOLUME_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_stand_volume_175 </td>
   <td style="text-align:left;"> lvltot_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP1_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp1_125 </td>
   <td style="text-align:left;"> lvlsp1_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP1_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp1_175 </td>
   <td style="text-align:left;"> lvlsp1_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP2_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp2_125 </td>
   <td style="text-align:left;"> lvlsp2_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP2_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp2_175 </td>
   <td style="text-align:left;"> lvlsp2_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP3_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp3_125 </td>
   <td style="text-align:left;"> lvlsp3_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP3_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp3_175 </td>
   <td style="text-align:left;"> lvlsp3_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP4_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp4_125 </td>
   <td style="text-align:left;"> lvlsp4_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP4_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp4_175 </td>
   <td style="text-align:left;"> lvlsp4_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP5_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp5_125 </td>
   <td style="text-align:left;"> lvlsp5_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP5_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp5_175 </td>
   <td style="text-align:left;"> lvlsp5_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP6_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp6_125 </td>
   <td style="text-align:left;"> lvlsp6_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> LIVE_VOL_PER_HA_SPP6_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> live_vol_per_ha_spp6_175 </td>
   <td style="text-align:left;"> lvlsp6_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_FOREST_DESCRIPTOR </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_forest_descriptor </td>
   <td style="text-align:left;"> nfor_desc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_PRODUCTIVE_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_productive_cd </td>
   <td style="text-align:left;"> np_code </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_PRODUCTIVE_DESCRIPTOR_CD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_productive_descriptor_cd </td>
   <td style="text-align:left;"> np_desc </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_VEG_COVER_PCT_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_veg_cover_pct_1 </td>
   <td style="text-align:left;"> cov_pct_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_VEG_COVER_PCT_2 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_veg_cover_pct_2 </td>
   <td style="text-align:left;"> cov_pct_2 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> NON_VEG_COVER_PCT_3 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> non_veg_cover_pct_3 </td>
   <td style="text-align:left;"> cov_pct_3 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> OPENING_ID </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> opening_id </td>
   <td style="text-align:left;"> open_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> OPENING_NUMBER </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> opening_number </td>
   <td style="text-align:left;"> open_num </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> org_unit_code </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> org_unit_code </td>
   <td style="text-align:left;"> orgunit_cd </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> org_unit_no </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> org_unit_no </td>
   <td style="text-align:left;"> orgunit_no </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJ_AGE_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> proj_age_1 </td>
   <td style="text-align:left;"> proj_age_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJ_AGE_CLASS_CD_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> p_age_cs_1 </td>
   <td style="text-align:left;"> p_age_cs_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJ_HEIGHT_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> proj_height_1 </td>
   <td style="text-align:left;"> proj_ht_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJ_HEIGHT_CLASS_CD_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> p_ht_cas_1 </td>
   <td style="text-align:left;"> p_ht_cas_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJECT </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> project </td>
   <td style="text-align:left;"> project_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 100 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> PROJECTED_DATE </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> projected_date </td>
   <td style="text-align:left;"> proj_date </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Date </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> QUAD_DIAM_125 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> quad_diam_125 </td>
   <td style="text-align:left;"> q_diam_125 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> QUAD_DIAM_175 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> quad_diam_225 </td>
   <td style="text-align:left;"> q_diam_175 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> REFERENCE_YEAR </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> reference_year </td>
   <td style="text-align:left;"> ref_year </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SITE_INDEX </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> site_index </td>
   <td style="text-align:left;"> site_index </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_1 </td>
   <td style="text-align:left;"> spec_cd_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_2 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_2 </td>
   <td style="text-align:left;"> spec_cd_2 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_3 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_3 </td>
   <td style="text-align:left;"> spec_cd_3 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_4 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_4 </td>
   <td style="text-align:left;"> spec_cd_4 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_5 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_5 </td>
   <td style="text-align:left;"> spec_cd_5 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_CD_6 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_cd_6 </td>
   <td style="text-align:left;"> spec_cd_6 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_1 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_1 </td>
   <td style="text-align:left;"> spec_pct_1 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_2 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_2 </td>
   <td style="text-align:left;"> spec_pct_2 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_3 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_3 </td>
   <td style="text-align:left;"> spec_pct_3 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_4 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_4 </td>
   <td style="text-align:left;"> spec_pct_4 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_5 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_5 </td>
   <td style="text-align:left;"> spec_pct_5 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> SPECIES_PCT_6 </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> species_pct_6 </td>
   <td style="text-align:left;"> spec_pct_6 </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Single </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> STAND_PERCENTAGE_DEAD </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> stand_percentage_dead </td>
   <td style="text-align:left;"> dead_pct </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> SmallInteger </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> VRI_DEAD_STEMS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> vri_dead_stems_per_ha </td>
   <td style="text-align:left;"> dead_stems </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> VRI_LIVE_STEMS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> vri_live_stems_per_ha </td>
   <td style="text-align:left;"> live_stems </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> WHOLE_STEM_BIOMASS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> whole_stem_biomass_per_ha </td>
   <td style="text-align:left;"> wstem_biom </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BARK_BIOMASS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> bark_biomass_per_ha </td>
   <td style="text-align:left;"> bark_biom </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> FOLIAGE_BIOMASS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> foliage_biomass_per_ha </td>
   <td style="text-align:left;"> folg_biom </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_COMP_LYR_R1_POLY </td>
   <td style="text-align:left;"> BRANCH_BIOMASS_PER_HA </td>
   <td style="text-align:left;"> vri </td>
   <td style="text-align:left;"> branch_biomass_per_ha </td>
   <td style="text-align:left;"> branch_biom </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> Double </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_CONSOLIDATED_CUT_BLOCKS_SP </td>
   <td style="text-align:left;"> OPENING_ID </td>
   <td style="text-align:left;"> cutblocks </td>
   <td style="text-align:left;"> cc_opening_id </td>
   <td style="text-align:left;"> cc_opening_id </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> Long </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_CONSOLIDATED_CUT_BLOCKS_SP </td>
   <td style="text-align:left;"> HARVEST_YEAR </td>
   <td style="text-align:left;"> cutblocks </td>
   <td style="text-align:left;"> cc_harvest_year </td>
   <td style="text-align:left;"> cc_harvest_year </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> VEG_CONSOLIDATED_CUT_BLOCKS_SP </td>
   <td style="text-align:left;"> DATA_SOURCE </td>
   <td style="text-align:left;"> cutblocks </td>
   <td style="text-align:left;"> cc_data_source </td>
   <td style="text-align:left;"> cc_data_source </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCL_CONSERVATION_LANDS_SP </td>
   <td style="text-align:left;"> CONSERVATION_LAND_TYPE </td>
   <td style="text-align:left;"> pvt_cnsrv_land </td>
   <td style="text-align:left;"> conservation_land_type </td>
   <td style="text-align:left;"> cnsrv_land_type </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 200 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_FISH_SENSITIVE_WS_POLY </td>
   <td style="text-align:left;"> FISH_SENSITIVE_WS_POLY_ID </td>
   <td style="text-align:left;"> fsws </td>
   <td style="text-align:left;"> fish_sensitive_ws_poly_id </td>
   <td style="text-align:left;"> fsw_polyid </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> Integer </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_FISH_SENSITIVE_WS_POLY </td>
   <td style="text-align:left;"> FSW_TAG </td>
   <td style="text-align:left;"> fsws </td>
   <td style="text-align:left;"> fsw_tag </td>
   <td style="text-align:left;"> fsw_tag </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_UNGULATE_WINTER_RANGE_SP_CONDITIONAL_HARVEST </td>
   <td style="text-align:left;"> UWR_NUMBER </td>
   <td style="text-align:left;"> uwr_cond </td>
   <td style="text-align:left;"> uwr_cond_harv_number </td>
   <td style="text-align:left;"> uwr_cond_harv_number </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_UNGULATE_WINTER_RANGE_SP_CONDITIONAL_HARVEST </td>
   <td style="text-align:left;"> TIMBER_HARVEST_CODE </td>
   <td style="text-align:left;"> uwr_cond </td>
   <td style="text-align:left;"> uwr_cond_harv_timber </td>
   <td style="text-align:left;"> uwr_cond_harv_timber </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_UNGULATE_WINTER_RANGE_SP_NO_HARVEST </td>
   <td style="text-align:left;"> UWR_NUMBER </td>
   <td style="text-align:left;"> uwr_nh </td>
   <td style="text-align:left;"> uwr_no_harv_number </td>
   <td style="text-align:left;"> uwr_no_harv_number </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_UNGULATE_WINTER_RANGE_SP_NO_HARVEST </td>
   <td style="text-align:left;"> TIMBER_HARVEST_CODE </td>
   <td style="text-align:left;"> uwr_nh </td>
   <td style="text-align:left;"> uwr_no_harv_timber </td>
   <td style="text-align:left;"> uwr_no_harv_timber </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_WILDLIFE_HABITAT_AREA_POLY </td>
   <td style="text-align:left;"> TAG </td>
   <td style="text-align:left;"> wha </td>
   <td style="text-align:left;"> tag </td>
   <td style="text-align:left;"> wha_tag </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_WILDLIFE_HABITAT_AREA_POLY </td>
   <td style="text-align:left;"> COMMON_SPECIES_NAME </td>
   <td style="text-align:left;"> wha </td>
   <td style="text-align:left;"> common_species_name </td>
   <td style="text-align:left;"> wha_species </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WCP_WILDLIFE_HABITAT_AREA_POLY </td>
   <td style="text-align:left;"> TIMBER_HARVEST_CODE </td>
   <td style="text-align:left;"> wha </td>
   <td style="text-align:left;"> timber_harvest_code </td>
   <td style="text-align:left;"> wha_harv_code </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 50 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WLS_COMMUNITY_WS_PUB_SVW </td>
   <td style="text-align:left;"> COMMUNITY_WS_NAME </td>
   <td style="text-align:left;"> cws </td>
   <td style="text-align:left;"> community_ws_name </td>
   <td style="text-align:left;"> cws_name </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 40 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> src </td>
   <td style="text-align:left;"> WLS_COMMUNITY_WS_PUB_SVW </td>
   <td style="text-align:left;"> COMMUNITY_WS_STATUS </td>
   <td style="text-align:left;"> cws </td>
   <td style="text-align:left;"> community_ws_status </td>
   <td style="text-align:left;"> cws_status </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> TRUE </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> String </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> NA </td>
  </tr>
</tbody>
</table>

## Non-standard Spatial Layers

The tsa16_nonstandard_lyrs.7z contains the non-standard (not included in the original analysis ready dataset) spatial layers complied during the review.

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table31) tsa16_ar2021</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> field </th>
   <th style="text-align:left;"> type </th>
   <th style="text-align:left;"> description </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> gr_skey </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Provincial Unique Identifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ogc_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Gdal unique identifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> feature_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> VRI indentifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> own_lbl </td>
   <td style="text-align:left;"> character varying </td>
   <td style="text-align:left;"> ownership label </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n2t_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Kwadacha FNWL </td>
  </tr>
  <tr>
   <td style="text-align:left;"> forest_fil </td>
   <td style="text-align:left;"> character varying(10) </td>
   <td style="text-align:left;"> Kwadacha FNWL </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mus_kech_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> MK </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> MK </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fire_threat_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Provincial Strategic Threat Assessment </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fire_threat_class </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Provincial Strategic Threat Assessment </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fn_overlap </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> FN Traditional Territories identifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fn_trad_terr_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> FN Traditional Territories identifier </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mugaha_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Mugaha Sensitive Area </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslt_join_final_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Results Retention </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslt_retention </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Results Retention </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fire_severity2_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Fire Severity Mapping </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fire_year </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Fire Severity Mapping </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fire_severity_grid </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Fire Severity Mapping </td>
  </tr>
  <tr>
   <td style="text-align:left;"> tsa16_ibs2018_sp_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2018 IBS AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> sp_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> 2018 IBS AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cutblocks2019_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2019 consolidated cutblocks id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cc_opening_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> opening id </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cc_harvest_year </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> harvest year </td>
  </tr>
  <tr>
   <td style="text-align:left;"> dmk_wolverine_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Wolverine herd initial </td>
  </tr>
  <tr>
   <td style="text-align:left;"> dmk_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Wolverine herd initial </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_recovery_zones_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Caribou Moritorium Zones </td>
  </tr>
  <tr>
   <td style="text-align:left;"> crz_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Caribou Moritorium Zones </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_mort_zone_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Caribou Moritorium Zones </td>
  </tr>
  <tr>
   <td style="text-align:left;"> moritorium_zone </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Caribou Moritorium Zones </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fisher_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Fisher WHA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fisher_no_harv </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Fisher WHA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibb2018_sp_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2018 IBB AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibb_sp_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> 2018 IBB AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibm_sampler_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2018 BCMPB </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cumkill2018 </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2018 BCMPB </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_no_harv_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_no_harv_number </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_no_harv_code </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_con_union_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> uwr_con_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslt_openings1129_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> RESULTS Openings </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslt_opening_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> RESULTS Openings </td>
  </tr>
  <tr>
   <td style="text-align:left;"> old_forest_ru_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Old Forest Constraints </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ru_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Old Forest Constraints </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ndt_type </td>
   <td style="text-align:left;"> character varying(12) </td>
   <td style="text-align:left;"> Old Forest Constraints </td>
  </tr>
  <tr>
   <td style="text-align:left;"> target_perc_old </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Old Forest Constraints </td>
  </tr>
  <tr>
   <td style="text-align:left;"> age_old_forest </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Old Forest Constraints </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibs2019_sp_id_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2019 IBS AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibs2019_sp_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> 2019 IBS AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibb2019_sp_id_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> 2019 IBB AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ibb2019_sp_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> 2019 IBB AOA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ndu_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Natural Disturbance Units </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ndu_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Natural Disturbance Units </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ndu_young_patch_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Young Patch ID </td>
  </tr>
  <tr>
   <td style="text-align:left;"> young_cohort_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> Young Patch ID </td>
  </tr>
  <tr>
   <td style="text-align:left;"> moose_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Mouse UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unit_type </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Mouse UWR </td>
  </tr>
  <tr>
   <td style="text-align:left;"> op_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Operating Areas 2018 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> op_area </td>
   <td style="text-align:left;"> character varying(25) </td>
   <td style="text-align:left;"> Operating Areas 2019 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> accum_ibs_2019_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Accumative IBS Mortality </td>
  </tr>
  <tr>
   <td style="text-align:left;"> accum_2019 </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> Accumative IBS Mortality </td>
  </tr>
  <tr>
   <td style="text-align:left;"> asev_2019 </td>
   <td style="text-align:left;"> character varying(3) </td>
   <td style="text-align:left;"> Accumative IBS Mortality </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslts_ret_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Results Retention </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rslt_ret_open_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> Results Retention </td>
  </tr>
  <tr>
   <td style="text-align:left;"> iso_mask_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Isolation Mask </td>
  </tr>
  <tr>
   <td style="text-align:left;"> isolation_mask_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Isolation Mask </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wolverine0315_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Wolverine herd final </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wolv0315_no_harv </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Wolverine herd final </td>
  </tr>
  <tr>
   <td style="text-align:left;"> tsa16_rs_op_areas_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Modeled Roadsheds </td>
  </tr>
  <tr>
   <td style="text-align:left;"> aws_group_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> FWA Watershed Groups </td>
  </tr>
  <tr>
   <td style="text-align:left;"> aws_group_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> FWA Watershed Groups </td>
  </tr>
  <tr>
   <td style="text-align:left;"> watershed_group_code </td>
   <td style="text-align:left;"> character varying(4) </td>
   <td style="text-align:left;"> FWA Watershed Groups </td>
  </tr>
  <tr>
   <td style="text-align:left;"> aws2020_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> FWA analysis watersheds </td>
  </tr>
  <tr>
   <td style="text-align:left;"> watershed_feature_id </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> FWA waterbodies </td>
  </tr>
  <tr>
   <td style="text-align:left;"> aws_waterbodies_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> FWA waterbodies </td>
  </tr>
  <tr>
   <td style="text-align:left;"> waterbody </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> FWA waterbodies </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_elev_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Low and High Elevation Caribou Habitat </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_elev_lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Low and High Elevation Caribou Habitat </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_ch_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Caribou critical habitat </td>
  </tr>
  <tr>
   <td style="text-align:left;"> caribou_ch_lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Caribou critical habitat </td>
  </tr>
  <tr>
   <td style="text-align:left;"> gb_assessment_id </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Grizzly Bear Assessment Units </td>
  </tr>
  <tr>
   <td style="text-align:left;"> assessment_unit_name </td>
   <td style="text-align:left;"> character varying(80) </td>
   <td style="text-align:left;"> Grizzly Bear Assessment Units </td>
  </tr>
  <tr>
   <td style="text-align:left;"> high_indicator_flag </td>
   <td style="text-align:left;"> character varying(25) </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> secure_core_cap_flag </td>
   <td style="text-align:left;"> character varying(20) </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> high_indicator_list </td>
   <td style="text-align:left;"> character varying(150) </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> gb_assessment_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> gbpu_max_conservation_concern_rank </td>
   <td style="text-align:left;"> character varying(5) </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> gbpu_max_conservation_concern_desc </td>
   <td style="text-align:left;"> character varying(30) </td>
   <td style="text-align:left;"> Grizzly Bear CEF metric </td>
  </tr>
  <tr>
   <td style="text-align:left;"> tsa16_oa_sheds2_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Modeled Operating Areas </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oa_id </td>
   <td style="text-align:left;"> smallint </td>
   <td style="text-align:left;"> Modeled Operating Areas </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oa_lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Modeled Operating Areas </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rd_shed_lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Modeled Roadsheds </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fsw20220513_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Fisheries Sensitive Watersheds </td>
  </tr>
  <tr>
   <td style="text-align:left;"> cfsw_name </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Fisheries Sensitive Watersheds </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wildland_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Wildlands RMA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wildland_lbl </td>
   <td style="text-align:left;"> character varying(50) </td>
   <td style="text-align:left;"> Wildlands RMA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fisher2_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Fisher Occupancy Model </td>
  </tr>
  <tr>
   <td style="text-align:left;"> perc_occ_2022_bc </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> Fisher Occupancy Model </td>
  </tr>
  <tr>
   <td style="text-align:left;"> perc_occ_2030_bc </td>
   <td style="text-align:left;"> double precision </td>
   <td style="text-align:left;"> Fisher Occupancy Model </td>
  </tr>
  <tr>
   <td style="text-align:left;"> arch_fid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Arch Sites </td>
  </tr>
  <tr>
   <td style="text-align:left;"> arch_grid </td>
   <td style="text-align:left;"> integer </td>
   <td style="text-align:left;"> Arch Sites </td>
  </tr>
</tbody>
</table>

## Yield

The tsa16_yield_curves221205.7z contains the yield curves used for the Mackenzie TSR. Three yield curve was produced for every hectare in the TSA: Current, Future, Disturbance Transition. The Current curve set contains NSYT and MSYT curves for natural and existing managed stands. The Future curve set contains transition curves post model harvest while the Disturbance set contains transition curves when stands are naturally disturbed in the model (for further discussion see Chapter \@ref(pathways).

<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table32) tsa16_yield</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> field </th>
   <th style="text-align:left;"> type </th>
   <th style="text-align:left;"> description </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> au </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> analysis unit </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr0 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr10 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year10 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr20 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year20 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr30 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year30 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr40 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year40 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr50 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year50 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr60 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year60 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr70 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year70 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr80 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year80 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr90 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year90 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr100 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year100 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr110 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year110 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr120 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year120 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr130 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year130 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr140 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year140 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr150 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year150 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr160 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year160 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr170 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year170 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr180 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year180 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr190 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year190 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr200 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year200 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr210 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year210 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr220 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year220 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr230 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr240 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year240 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr250 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year250 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr260 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year260 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr270 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year270 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr280 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year280 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr290 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year290 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr300 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year300 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr310 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year310 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr320 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year320 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr330 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year330 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr340 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year340 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr350 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year350 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr360 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year360 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr370 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year370 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr380 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year380 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr390 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year390 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> yr400 </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> volume at year400 </td>
  </tr>
</tbody>
</table>
