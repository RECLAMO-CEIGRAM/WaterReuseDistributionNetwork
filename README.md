# WaterReuseDistributionNetwork [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4662471.svg)](https://doi.org/10.5281/zenodo.4662471)

Algorithm developed by Antonio Bolinches (antonio.bolinches@upm.es) for research project RECLAMO.

![IMG](https://github.com/RECLAMO-CEIGRAM/WaterReuseDistributionNetwork/blob/main/img/Captura%20de%20Pantalla%202021-04-05%20a%20la(s)%2011.42.34.png)

The algorithm defines the optimal pipe distribution network providing regenerated water from a Water Regeneration Plant to agricultural land plots. The algorithm is written as a VBA macro in an Excel sheet. The inputs and outputs of the algorithm are worksheets within the Excel file, and the algorithm is embedded in the file as a module. The algorithm uses the working assumption that each pipe is defined (length, head) by the initial and final point positions. The user can choose two criterions for the optimization: Minimum Distance, which at each iteration step chooses the shortest pipe that connects a new plot to the existing distribution tree; or the Maximum (Benefit-Cost), which at each iteration step chooses the pipe connection which maximizes the Benefit (calculated as additional annual crop yield due to irrigation) minus Cost (calculated as the annual equivalent of the initial installation cost plus the operational costs). While the Maximum (Benefit-Cost) criterion may offer a better solution from the CBA (Cost and Benefit Analysis) point of view, it is more prone to inaccuracies due to the initial working assuption.

**The steps to use the algorithm are the following:**
  - Introduce the values in the Constants and Input tab.
  - Run the algorithm (“Calculate pipe network” button in the Input tab)
  -  Inspect the network in the Output tab


**Constants tab**

In the first tab of the Excel sheet the user can choose the criterion (Minimum Distance, or Maximum Benefit-Cost) and change the constants that are used in the calculation: Water density, Gravity; and in the case of Maximum (Benefit-Cost) criterion: Pipe linear loss, Price of electricity, Discount rate, Pipe Lifetime, Pump efficiency, Irrigation pressure, Pipe unit cost.

Worksheet | Line | Column | Variable_name | Units | Variable_type   
--- | --- | --- | --- |--- |--- 
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 8 | 3 | Water density | kg/m3 | real |
Constants | 9 | 3 | Gravity | m/s2 | text |
Constants | 13 | 3 | Pipe linear loss | m head per m legth | real |
Constants | 15 | 3 | Price of electricity | EUR/KWh | real |
Constants | 17 | 3 | Discount rate | - | real |
Constants | 18| 3 | Pipe Lifetime | years | real |
Constants | 20 | 3 | Pump efficiency | - | real |
Constants | 22 | 3 | Irrigation pressure | m of water column | real |
Constants | 24 | 3 | Pipe unit cost | EUR/m | real |

**Input tab**

The user can introduce the initial data in the input tab worksheet.
The Water Regeneration Plant (WRP) data is introduced in the upper part of the worksheet:

Worksheet | Line | Column | Variable_name | Units | Variable_type   
--- | --- | --- | --- |--- |--- 
Input | 8 | 3 | WRPname | - | text |
Input | 8 | 4 | X | m | real |
Input | 8 | 5 | Y | m| real |
Input | 8 | 6 | Elevation | m | real |
Input | 8 | 7 | Water Offer| m3/year | real |


X and Y coordinates must be introduced in a Projected Coordinate System (UTM for example), and the Elevation variable is used for the head calculations. It can be introduced as elevation above sea level or above a custom reference, as long as it is consistent for all elevation data. The Water Offer variable is introduced to help the user identify how many land plots can be connected.

The data of the land plots to be irrigated is introduced afterwards (one line for each land plot):

Worksheet | Line | Column | Variable_name | Units | Variable_type   
--- | --- | --- | --- |--- |--- 
Input | starting from 13 | 2 | ClSeqNum | - | text |
Input | starting from 13 | 3 | ClientID | - | text |
Input | starting from 13 | 4 | X | m | real |
Input | starting from 13 | 5 | Y | m | real |
Input | starting from 13 | 6 | Elevation | m | real |
Input | starting from 13 | 7 | Water Demand | m3/year | real |
Input | starting from 13 | 8 | Benefit | EUR/year | real |
Input | starting from 13 | 9 | Rwrp | m | real |


**Output tab**

Once the algorithm is run, it will create one line for each pipe, starting from line 7.

Worksheet | Line | Column | Variable_name | Units | Variable_type   
--- | --- | --- | --- |--- |--- 
Output | 2 | starting from 7 | Pipe_num | - | integer |
Output | 3 | starting from 7 | From(ini) | - | text |
Output | 4 | starting from 7 | To(end) | - | text |
Output | 5 | starting from 7 | X_ini | m | real |
Output | 6 | starting from 7 | Y_ini| m | real |
Output | 7 | starting from 7 | X_end| m | real |
Output | 8 | starting from 7 | Y_end | m | real |
Output | 9 | starting from 7 | Pipe length | m | real |
Output | 10| starting from 7 | Orientation | deg | real |
Output | 11| starting from 7 | Elev_ini | m | real |
Output | 12 | starting from 7 | Elev_end | m | real |
Output | 13| starting from 7 | Geom_head| m | real |
Output | 14 | starting from 7 | Pipe_end_Served_Area_ha| ha | real |
Output | 15 | starting from 7 | Pipe_end_served_volume | m3/year | real |
Output | 16 | starting from 7 | Pipe_end_cumulative_length| m | real |
Output | 17 | starting from 7 | Pipe_end_cumulative_area | ha | real |
Output | 18 | starting from 7 | Pipe_end_cumul_vol | m3/year | real |
Output | 19 | starting from 7 | Father_pipe | - | integer |
Output | 20 | starting from 7 | parent_count | - | integer |


Pipe_num is a sequential identificator for each pipe. From(ini) and To(end) identify the initial and final points of the pipe using the WRPname or the ClientID. The coordinates and elevation of initial and end points are identified, and the pipe length, orientation (0 deg for North) and geometrical head are calculated.

The area and water volume consumption of the end point are calculated. For pipes where the end point is also the initial point of subsequent pipes, the cumulative served area and water volume are also calculated. Finally, the Father_pipe is identified and the number of pipes from the initial point to the WRP (parent_count) is calculated.




