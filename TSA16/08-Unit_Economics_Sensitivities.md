



# Unit Economics Sensitivities
## Geographic Tranche

A geographic tranche sensitivity was developed to assess and visualize risk within the base case associated with the log delivery systems in the unit.

A unique aspect of Mackenzie TSA is the relatively large area served by water-based transport (barge and boom) of logs across Williston Reservoir.  Some water transport areas consist of valleys in rugged terrain with disconnected road networks, completely accessed via the tow/barge landing sites (e.g., along Peace Arm). Other areas use water transport due to the long distances required (e.g., north end of the reservoir), even though there are connecting roads (e.g., trucks may not have to be transported by barge, but log transport is more economic via tow/barge).  Further, some water-transport areas also require long road transport to reach the landing.

Consequently, the unit has the highest weighted average delivered log costs in the Interior. There is a structural operating cost differential of between $20-25/m3 between the winter-roaded (year-round access) southern portion of the TSA and rest of the TSA (ROT). The higher operating costs associated with the ROT significantly limit the ability to action low quality (damaged) timber.

For the geographic tranche sensitivity, the unit was subdivided into zones based on the “remoteness” of the road system and whether the system within the zone was connected to the “winter-roaded” portion of the TSA or was dependent upon the water transportation system to move timber to either the milling complex in Mackenzie or to other milling centers in the region.

Four risk classes were defined based on access and transport geography: 

  - Risk class 1: Areas accessible by “non-remote” roads in the south-west partition (teal), which comprise 33 percent of the timber harvesting land base (THLB).

  - Risk class 2: Areas accessible by roads outside the south-west partition or from areas with “remote” road access (blue), which comprise 16 percent of the THLB.

  - Risk class 3: Areas that involve water transport on Williston Reservoir and access via “non-remote” roads (red), which comprise 35 percent of the THLB.

  - Risk class 4: Areas that involve water transport and access via “remote” road access areas (yellow), which comprise 16 percent of the THLB.

Areas that require barging were identified using road landings on Williston Reservoir, and associated road sub-networks that were either (a) not connected to any other roads to the south end of the TSA; or (b) at the mid to northern end of the reservoir with the barge landing as the primary outlet for timber transport.

“Remote” road access was defined using estimated distance to either a road exit point on the southern boundary of the TSA or to a barge landing site. Distances more than 50km ( 3 hours cycle time) were classified as remote.


<div class="figure" style="text-align: center">
<img src="images2/geoTranche1.png" alt="Geographic Risk Zones" width="50%" />
<p class="caption">(\#fig:figure38)Geographic Risk Zones</p>
</div>

The results from the geographic area risk classes indicate about 40 percent of the total timber supply for the TSA over the mid to long-term is supported by areas with good road access in the south-west partition (Tranche 1). An additional 12 percent is supported by other areas not involving water transport (Tranche 2). Approximately 33 percent is supported by areas that involve barge access, but with reasonably short road access (Tranche 3); and
Approximately 15 percent is supported by areas that involve barge and as well as relatively remote road access (Tranche 4).

<div class="figure" style="text-align: center">
<img src="images2/geoTranche2.png" alt="Geographic Tranches within the base case" width="100%" />
<p class="caption">(\#fig:figure39)Geographic Tranches within the base case</p>
</div>
These tranches represent the timber supply associated with increasing access and transport costs, and hence decreasing likelihood of harvest depending on economic market conditions. 
Tranche 1 (coloured in teal on the map) represents the flow that is most likely achievable given the cost structure in the unit and therefore is the least risk contribution. 

Given the structural cost differential that makes the level of activity in the unit highly sensitive by variations in market prices, Tranche 4 (the portion of the unit coloured in yellow on the map) represents the least achievable and therefore the portion that contributes the greatest risk to realizing the base case over the long term. 

## Operating Areas

Most timber supply models assume a single agent operating within a unit, with the entire unit available for development at all times during the projection. The limitations of these assumptions are that the model design ignores the cost of constructing and maintaining log transportation systems which, in turn, may overestimate merchantable growing stock availability and accessibility. 

In realty most units have multiple agents operating simultaneously, creating localized, geographically concentrated development within discrete operating areas. Operating areas become active then inactive over time as merchantable growing stock becomes depleted, agents and market conditions change, and/or the cost of further development exceed the value of the residual growing stock that can be accessed.

In order to assess the effects of operating areas on the base case harvest projection for the Mackenzie TSR operating areas where simulated and access constraints were applied. 

Operating area access constraints limit the number of operating areas that can be accessed during a given period, how long operating areas remain accessible once entered, and how long operating areas subsequently remain inactive (and not accessible). When the maximum limit on the number of active operating areas is reached (specified as a percentage of THLB that can be active), no further operating areas can be activated, and logging access is restricted to the active operating areas. 

Harvest priority is focused into active operating areas before activating additional operating areas, provided the maximum limit has not yet been reached, thereby concentrating harvest in space and time. At any point in time, operating areas may be active (for a given period), inactive and available, or inactive and not available (until a post-access rest period has passed).

Operating area access constraints consist of two main elements:

  - State of individual “operating areas” (user defined): Initially, all operating areas are inactive. Upon the first logging entry, an operating area becomes active. An active operating area remains active for a specified number of years, after which it is assigned to a resting (or post-active) status for a specified number of years. Resting operating areas cannot be accessed. After the rest period, an operating area returns to active status and may be accessed. 
  
  - Overall limit on active operating areas: This refers to a maximum limit on the total amount of THLB in active operating areas allowed at any time. Once this limit is reached, no inactive operating areas may be activated, and logging is restricted to the current set of active operating areas until one or more are deactivated. To avoid reaching the limit too quickly, and to concentrate harvest in active operating areas, logging preference focuses on active operating areas.

To use operating area access constraints requires the input of an Operating Areas grid with values from 1 to n, each specifying an operating area. For Mackenzie 9 discrete operating areas were identified, each comprising (on average) 4 (1-8) contributing roadsheds to facilitate the application of operational road constraints within operating areas. 

The following maps identify the timber supply operating areas (left with operating area name in red and contributing  roadshed boundary in white) and contributing roadsheds (right…see Roadshed section for details). Red points (left) are harvest flow sinks (water drops or road network exit points). Roadsheds are named after their corresponding harvest flow sink (in black).  

<div class="figure" style="text-align: center">
<img src="images2/oa1.bmp" alt="Operating Areas and Roadsheds" width="80%" />
<p class="caption">(\#fig:figure41)Operating Areas and Roadsheds</p>
</div>
For the operating area access sensitivity, the operating area durations were set at 20-year active followed by a 20-year inactive (lock-out) period with 100% of the THLB available at all times (not limiting). The model selected the initial operating areas to activate based on harvest queue priorities (maximum volume relative to CMAI closest to the milling complex and road network) then proceeded to harvest and develop the road network until further areas were needed to be activated to meet the overall harvest request or the duration threshold was met.

The following figure depicts the spatial progression of harvest in the base case projection over the first 3 timesteps (decades) from left to right. By the end of the third decade eight of the operating areas area actively contributing to the harvest flow with the associated road network activation, construction, and maintenance costs.


<div class="figure" style="text-align: center">
<img src="images2/harv_prog_bc.png" alt="Base case harvest progression" width="80%" />
<p class="caption">(\#fig:figure42)Base case harvest progression</p>
</div>
As harvest progresses northward more operating areas are activated and remain active over the first century before repeating the cycle.

The following figure depicts the spatial progression of harvest in the operating area access sensitivity projection over the first 3 timesteps (decades) from left to right. Over the first three decades harvest is concentrated in no more than 4 operating areas at any given time with two becoming inactive after the first 20 years of development.

<div class="figure" style="text-align: center">
<img src="images2/harv_prog2.png" alt="Operating area constraint harvest progression" width="80%" />
<p class="caption">(\#fig:figure43)Operating area constraint harvest progression</p>
</div>
On average 3 operating areas are active at any given point of time with on average 3 units inactive and unavailable. Harvest follows a similar south to north pattern but with a more structured, systematic progression of development, similar to what one sees as current practice.   

The following chart contrasts the harvest projection attainable with an operating area access constraint with the base case harvest projection. Applying an operating area driven harvest progression reduces the short-term harvest projection by 11.5% and 3% in the mid-term. 

The spatial restriction and duration timing imposed by operating areas sensitivity limits stand availability for harvest but better reflects the tactical development of the unit. This suggests that there is risk associated with the base case harvest sequence assumptions and that the short-term base case harvest level may not be operationally achievable.

<div class="figure" style="text-align: center">
<img src="images2/oa_flow.png" alt="Operating area harvest flow" width="80%" />
<p class="caption">(\#fig:figure44)Operating area harvest flow</p>
</div>

## Development Costs
### Roadsheds

A roadshed is defined as a group of one or more adjacent exit points (e.g., log handling sites), and all the road segments that are connected to those sites. Analogous to a watershed, wood harvesting in a roadshed flows from further inland to these exit points. For the purposes of modeling the potential effects of development costs on harvest flow the TSA has been subdivided into 41 discrete roadsheds, the aggregate of which form a seamless surface for the TSA. As mentioned previously whole roadsheds are organized into and contribute to 9 discrete operating areas.

The timber supply model tracks information for both individual road segments and entire roadsheds. The net relative cost of each road segment is computed using the road cost surface (represented as the sum of relative cost values across the length of each segment) and summarised for each roadshed. Cost values can be considered a measure of the degree of difficulty moving across a landscape or through a roadshed (A cost input to a timber supply model can be a single raster and is generally the result of the composite of multiple rasters. The units assigned to the cost raster can be any type of cost desired: dollar cost, time, energy expended, or a unitless system that derives its meaning relative to the cost assigned to other cells. The values on the input cost raster can be integer or floating point, but they cannot be negative or 0 (you cannot have a negative or zero cost). The cost raster cannot contain values of 0 since the algorithm is a multiplicative process). 

During harvest, the volume and relative value of stands harvested, and the length and cost of road segments that are built by the model (“activated” from the road network) is tracked by roadshed. The model also tracks the length and cost of previously built segments that are maintained (accessed for the first time in the period). At present, roads are built once, and maintained up to once per period. In addition, hauling effort is tracked as sum of haul distance for each m3 (volume-weighted haul distance).

The following table identifies contributing roadsheds by operating area. Operating areas are identified with the prefix “oa” while contributing roadsheds are identified with the prefix “rs”.


<table class="table table-striped" style="font-size: 8px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:table10) Roadshed Summary</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Operating Areas </th>
   <th style="text-align:right;"> Existing (km) </th>
   <th style="text-align:right;"> Future (km) </th>
   <th style="text-align:right;"> Total (km) </th>
   <th style="text-align:left;"> THLB (ha) </th>
   <th style="text-align:left;"> CMM (m3) </th>
   <th style="text-align:left;"> Total THLB (%) </th>
   <th style="text-align:left;"> OA THLB (%) </th>
   <th style="text-align:left;"> Total CMM (%) </th>
   <th style="text-align:left;"> OA CMM (%) </th>
   <th style="text-align:right;"> mn THLB accessed (ha/km) </th>
   <th style="text-align:left;"> CMM/km </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> oaBear_Valley </td>
   <td style="text-align:right;"> 849.8 </td>
   <td style="text-align:right;"> 976.3 </td>
   <td style="text-align:right;"> 1,826.1 </td>
   <td style="text-align:left;"> 67,927 </td>
   <td style="text-align:left;"> 11,070,924 </td>
   <td style="text-align:left;"> 5.53% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 7.32% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 37 </td>
   <td style="text-align:left;"> 6,063 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsBear Valley </td>
   <td style="text-align:right;"> 708.7 </td>
   <td style="text-align:right;"> 543.8 </td>
   <td style="text-align:right;"> 1,252.5 </td>
   <td style="text-align:left;"> 46,594 </td>
   <td style="text-align:left;"> 7,838,643 </td>
   <td style="text-align:left;"> 3.79% </td>
   <td style="text-align:left;"> 68.59% </td>
   <td style="text-align:left;"> 5.18% </td>
   <td style="text-align:left;"> 70.80% </td>
   <td style="text-align:right;"> 37 </td>
   <td style="text-align:left;"> 6,258 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsLost Cabin </td>
   <td style="text-align:right;"> 72.9 </td>
   <td style="text-align:right;"> 208.3 </td>
   <td style="text-align:right;"> 281.2 </td>
   <td style="text-align:left;"> 8,254 </td>
   <td style="text-align:left;"> 1,370,846 </td>
   <td style="text-align:left;"> 0.67% </td>
   <td style="text-align:left;"> 15.40% </td>
   <td style="text-align:left;"> 0.91% </td>
   <td style="text-align:left;"> 12.38% </td>
   <td style="text-align:right;"> 29 </td>
   <td style="text-align:left;"> 4,875 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_11 </td>
   <td style="text-align:right;"> 24.1 </td>
   <td style="text-align:right;"> 41.0 </td>
   <td style="text-align:right;"> 65.1 </td>
   <td style="text-align:left;"> 2,739 </td>
   <td style="text-align:left;"> 382,186 </td>
   <td style="text-align:left;"> 0.22% </td>
   <td style="text-align:left;"> 3.56% </td>
   <td style="text-align:left;"> 0.25% </td>
   <td style="text-align:left;"> 3.45% </td>
   <td style="text-align:right;"> 42 </td>
   <td style="text-align:left;"> 5,871 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_16 </td>
   <td style="text-align:right;"> 11.7 </td>
   <td style="text-align:right;"> 4.0 </td>
   <td style="text-align:right;"> 15.7 </td>
   <td style="text-align:left;"> 272 </td>
   <td style="text-align:left;"> 30,988 </td>
   <td style="text-align:left;"> 0.02% </td>
   <td style="text-align:left;"> 0.86% </td>
   <td style="text-align:left;"> 0.02% </td>
   <td style="text-align:left;"> 0.28% </td>
   <td style="text-align:right;"> 17 </td>
   <td style="text-align:left;"> 1,974 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_19 </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:right;"> 18.0 </td>
   <td style="text-align:right;"> 18.1 </td>
   <td style="text-align:left;"> 373 </td>
   <td style="text-align:left;"> 40,859 </td>
   <td style="text-align:left;"> 0.03% </td>
   <td style="text-align:left;"> 0.99% </td>
   <td style="text-align:left;"> 0.03% </td>
   <td style="text-align:left;"> 0.37% </td>
   <td style="text-align:right;"> 21 </td>
   <td style="text-align:left;"> 2,257 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_22 </td>
   <td style="text-align:right;"> 15.7 </td>
   <td style="text-align:right;"> 5.6 </td>
   <td style="text-align:right;"> 21.3 </td>
   <td style="text-align:left;"> 881 </td>
   <td style="text-align:left;"> 118,134 </td>
   <td style="text-align:left;"> 0.07% </td>
   <td style="text-align:left;"> 1.17% </td>
   <td style="text-align:left;"> 0.08% </td>
   <td style="text-align:left;"> 1.07% </td>
   <td style="text-align:right;"> 41 </td>
   <td style="text-align:left;"> 5,546 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_25 </td>
   <td style="text-align:right;"> 14.1 </td>
   <td style="text-align:right;"> 7.8 </td>
   <td style="text-align:right;"> 21.9 </td>
   <td style="text-align:left;"> 524 </td>
   <td style="text-align:left;"> 54,188 </td>
   <td style="text-align:left;"> 0.04% </td>
   <td style="text-align:left;"> 1.20% </td>
   <td style="text-align:left;"> 0.04% </td>
   <td style="text-align:left;"> 0.49% </td>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:left;"> 2,474 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rswater_drop_10 </td>
   <td style="text-align:right;"> 2.5 </td>
   <td style="text-align:right;"> 147.8 </td>
   <td style="text-align:right;"> 150.3 </td>
   <td style="text-align:left;"> 8,291 </td>
   <td style="text-align:left;"> 1,235,080 </td>
   <td style="text-align:left;"> 0.67% </td>
   <td style="text-align:left;"> 8.23% </td>
   <td style="text-align:left;"> 0.82% </td>
   <td style="text-align:left;"> 11.16% </td>
   <td style="text-align:right;"> 55 </td>
   <td style="text-align:left;"> 8,217 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaBlackwater </td>
   <td style="text-align:right;"> 9,041.1 </td>
   <td style="text-align:right;"> 1,531.4 </td>
   <td style="text-align:right;"> 10,572.5 </td>
   <td style="text-align:left;"> 347,610 </td>
   <td style="text-align:left;"> 43,766,757 </td>
   <td style="text-align:left;"> 28.28% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 28.93% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 33 </td>
   <td style="text-align:left;"> 4,140 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsBlackwater </td>
   <td style="text-align:right;"> 1,121.4 </td>
   <td style="text-align:right;"> 113.1 </td>
   <td style="text-align:right;"> 1,234.5 </td>
   <td style="text-align:left;"> 38,325 </td>
   <td style="text-align:left;"> 3,797,015 </td>
   <td style="text-align:left;"> 3.12% </td>
   <td style="text-align:left;"> 11.68% </td>
   <td style="text-align:left;"> 2.51% </td>
   <td style="text-align:left;"> 8.68% </td>
   <td style="text-align:right;"> 31 </td>
   <td style="text-align:left;"> 3,076 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsNation </td>
   <td style="text-align:right;"> 1,375.8 </td>
   <td style="text-align:right;"> 232.0 </td>
   <td style="text-align:right;"> 1,607.8 </td>
   <td style="text-align:left;"> 66,799 </td>
   <td style="text-align:left;"> 9,138,830 </td>
   <td style="text-align:left;"> 5.43% </td>
   <td style="text-align:left;"> 15.21% </td>
   <td style="text-align:left;"> 6.04% </td>
   <td style="text-align:left;"> 20.88% </td>
   <td style="text-align:right;"> 42 </td>
   <td style="text-align:left;"> 5,684 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_000 </td>
   <td style="text-align:right;"> 8.3 </td>
   <td style="text-align:right;"> 3.4 </td>
   <td style="text-align:right;"> 11.7 </td>
   <td style="text-align:left;"> 527 </td>
   <td style="text-align:left;"> 33,994 </td>
   <td style="text-align:left;"> 0.04% </td>
   <td style="text-align:left;"> 0.11% </td>
   <td style="text-align:left;"> 0.02% </td>
   <td style="text-align:left;"> 0.08% </td>
   <td style="text-align:right;"> 45 </td>
   <td style="text-align:left;"> 2,906 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_34 </td>
   <td style="text-align:right;"> 247.2 </td>
   <td style="text-align:right;"> 83.0 </td>
   <td style="text-align:right;"> 330.2 </td>
   <td style="text-align:left;"> 8,838 </td>
   <td style="text-align:left;"> 1,789,014 </td>
   <td style="text-align:left;"> 0.72% </td>
   <td style="text-align:left;"> 3.12% </td>
   <td style="text-align:left;"> 1.18% </td>
   <td style="text-align:left;"> 4.09% </td>
   <td style="text-align:right;"> 27 </td>
   <td style="text-align:left;"> 5,418 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_37 </td>
   <td style="text-align:right;"> 1,093.1 </td>
   <td style="text-align:right;"> 185.5 </td>
   <td style="text-align:right;"> 1,278.6 </td>
   <td style="text-align:left;"> 52,196 </td>
   <td style="text-align:left;"> 4,057,577 </td>
   <td style="text-align:left;"> 4.25% </td>
   <td style="text-align:left;"> 12.09% </td>
   <td style="text-align:left;"> 2.68% </td>
   <td style="text-align:left;"> 9.27% </td>
   <td style="text-align:right;"> 41 </td>
   <td style="text-align:left;"> 3,173 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_38 </td>
   <td style="text-align:right;"> 1,823.7 </td>
   <td style="text-align:right;"> 142.0 </td>
   <td style="text-align:right;"> 1,965.7 </td>
   <td style="text-align:left;"> 68,358 </td>
   <td style="text-align:left;"> 8,074,453 </td>
   <td style="text-align:left;"> 5.56% </td>
   <td style="text-align:left;"> 18.59% </td>
   <td style="text-align:left;"> 5.34% </td>
   <td style="text-align:left;"> 18.45% </td>
   <td style="text-align:right;"> 35 </td>
   <td style="text-align:left;"> 4,108 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsTsedeka Crk </td>
   <td style="text-align:right;"> 3,371.6 </td>
   <td style="text-align:right;"> 772.4 </td>
   <td style="text-align:right;"> 4,144.0 </td>
   <td style="text-align:left;"> 112,567 </td>
   <td style="text-align:left;"> 16,875,873 </td>
   <td style="text-align:left;"> 9.16% </td>
   <td style="text-align:left;"> 39.20% </td>
   <td style="text-align:left;"> 11.15% </td>
   <td style="text-align:left;"> 38.56% </td>
   <td style="text-align:right;"> 27 </td>
   <td style="text-align:left;"> 4,072 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaCentennial </td>
   <td style="text-align:right;"> 6,245.2 </td>
   <td style="text-align:right;"> 991.5 </td>
   <td style="text-align:right;"> 7,236.7 </td>
   <td style="text-align:left;"> 237,184 </td>
   <td style="text-align:left;"> 24,292,201 </td>
   <td style="text-align:left;"> 19.29% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 16.06% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 33 </td>
   <td style="text-align:left;"> 3,357 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsCentennial </td>
   <td style="text-align:right;"> 221.4 </td>
   <td style="text-align:right;"> 36.6 </td>
   <td style="text-align:right;"> 258.0 </td>
   <td style="text-align:left;"> 8,402 </td>
   <td style="text-align:left;"> 548,269 </td>
   <td style="text-align:left;"> 0.68% </td>
   <td style="text-align:left;"> 3.57% </td>
   <td style="text-align:left;"> 0.36% </td>
   <td style="text-align:left;"> 2.26% </td>
   <td style="text-align:right;"> 33 </td>
   <td style="text-align:left;"> 2,125 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsFries Crk </td>
   <td style="text-align:right;"> 661.4 </td>
   <td style="text-align:right;"> 65.8 </td>
   <td style="text-align:right;"> 727.2 </td>
   <td style="text-align:left;"> 23,512 </td>
   <td style="text-align:left;"> 1,549,293 </td>
   <td style="text-align:left;"> 1.91% </td>
   <td style="text-align:left;"> 10.05% </td>
   <td style="text-align:left;"> 1.02% </td>
   <td style="text-align:left;"> 6.38% </td>
   <td style="text-align:right;"> 32 </td>
   <td style="text-align:left;"> 2,130 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsManson </td>
   <td style="text-align:right;"> 3,168.7 </td>
   <td style="text-align:right;"> 474.7 </td>
   <td style="text-align:right;"> 3,643.4 </td>
   <td style="text-align:left;"> 112,190 </td>
   <td style="text-align:left;"> 12,363,096 </td>
   <td style="text-align:left;"> 9.13% </td>
   <td style="text-align:left;"> 50.35% </td>
   <td style="text-align:left;"> 8.17% </td>
   <td style="text-align:left;"> 50.89% </td>
   <td style="text-align:right;"> 31 </td>
   <td style="text-align:left;"> 3,393 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_000 </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:right;"> NA </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:left;"> 29 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:right;"> 292 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_35 </td>
   <td style="text-align:right;"> 2,193.6 </td>
   <td style="text-align:right;"> 414.4 </td>
   <td style="text-align:right;"> 2,608.0 </td>
   <td style="text-align:left;"> 93,051 </td>
   <td style="text-align:left;"> 9,831,543 </td>
   <td style="text-align:left;"> 7.57% </td>
   <td style="text-align:left;"> 36.04% </td>
   <td style="text-align:left;"> 6.50% </td>
   <td style="text-align:left;"> 40.47% </td>
   <td style="text-align:right;"> 36 </td>
   <td style="text-align:left;"> 3,770 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaClearwater </td>
   <td style="text-align:right;"> 597.4 </td>
   <td style="text-align:right;"> 584.9 </td>
   <td style="text-align:right;"> 1,182.3 </td>
   <td style="text-align:left;"> 46,701 </td>
   <td style="text-align:left;"> 7,499,194 </td>
   <td style="text-align:left;"> 3.80% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 4.96% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 40 </td>
   <td style="text-align:left;"> 6,343 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsClearwater </td>
   <td style="text-align:right;"> 211.6 </td>
   <td style="text-align:right;"> 91.3 </td>
   <td style="text-align:right;"> 302.9 </td>
   <td style="text-align:left;"> 9,261 </td>
   <td style="text-align:left;"> 1,640,184 </td>
   <td style="text-align:left;"> 0.75% </td>
   <td style="text-align:left;"> 25.62% </td>
   <td style="text-align:left;"> 1.08% </td>
   <td style="text-align:left;"> 21.87% </td>
   <td style="text-align:right;"> 31 </td>
   <td style="text-align:left;"> 5,415 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_13 </td>
   <td style="text-align:right;"> 32.3 </td>
   <td style="text-align:right;"> 81.1 </td>
   <td style="text-align:right;"> 113.4 </td>
   <td style="text-align:left;"> 6,061 </td>
   <td style="text-align:left;"> 693,195 </td>
   <td style="text-align:left;"> 0.49% </td>
   <td style="text-align:left;"> 9.59% </td>
   <td style="text-align:left;"> 0.46% </td>
   <td style="text-align:left;"> 9.24% </td>
   <td style="text-align:right;"> 53 </td>
   <td style="text-align:left;"> 6,113 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_14 </td>
   <td style="text-align:right;"> 63.4 </td>
   <td style="text-align:right;"> 11.0 </td>
   <td style="text-align:right;"> 74.4 </td>
   <td style="text-align:left;"> 2,875 </td>
   <td style="text-align:left;"> 440,271 </td>
   <td style="text-align:left;"> 0.23% </td>
   <td style="text-align:left;"> 6.29% </td>
   <td style="text-align:left;"> 0.29% </td>
   <td style="text-align:left;"> 5.87% </td>
   <td style="text-align:right;"> 39 </td>
   <td style="text-align:left;"> 5,918 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_20 </td>
   <td style="text-align:right;"> 15.2 </td>
   <td style="text-align:right;"> 38.8 </td>
   <td style="text-align:right;"> 54.0 </td>
   <td style="text-align:left;"> 1,312 </td>
   <td style="text-align:left;"> 296,989 </td>
   <td style="text-align:left;"> 0.11% </td>
   <td style="text-align:left;"> 4.57% </td>
   <td style="text-align:left;"> 0.20% </td>
   <td style="text-align:left;"> 3.96% </td>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:left;"> 5,500 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_21 </td>
   <td style="text-align:right;"> 10.0 </td>
   <td style="text-align:right;"> 9.1 </td>
   <td style="text-align:right;"> 19.1 </td>
   <td style="text-align:left;"> 388 </td>
   <td style="text-align:left;"> 30,548 </td>
   <td style="text-align:left;"> 0.03% </td>
   <td style="text-align:left;"> 1.62% </td>
   <td style="text-align:left;"> 0.02% </td>
   <td style="text-align:left;"> 0.41% </td>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:left;"> 1,599 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_23 </td>
   <td style="text-align:right;"> 5.9 </td>
   <td style="text-align:right;"> 3.7 </td>
   <td style="text-align:right;"> 9.6 </td>
   <td style="text-align:left;"> 219 </td>
   <td style="text-align:left;"> 56,153 </td>
   <td style="text-align:left;"> 0.02% </td>
   <td style="text-align:left;"> 0.81% </td>
   <td style="text-align:left;"> 0.04% </td>
   <td style="text-align:left;"> 0.75% </td>
   <td style="text-align:right;"> 23 </td>
   <td style="text-align:left;"> 5,849 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_26 </td>
   <td style="text-align:right;"> 3.9 </td>
   <td style="text-align:right;"> 10.9 </td>
   <td style="text-align:right;"> 14.8 </td>
   <td style="text-align:left;"> 1,163 </td>
   <td style="text-align:left;"> 113,784 </td>
   <td style="text-align:left;"> 0.09% </td>
   <td style="text-align:left;"> 1.25% </td>
   <td style="text-align:left;"> 0.08% </td>
   <td style="text-align:left;"> 1.52% </td>
   <td style="text-align:right;"> 79 </td>
   <td style="text-align:left;"> 7,688 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_28 </td>
   <td style="text-align:right;"> 16.3 </td>
   <td style="text-align:right;"> 154.7 </td>
   <td style="text-align:right;"> 171.0 </td>
   <td style="text-align:left;"> 9,439 </td>
   <td style="text-align:left;"> 1,262,031 </td>
   <td style="text-align:left;"> 0.77% </td>
   <td style="text-align:left;"> 14.46% </td>
   <td style="text-align:left;"> 0.83% </td>
   <td style="text-align:left;"> 16.83% </td>
   <td style="text-align:right;"> 55 </td>
   <td style="text-align:left;"> 7,380 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_31 </td>
   <td style="text-align:right;"> 238.8 </td>
   <td style="text-align:right;"> 184.3 </td>
   <td style="text-align:right;"> 423.1 </td>
   <td style="text-align:left;"> 15,984 </td>
   <td style="text-align:left;"> 2,966,041 </td>
   <td style="text-align:left;"> 1.30% </td>
   <td style="text-align:left;"> 35.79% </td>
   <td style="text-align:left;"> 1.96% </td>
   <td style="text-align:left;"> 39.55% </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:left;"> 7,010 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaDeserters_crk </td>
   <td style="text-align:right;"> 2,506.3 </td>
   <td style="text-align:right;"> 922.8 </td>
   <td style="text-align:right;"> 3,429.1 </td>
   <td style="text-align:left;"> 60,301 </td>
   <td style="text-align:left;"> 8,242,538 </td>
   <td style="text-align:left;"> 4.91% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 5.45% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:left;"> 2,404 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsDeserters_crk </td>
   <td style="text-align:right;"> 2,506.3 </td>
   <td style="text-align:right;"> 922.8 </td>
   <td style="text-align:right;"> 3,429.1 </td>
   <td style="text-align:left;"> 60,301 </td>
   <td style="text-align:left;"> 8,242,538 </td>
   <td style="text-align:left;"> 4.91% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 5.45% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:left;"> 2,404 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaExcluded </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:right;"> NA </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 562 </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:left;"> 5,625 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsExcluded </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:right;"> NA </td>
   <td style="text-align:right;"> 0.1 </td>
   <td style="text-align:left;"> 2 </td>
   <td style="text-align:left;"> 562 </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:left;"> 5,625 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaFactor_Ross </td>
   <td style="text-align:right;"> 5,627.1 </td>
   <td style="text-align:right;"> 1,154.9 </td>
   <td style="text-align:right;"> 6,782.0 </td>
   <td style="text-align:left;"> 212,350 </td>
   <td style="text-align:left;"> 23,780,030 </td>
   <td style="text-align:left;"> 17.27% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 15.72% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 31 </td>
   <td style="text-align:left;"> 3,506 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsFactor Ross </td>
   <td style="text-align:right;"> 264.8 </td>
   <td style="text-align:right;"> 43.9 </td>
   <td style="text-align:right;"> 308.7 </td>
   <td style="text-align:left;"> 10,628 </td>
   <td style="text-align:left;"> 1,262,276 </td>
   <td style="text-align:left;"> 0.86% </td>
   <td style="text-align:left;"> 4.55% </td>
   <td style="text-align:left;"> 0.83% </td>
   <td style="text-align:left;"> 5.31% </td>
   <td style="text-align:right;"> 34 </td>
   <td style="text-align:left;"> 4,089 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsMesilinka </td>
   <td style="text-align:right;"> 1,056.8 </td>
   <td style="text-align:right;"> 33.9 </td>
   <td style="text-align:right;"> 1,090.7 </td>
   <td style="text-align:left;"> 28,734 </td>
   <td style="text-align:left;"> 2,499,744 </td>
   <td style="text-align:left;"> 2.34% </td>
   <td style="text-align:left;"> 16.08% </td>
   <td style="text-align:left;"> 1.65% </td>
   <td style="text-align:left;"> 10.51% </td>
   <td style="text-align:right;"> 26 </td>
   <td style="text-align:left;"> 2,292 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsMica Crk </td>
   <td style="text-align:right;"> 434.7 </td>
   <td style="text-align:right;"> 64.4 </td>
   <td style="text-align:right;"> 499.1 </td>
   <td style="text-align:left;"> 14,908 </td>
   <td style="text-align:left;"> 1,565,253 </td>
   <td style="text-align:left;"> 1.21% </td>
   <td style="text-align:left;"> 7.36% </td>
   <td style="text-align:left;"> 1.03% </td>
   <td style="text-align:left;"> 6.58% </td>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:left;"> 3,136 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsOmineca </td>
   <td style="text-align:right;"> 3,870.0 </td>
   <td style="text-align:right;"> 1,012.7 </td>
   <td style="text-align:right;"> 4,882.7 </td>
   <td style="text-align:left;"> 158,058 </td>
   <td style="text-align:left;"> 18,452,758 </td>
   <td style="text-align:left;"> 12.86% </td>
   <td style="text-align:left;"> 71.99% </td>
   <td style="text-align:left;"> 12.20% </td>
   <td style="text-align:left;"> 77.60% </td>
   <td style="text-align:right;"> 32 </td>
   <td style="text-align:left;"> 3,779 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rswater_drop_0 </td>
   <td style="text-align:right;"> 0.8 </td>
   <td style="text-align:right;"> NA </td>
   <td style="text-align:right;"> 0.8 </td>
   <td style="text-align:left;"> 22 </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 0.01% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:left;"> 0.00% </td>
   <td style="text-align:right;"> 28 </td>
   <td style="text-align:left;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaIngenika </td>
   <td style="text-align:right;"> 1,281.3 </td>
   <td style="text-align:right;"> 1,260.1 </td>
   <td style="text-align:right;"> 2,541.4 </td>
   <td style="text-align:left;"> 115,360 </td>
   <td style="text-align:left;"> 12,514,572 </td>
   <td style="text-align:left;"> 9.38% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 8.27% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 45 </td>
   <td style="text-align:left;"> 4,924 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsIngenika </td>
   <td style="text-align:right;"> 883.5 </td>
   <td style="text-align:right;"> 1,112.0 </td>
   <td style="text-align:right;"> 1,995.5 </td>
   <td style="text-align:left;"> 90,559 </td>
   <td style="text-align:left;"> 10,011,657 </td>
   <td style="text-align:left;"> 7.37% </td>
   <td style="text-align:left;"> 78.52% </td>
   <td style="text-align:left;"> 6.62% </td>
   <td style="text-align:left;"> 80.00% </td>
   <td style="text-align:right;"> 45 </td>
   <td style="text-align:left;"> 5,017 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsPelly Crk </td>
   <td style="text-align:right;"> 214.1 </td>
   <td style="text-align:right;"> 82.3 </td>
   <td style="text-align:right;"> 296.4 </td>
   <td style="text-align:left;"> 13,336 </td>
   <td style="text-align:left;"> 1,711,304 </td>
   <td style="text-align:left;"> 1.08% </td>
   <td style="text-align:left;"> 11.66% </td>
   <td style="text-align:left;"> 1.13% </td>
   <td style="text-align:left;"> 13.67% </td>
   <td style="text-align:right;"> 45 </td>
   <td style="text-align:left;"> 5,774 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsSwannell </td>
   <td style="text-align:right;"> 183.7 </td>
   <td style="text-align:right;"> 65.8 </td>
   <td style="text-align:right;"> 249.5 </td>
   <td style="text-align:left;"> 11,466 </td>
   <td style="text-align:left;"> 791,611 </td>
   <td style="text-align:left;"> 0.93% </td>
   <td style="text-align:left;"> 9.82% </td>
   <td style="text-align:left;"> 0.52% </td>
   <td style="text-align:left;"> 6.33% </td>
   <td style="text-align:right;"> 46 </td>
   <td style="text-align:left;"> 3,173 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaOspika </td>
   <td style="text-align:right;"> 1,805.9 </td>
   <td style="text-align:right;"> 1,611.1 </td>
   <td style="text-align:right;"> 3,417.0 </td>
   <td style="text-align:left;"> 137,405 </td>
   <td style="text-align:left;"> 19,704,639 </td>
   <td style="text-align:left;"> 11.18% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 13.02% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 40 </td>
   <td style="text-align:left;"> 5,767 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsChowika </td>
   <td style="text-align:right;"> 322.2 </td>
   <td style="text-align:right;"> 252.4 </td>
   <td style="text-align:right;"> 574.6 </td>
   <td style="text-align:left;"> 22,027 </td>
   <td style="text-align:left;"> 3,024,125 </td>
   <td style="text-align:left;"> 1.79% </td>
   <td style="text-align:left;"> 16.82% </td>
   <td style="text-align:left;"> 2.00% </td>
   <td style="text-align:left;"> 15.35% </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:left;"> 5,263 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsDavis </td>
   <td style="text-align:right;"> 612.8 </td>
   <td style="text-align:right;"> 214.1 </td>
   <td style="text-align:right;"> 826.9 </td>
   <td style="text-align:left;"> 31,641 </td>
   <td style="text-align:left;"> 4,121,670 </td>
   <td style="text-align:left;"> 2.57% </td>
   <td style="text-align:left;"> 24.20% </td>
   <td style="text-align:left;"> 2.72% </td>
   <td style="text-align:left;"> 20.92% </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:left;"> 4,984 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsOspika </td>
   <td style="text-align:right;"> 870.9 </td>
   <td style="text-align:right;"> 1,144.6 </td>
   <td style="text-align:right;"> 2,015.5 </td>
   <td style="text-align:left;"> 83,737 </td>
   <td style="text-align:left;"> 12,558,843 </td>
   <td style="text-align:left;"> 6.81% </td>
   <td style="text-align:left;"> 58.98% </td>
   <td style="text-align:left;"> 8.30% </td>
   <td style="text-align:left;"> 63.74% </td>
   <td style="text-align:right;"> 42 </td>
   <td style="text-align:left;"> 6,231 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> oaThutade </td>
   <td style="text-align:right;"> 889.0 </td>
   <td style="text-align:right;"> 110.2 </td>
   <td style="text-align:right;"> 999.2 </td>
   <td style="text-align:left;"> 4,500 </td>
   <td style="text-align:left;"> 421,043 </td>
   <td style="text-align:left;"> 0.37% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 0.28% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> 421 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> rsroad_outlet_000 </td>
   <td style="text-align:right;"> 889.0 </td>
   <td style="text-align:right;"> 110.2 </td>
   <td style="text-align:right;"> 999.2 </td>
   <td style="text-align:left;"> 4,500 </td>
   <td style="text-align:left;"> 421,043 </td>
   <td style="text-align:left;"> 0.37% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 0.28% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> 421 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Grand Total </td>
   <td style="text-align:right;"> 28,843.2 </td>
   <td style="text-align:right;"> 9,143.2 </td>
   <td style="text-align:right;"> 37,986.4 </td>
   <td style="text-align:left;"> 1,229,341 </td>
   <td style="text-align:left;"> 151,292,460 </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:left;"> 100.00% </td>
   <td style="text-align:right;"> 32 </td>
   <td style="text-align:left;"> 3,983 </td>
  </tr>
</tbody>
</table>

A total of approximately 38 000 km of road (~ 29 000  current, 9 000 future) are projected to be activated, developed and or maintained to support the base case harvest projection. The average roadshed contains approximately 700 km of existing road with a further 235 km of projected road development over the planning horizon. The mean current merchantable mature volume (cmm) per km of road developed or maintained for the TSA is approximately 4000 m3/km. Fifty-eight percent (24/41) of the roadsheds within the TSA have cmm/km ratios larger than the TSA mean while 10 roadsheds fall below the 20 percentile (2380m3/km) of all cmm/km ratios.

### Development Cost Constraints

A road building constraint is defined, for each roadshed and in each period, as an upper limit on the mean cost of roads built per unit value or volume of wood harvested in the roadshed. A road maintenance constraint is defined as an upper limit on the mean cost of roads maintained per unit value or volume of wood harvested in the roadshed during the period.

At the start of each period, the period building and maintenance costs are reset to 0. As logging proceeds, cost, volume and/or value all increase, and the cost:volume and cost:value ratios are tracked. If the ratios reach or pass the allowable building or maintenance constraints (e.g., due to logging of blocks that have relatively high cost and/or relatively low volume), then no further roads can be built/maintained in the period.

If the nearest road is not yet built, a test is made as to whether building this segment would exceed the construction constraint limit for the roadshed. Specifically, the test is for whether the net relative cost (total relative cost of roads built so far during the period plus the cost for this segment) divided by the net value or volume harvested (the relative value of volume harvested so far during the period plus the relative value of volume available for this road segment) is less than the constraint cost per unit value for road construction. 

When applying road constraints, some areas may never be accessed if the cost per length of road is high relative to the available value (which depends on the area of THLB, productivity of stands and relative species value). Some areas will be accessed with delay (compared to not applying road constraints) if available volume must increase to satisfy the road cost requirements. Other areas will be unaffected (e.g., areas with dense, high productivity THLB, with existing road access close to water entry points).

Sensitivity analysis explored regulating harvest flow by establishing relative road and maintenance cost thresholds for each of the 41 roadsheds. Road and maintenance cost thresholds were based on the 75th, 85th, 90th  and 95th  percentiles for all units over the first 100 years of the base case harvest projection (unregulated).

By applying the 95th percentile threshold of the median cost per m3 developed and/or maintained across all roadsheds over the first 100 years of the projection drops road development costs by 50% relative to the base case. Applying more stringent thresholds (75th percentile thru 90th  percentile) lowers the median cost further. Concomitantly, short term volume availability becomes more limited as stands that are harvested in the base case are deferred until the cost/volume ratio falls below threshold values. 

Applying the 95th percentile of each roadshed’s mean cost per m3 develop from over the first 100 years of the projection reduces the short-term harvest level by 5% (135 000 m3/yr.) suggesting the base case overestimates volume availability when the relative road development and maintenance costs are not factored into the harvest flow.

Additional sensitivity analysis explored the effects of combining both operating areas (to sequence harvest flows) with contributing development cost constraints (to emulated cost pressure on harvest flow). The base case 95th percentile mean cost per m3 develop threshold was maintained for all roadsheds across the planning horizon.

Combining the operating area access constraint with a road cost constraint lowers the starting harvest level to the maximum even flow of 2.43M3/yr equaling a 17% reduction relative to the base case.

<div class="figure" style="text-align: center">
<img src="images2/oa_rs.png" alt="Operating area and RoadShed harvest flow" width="80%" />
<p class="caption">(\#fig:figure45)Operating area and RoadShed harvest flow</p>
</div>
## Relative Value

Volume (m3, m3/year, m3/ha) is one of the basic drivers of timber supply modelling. However,
timber economics is also driven by timber value, which depends on species, log grade and other factors. While the overall economics of production are generally outside the scope of timber supply modelling, the differential value of volume can influence the sequencing of harvest, and hence have timber supply consequences.

As a first step to introduce differential value of volume, STSM2020 models relative differences in stand values per cubic metre of merchantable volume by species. Relative values are specified for each species as a multiplier per unit m3 of volume, and applied based on lead species of a stand (defined for each timber analysis unit).

As an example, relative values in the 2020 Haida Gwaii TSR analysis were derived using log
market prices. For example, over the preceding decade, the average market value per m3 of cedar was significantly higher than hemlock. As these market prices vary by year, scenarios can apply average values, or higher/lower market values. If this feature is not used, all relative values should be set to 1, which means relative value is the same as volume.

Relative stand values are computed dynamically for each grid cell as value/m3 multiplied by
merchantable volume and tracked in a layer similar to volume per hectare. Also, similar to
volume per ha, relative value can be tracked and supported at higher scales, such as cut block, woodshed or management unit.

In addition to reporting, relative values can be used to influence stand harvest preference (e.g.,there are some harvest preference options based on relative value) and road access. Both may influence harvest sequence, which in turn may affect timber supply outcome.

Sensitivity analysis explored the effects of applying relative species values to historically problem timber profiles, then prioritizing the highest relative valued stands in the harvest queue.  For this sensitivity deciduous leading stands were given a value multiplier of 0.1, while balsam-leading stands were given a value multiplier of 0.75.
 
The upper chart depicts the relative value species contribution to the base case. The solid black line represents the volume harvested while the solid red line represents unitless relative value of the harvest given the contributions of problem timber profiles (dashed blue for deciduous proportion [right y axis]and dashed gold line for the balsam proportion.) The dashed grey line represents the ratio of relative value to volume harvested [right y axis]. 

As harvest progresses into the mid-term the projection becomes increasingly dependant upon the contributions of lower relative valued stands(with harvested value decreasing) to sustain the maximum even flow harvest level. 

The lower chart depicts a flowed projection (MK scenario) where harvest prioritizes highest relative value stands. 


<div class="figure" style="text-align: center">
<img src="images2/rev_val.png" alt="Relative Value" width="80%" />
<p class="caption">(\#fig:figure46)Relative Value</p>
</div>


Adopting a highest value priority while maintaining the maximum even flow harvest level of 2.43 Mm3/yr. requires a lower initial short-term, reducing the harvest level by 6.5% per annum    (2.75 Mm3/yr) over the first decade relative to the base case. The long-term harvest level is also reduced by approximately 3% per annum.




