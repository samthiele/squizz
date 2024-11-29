# About
Squizz is prototype application gathers social and environmental data and combines them in a way that lets you explore mining's potential impact in Europe.

It aims to help identify and explore the various pathways in which mining can have positive and negative impacts, to promote shared value rather than conflict. While hugely challenging, identifying regions where which mining can co-create mutual benefit to society (and the environment) is crucial to ensuring sustainable and local supply of the raw materials used by society.

# How can I use Squizz?

Use the toolbar on the left to chose your personal, company or community priorities using the "Priorities" sliders, moving them to the right to increase priority and the left to decrease it.

Then specify the potential mine properties. Options here are:

**Mine Size**: *Is the mining operation Minor (0.01), Moderate (0.1), Major (0.5) or Giant (1.0).*

**Operation Type**: *Underground mine or open-pit.*

**Local Investment**: *Does the mine operator make a Minor (0.01), Moderate (0.1), Major (0.5) or Giant (1.0) contribution to local community development.*

Finally, click `Apply` to update the map viewer to reflect your changes. By default the map shows the *Shared Value Index*, a combination of all potential mine impacts weighted by your chosen priorites, but individual impacts and aspects can be shown instead using the `Attribute` dropdown.

This `Attribute` dropdown can also be used to visualise the input spatial data (mapping environmental and spatial context) used to determine these potential impacts.

Specific locations (hexagons) can be selected by clicking them, to explore the *impact tendency graph*, which combines these spatial indices to semi-quantitatively predict the tendency (positive or negative) of a new mine. Hover the mouse over any edge in this graph to get more information on how each relationship has been approximated, or scroll to the bottom of the page to see each individual impact pathway (divided into potential positive impacts and potential sources of conflict).

# How does Squizz work?

Squizz combines a set of environmental and societal indicators (as shown in the lower half of the `Attribute` graph) with an impact graph to semi-quantitatively explore the potential impacts of a mining operation given it's geospatial and societal context.

The impact graph contains directed edges that denote the (positive or negative) impact that a change in one property causes on another. Thus the effect of an increase in mining (the root node) is propagated through the graph to determine its cascading effect on all other properties in the graph, including Shared Value.

Edge edge is assigned a weight (which mathematically is a partial derivative) that determines the sign (positive or negative) and magnitude of these impacts. The weights can be constant, based on the selected `Priorities` and `Mine Properties`, or derived from the geospatial indices. For example, *Deforestation* always has a strong negative impact on *Forests*, so the edge between *Deforestation* and *Forests* is assigned a constant weight of -1. The amount of *Deforestation* depends on the amount of existing forest cover, so the edge between *Mine footprint* and *Deforestation* gets a weight that is equal to the *Forest area* spatial index (proportion of each hexagon containing forest now).

Hover the mouse over a weight in the impact graph to see the equation used to calculate it, and a description of the effects that this aims to capture.

Note that this approach is semi-quantitative, as assigning meaningful magnitudes to the edge weights is challenging. Instead, all the spatial indices (and other adjustable properties) are carefully normalised to range between 0 and 1, such that edge weights can be computed in a way that focuses on the relative strength of a relationship (to an order of magnitude; e.g., 1 indicates a very very strong link, while 0.1 indicates a weak link). 

As such the results should be used as a guide to identify potential pathways to shared value (and risks that could lead to conflict), but should not be interpreted quantitatively. We aim to create results with meaningful "impact tendencies" (i.e. the sign of the impact indicating potential positive or negative outcomes), but the magnitudes should not be over-interpreted (but can be treated as similar to an uncertainty value).


# Data sources

Specific sources for each dataset used in Squizz can be seen by clicking the link at the top-left of the screen when it is displayed in the map.

### Societal data
Social data has been derived from two main sources: the Eurostat database and the 2022 edition of the EU Regional Competitiveness Index (RCI). Eurostat is the European Union's primary statistical repository, offering a comprehensive range of data on the EU, its member states, and candidate countries. It provides harmonized, high-quality statistics across diverse fields, including economy, population, trade, environment, health, and education, enabling cross-country comparisons within the European context. We have focused on NUTS level 2 data to ensure some level of spatial granularity.

The EU Regional Competitiveness Index (RCI) 2.0 is a comprehensive tool designed to assess the competitiveness of European Union regions, providing insights into their capacity to offer an attractive and sustainable environment for businesses and residents. Updated to reflect recent data and refined methodologies, RCI 2.0 measures competitiveness through 11 pillars grouped into three thematic areas: Basic, Efficiency, and Innovation factors. These include indicators such as infrastructure, education, health, market size, and technological readiness. The index aims to support evidence-based policymaking, fostering regional development and reducing disparities by highlighting strengths and areas for improvement across regions, ultimately contributing to the EU’s cohesion and growth objectives.

### Environmental data
Environmental and physical context information has been largely derived from from the Coordination of Information on the Environment (CORINE) land cover classification and the European Soil Data Centre (ESDAC) Land Degradation in Europe dataset. The Emerald and Natura2000 protected site outlines were also used to map out environmentally significant protected areas.

The European Soil Data Centre (ESDAC) "Land Degradation in Europe" dataset offers a comprehensive assessment of land degradation across European agricultural and arable lands. This dataset includes the Land Multi-degradation Index (LMI), developed by integrating 12 indicators that represent various degradation processes such as soil erosion, organic carbon decline, and salinization.  In our context this dataset is especially useful for identifying potential sources for environmental shared value through remediation of legacy environmental damage.






