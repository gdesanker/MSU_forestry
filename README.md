# MSU_forestry


**tile _rasters3.py**

**Splits a landsat 8 scene into tiles, tile size of 1000 pixels**

**run_tiles_rasters3.py**
Runs the tile_rasters3.py script for each landsat 8 scene in the ~/Kruger/tiles_k/ directory. Each tile position and number for one scene, correspond with every other scene. 

**gapfillnew_Kruger.R**
Selects one tiles location at a time, and stacks all landsat tiles at the location as a dataframe. Replaces all 0 with NA and marks rows that can or cannot be gapfilled (not.missing T/F). For all rows that can be gapfilled, TSGFlinear gapfills the rows and binds them to the rest of the dataframe.

**spline_Serengeti.R**
Gapfills using the TSGFspline function

**bind_pca_kmeans_qda_histogram.R**
below

**figures_Kruger.R**
below


## Kruger

**Data processing:
Outputs from bind_pca_kmeans_qda_histogram.R script**

1. Cbind gapfilled dataframes with transformed aspect for each scene

    a. Dataframe of all tiles for a site
    
2. Pull out one NDVI scene, aspect, slope, geology and transformed aspect to use for figures

    a. ndvi, slope, aspect and elevation dataframes
    
3. Cbind geology to gapfilled dataframe (from 1)

    a. gapfilled dataframe with geology
    
4. Determine number of PCs for Kmeans

    a. PC signals dataframe
    
    b. PC scores object
    
5. Determine number of clusters:

    a. Elbow method: Figure and number of clusters
        
    b. Silhouette method: Figure and number of clusters
        
6. Keams clustering algorithm with kmeansarma

    a. Number of clusters
    
    b. Gapfilled dataframe with all envi variables and kmeans cluster assignment
    
7. Discriminant analysis

    a. Lda model summary
    
    b. Confusion matrix for lda
    
8. Pull out NDVI rows for each cluster

    a. Dataframes for each cluster assignment

**Figures:**

1) PCA screeplot

2) Phenoregion raster map showing cluster assignments in the study site

3) Landcover histograms for each phenoregion

    a)Reclassify numbers to landcover type names
    
    b)Filter by cluster assignment
    
    c)Histograms for each cluster assignment showing count of landcover types
    
4) NDVI profiles for each phenoregion, with average NDVI and quantiles (raining seasons?)

5) Precipitation plots with rainy seasons
