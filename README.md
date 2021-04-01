# WaterReuseDistributionNetwork
Algorithm developed by Antonio Bolinches (antonio.bolinches@upm.es) for research project RECLAMO.

The algorithm defines the optimal pipe distribution network providing regenerated water from a Water Regeneration Plant to agricultural land plots.

The algorithm is written as a VBA macro in an Excel sheet. The inputs and outputs of the algorithm are worksheets within the Excel file, and the algorithm is embedded in the file as a module.

The algorithm uses the working assumption that each pipe is defined (length, head) by the initial and final point positions. The user can choose two criterions for the optimization: Minimum Distance, which at each iteration step chooses the shortest pipe that connects a new plot to the existing distribution tree; or the Maximum (Benefit-Cost), which at each iteration step chooses the pipe connection which maximizes the Benefit (calculated as additional annual crop yield due to irrigation) minus Cost (calculated as the annual equivalent of the initial installation cost plus the operational costs). While the Maximum (Benefit-Cost) criterion may offer a better solution from the CBA (Cost and Benefit Analysis) point of view, it is more prone to inaccuracies due to the initial working assuption.

**The steps to use the algorithm are the following:**
  - Introduce the values in the Constants and Input tab.
  - Run the algorithm (“Calculate pipe network” button in the Input tab)
  -  Inspect the network in the Output tab


**Constants tab**

In the first tab of the Excel sheet the user can choose the criterion (Minimum Distance, or Maximum Benefit-Cost) and change the constants that are used in the calculation: Water density, Gravity; and in the case of Maximum (Benefit-Cost) criterion: Pipe linear loss, Price of electricity, Discount rate, Pipe Lifetime, Pump efficiency, Irrigation pressure, Pipe unit cost.

Worksheet |Line|Column |Variable name| Units | Variable type | 
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- |---
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
Constants | 4 | 3 | Optimization criterion | - | text |
