![Vector banner](./banner.png)

# How to use Squizz

Use the toolbar on the left to explore the context and possiblities associated with a hypothetical new mine, and identify possible opportunities and conflicts. The tabs at the top of the toolbar break this challenging task into more digestible chunks, as described below.

## Context tab
Use this tab to visualise spatial data capturing environmental and social context. These are sourced (largely) from EU databases, as described in the "info" box in the top left of the screen. Click the title of this "info" box to see the data source.

## Impact tab
Select the properties (size, type and financial commitment to ESG) of a hypothetical new mine and explore possible local impacts, given the spatial and social context described above.

The currently implemented mine properties considered when computing impact tendency are:

**Deposit Size**: *Is the mining operation Minor (0.01), Moderate (0.1), Major (0.5) or Giant (1.0), relative to the largest metal deposits (and associated mines) on earth (giant deposits).*

**Operation Type**: *Underground mine or open-pit mine.*

**Local Investment**: *Does the mine operator make a Minor (0.01), Moderate (0.1), Major (0.5) or Giant (1.0) contribution to local community development. This can be thought of as the share of mining revenue allocated to ESG relevant activities.*

## Tradeoffs tab
Choose your priorities (left = low, right = high), and see how the indicated impacts (computed using the values chosen in the previous tab) stack up, to explore the trade-offs between different impacts.

----

Please note that you need to click `Apply` to recompute the model after changing Mine Properties or Priorities.

----

# Impact pathways

Importantly, specific locations (hexagons) can be inspected by clicking them. This will show the *ESGi* index computed for this hexagon (given the Mine Properties and Priorities you have chosen), and the various impact pathways that were considered while computing it. These pathways, and their individual impact tendencies, are organised into possible opportunites (positive tendencies) and possible conflicts (negative tendencies). 

# How does Squizz work?

Squizz combines a set of environmental and societal indicators (as shown in the lower half of the `Attribute` graph), with an impact graph to semi-quantitatively explore the potential impact tendencies (positive vs negative) of a new mining operation across geospatial and societal contexts.

The impact graph contains directed edges that represent the (positive or negative) impact that a change in one property causes on another. Thus the effect of an increase in mining (the root node) is propagated through the graph to determine its cascading effect on all other properties in the graph.

Each edge is assigned a weight (which mathematically is a partial derivative) that determines the sign (positive or negative) and magnitude of these impacts. The weights can be constant, based on the selected `Priorities` and `Mine Properties`, or derived from the geospatial indices.

 For example, *Deforestation* always has a strong negative impact on *Forests*, so the edge between *Deforestation* and *Forests* is assigned a constant weight of -1. The amount of *Deforestation* depends on the amount of existing forest cover, so the edge between *Mine footprint* and *Deforestation* gets a weight that is equal to the *Forest area* spatial index (proportion of each hexagon containing forest now).

Hover the mouse over a weight in the impact graph to see the equation used to calculate it, and a description of the effects that this aims to capture.

After computing edge weights, impact tendencies are computed using the chain-rule: starting with a set change in mining (+1, i.e. a new mine) and multiplying this seed by each edge value to propagate downstream changes and compute mining's impact tendency on each property in the graph. Where multiple impact pathways converge, their effects are summed together to (crudely) estimate the net impact.

Note that this approach is semi-quantitative, as assigning magnitudes to the edge weights is challenging. Instead, all the spatial indices (and other adjustable properties) are carefully normalised to range between 0 and 1, such that edge weights represent the relative strength of a relationship (to an order of magnitude; e.g., 1 indicates a very very strong positive effect, while -0.1 indicates a weak negative effect). 

As such, the results should only be used as a guide for identifying potential pathways to shared value, and risks that could lead to conflict, based on the sign (positive or negative tendency) of the outputs. They should not be used quantitatively. Instead, the magnitude of the estimated impact tendency can be interpreted similar to a confidence (high absolute values) or uncertainty (low absolute values) estimate. 

# Data sources

Specific sources for each dataset used in Squizz can be seen by clicking the link at the top-left of the screen when it is displayed in the map.

### Societal data
Social data has been derived from two main sources: the Eurostat database and the 2022 edition of the EU Regional Competitiveness Index (RCI). Eurostat is the European Union's primary statistical repository, offering a comprehensive range of data on the EU, its member states, and candidate countries. It provides harmonized, high-quality statistics across diverse fields, including economy, population, trade, environment, health, and education, enabling cross-country comparisons within the European context. We have focused on NUTS level 2 data to ensure some level of spatial granularity.

The EU Regional Competitiveness Index (RCI) 2.0 is a comprehensive tool designed to assess the competitiveness of European Union regions, providing insights into their capacity to offer an attractive and sustainable environment for businesses and residents. Updated to reflect recent data and refined methodologies, RCI 2.0 measures competitiveness through 11 pillars grouped into three thematic areas: Basic, Efficiency, and Innovation factors. These include indicators such as infrastructure, education, health, market size, and technological readiness.

### Environmental data
Environmental and physical context information has been largely derived from from the Coordination of Information on the Environment (CORINE) land cover classification and the European Soil Data Centre (ESDAC) Land Degradation in Europe dataset. The Emerald and Natura2000 protected site outlines were also used to map out environmentally significant protected areas.

The ESDAC Land Degradation in Europe dataset offers a comprehensive assessment of land degradation across European agricultural and arable lands. This dataset includes the Land Multi-degradation Index (LMI), developed by integrating 12 indicators that represent various degradation processes such as soil erosion, organic carbon decline, and salinization.  In our context this dataset is especially useful for identifying potential sources for environmental shared value through remediation of legacy environmental damage.






