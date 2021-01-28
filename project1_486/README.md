What is the topic?  
- Predicted coronavirus hotspots in Maryland. 

What are the data and where is the data obtained from (provide links too)?
- Prior research was done to determine factors that increased transmission rate and fatalities.
  https://www.statnews.com/2020/03/03/who-is-getting-sick-and-how-sick-a-breakdown-of-coronavirus-risk-by-demographic-factors/
  https://www.health.harvard.edu/blog/as-coronavirus-spreads-many-questions-and-some-answers-2020022719004
 - Data was gathered from these websites in order to create the map 

Are there any necessary transformations or subsets you need to do to the data?
- The Maryland Census Tract data had to be seperated into three parts, people per square mile (high density), age range (30-79), and homeowners versus renters (economic demographic). 

What is the analysis you'll be performing on your data sets?
- Polygon to Raster by attribute, vector statistics, and raster calculator. 

What outputs will you be creating and how are they directly connected to the class
- I will be creating 4 different rasters in order to add them together to create a risk map. 

All statistics were performed in QGIS. Vector > Analysis Tools > Basic Statistics for Fields 

Creation of Map in QGIS (Expression builder)
Maryland Census Tract (Polygon to raster, pick attribute field)
- people ages 30 - 80: used expression builder: OutRas = Con(("MEANAGE" >= 30) & ("MEANAGE" <= 80), 1, 0)
- people per sq mile mean: 4864.6 so expression builder: OutRas = Con("PSQM", 1, 0, "VALUE > 4864.6")
- percent homeowners vs. renters mean: 66.9 so expression builder: OutRas = Con('POWN", 1, 0, "VALUE > 67)

Center for Disease Control  
- Heart disease per 1000 beneficiary mean 131: expression builder: OutRas = Con('1mdheart", 1, 0, "VALUE > 131)

Data analysis:
- Due to high population density in Baltimore, it seems Baltimore County has the most risk. 
