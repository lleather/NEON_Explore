Task: Compare outputs of NEON canopy height model to actual data.

    options(stringsAsFactors = F)

    #load libraries
    library(neonUtilities)
    library(geoNEON)
    library(raster)

    ## Loading required package: sp

    library(ggplot2)
    library(tidyverse) #this is important for data processing!

    ## ── Attaching packages ───────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ tibble  1.4.2     ✔ purrr   0.2.5
    ## ✔ tidyr   0.8.2     ✔ dplyr   0.7.7
    ## ✔ readr   1.1.1     ✔ stringr 1.3.1
    ## ✔ tibble  1.4.2     ✔ forcats 0.3.0

    ## ── Conflicts ──────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ tidyr::extract() masks raster::extract()
    ## ✖ dplyr::filter()  masks stats::filter()
    ## ✖ dplyr::lag()     masks stats::lag()
    ## ✖ dplyr::select()  masks raster::select()

    #make default plot white on white background
    th <- theme_bw()+ theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank())
    theme_set(th)


    proj_dir <- "/Users/lilaleatherman/Documents/current projects/github/NEON_Explore/LeathermanLST_ExploreNEONData"

    data_dir <- "/Users/lilaleatherman/Documents/current projects/github/neon_data_workshop/data"

    vegmap <- read.delim(paste0(data_dir, "/filesToStack10098/stackedFiles/vst_mappingandtagging.csv"), sep = ",")

    vegind <- read.delim(paste0(data_dir, "/filesToStack10098/stackedFiles/vst_apparentindividual.csv"), sep = ",")

geoNEON provides functionality for spatial data around NEON data. For
example, mapping and tagging data locations are relative to a named
point, but don't have absolute location data themselves. geoNEON allows
you to calculate the locations.

based on namedLocation, pointID, stemDistance, stemAzimuth - calculates
the location by querying API

    #get lat / long from NEON
    vegmap <- geoNEON::def.calc.geo.os(vegmap, "vst_mappingandtagging")

    ## 
      |                                                                       
      |                                                                 |   0%
      |                                                                       
      |                                                                 |   1%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_089.basePlot.vst.NA

    ## 
      |                                                                       
      |=                                                                |   2%
      |                                                                       
      |==                                                               |   3%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_082.basePlot.vst.NA

    ## 
      |                                                                       
      |==                                                               |   4%
      |                                                                       
      |===                                                              |   5%
      |                                                                       
      |====                                                             |   6%
      |                                                                       
      |====                                                             |   7%
      |                                                                       
      |=====                                                            |   8%
      |                                                                       
      |======                                                           |   9%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_083.basePlot.vst.NA

    ## 
      |                                                                       
      |======                                                           |  10%
      |                                                                       
      |=======                                                          |  11%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_077.basePlot.vst.NA

    ## 
      |                                                                       
      |========                                                         |  12%
      |                                                                       
      |========                                                         |  13%
      |                                                                       
      |=========                                                        |  14%
      |                                                                       
      |=========                                                        |  15%
      |                                                                       
      |==========                                                       |  15%
      |                                                                       
      |==========                                                       |  16%
      |                                                                       
      |===========                                                      |  17%
      |                                                                       
      |===========                                                      |  18%
      |                                                                       
      |============                                                     |  18%
      |                                                                       
      |============                                                     |  19%
      |                                                                       
      |=============                                                    |  20%
      |                                                                       
      |=============                                                    |  21%
      |                                                                       
      |==============                                                   |  21%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_086.basePlot.vst.NA

    ## 
      |                                                                       
      |==============                                                   |  22%
      |                                                                       
      |===============                                                  |  23%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_081.basePlot.vst.NA

    ## 
      |                                                                       
      |===============                                                  |  24%
      |                                                                       
      |================                                                 |  24%
      |                                                                       
      |================                                                 |  25%
      |                                                                       
      |=================                                                |  26%
      |                                                                       
      |=================                                                |  27%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_070.basePlot.vst.NA

    ## 
      |                                                                       
      |==================                                               |  27%
      |                                                                       
      |==================                                               |  28%
      |                                                                       
      |===================                                              |  29%
      |                                                                       
      |===================                                              |  30%
      |                                                                       
      |====================                                             |  31%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_076.basePlot.vst.NA

    ## 
      |                                                                       
      |=====================                                            |  32%
      |                                                                       
      |=====================                                            |  33%
      |                                                                       
      |======================                                           |  34%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_078.basePlot.vst.NA

    ## 
      |                                                                       
      |=======================                                          |  35%
      |                                                                       
      |=======================                                          |  36%
      |                                                                       
      |========================                                         |  37%
      |                                                                       
      |=========================                                        |  38%
      |                                                                       
      |=========================                                        |  39%
      |                                                                       
      |==========================                                       |  40%
      |                                                                       
      |===========================                                      |  41%
      |                                                                       
      |===========================                                      |  42%
      |                                                                       
      |============================                                     |  43%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_072.basePlot.vst.NA

    ## 
      |                                                                       
      |============================                                     |  44%
      |                                                                       
      |=============================                                    |  44%
      |                                                                       
      |=============================                                    |  45%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_074.basePlot.vst.NA

    ## 
      |                                                                       
      |==============================                                   |  46%
      |                                                                       
      |==============================                                   |  47%
      |                                                                       
      |===============================                                  |  47%
      |                                                                       
      |===============================                                  |  48%
      |                                                                       
      |================================                                 |  49%
      |                                                                       
      |================================                                 |  50%
      |                                                                       
      |=================================                                |  50%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_080.basePlot.vst.NA

    ## 
      |                                                                       
      |=================================                                |  51%
      |                                                                       
      |==================================                               |  52%
      |                                                                       
      |==================================                               |  53%
      |                                                                       
      |===================================                              |  53%
      |                                                                       
      |===================================                              |  54%
      |                                                                       
      |====================================                             |  55%
      |                                                                       
      |====================================                             |  56%
      |                                                                       
      |=====================================                            |  56%
      |                                                                       
      |=====================================                            |  57%
      |                                                                       
      |======================================                           |  58%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_073.basePlot.vst.NA

    ## 
      |                                                                       
      |======================================                           |  59%
      |                                                                       
      |=======================================                          |  60%
      |                                                                       
      |========================================                         |  61%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_079.basePlot.vst.NA

    ## 
      |                                                                       
      |========================================                         |  62%
      |                                                                       
      |=========================================                        |  63%
      |                                                                       
      |==========================================                       |  64%
      |                                                                       
      |==========================================                       |  65%
      |                                                                       
      |===========================================                      |  66%
      |                                                                       
      |============================================                     |  67%
      |                                                                       
      |============================================                     |  68%
      |                                                                       
      |=============================================                    |  69%
      |                                                                       
      |==============================================                   |  70%
      |                                                                       
      |==============================================                   |  71%
      |                                                                       
      |===============================================                  |  72%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_085.basePlot.vst.NA

    ## 
      |                                                                       
      |===============================================                  |  73%
      |                                                                       
      |================================================                 |  73%
      |                                                                       
      |================================================                 |  74%
      |                                                                       
      |=================================================                |  75%
      |                                                                       
      |=================================================                |  76%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_084.basePlot.vst.NA

    ## 
      |                                                                       
      |==================================================               |  76%
      |                                                                       
      |==================================================               |  77%
      |                                                                       
      |===================================================              |  78%
      |                                                                       
      |===================================================              |  79%
      |                                                                       
      |====================================================             |  79%
      |                                                                       
      |====================================================             |  80%
      |                                                                       
      |=====================================================            |  81%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_087.basePlot.vst.NA

    ## 
      |                                                                       
      |=====================================================            |  82%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_088.basePlot.vst.NA

    ## 
      |                                                                       
      |======================================================           |  82%
      |                                                                       
      |======================================================           |  83%
      |                                                                       
      |=======================================================          |  84%
      |                                                                       
      |=======================================================          |  85%
      |                                                                       
      |========================================================         |  85%
      |                                                                       
      |========================================================         |  86%
      |                                                                       
      |=========================================================        |  87%
      |                                                                       
      |=========================================================        |  88%
      |                                                                       
      |==========================================================       |  89%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_071.basePlot.vst.NA

    ## 
      |                                                                       
      |===========================================================      |  90%
      |                                                                       
      |===========================================================      |  91%
      |                                                                       
      |============================================================     |  92%
      |                                                                       
      |=============================================================    |  93%
      |                                                                       
      |=============================================================    |  94%
      |                                                                       
      |==============================================================   |  95%

    ## Warning in geoNEON::def.extr.geo.os(data, locCol = locCol,
    ## locOnly = F): WARNING: the following namedLocation was not found:
    ## WREF_075.basePlot.vst.NA

    ## 
      |                                                                       
      |===============================================================  |  96%
      |                                                                       
      |===============================================================  |  97%
      |                                                                       
      |================================================================ |  98%
      |                                                                       
      |=================================================================|  99%
      |                                                                       
      |=================================================================| 100%

    ## Warning in def.calc.latlong(point.loc): one or more rows had missing inputs
    ## for easting, northing, or UTM zone and were not converted

    #join locations with stem diameter
    veg <- merge(vegmap, vegind, by = c("individualID", "namedLocation", "domainID", "siteID", "plotID"))

    #plot stem diameters
    veg %>%
      filter(plotID == "WREF_085") %>%                    #looking at only one plot
      ggplot(aes(x = adjEasting, y = adjNorthing)) +
      geom_point(aes(size = stemDiameter/100), shape = 1)

    ## Warning: Removed 63 rows containing missing values (geom_point).

![](neon_compareData_files/figure-markdown_strict/look%20at%20stem%20diameter%20in%20plots-1.png)

    #plot stem diameters
    veg %>%
      filter(plotID == "WREF_085") %>%                    #looking at only one plot
      ggplot(aes(x = height)) +
      geom_bar() + 
      labs(title = "histogram of tree heights")

![](neon_compareData_files/figure-markdown_strict/look%20at%20stem%20diameter%20in%20plots-2.png)

    #download AOP data
    byTileAOP(dpID = "DP3.30015.001", site = "WREF", year = "2017", # canopy height model
              easting = 580000, northing = 5075000, savepath = data_dir, check.size = F)  #here we're just using one value for E+N, but you can use a vector for E+N as well

    ## Successfully downloaded  2  files.
    ## NEON_D16_WREF_DP1_580000_5075000_classified_point_cloud.kml downloaded to /Users/lilaleatherman/Documents/current projects/github/neon_data_workshop/data/DP3.30015.001/2017/FullSite/D16/2017_WREF_1/Metadata/DiscreteLidar/TileBoundary/kmls
    ## NEON_D16_WREF_DP3_580000_5075000_CHM.tif downloaded to /Users/lilaleatherman/Documents/current projects/github/neon_data_workshop/data/DP3.30015.001/2017/FullSite/D16/2017_WREF_1/L3/DiscreteLidar/CanopyHeightModelGtif

    #load: canopy height model
    chm <- raster(paste0(data_dir, "/DP3.30015.001/2017/FullSite/D16/2017_WREF_1/L3/DiscreteLidar/CanopyHeightModelGtif/NEON_D16_WREF_DP3_580000_5075000_CHM.tif"))

    #basic plot
    plot(chm, col = topo.colors(6))

![](neon_compareData_files/figure-markdown_strict/look%20at%20AOP%20data-1.png)

    #plot using ggplot
    library(viridis)

    ## Loading required package: viridisLite

    #write function to convert raster to ggplot-friendly format
    raster_to_pts_gg <- function(raster) {
      spdf <- as(raster, "SpatialPixelsDataFrame")
      df <- as.data.frame(spdf)
      colnames(df) <- c("value", "x", "y")
      df
    }

    chm_gg <- raster_to_pts_gg(chm)

    ggplot() + 
      geom_raster(data = chm_gg, aes(x = x, y = y, fill = value)) + 
      scale_fill_viridis() + 
      #remove default plotting background
      theme_bw() + theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank())

![](neon_compareData_files/figure-markdown_strict/look%20at%20AOP%20data-2.png)

    ## extract values of CHM to points in veg data frame
    veg_sub <- veg %>%
      filter(!is.na(adjEasting) & !is.na(adjNorthing)) 

    veg_xy <- veg_sub %>%
      select(adjEasting, adjNorthing)

    #convert veg points to spatial points data frame
    coordinates(veg_xy) <- ~adjEasting + adjNorthing
    veg_sp <- SpatialPointsDataFrame(coords = veg_xy, data = veg_sub, proj4string = crs(chm))

    #extract the values from the canopy height model to the points
    model_height <- raster::extract(chm, veg_sp)

    #turn extracted points into df to bind
    model_height <- data.frame(model_height)

    #combine model vals back with original df
    veg_full <- bind_cols(veg_sub, model_height)

    #do some cool stats!
