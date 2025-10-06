## In the following section example R code is provided for dRBS ##

## Modelling the depletion and recovery of VMEs indicator taxa following bottom trawling activity in New Zealand waters ##

##------------------------------  Authors: Edoardo Zelli & Fabrice Stephenson
##------------------------------  Start date : September 2023
##------------------------------  End date : June 2024


#********************** dynamic Relative Benthic Status (RBS) ******************

#*******************************************************************************
#*******************************************************************************
#*******************************************************************************


library(rgdal); library(sf); library(raster); library(stringr)

home <- "C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/"
setwd((home))


##################################################################################################################
# CBR
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
CBR_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
CBR.Q.D. <- raster("CBR.pred.AB_mean_present.tif")
CBR_internal_SSP2 <- CBR.Q.D. * mask_SSP2vsPres
CBR_internal_SSP2[CBR_internal_SSP2 == 0] <- NA
plot(CBR_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(CBR_internal_SSP2, "CBR_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
CBR_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
CBR.Q.D. <- raster("CBR.pred.AB_mean_present.tif")
CBR_external_SSP2 <- CBR.Q.D. * mask_SSP2vsPres
CBR_external_SSP2[CBR_external_SSP2 == 0] <- NA
plot(CBR_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(CBR_external_SSP2, "CBR_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
CBR_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
CBR.Q.D. <- raster("CBR.pred.AB_mean_present.tif")
CBR_internal_SSP3 <- CBR.Q.D. * mask_SSP3vsPres
CBR_internal_SSP3[CBR_internal_SSP3 == 0] <- NA
plot(CBR_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(CBR_internal_SSP3, "CBR_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
CBR_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
CBR.Q.D. <- raster("CBR.pred.AB_mean_present.tif")
CBR_external_SSP3 <- CBR.Q.D. * mask_SSP3vsPres
CBR_external_SSP3[CBR_external_SSP3 == 0] <- NA
plot(CBR_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(CBR_external_SSP3, "CBR_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# COB
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
COB_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
COB.Q.D. <- raster("COB.pred.AB_mean_present.tif")
COB_internal_SSP2 <- COB.Q.D. * mask_SSP2vsPres
COB_internal_SSP2[COB_internal_SSP2 == 0] <- NA
plot(COB_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(COB_internal_SSP2, "COB_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
COB_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
COB.Q.D. <- raster("COB.pred.AB_mean_present.tif")
COB_external_SSP2 <- COB.Q.D. * mask_SSP2vsPres
COB_external_SSP2[COB_external_SSP2 == 0] <- NA
plot(COB_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(COB_external_SSP2, "COB_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
COB_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
COB.Q.D. <- raster("COB.pred.AB_mean_present.tif")
COB_internal_SSP3 <- COB.Q.D. * mask_SSP3vsPres
COB_internal_SSP3[COB_internal_SSP3 == 0] <- NA
plot(COB_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(COB_internal_SSP3, "COB_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
COB_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
COB.Q.D. <- raster("COB.pred.AB_mean_present.tif")
COB_external_SSP3 <- COB.Q.D. * mask_SSP3vsPres
COB_external_SSP3[COB_external_SSP3 == 0] <- NA
plot(COB_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(COB_external_SSP3, "COB_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# DEM
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
DEM_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
DEM.Q.D. <- raster("DEM.pred.AB_mean_present.tif")
DEM_internal_SSP2 <- DEM.Q.D. * mask_SSP2vsPres
DEM_internal_SSP2[DEM_internal_SSP2 == 0] <- NA
plot(DEM_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(DEM_internal_SSP2, "DEM_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
DEM_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
DEM.Q.D. <- raster("DEM.pred.AB_mean_present.tif")
DEM_external_SSP2 <- DEM.Q.D. * mask_SSP2vsPres
DEM_external_SSP2[DEM_external_SSP2 == 0] <- NA
plot(DEM_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(DEM_external_SSP2, "DEM_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
DEM_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
DEM.Q.D. <- raster("DEM.pred.AB_mean_present.tif")
DEM_internal_SSP3 <- DEM.Q.D. * mask_SSP3vsPres
DEM_internal_SSP3[DEM_internal_SSP3 == 0] <- NA
plot(DEM_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(DEM_internal_SSP3, "DEM_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
DEM_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
DEM.Q.D. <- raster("DEM.pred.AB_mean_present.tif")
DEM_external_SSP3 <- DEM.Q.D. * mask_SSP3vsPres
DEM_external_SSP3[DEM_external_SSP3 == 0] <- NA
plot(DEM_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(DEM_external_SSP3, "DEM_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# GD
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GD_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
GD.Q.D. <- raster("GD.pred.AB_mean_present.tif")
GD_internal_SSP2 <- GD.Q.D. * mask_SSP2vsPres
GD_internal_SSP2[GD_internal_SSP2 == 0] <- NA
plot(GD_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(GD_internal_SSP2, "GD_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GD_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
GD.Q.D. <- raster("GD.pred.AB_mean_present.tif")
GD_external_SSP2 <- GD.Q.D. * mask_SSP2vsPres
GD_external_SSP2[GD_external_SSP2 == 0] <- NA
plot(GD_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(GD_external_SSP2, "GD_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GD_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
GD.Q.D. <- raster("GD.pred.AB_mean_present.tif")
GD_internal_SSP3 <- GD.Q.D. * mask_SSP3vsPres
GD_internal_SSP3[GD_internal_SSP3 == 0] <- NA
plot(GD_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(GD_internal_SSP3, "GD_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GD_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
GD.Q.D. <- raster("GD.pred.AB_mean_present.tif")
GD_external_SSP3 <- GD.Q.D. * mask_SSP3vsPres
GD_external_SSP3[GD_external_SSP3 == 0] <- NA
plot(GD_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(GD_external_SSP3, "GD_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# GOC
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GOC_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
GOC.Q.D. <- raster("GOC.pred.AB_mean_present.tif")
GOC_internal_SSP2 <- GOC.Q.D. * mask_SSP2vsPres
GOC_internal_SSP2[GOC_internal_SSP2 == 0] <- NA
plot(GOC_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(GOC_internal_SSP2, "GOC_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GOC_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
GOC.Q.D. <- raster("GOC.pred.AB_mean_present.tif")
GOC_external_SSP2 <- GOC.Q.D. * mask_SSP2vsPres
GOC_external_SSP2[GOC_external_SSP2 == 0] <- NA
plot(GOC_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(GOC_external_SSP2, "GOC_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GOC_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
GOC.Q.D. <- raster("GOC.pred.AB_mean_present.tif")
GOC_internal_SSP3 <- GOC.Q.D. * mask_SSP3vsPres
GOC_internal_SSP3[GOC_internal_SSP3 == 0] <- NA
plot(GOC_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(GOC_internal_SSP3, "GOC_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GOC_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
GOC.Q.D. <- raster("GOC.pred.AB_mean_present.tif")
GOC_external_SSP3 <- GOC.Q.D. * mask_SSP3vsPres
GOC_external_SSP3[GOC_external_SSP3 == 0] <- NA
plot(GOC_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(GOC_external_SSP3, "GOC_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# HEX
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
HEX_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
HEX.Q.D. <- raster("HEX.pred.AB_mean_present.tif")
HEX_internal_SSP2 <- HEX.Q.D. * mask_SSP2vsPres
HEX_internal_SSP2[HEX_internal_SSP2 == 0] <- NA
plot(HEX_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(HEX_internal_SSP2, "HEX_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
HEX_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
HEX.Q.D. <- raster("HEX.pred.AB_mean_present.tif")
HEX_external_SSP2 <- HEX.Q.D. * mask_SSP2vsPres
HEX_external_SSP2[HEX_external_SSP2 == 0] <- NA
plot(HEX_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(HEX_external_SSP2, "HEX_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
HEX_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
HEX.Q.D. <- raster("HEX.pred.AB_mean_present.tif")
HEX_internal_SSP3 <- HEX.Q.D. * mask_SSP3vsPres
HEX_internal_SSP3[HEX_internal_SSP3 == 0] <- NA
plot(HEX_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(HEX_internal_SSP3, "HEX_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
HEX_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
HEX.Q.D. <- raster("HEX.pred.AB_mean_present.tif")
HEX_external_SSP3 <- HEX.Q.D. * mask_SSP3vsPres
HEX_external_SSP3[HEX_external_SSP3 == 0] <- NA
plot(HEX_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(HEX_external_SSP3, "HEX_external_SSP3.tif", overwrite=TRUE)


##################################################################################################################
# PRI
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PRI_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
PRI.Q.D. <- raster("PRI.pred.AB_mean_present.tif")
PRI_internal_SSP2 <- PRI.Q.D. * mask_SSP2vsPres
PRI_internal_SSP2[PRI_internal_SSP2 == 0] <- NA
plot(PRI_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(PRI_internal_SSP2, "PRI_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PRI_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
PRI.Q.D. <- raster("PRI.pred.AB_mean_present.tif")
PRI_external_SSP2 <- PRI.Q.D. * mask_SSP2vsPres
PRI_external_SSP2[PRI_external_SSP2 == 0] <- NA
plot(PRI_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(PRI_external_SSP2, "PRI_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PRI_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
PRI.Q.D. <- raster("PRI.pred.AB_mean_present.tif")
PRI_internal_SSP3 <- PRI.Q.D. * mask_SSP3vsPres
PRI_internal_SSP3[PRI_internal_SSP3 == 0] <- NA
plot(PRI_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(PRI_internal_SSP3, "PRI_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PRI_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
PRI.Q.D. <- raster("PRI.pred.AB_mean_present.tif")
PRI_external_SSP3 <- PRI.Q.D. * mask_SSP3vsPres
PRI_external_SSP3[PRI_external_SSP3 == 0] <- NA
plot(PRI_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(PRI_external_SSP3, "PRI_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# PTU
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PTU_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
PTU.Q.D. <- raster("PTU.pred.AB_mean_present.tif")
PTU_internal_SSP2 <- PTU.Q.D. * mask_SSP2vsPres
PTU_internal_SSP2[PTU_internal_SSP2 == 0] <- NA
plot(PTU_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(PTU_internal_SSP2, "PTU_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PTU_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
PTU.Q.D. <- raster("PTU.pred.AB_mean_present.tif")
PTU_external_SSP2 <- PTU.Q.D. * mask_SSP2vsPres
PTU_external_SSP2[PTU_external_SSP2 == 0] <- NA
plot(PTU_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(PTU_external_SSP2, "PTU_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PTU_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
PTU.Q.D. <- raster("PTU.pred.AB_mean_present.tif")
PTU_internal_SSP3 <- PTU.Q.D. * mask_SSP3vsPres
PTU_internal_SSP3[PTU_internal_SSP3 == 0] <- NA
plot(PTU_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(PTU_internal_SSP3, "PTU_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PTU_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
PTU.Q.D. <- raster("PTU.pred.AB_mean_present.tif")
PTU_external_SSP3 <- PTU.Q.D. * mask_SSP3vsPres
PTU_external_SSP3[PTU_external_SSP3 == 0] <- NA
plot(PTU_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(PTU_external_SSP3, "PTU_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# RAD
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
RAD_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
RAD.Q.D. <- raster("RAD.pred.AB_mean_present.tif")
RAD_internal_SSP2 <- RAD.Q.D. * mask_SSP2vsPres
RAD_internal_SSP2[RAD_internal_SSP2 == 0] <- NA
plot(RAD_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(RAD_internal_SSP2, "RAD_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
RAD_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
RAD.Q.D. <- raster("RAD.pred.AB_mean_present.tif")
RAD_external_SSP2 <- RAD.Q.D. * mask_SSP2vsPres
RAD_external_SSP2[RAD_external_SSP2 == 0] <- NA
plot(RAD_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(RAD_external_SSP2, "RAD_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
RAD_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
RAD.Q.D. <- raster("RAD.pred.AB_mean_present.tif")
RAD_internal_SSP3 <- RAD.Q.D. * mask_SSP3vsPres
RAD_internal_SSP3[RAD_internal_SSP3 == 0] <- NA
plot(RAD_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(RAD_internal_SSP3, "RAD_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
RAD_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
RAD.Q.D. <- raster("RAD.pred.AB_mean_present.tif")
RAD_external_SSP3 <- RAD.Q.D. * mask_SSP3vsPres
RAD_external_SSP3[RAD_external_SSP3 == 0] <- NA
plot(RAD_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(RAD_external_SSP3, "RAD_external_SSP3.tif", overwrite=TRUE)

##################################################################################################################
# STY
###################################################################################################################

# CREATING LAYERS REFLECTING CURRENT DENSITY WITHIN INTERNAL AND EXTERNAL REFUGIA 

#############  ----------------  SSP2  ----------------  ############# 

# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
STY_internal_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
STY.Q.D. <- raster("STY.pred.AB_mean_present.tif")
STY_internal_SSP2 <- STY.Q.D. * mask_SSP2vsPres
STY_internal_SSP2[STY_internal_SSP2 == 0] <- NA
plot(STY_internal_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
writeRaster(STY_internal_SSP2, "STY_internal_SSP2.tif", overwrite=TRUE)


# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
STY_external_extent_SSP2 <- sum(na.omit(values(mask_SSP2vsPres)))
STY.Q.D. <- raster("STY.pred.AB_mean_present.tif")
STY_external_SSP2 <- STY.Q.D. * mask_SSP2vsPres
STY_external_SSP2[STY_external_SSP2 == 0] <- NA
plot(STY_external_SSP2)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
writeRaster(STY_external_SSP2, "STY_external_SSP2.tif", overwrite=TRUE)


#############  ----------------  SSP3  ----------------  #############


# INTERNAL REFUGIA 

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
STY_internal_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
STY.Q.D. <- raster("STY.pred.AB_mean_present.tif")
STY_internal_SSP3 <- STY.Q.D. * mask_SSP3vsPres
STY_internal_SSP3[STY_internal_SSP3 == 0] <- NA
plot(STY_internal_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
writeRaster(STY_internal_SSP3, "STY_internal_SSP3.tif", overwrite=TRUE)

# EXTERNAL REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
STY_external_extent_SSP3 <- sum(na.omit(values(mask_SSP3vsPres)))
STY.Q.D. <- raster("STY.pred.AB_mean_present.tif")
STY_external_SSP3 <- STY.Q.D. * mask_SSP3vsPres
STY_external_SSP3[STY_external_SSP3 == 0] <- NA
plot(STY_external_SSP3)
setwd(home)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
writeRaster(STY_external_SSP3, "STY_external_SSP3.tif", overwrite=TRUE)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

### ------------------------------  CALCUATEING dRBS (1.SAR; 2.TAXA SDM; 3. D & R values; 4.computing dRBS) ----------------------------------####

### #2; #3 and #4 repeat for baseline (previously calculated) and dRBS (calculated through the loop) and for different scanrios: 


# overall baseline (abundance at present-day BEFORE fishery impact)
# overall dRBS (abundance at present-day AFTER fishery impact)

# primary habitat baseline
# primary habitat dRBS

# internal refugia (under SSP2 and SSP3) baseline
# internal refugia (under SSP2 and SSP3) dRBS

# external refugia (under SSP2 and SSP3) baseline
# external refugia (under SSP2 and SSP3) dRBS


###################################################################################################################
# LOAD SAR
###################################################################################################################

# 1. load all SAR layers in list and generate 30-year RASTERBRICK (list of 30 layers)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/Present_Env_predictors_EEZ")
mask <- raster("Present_Bathymetry.tif")
mask[mask < 150] <- 1
plot(mask)

# creating the SAR object (list of 30 years length of fishing activity layers)
home <- "C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/"
setwd((home))
#dR_twl <- read.csv2("d and r_final.csv")

years <- c(1990:2019)
SAR <- list()
for (i in 1:length(years)){
  SAR[[i]] <- raster(paste("SAR/SAR_", years[i], ".tif", sep = ""))
  names(SAR)[i] <- paste("SAR_", years[i], sep = "")
  names(SAR[[i]]) <- paste("SAR_", years[i], sep = "")
  
  if (i == 1){
    SAR.30 <- SAR[[i]]
  } else {
    SAR.30 <- SAR.30 + SAR[[i]]
  }
}

# raster stack of all SAR over time
mask <- resample(mask, SAR[[1]], method="ngb")

SAR <- stack(SAR)
SAR <- SAR * mask
plot(SAR[[30]])

# mean SAR
SAR.30.mean <- SAR.30 / length(years)
SAR.30.mean <- SAR.30.mean * mask
plot(SAR.30.mean)
writeRaster(SAR.30.mean, "SAR.30.mean.tif", overwrite=TRUE)

# # adjusting SAR rasterbrick
# # adjusting extent of SAR 
# e <- extent(5149110, 7448471, -5653402, -2243293)
# # reset nrow and ncol
# s <- raster(e, nrows=3411, ncols=2300, crs=B@crs)
# # use this raster to reproject your original raster (crs is the same)
# SAR.r <- resample(SAR, s, method="ngb")
# #save SAR resampled (SAR.r)
# setwd(home)
# writeRaster(SAR.r, "SAR.r.tif", overwrite=TRUE)

#load SAR resampled (SAR.r)
setwd(home)
SAR.r <- brick('SAR.r.tif')

################################################################################
################################################################################

##################################################################################################################
# OVERALL
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_OVERALL")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_OVERALL")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

###################################################################################################################
# PRIMARY HABITATS 
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_PRIMARY")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_PRIMARY")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

###################################################################################################################
# INTERNAL REFUGIA (SSP2)
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_INTERNAL_SSP2")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

###################################################################################################################
# INTERNAL REFUGIA (SSP3)
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_INTERNAL_SSP3")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

###################################################################################################################
# EXTERNAL REFUGIA (SSP2)
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_EXTERNAL_SSP2")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

###################################################################################################################
# EXTERNAL REFUGIA (SSP3)
###################################################################################################################

### 2. Loading taxon SDMs in one go

# load d and R values
setwd(home)
dR_twl <- read.csv2("D AND R.csv")
taxon <- dR_twl$Taxon
taxon.names <- str_remove(list.files(paste0(home, "/BASELINE/TAXA_SDM_EXTERNAL_SSP3")), "_ENS_HUR.tif")

################################################################################
################################################################################

### 3. Loading all taxa distribution layers in list in one go

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")

taxa.r <- list()
for (i in 1:length(taxon)){
  taxa.r[[i]] <- raster(paste(taxon.names[i]))
  mask <- resample(mask, taxa.r[[1]], method="ngb")
  taxa.r[[i]] <- taxa.r[[i]] * mask
  names(taxa.r)[i] <- taxon[i]
  names(taxa.r[[i]]) <- taxon[i]
}
# plot(taxa.r[[4]])

################################################################################
################################################################################

### 4. Calculating dRBS

scenario <- c("base","best","worst")
D.comb <- c("d","d_lo","d_hi")
R.comb <- c("r","r_hi","r_lo")

for (i in 1:length(taxon)){
  t <- taxon[i]
  for (j in 1:length(scenario)){
    # taxon specific D and R
    D <- as.numeric(dR_twl[dR_twl$Taxon==t, D.comb[j]]); 
    R <- as.numeric(dR_twl[dR_twl$Taxon==t, R.comb[j]])
    # Carrying capacity and starting biomass as hurdle sdm prediction
    K <- taxa.r[[t]]; B <- taxa.r[[t]]
    # plot(K)
    
    # dRBS
    dRBS.t <- list()
    for(k in 1:nlayers(SAR.r)){
      Fishing <- SAR.r[[k]]
      chnge.B <- suppressWarnings(R * B * (1-B/K)-D*Fishing*B) # surpessing warning about different extents
      B <- B + chnge.B
      B[B < 0] <- 0
      # plot(B)
      
      dRBS.t[[k]] <- B
      names(dRBS.t)[k] <- names(SAR.r[[k]])
      names(dRBS.t[[k]]) <- names(SAR.r[[k]])
      
    }
    
    print(paste0("Finished Iteration For Taxa: ", t,", and Scenario: ", scenario[j]))
    dRBS.t <- stack(dRBS.t)
    
    setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
    writeRaster(dRBS.t[["layer.30"]], file = paste0(t, "_dRBS.t_", scenario[j], ".tif"), overwrite=TRUE)
    
  }
}

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

############# SUMMARY TABLE - BEFORE FISHERY IMPACT #############   DENSITY ####


density_matrix_refugia_baseline <- array(0, c(10,6))
colnames(density_matrix_refugia_baseline) <- c("overall","primary","internal_SSP2","internal_SSP3","external_SSP2", "external_SSP3")
rownames(density_matrix_refugia_baseline) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")

# OVERALL

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_OVERALL")
density_matrix_refugia_baseline[1,1] <- sum(na.omit(values(raster("CBR.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[2,1] <- sum(na.omit(values(raster("COB.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[3,1] <- sum(na.omit(values(raster("DEM.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[4,1] <- sum(na.omit(values(raster("GD.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[5,1] <- sum(na.omit(values(raster("GOC.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[6,1] <- sum(na.omit(values(raster("HEX.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[7,1] <- sum(na.omit(values(raster("PRI.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[8,1] <- sum(na.omit(values(raster("PTU.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[9,1] <- sum(na.omit(values(raster("RAD.pred.AB_mean_present.tif"))))
density_matrix_refugia_baseline[10,1] <- sum(na.omit(values(raster("STY.pred.AB_mean_present.tif"))))


# PRIMARY HABITATS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_PRIMARY")
density_matrix_refugia_baseline[1,2] <- sum(na.omit(values(raster("CBR.present.Q.D.tif"))))
density_matrix_refugia_baseline[2,2] <- sum(na.omit(values(raster("COB.present.Q.D.tif"))))
density_matrix_refugia_baseline[3,2] <- sum(na.omit(values(raster("DEM.present.Q.D.tif"))))
density_matrix_refugia_baseline[4,2] <- sum(na.omit(values(raster("GD.present.Q.D.tif"))))
density_matrix_refugia_baseline[5,2] <- sum(na.omit(values(raster("GOC.present.Q.D.tif"))))
density_matrix_refugia_baseline[6,2] <- sum(na.omit(values(raster("HEX.present.Q.D.tif"))))
density_matrix_refugia_baseline[7,2] <- sum(na.omit(values(raster("PRI.present.Q.D.tif"))))
density_matrix_refugia_baseline[8,2] <- sum(na.omit(values(raster("PTU.present.Q.D.tif"))))
density_matrix_refugia_baseline[9,2] <- sum(na.omit(values(raster("RAD.present.Q.D.tif"))))
density_matrix_refugia_baseline[10,2] <- sum(na.omit(values(raster("STY.present.Q.D.tif"))))

# REFUGIA

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
density_matrix_refugia_baseline[1,3] <- sum(na.omit(values(raster("CBR_internal_SSP2.tif"))))
density_matrix_refugia_baseline[2,3] <- sum(na.omit(values(raster("COB_internal_SSP2.tif"))))
density_matrix_refugia_baseline[3,3] <- sum(na.omit(values(raster("DEM_internal_SSP2.tif"))))
density_matrix_refugia_baseline[4,3] <- sum(na.omit(values(raster("GD_internal_SSP2.tif"))))
density_matrix_refugia_baseline[5,3] <- sum(na.omit(values(raster("GOC_internal_SSP2.tif"))))
density_matrix_refugia_baseline[6,3] <- sum(na.omit(values(raster("HEX_internal_SSP2.tif"))))
density_matrix_refugia_baseline[7,3] <- sum(na.omit(values(raster("PRI_internal_SSP2.tif"))))
density_matrix_refugia_baseline[8,3] <- sum(na.omit(values(raster("PTU_internal_SSP2.tif"))))
density_matrix_refugia_baseline[9,3] <- sum(na.omit(values(raster("RAD_internal_SSP2.tif"))))
density_matrix_refugia_baseline[10,3] <- sum(na.omit(values(raster("STY_internal_SSP2.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
density_matrix_refugia_baseline[1,4] <- sum(na.omit(values(raster("CBR_internal_SSP3.tif"))))
density_matrix_refugia_baseline[2,4] <- sum(na.omit(values(raster("COB_internal_SSP3.tif"))))
density_matrix_refugia_baseline[3,4] <- sum(na.omit(values(raster("DEM_internal_SSP3.tif"))))
density_matrix_refugia_baseline[4,4] <- sum(na.omit(values(raster("GD_internal_SSP3.tif"))))
density_matrix_refugia_baseline[5,4] <- sum(na.omit(values(raster("GOC_internal_SSP3.tif"))))
density_matrix_refugia_baseline[6,4] <- sum(na.omit(values(raster("HEX_internal_SSP3.tif"))))
density_matrix_refugia_baseline[7,4] <- sum(na.omit(values(raster("PRI_internal_SSP3.tif"))))
density_matrix_refugia_baseline[8,4] <- sum(na.omit(values(raster("PTU_internal_SSP3.tif"))))
density_matrix_refugia_baseline[9,4] <- sum(na.omit(values(raster("RAD_internal_SSP3.tif"))))
density_matrix_refugia_baseline[10,4] <- sum(na.omit(values(raster("STY_internal_SSP3.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
density_matrix_refugia_baseline[1,5] <- sum(na.omit(values(raster("CBR_external_SSP2.tif"))))
density_matrix_refugia_baseline[2,5] <- sum(na.omit(values(raster("COB_external_SSP2.tif"))))
density_matrix_refugia_baseline[3,5] <- sum(na.omit(values(raster("DEM_external_SSP2.tif"))))
density_matrix_refugia_baseline[4,5] <- sum(na.omit(values(raster("GD_external_SSP2.tif"))))
density_matrix_refugia_baseline[5,5] <- sum(na.omit(values(raster("GOC_external_SSP2.tif"))))
density_matrix_refugia_baseline[6,5] <- sum(na.omit(values(raster("HEX_external_SSP2.tif"))))
density_matrix_refugia_baseline[7,5] <- sum(na.omit(values(raster("PRI_external_SSP2.tif"))))
density_matrix_refugia_baseline[8,5] <- sum(na.omit(values(raster("PTU_external_SSP2.tif"))))
density_matrix_refugia_baseline[9,5] <- sum(na.omit(values(raster("RAD_external_SSP2.tif"))))
density_matrix_refugia_baseline[10,5] <- sum(na.omit(values(raster("STY_external_SSP2.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
density_matrix_refugia_baseline[1,6] <- sum(na.omit(values(raster("CBR_external_SSP3.tif"))))
density_matrix_refugia_baseline[2,6] <- sum(na.omit(values(raster("COB_external_SSP3.tif"))))
density_matrix_refugia_baseline[3,6] <- sum(na.omit(values(raster("DEM_external_SSP3.tif"))))
density_matrix_refugia_baseline[4,6] <- sum(na.omit(values(raster("GD_external_SSP3.tif"))))
density_matrix_refugia_baseline[5,6] <- sum(na.omit(values(raster("GOC_external_SSP3.tif"))))
density_matrix_refugia_baseline[6,6] <- sum(na.omit(values(raster("HEX_external_SSP3.tif"))))
density_matrix_refugia_baseline[7,6] <- sum(na.omit(values(raster("PRI_external_SSP3.tif"))))
density_matrix_refugia_baseline[8,6] <- sum(na.omit(values(raster("PTU_external_SSP3.tif"))))
density_matrix_refugia_baseline[9,6] <- sum(na.omit(values(raster("RAD_external_SSP3.tif"))))
density_matrix_refugia_baseline[10,6] <- sum(na.omit(values(raster("STY_external_SSP3.tif"))))


print(density_matrix_refugia_baseline)


################################################################################
################################################################################

############# SUMMARY TABLE - AFTER FISHERY IMPACT (dRBS calculation) #############  DENSITY ####

# NB. calculations are for "base" status. Switch with "worst" or "best" to calculate stats for other status

density_matrix_refugia_dRBS <- array(0, c(10,6))
colnames(density_matrix_refugia_dRBS) <- c("overall","primary","internal_SSP2","internal_SSP3","external_SSP2", "external_SSP3")
rownames(density_matrix_refugia_dRBS) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")


setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
density_matrix_refugia_dRBS[1,1] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,1] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,1] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,1] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,1] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,1] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,1] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[8,1] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,1] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,1] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
density_matrix_refugia_dRBS[1,2] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,2] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,2] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,2] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,2] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,2] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,2] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[8,2] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,2] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,2] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
density_matrix_refugia_dRBS[1,3] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,3] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,3] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,3] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,3] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,3] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,3] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[8,3] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,3] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,3] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
density_matrix_refugia_dRBS[1,4] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,4] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,4] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,4] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,4] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,4] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,4] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif")))) 
density_matrix_refugia_dRBS[8,4] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,4] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,4] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
density_matrix_refugia_dRBS[1,5] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,5] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,5] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,5] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,5] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,5] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,5] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[8,5] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,5] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,5] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
density_matrix_refugia_dRBS[1,6] <- sum(na.omit(values(raster("Scleractinia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[2,6] <- sum(na.omit(values(raster("Antipatharia_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[3,6] <- sum(na.omit(values(raster("Demospongiae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[4,6] <- sum(na.omit(values(raster("Goniocorella_dumosa_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[5,6] <- sum(na.omit(values(raster("Gorgonians_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[6,6] <- sum(na.omit(values(raster("Hexactinellida_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[7,6] <- sum(na.omit(values(raster("Primnoidae_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[8,6] <- sum(na.omit(values(raster("Pennatulacea_dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[9,6] <- sum(na.omit(values(raster("Radicipes_spp._dRBS.t_base.tif"))))
density_matrix_refugia_dRBS[10,6] <- sum(na.omit(values(raster("Stylasteridae_dRBS.t_base.tif"))))

print(density_matrix_refugia_baseline)
print(density_matrix_refugia_dRBS)

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


############################### EXTENT  ########################################

################################################################################
# CBR
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
CBR_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
CBR_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
CBR_internal_SSP2_dRBS <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
CBR.present <- raster("CBR.pred.AB_mean_present.tif")
Q_pres <- quantile(CBR.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
CBR_internal_ext_SSP2.Q_dRBS <- CBR_internal_SSP2_dRBS
CBR_internal_ext_SSP2.Q_dRBS[values(CBR_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
CBR_internal_ext_SSP2.Q_dRBS[values(CBR_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(CBR_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(CBR_internal_ext_SSP2.Q_dRBS, "CBR_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
CBR_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(CBR_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
CBR_internal_SSP3_dRBS <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
CBR.present <- raster("CBR.pred.AB_mean_present.tif")
Q_pres <- quantile(CBR.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
CBR_internal_ext_SSP3.Q_dRBS <- CBR_internal_SSP3_dRBS
CBR_internal_ext_SSP3.Q_dRBS[values(CBR_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
CBR_internal_ext_SSP3.Q_dRBS[values(CBR_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(CBR_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(CBR_internal_ext_SSP3.Q_dRBS, "CBR_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
CBR_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(CBR_internal_ext_SSP3.Q_dRBS)))


################################################################################
# COB
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
COB_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
COB_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
COB_internal_SSP2_dRBS <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
COB.present <- raster("COB.pred.AB_mean_present.tif")
Q_pres <- quantile(COB.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
COB_internal_ext_SSP2.Q_dRBS <- COB_internal_SSP2_dRBS
COB_internal_ext_SSP2.Q_dRBS[values(COB_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
COB_internal_ext_SSP2.Q_dRBS[values(COB_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(COB_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(COB_internal_ext_SSP2.Q_dRBS, "COB_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
COB_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(COB_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
COB_internal_SSP3_dRBS <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
COB.present <- raster("COB.pred.AB_mean_present.tif")
Q_pres <- quantile(COB.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
COB_internal_ext_SSP3.Q_dRBS <- COB_internal_SSP3_dRBS
COB_internal_ext_SSP3.Q_dRBS[values(COB_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
COB_internal_ext_SSP3.Q_dRBS[values(COB_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(COB_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(COB_internal_ext_SSP3.Q_dRBS, "COB_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
COB_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(COB_internal_ext_SSP3.Q_dRBS)))


################################################################################
# DEM
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
DEM_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
DEM_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
DEM_internal_SSP2_dRBS <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
DEM.present <- raster("DEM.pred.AB_mean_present.tif")
Q_pres <- quantile(DEM.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
DEM_internal_ext_SSP2.Q_dRBS <- DEM_internal_SSP2_dRBS
DEM_internal_ext_SSP2.Q_dRBS[values(DEM_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
DEM_internal_ext_SSP2.Q_dRBS[values(DEM_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(DEM_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(DEM_internal_ext_SSP2.Q_dRBS, "DEM_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
DEM_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(DEM_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
DEM_internal_SSP3_dRBS <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
DEM.present <- raster("DEM.pred.AB_mean_present.tif")
Q_pres <- quantile(DEM.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
DEM_internal_ext_SSP3.Q_dRBS <- DEM_internal_SSP3_dRBS
DEM_internal_ext_SSP3.Q_dRBS[values(DEM_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
DEM_internal_ext_SSP3.Q_dRBS[values(DEM_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(DEM_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(DEM_internal_ext_SSP3.Q_dRBS, "DEM_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
DEM_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(DEM_internal_ext_SSP3.Q_dRBS)))


################################################################################
# GD
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GD_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GD_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GD_internal_SSP2_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GD_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
GD.present <- raster("GD.pred.AB_mean_present.tif")
Q_pres <- quantile(GD.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
GD_internal_ext_SSP2.Q_dRBS <- GD_internal_SSP2_dRBS
GD_internal_ext_SSP2.Q_dRBS[values(GD_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
GD_internal_ext_SSP2.Q_dRBS[values(GD_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(GD_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GD_internal_ext_SSP2.Q_dRBS, "GD_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
GD_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(GD_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GD_internal_SSP3_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GD_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
GD.present <- raster("GD.pred.AB_mean_present.tif")
Q_pres <- quantile(GD.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
GD_internal_ext_SSP3.Q_dRBS <- GD_internal_SSP3_dRBS
GD_internal_ext_SSP3.Q_dRBS[values(GD_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
GD_internal_ext_SSP3.Q_dRBS[values(GD_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(GD_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GD_internal_ext_SSP3.Q_dRBS, "GD_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
GD_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(GD_internal_ext_SSP3.Q_dRBS)))

################################################################################
# GOC
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GOC_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GOC_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GOC_internal_SSP2_dRBS <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
GOC.present <- raster("GOC.pred.AB_mean_present.tif")
Q_pres <- quantile(GOC.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
GOC_internal_ext_SSP2.Q_dRBS <- GOC_internal_SSP2_dRBS
GOC_internal_ext_SSP2.Q_dRBS[values(GOC_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
GOC_internal_ext_SSP2.Q_dRBS[values(GOC_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(GOC_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GOC_internal_ext_SSP2.Q_dRBS, "GOC_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
GOC_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(GOC_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GOC_internal_SSP3_dRBS <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
GOC.present <- raster("GOC.pred.AB_mean_present.tif")
Q_pres <- quantile(GOC.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
GOC_internal_ext_SSP3.Q_dRBS <- GOC_internal_SSP3_dRBS
GOC_internal_ext_SSP3.Q_dRBS[values(GOC_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
GOC_internal_ext_SSP3.Q_dRBS[values(GOC_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(GOC_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GOC_internal_ext_SSP3.Q_dRBS, "GOC_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
GOC_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(GOC_internal_ext_SSP3.Q_dRBS)))

################################################################################
# HEX
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
HEX_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
HEX_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
HEX_internal_SSP2_dRBS <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
HEX.present <- raster("HEX.pred.AB_mean_present.tif")
Q_pres <- quantile(HEX.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
HEX_internal_ext_SSP2.Q_dRBS <- HEX_internal_SSP2_dRBS
HEX_internal_ext_SSP2.Q_dRBS[values(HEX_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
HEX_internal_ext_SSP2.Q_dRBS[values(HEX_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(HEX_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(HEX_internal_ext_SSP2.Q_dRBS, "HEX_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
HEX_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(HEX_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
HEX_internal_SSP3_dRBS <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
HEX.present <- raster("HEX.pred.AB_mean_present.tif")
Q_pres <- quantile(HEX.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
HEX_internal_ext_SSP3.Q_dRBS <- HEX_internal_SSP3_dRBS
HEX_internal_ext_SSP3.Q_dRBS[values(HEX_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
HEX_internal_ext_SSP3.Q_dRBS[values(HEX_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(HEX_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(HEX_internal_ext_SSP3.Q_dRBS, "HEX_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
HEX_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(HEX_internal_ext_SSP3.Q_dRBS)))

################################################################################
# PRI
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PRI_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PRI_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PRI_internal_SSP2_dRBS <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
PRI.present <- raster("PRI.pred.AB_mean_present.tif")
Q_pres <- quantile(PRI.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
PRI_internal_ext_SSP2.Q_dRBS <- PRI_internal_SSP2_dRBS
PRI_internal_ext_SSP2.Q_dRBS[values(PRI_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
PRI_internal_ext_SSP2.Q_dRBS[values(PRI_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(PRI_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PRI_internal_ext_SSP2.Q_dRBS, "PRI_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
PRI_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(PRI_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PRI_internal_SSP3_dRBS <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
PRI.present <- raster("PRI.pred.AB_mean_present.tif")
Q_pres <- quantile(PRI.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
PRI_internal_ext_SSP3.Q_dRBS <- PRI_internal_SSP3_dRBS
PRI_internal_ext_SSP3.Q_dRBS[values(PRI_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
PRI_internal_ext_SSP3.Q_dRBS[values(PRI_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(PRI_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PRI_internal_ext_SSP3.Q_dRBS, "PRI_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
PRI_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(PRI_internal_ext_SSP3.Q_dRBS)))

################################################################################
# PTU
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PTU_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PTU_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PTU_internal_SSP2_dRBS <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
PTU.present <- raster("PTU.pred.AB_mean_present.tif")
Q_pres <- quantile(PTU.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
PTU_internal_ext_SSP2.Q_dRBS <- PTU_internal_SSP2_dRBS
PTU_internal_ext_SSP2.Q_dRBS[values(PTU_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
PTU_internal_ext_SSP2.Q_dRBS[values(PTU_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(PTU_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PTU_internal_ext_SSP2.Q_dRBS, "PTU_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
PTU_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(PTU_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PTU_internal_SSP3_dRBS <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
PTU.present <- raster("PTU.pred.AB_mean_present.tif")
Q_pres <- quantile(PTU.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
PTU_internal_ext_SSP3.Q_dRBS <- PTU_internal_SSP3_dRBS
PTU_internal_ext_SSP3.Q_dRBS[values(PTU_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
PTU_internal_ext_SSP3.Q_dRBS[values(PTU_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(PTU_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PTU_internal_ext_SSP3.Q_dRBS, "PTU_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
PTU_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(PTU_internal_ext_SSP3.Q_dRBS)))

################################################################################
# RAD
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
RAD_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
RAD_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
RAD_internal_SSP2_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
RAD.present <- raster("RAD.pred.AB_mean_present.tif")
Q_pres <- quantile(RAD.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
RAD_internal_ext_SSP2.Q_dRBS <- RAD_internal_SSP2_dRBS
RAD_internal_ext_SSP2.Q_dRBS[values(RAD_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
RAD_internal_ext_SSP2.Q_dRBS[values(RAD_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(RAD_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(RAD_internal_ext_SSP2.Q_dRBS, "RAD_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
RAD_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(RAD_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
RAD_internal_SSP3_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
RAD.present <- raster("RAD.pred.AB_mean_present.tif")
Q_pres <- quantile(RAD.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
RAD_internal_ext_SSP3.Q_dRBS <- RAD_internal_SSP3_dRBS
RAD_internal_ext_SSP3.Q_dRBS[values(RAD_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
RAD_internal_ext_SSP3.Q_dRBS[values(RAD_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(RAD_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(RAD_internal_ext_SSP3.Q_dRBS, "RAD_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
RAD_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(RAD_internal_ext_SSP3.Q_dRBS)))

################################################################################
# STY
################################################################################

######  baseline

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==1] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
STY_internal_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==1] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
STY_internal_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# internal refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
STY_internal_SSP2_dRBS <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_internal_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
STY.present <- raster("STY.pred.AB_mean_present.tif")
Q_pres <- quantile(STY.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
STY_internal_ext_SSP2.Q_dRBS <- STY_internal_SSP2_dRBS
STY_internal_ext_SSP2.Q_dRBS[values(STY_internal_ext_SSP2.Q_dRBS) < Q_pres] <- 0
STY_internal_ext_SSP2.Q_dRBS[values(STY_internal_ext_SSP2.Q_dRBS) >= Q_pres] <- 1
plot(STY_internal_ext_SSP2.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(STY_internal_ext_SSP2.Q_dRBS, "STY_internal_ext_SSP2.Q_dRBS", overwrite=TRUE)
STY_internal_ext_SSP2.Q_dRBS <- sum(na.omit(values(STY_internal_ext_SSP2.Q_dRBS)))

# internal refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
STY_internal_SSP3_dRBS <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_internal_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
STY.present <- raster("STY.pred.AB_mean_present.tif")
Q_pres <- quantile(STY.present, na.rm=TRUE, probs = c(0.98)) # occurrence at 98th percentile (at present abundance)
STY_internal_ext_SSP3.Q_dRBS <- STY_internal_SSP3_dRBS
STY_internal_ext_SSP3.Q_dRBS[values(STY_internal_ext_SSP3.Q_dRBS) < Q_pres] <- 0
STY_internal_ext_SSP3.Q_dRBS[values(STY_internal_ext_SSP3.Q_dRBS) >= Q_pres] <- 1
plot(STY_internal_ext_SSP3.Q_dRBS)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(STY_internal_ext_SSP3.Q_dRBS, "STY_internal_ext_SSP3.Q_dRBS", overwrite=TRUE)
STY_internal_ext_SSP3.Q_dRBS <- sum(na.omit(values(STY_internal_ext_SSP3.Q_dRBS)))

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

############# SUMMARY TABLE - INTERNAL REFUGIA #############   EXTENT  ####

extent_matrix_internal_refugia <- array(0, c(10,4))
colnames(extent_matrix_internal_refugia) <- c("internal_SSP2_baseline","internal_SSP2_dRBS","internal_SSP3_baseline", "internal_SSP3_dRBS")
rownames(extent_matrix_internal_refugia) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")


extent_matrix_internal_refugia[1,1] <- CBR_internal_extent_SSP2_basline
extent_matrix_internal_refugia[1,2] <- CBR_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[1,3] <- CBR_internal_extent_SSP3_basline
extent_matrix_internal_refugia[1,4] <- CBR_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[2,1] <- COB_internal_extent_SSP2_basline
extent_matrix_internal_refugia[2,2] <- COB_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[2,3] <- COB_internal_extent_SSP3_basline
extent_matrix_internal_refugia[2,4] <- COB_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[3,1] <- DEM_internal_extent_SSP2_basline
extent_matrix_internal_refugia[3,2] <- DEM_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[3,3] <- DEM_internal_extent_SSP3_basline
extent_matrix_internal_refugia[3,4] <- DEM_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[4,1] <- GD_internal_extent_SSP2_basline
extent_matrix_internal_refugia[4,2] <- GD_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[4,3] <- GD_internal_extent_SSP3_basline
extent_matrix_internal_refugia[4,4] <- GD_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[5,1] <- GOC_internal_extent_SSP2_basline
extent_matrix_internal_refugia[5,2] <- GOC_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[5,3] <- GOC_internal_extent_SSP3_basline
extent_matrix_internal_refugia[5,4] <- GOC_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[6,1] <- HEX_internal_extent_SSP2_basline
extent_matrix_internal_refugia[6,2] <- HEX_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[6,3] <- HEX_internal_extent_SSP3_basline
extent_matrix_internal_refugia[6,4] <- HEX_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[7,1] <- PRI_internal_extent_SSP2_basline
extent_matrix_internal_refugia[7,2] <- PRI_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[7,3] <- PRI_internal_extent_SSP3_basline
extent_matrix_internal_refugia[7,4] <- PRI_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[8,1] <- PTU_internal_extent_SSP2_basline
extent_matrix_internal_refugia[8,2] <- PTU_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[8,3] <- PTU_internal_extent_SSP3_basline
extent_matrix_internal_refugia[8,4] <- PTU_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[9,1] <- RAD_internal_extent_SSP2_basline
extent_matrix_internal_refugia[9,2] <- RAD_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[9,3] <- RAD_internal_extent_SSP3_basline
extent_matrix_internal_refugia[9,4] <- RAD_internal_ext_SSP3.Q_dRBS

extent_matrix_internal_refugia[10,1] <- STY_internal_extent_SSP2_basline
extent_matrix_internal_refugia[10,2] <- STY_internal_ext_SSP2.Q_dRBS
extent_matrix_internal_refugia[10,3] <- STY_internal_extent_SSP3_basline
extent_matrix_internal_refugia[10,4] <- STY_internal_ext_SSP3.Q_dRBS


print(extent_matrix_internal_refugia)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

################################################################################
# CBR
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
CBR_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
CBR_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
CBR_external_SSP2_dRBS <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_external_SSP2_dRBS)
CBR_external.Q_SSP2_dRBS <- CBR_external_SSP2_dRBS * SSP2vsPres
plot(CBR_external.Q_SSP2_dRBS)
CBR_external.Q_SSP2_dRBS[values(CBR_external.Q_SSP2_dRBS) <= 0 ] <- 0
CBR_external.Q_SSP2_dRBS[values(CBR_external.Q_SSP2_dRBS) >= 1] <- 1
plot(CBR_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(CBR_external.Q_SSP2_dRBS, "CBR_external.Q_SSP2_dRBS", overwrite=TRUE)
CBR_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(CBR_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
CBR_external_SSP3_dRBS <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_external_SSP3_dRBS)
CBR_external.Q_SSP3_dRBS <- CBR_external_SSP3_dRBS * SSP3vsPres
plot(CBR_external.Q_SSP3_dRBS)
CBR_external.Q_SSP3_dRBS[values(CBR_external.Q_SSP3_dRBS) <= 0 ] <- 0
CBR_external.Q_SSP3_dRBS[values(CBR_external.Q_SSP3_dRBS) >= 1] <- 1
plot(CBR_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(CBR_external.Q_SSP3_dRBS, "CBR_external.Q_SSP3_dRBS", overwrite=TRUE)
CBR_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(CBR_external.Q_SSP3_dRBS)))


################################################################################
# COB
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
COB_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
COB_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
COB_external_SSP2_dRBS <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_external_SSP2_dRBS)
COB_external.Q_SSP2_dRBS <- COB_external_SSP2_dRBS * SSP2vsPres
plot(COB_external.Q_SSP2_dRBS)
COB_external.Q_SSP2_dRBS[values(COB_external.Q_SSP2_dRBS) <= 0 ] <- 0
COB_external.Q_SSP2_dRBS[values(COB_external.Q_SSP2_dRBS) >= 1] <- 1
plot(COB_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(COB_external.Q_SSP2_dRBS, "COB_external.Q_SSP2_dRBS", overwrite=TRUE)
COB_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(COB_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
COB_external_SSP3_dRBS <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_external_SSP3_dRBS)
COB_external.Q_SSP3_dRBS <- COB_external_SSP3_dRBS * SSP3vsPres
plot(COB_external.Q_SSP3_dRBS)
COB_external.Q_SSP3_dRBS[values(COB_external.Q_SSP3_dRBS) <= 0 ] <- 0
COB_external.Q_SSP3_dRBS[values(COB_external.Q_SSP3_dRBS) >= 1] <- 1
plot(COB_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(COB_external.Q_SSP3_dRBS, "COB_external.Q_SSP3_dRBS", overwrite=TRUE)
COB_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(COB_external.Q_SSP3_dRBS)))


################################################################################
# DEM
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
DEM_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
DEM_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
DEM_external_SSP2_dRBS <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_external_SSP2_dRBS)
DEM_external.Q_SSP2_dRBS <- DEM_external_SSP2_dRBS * SSP2vsPres
plot(DEM_external.Q_SSP2_dRBS)
DEM_external.Q_SSP2_dRBS[values(DEM_external.Q_SSP2_dRBS) <= 0 ] <- 0
DEM_external.Q_SSP2_dRBS[values(DEM_external.Q_SSP2_dRBS) >= 1] <- 1
plot(DEM_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(DEM_external.Q_SSP2_dRBS, "DEM_external.Q_SSP2_dRBS", overwrite=TRUE)
DEM_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(DEM_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
DEM_external_SSP3_dRBS <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_external_SSP3_dRBS)
DEM_external.Q_SSP3_dRBS <- DEM_external_SSP3_dRBS * SSP3vsPres
plot(DEM_external.Q_SSP3_dRBS)
DEM_external.Q_SSP3_dRBS[values(DEM_external.Q_SSP3_dRBS) <= 0 ] <- 0
DEM_external.Q_SSP3_dRBS[values(DEM_external.Q_SSP3_dRBS) >= 1] <- 1
plot(DEM_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(DEM_external.Q_SSP3_dRBS, "DEM_external.Q_SSP3_dRBS", overwrite=TRUE)
DEM_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(DEM_external.Q_SSP3_dRBS)))


################################################################################
# GDU
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GDU_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GDU_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GDU_external_SSP2_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_external_SSP2_dRBS)
GDU_external.Q_SSP2_dRBS <- GDU_external_SSP2_dRBS * SSP2vsPres
plot(GDU_external.Q_SSP2_dRBS)
GDU_external.Q_SSP2_dRBS[values(GDU_external.Q_SSP2_dRBS) <= 0 ] <- 0
GDU_external.Q_SSP2_dRBS[values(GDU_external.Q_SSP2_dRBS) >= 1] <- 1
plot(GDU_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GDU_external.Q_SSP2_dRBS, "GDU_external.Q_SSP2_dRBS", overwrite=TRUE)
GDU_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(GDU_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GDU_external_SSP3_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_external_SSP3_dRBS)
GDU_external.Q_SSP3_dRBS <- GDU_external_SSP3_dRBS * SSP3vsPres
plot(GDU_external.Q_SSP3_dRBS)
GDU_external.Q_SSP3_dRBS[values(GDU_external.Q_SSP3_dRBS) <= 0 ] <- 0
GDU_external.Q_SSP3_dRBS[values(GDU_external.Q_SSP3_dRBS) >= 1] <- 1
plot(GDU_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GDU_external.Q_SSP3_dRBS, "GDU_external.Q_SSP3_dRBS", overwrite=TRUE)
GDU_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(GDU_external.Q_SSP3_dRBS)))


################################################################################
# GOC
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
GOC_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
GOC_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GOC_external_SSP2_dRBS <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_external_SSP2_dRBS)
GOC_external.Q_SSP2_dRBS <- GOC_external_SSP2_dRBS * SSP2vsPres
plot(GOC_external.Q_SSP2_dRBS)
GOC_external.Q_SSP2_dRBS[values(GOC_external.Q_SSP2_dRBS) <= 0 ] <- 0
GOC_external.Q_SSP2_dRBS[values(GOC_external.Q_SSP2_dRBS) >= 1] <- 1
plot(GOC_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GOC_external.Q_SSP2_dRBS, "GOC_external.Q_SSP2_dRBS", overwrite=TRUE)
GOC_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(GOC_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GOC_external_SSP3_dRBS <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_external_SSP3_dRBS)
GOC_external.Q_SSP3_dRBS <- GOC_external_SSP3_dRBS * SSP3vsPres
plot(GOC_external.Q_SSP3_dRBS)
GOC_external.Q_SSP3_dRBS[values(GOC_external.Q_SSP3_dRBS) <= 0 ] <- 0
GOC_external.Q_SSP3_dRBS[values(GOC_external.Q_SSP3_dRBS) >= 1] <- 1
plot(GOC_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(GOC_external.Q_SSP3_dRBS, "GOC_external.Q_SSP3_dRBS", overwrite=TRUE)
GOC_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(GOC_external.Q_SSP3_dRBS)))


################################################################################
# HEX
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
HEX_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
HEX_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
HEX_external_SSP2_dRBS <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_external_SSP2_dRBS)
HEX_external.Q_SSP2_dRBS <- HEX_external_SSP2_dRBS * SSP2vsPres
plot(HEX_external.Q_SSP2_dRBS)
HEX_external.Q_SSP2_dRBS[values(HEX_external.Q_SSP2_dRBS) <= 0 ] <- 0
HEX_external.Q_SSP2_dRBS[values(HEX_external.Q_SSP2_dRBS) >= 1] <- 1
plot(HEX_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(HEX_external.Q_SSP2_dRBS, "HEX_external.Q_SSP2_dRBS", overwrite=TRUE)
HEX_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(HEX_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
HEX_external_SSP3_dRBS <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_external_SSP3_dRBS)
HEX_external.Q_SSP3_dRBS <- HEX_external_SSP3_dRBS * SSP3vsPres
plot(HEX_external.Q_SSP3_dRBS)
HEX_external.Q_SSP3_dRBS[values(HEX_external.Q_SSP3_dRBS) <= 0 ] <- 0
HEX_external.Q_SSP3_dRBS[values(HEX_external.Q_SSP3_dRBS) >= 1] <- 1
plot(HEX_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(HEX_external.Q_SSP3_dRBS, "HEX_external.Q_SSP3_dRBS", overwrite=TRUE)
HEX_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(HEX_external.Q_SSP3_dRBS)))


################################################################################
# PRI
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PRI_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PRI_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PRI_external_SSP2_dRBS <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_external_SSP2_dRBS)
PRI_external.Q_SSP2_dRBS <- PRI_external_SSP2_dRBS * SSP2vsPres
plot(PRI_external.Q_SSP2_dRBS)
PRI_external.Q_SSP2_dRBS[values(PRI_external.Q_SSP2_dRBS) <= 0 ] <- 0
PRI_external.Q_SSP2_dRBS[values(PRI_external.Q_SSP2_dRBS) >= 1] <- 1
plot(PRI_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PRI_external.Q_SSP2_dRBS, "PRI_external.Q_SSP2_dRBS", overwrite=TRUE)
PRI_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(PRI_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PRI_external_SSP3_dRBS <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_external_SSP3_dRBS)
PRI_external.Q_SSP3_dRBS <- PRI_external_SSP3_dRBS * SSP3vsPres
plot(PRI_external.Q_SSP3_dRBS)
PRI_external.Q_SSP3_dRBS[values(PRI_external.Q_SSP3_dRBS) <= 0 ] <- 0
PRI_external.Q_SSP3_dRBS[values(PRI_external.Q_SSP3_dRBS) >= 1] <- 1
plot(PRI_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PRI_external.Q_SSP3_dRBS, "PRI_external.Q_SSP3_dRBS", overwrite=TRUE)
PRI_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(PRI_external.Q_SSP3_dRBS)))


################################################################################
# PTU
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
PTU_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
PTU_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PTU_external_SSP2_dRBS <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_external_SSP2_dRBS)
PTU_external.Q_SSP2_dRBS <- PTU_external_SSP2_dRBS * SSP2vsPres
plot(PTU_external.Q_SSP2_dRBS)
PTU_external.Q_SSP2_dRBS[values(PTU_external.Q_SSP2_dRBS) <= 0 ] <- 0
PTU_external.Q_SSP2_dRBS[values(PTU_external.Q_SSP2_dRBS) >= 1] <- 1
plot(PTU_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PTU_external.Q_SSP2_dRBS, "PTU_external.Q_SSP2_dRBS", overwrite=TRUE)
PTU_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(PTU_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PTU_external_SSP3_dRBS <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_external_SSP3_dRBS)
PTU_external.Q_SSP3_dRBS <- PTU_external_SSP3_dRBS * SSP3vsPres
plot(PTU_external.Q_SSP3_dRBS)
PTU_external.Q_SSP3_dRBS[values(PTU_external.Q_SSP3_dRBS) <= 0 ] <- 0
PTU_external.Q_SSP3_dRBS[values(PTU_external.Q_SSP3_dRBS) >= 1] <- 1
plot(PTU_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(PTU_external.Q_SSP3_dRBS, "PTU_external.Q_SSP3_dRBS", overwrite=TRUE)
PTU_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(PTU_external.Q_SSP3_dRBS)))


################################################################################
# RAD
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
RAD_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
RAD_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
RAD_external_SSP2_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_external_SSP2_dRBS)
RAD_external.Q_SSP2_dRBS <- RAD_external_SSP2_dRBS * SSP2vsPres
plot(RAD_external.Q_SSP2_dRBS)
RAD_external.Q_SSP2_dRBS[values(RAD_external.Q_SSP2_dRBS) <= 0 ] <- 0
RAD_external.Q_SSP2_dRBS[values(RAD_external.Q_SSP2_dRBS) >= 1] <- 1
plot(RAD_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(RAD_external.Q_SSP2_dRBS, "RAD_external.Q_SSP2_dRBS", overwrite=TRUE)
RAD_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(RAD_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
RAD_external_SSP3_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_external_SSP3_dRBS)
RAD_external.Q_SSP3_dRBS <- RAD_external_SSP3_dRBS * SSP3vsPres
plot(RAD_external.Q_SSP3_dRBS)
RAD_external.Q_SSP3_dRBS[values(RAD_external.Q_SSP3_dRBS) <= 0 ] <- 0
RAD_external.Q_SSP3_dRBS[values(RAD_external.Q_SSP3_dRBS) >= 1] <- 1
plot(RAD_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(RAD_external.Q_SSP3_dRBS, "RAD_external.Q_SSP3_dRBS", overwrite=TRUE)
RAD_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(RAD_external.Q_SSP3_dRBS)))


################################################################################
# STY
################################################################################

######  baseline

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP2vsPres <- raster("SSP2vsPres.tif")
mask_SSP2vsPres <- SSP2vsPres
mask_SSP2vsPres[mask_SSP2vsPres ==2] <- 10
mask_SSP2vsPres[mask_SSP2vsPres <10] <- 0
mask_SSP2vsPres[mask_SSP2vsPres ==10] <- 1
plot(mask_SSP2vsPres)
STY_external_extent_SSP2_basline <- sum(na.omit(values(mask_SSP2vsPres)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
SSP3vsPres <- raster("SSP3vsPres.tif")
mask_SSP3vsPres <- SSP3vsPres
mask_SSP3vsPres[mask_SSP3vsPres ==2] <- 10
mask_SSP3vsPres[mask_SSP3vsPres <10] <- 0
mask_SSP3vsPres[mask_SSP3vsPres ==10] <- 1
plot(mask_SSP3vsPres)
STY_external_extent_SSP3_basline <- sum(na.omit(values(mask_SSP3vsPres)))


###### dRBS 

# external refugia SSP2

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
STY_external_SSP2_dRBS <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_external_SSP2_dRBS)
STY_external.Q_SSP2_dRBS <- STY_external_SSP2_dRBS * SSP2vsPres
plot(STY_external.Q_SSP2_dRBS)
STY_external.Q_SSP2_dRBS[values(STY_external.Q_SSP2_dRBS) <= 0 ] <- 0
STY_external.Q_SSP2_dRBS[values(STY_external.Q_SSP2_dRBS) >= 1] <- 1
plot(STY_external.Q_SSP2_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(STY_external.Q_SSP2_dRBS, "STY_external.Q_SSP2_dRBS", overwrite=TRUE)
STY_external_ext_SSP2.Q_dRBS <- sum(na.omit(values(STY_external.Q_SSP2_dRBS)))

# external refugia SSP3

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
STY_external_SSP3_dRBS <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_external_SSP3_dRBS)
STY_external.Q_SSP3_dRBS <- STY_external_SSP3_dRBS * SSP3vsPres
plot(STY_external.Q_SSP3_dRBS)
STY_external.Q_SSP3_dRBS[values(STY_external.Q_SSP3_dRBS) <= 0 ] <- 0
STY_external.Q_SSP3_dRBS[values(STY_external.Q_SSP3_dRBS) >= 1] <- 1
plot(STY_external.Q_SSP3_dRBS)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/extent")
writeRaster(STY_external.Q_SSP3_dRBS, "STY_external.Q_SSP3_dRBS", overwrite=TRUE)
STY_external_ext_SSP3.Q_dRBS <- sum(na.omit(values(STY_external.Q_SSP3_dRBS)))

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

############# SUMMARY TABLE - EXTERNAL REFUGIA #############   EXTENT  ####

extent_matrix_external_refugia <- array(0, c(10,4))
colnames(extent_matrix_external_refugia) <- c("external_SSP2_baseline","external_SSP2_dRBS","external_SSP3_baseline", "external_SSP3_dRBS")
rownames(extent_matrix_external_refugia) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")


extent_matrix_external_refugia[1,1] <- CBR_external_extent_SSP2_basline
extent_matrix_external_refugia[1,2] <- CBR_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[1,3] <- CBR_external_extent_SSP3_basline
extent_matrix_external_refugia[1,4] <- CBR_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[2,1] <- COB_external_extent_SSP2_basline
extent_matrix_external_refugia[2,2] <- COB_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[2,3] <- COB_external_extent_SSP3_basline
extent_matrix_external_refugia[2,4] <- COB_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[3,1] <- DEM_external_extent_SSP2_basline
extent_matrix_external_refugia[3,2] <- DEM_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[3,3] <- DEM_external_extent_SSP3_basline
extent_matrix_external_refugia[3,4] <- DEM_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[4,1] <- GDU_external_extent_SSP2_basline
extent_matrix_external_refugia[4,2] <- GDU_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[4,3] <- GDU_external_extent_SSP3_basline
extent_matrix_external_refugia[4,4] <- GDU_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[5,1] <- GOC_external_extent_SSP2_basline
extent_matrix_external_refugia[5,2] <- GOC_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[5,3] <- GOC_external_extent_SSP3_basline
extent_matrix_external_refugia[5,4] <- GOC_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[6,1] <- HEX_external_extent_SSP2_basline
extent_matrix_external_refugia[6,2] <- HEX_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[6,3] <- HEX_external_extent_SSP3_basline
extent_matrix_external_refugia[6,4] <- HEX_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[7,1] <- PRI_external_extent_SSP2_basline
extent_matrix_external_refugia[7,2] <- PRI_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[7,3] <- PRI_external_extent_SSP3_basline
extent_matrix_external_refugia[7,4] <- PRI_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[8,1] <- PTU_external_extent_SSP2_basline
extent_matrix_external_refugia[8,2] <- PTU_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[8,3] <- PTU_external_extent_SSP3_basline
extent_matrix_external_refugia[8,4] <- PTU_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[9,1] <- RAD_external_extent_SSP2_basline
extent_matrix_external_refugia[9,2] <- RAD_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[9,3] <- RAD_external_extent_SSP3_basline
extent_matrix_external_refugia[9,4] <- RAD_external_ext_SSP3.Q_dRBS

extent_matrix_external_refugia[10,1] <- STY_external_extent_SSP2_basline
extent_matrix_external_refugia[10,2] <- STY_external_ext_SSP2.Q_dRBS
extent_matrix_external_refugia[10,3] <- STY_external_extent_SSP3_basline
extent_matrix_external_refugia[10,4] <- STY_external_ext_SSP3.Q_dRBS


print(extent_matrix_internal_refugia)
print(extent_matrix_external_refugia)


#*******************************************************************************
#*******************************************************************************
#*******************************************************************************

#### DENSITY LOSS --- ISOLATING HABITAT LOSS FOLLOWING FISHING IMPACTS WITHIN INTERNAL REFUGIA

library(rgdal); library(sf); library(raster); library(stringr)

#===============================================================================
#===============================================================================

# REFUGIA (INTERNAL AND EXTERNAL)

#### internal refugia SSP2

# CBR


setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
CBR_baseline <- raster("CBR_internal_SSP2.tif")
plot(CBR_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
CBR_dRBS_SSP2 <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_dRBS_SSP2)
CBR_loss_SSP2_internal <- CBR_dRBS_SSP2 - CBR_baseline
plot(CBR_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(CBR_loss_SSP2_internal, "CBR_loss_SSP2_internal.tif", overwrite=TRUE)

CBR_loss_SSP2_internal[CBR_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# CBR

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
CBR_baseline <- raster("CBR_internal_SSP3.tif")
plot(CBR_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
CBR_dRBS_SSP3 <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_dRBS_SSP3)
CBR_loss_SSP3_internal <- CBR_dRBS_SSP3 - CBR_baseline
plot(CBR_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(CBR_loss_SSP3_internal, "CBR_loss_SSP3_internal.tif", overwrite=TRUE)

CBR_loss_SSP3_internal[CBR_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# CBR

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
CBR_baseline <- raster("CBR_external_SSP2.tif")
plot(CBR_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
CBR_dRBS_SSP2 <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_dRBS_SSP2)
CBR_loss_SSP2_external <- CBR_dRBS_SSP2 - CBR_baseline
plot(CBR_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(CBR_loss_SSP2_external, "CBR_loss_SSP2_external.tif", overwrite=TRUE)

CBR_loss_SSP2_external[CBR_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# CBR

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
CBR_baseline <- raster("CBR_external_SSP3.tif")
plot(CBR_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
CBR_dRBS_SSP3 <- raster("Scleractinia_dRBS.t_base.tif")
plot(CBR_dRBS_SSP3)
CBR_loss_SSP3_external <- CBR_dRBS_SSP3 - CBR_baseline
plot(CBR_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(CBR_loss_SSP3_external, "CBR_loss_SSP3_external.tif", overwrite=TRUE)

CBR_loss_SSP3_external[CBR_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


# COB

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
COB_baseline <- raster("COB_internal_SSP2.tif")
plot(COB_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
COB_dRBS_SSP2 <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_dRBS_SSP2)
COB_loss_SSP2_internal <- COB_dRBS_SSP2 - COB_baseline
plot(COB_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(COB_loss_SSP2_internal, "COB_loss_SSP2_internal.tif", overwrite=TRUE)

COB_loss_SSP2_internal[COB_loss_SSP2_internal >=0] <- NA


#### internal refugia SSP3

# COB

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
COB_baseline <- raster("COB_internal_SSP3.tif")
plot(COB_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
COB_dRBS_SSP3 <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_dRBS_SSP3)
COB_loss_SSP3_internal <- COB_dRBS_SSP3 - COB_baseline
plot(COB_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(COB_loss_SSP3_internal, "COB_loss_SSP3_internal.tif", overwrite=TRUE)

COB_loss_SSP3_internal[COB_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# COB

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
COB_baseline <- raster("COB_external_SSP2.tif")
plot(COB_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
COB_dRBS_SSP2 <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_dRBS_SSP2)
COB_loss_SSP2_external <- COB_dRBS_SSP2 - COB_baseline
plot(COB_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(COB_loss_SSP2_external, "COB_loss_SSP2_external.tif", overwrite=TRUE)

COB_loss_SSP2_external[COB_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# COB

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
COB_baseline <- raster("COB_external_SSP3.tif")
plot(COB_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
COB_dRBS_SSP3 <- raster("Antipatharia_dRBS.t_base.tif")
plot(COB_dRBS_SSP3)
COB_loss_SSP3_external <- COB_dRBS_SSP3 - COB_baseline
plot(COB_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(COB_loss_SSP3_external, "COB_loss_SSP3_external.tif", overwrite=TRUE)

COB_loss_SSP3_external[COB_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


# DEM

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
DEM_baseline <- raster("DEM_internal_SSP2.tif")
plot(DEM_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
DEM_dRBS_SSP2 <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_dRBS_SSP2)
DEM_loss_SSP2_internal <- DEM_dRBS_SSP2 - DEM_baseline
plot(DEM_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(DEM_loss_SSP2_internal, "DEM_loss_SSP2_internal.tif", overwrite=TRUE)

DEM_loss_SSP2_internal[DEM_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# DEM

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
DEM_baseline <- raster("DEM_internal_SSP3.tif")
plot(DEM_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
DEM_dRBS_SSP3 <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_dRBS_SSP3)
DEM_loss_SSP3_internal <- DEM_dRBS_SSP3 - DEM_baseline
plot(DEM_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(DEM_loss_SSP3_internal, "DEM_loss_SSP3_internal.tif", overwrite=TRUE)

DEM_loss_SSP3_internal[DEM_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# DEM

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
DEM_baseline <- raster("DEM_external_SSP2.tif")
plot(DEM_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
DEM_dRBS_SSP2 <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_dRBS_SSP2)
DEM_loss_SSP2_external <- DEM_dRBS_SSP2 - DEM_baseline
plot(DEM_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(DEM_loss_SSP2_external, "DEM_loss_SSP2_external.tif", overwrite=TRUE)

DEM_loss_SSP2_external[DEM_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# DEM

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
DEM_baseline <- raster("DEM_external_SSP3.tif")
plot(DEM_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
DEM_dRBS_SSP3 <- raster("Demospongiae_dRBS.t_base.tif")
plot(DEM_dRBS_SSP3)
DEM_loss_SSP3_external <- DEM_dRBS_SSP3 - DEM_baseline
plot(DEM_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(DEM_loss_SSP3_external, "DEM_loss_SSP3_external.tif", overwrite=TRUE)

DEM_loss_SSP3_external[DEM_loss_SSP3_external >=0] <- NA

###############################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# GDU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
GDU_baseline <- raster("GD_internal_SSP2.tif")
plot(GDU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GDU_dRBS_SSP2 <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_dRBS_SSP2)
GDU_loss_SSP2_internal <- GDU_dRBS_SSP2 - GDU_baseline
plot(GDU_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(GDU_loss_SSP2_internal, "GDU_loss_SSP2_internal.tif", overwrite=TRUE)

GDU_loss_SSP2_internal[GDU_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# GDU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
GDU_baseline <- raster("GD_internal_SSP3.tif")
plot(GDU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GDU_dRBS_SSP3 <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_dRBS_SSP3)
GDU_loss_SSP3_internal <- GDU_dRBS_SSP3 - GDU_baseline
plot(GDU_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(GDU_loss_SSP3_internal, "GDU_loss_SSP3_internal.tif", overwrite=TRUE)

GDU_loss_SSP3_internal[GDU_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# GDU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
GDU_baseline <- raster("GD_external_SSP2.tif")
plot(GDU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GDU_dRBS_SSP2 <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_dRBS_SSP2)
GDU_loss_SSP2_external <- GDU_dRBS_SSP2 - GDU_baseline
plot(GDU_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(GDU_loss_SSP2_external, "GDU_loss_SSP2_external.tif", overwrite=TRUE)

GDU_loss_SSP2_external[GDU_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# GDU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
GDU_baseline <- raster("GD_external_SSP3.tif")
plot(GDU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GDU_dRBS_SSP3 <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
plot(GDU_dRBS_SSP3)
GDU_loss_SSP3_external <- GDU_dRBS_SSP3 - GDU_baseline
plot(GDU_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(GDU_loss_SSP3_external, "GDU_loss_SSP3_external.tif", overwrite=TRUE)

GDU_loss_SSP3_external[GDU_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


# GOC

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
GOC_baseline <- raster("GOC_internal_SSP2.tif")
plot(GOC_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GOC_dRBS_SSP2 <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_dRBS_SSP2)
GOC_loss_SSP2_internal <- GOC_dRBS_SSP2 - GOC_baseline
plot(GOC_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(GOC_loss_SSP2_internal, "GOC_loss_SSP2_internal.tif", overwrite=TRUE)

GOC_loss_SSP2_internal[GOC_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# GOC

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
GOC_baseline <- raster("GOC_internal_SSP3.tif")
plot(GOC_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GOC_dRBS_SSP3 <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_dRBS_SSP3)
GOC_loss_SSP3_internal <- GOC_dRBS_SSP3 - GOC_baseline
plot(GOC_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(GOC_loss_SSP3_internal, "GOC_loss_SSP3_internal.tif", overwrite=TRUE)

GOC_loss_SSP3_internal[GOC_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# GOC

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
GOC_baseline <- raster("GOC_external_SSP2.tif")
plot(GOC_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GOC_dRBS_SSP2 <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_dRBS_SSP2)
GOC_loss_SSP2_external <- GOC_dRBS_SSP2 - GOC_baseline
plot(GOC_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(GOC_loss_SSP2_external, "GOC_loss_SSP2_external.tif", overwrite=TRUE)

GOC_loss_SSP2_external[GOC_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# GOC

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
GOC_baseline <- raster("GOC_external_SSP3.tif")
plot(GOC_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GOC_dRBS_SSP3 <- raster("Gorgonians_dRBS.t_base.tif")
plot(GOC_dRBS_SSP3)
GOC_loss_SSP3_external <- GOC_dRBS_SSP3 - GOC_baseline
plot(GOC_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(GOC_loss_SSP3_external, "GOC_loss_SSP3_external.tif", overwrite=TRUE)

GOC_loss_SSP3_external[GOC_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# HEX

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
HEX_baseline <- raster("HEX_internal_SSP2.tif")
plot(HEX_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
HEX_dRBS_SSP2 <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_dRBS_SSP2)
HEX_loss_SSP2_internal <- HEX_dRBS_SSP2 - HEX_baseline
plot(HEX_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(HEX_loss_SSP2_internal, "HEX_loss_SSP2_internal.tif", overwrite=TRUE)

HEX_loss_SSP2_internal[HEX_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# HEX

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
HEX_baseline <- raster("HEX_internal_SSP3.tif")
plot(HEX_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
HEX_dRBS_SSP3 <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_dRBS_SSP3)
HEX_loss_SSP3_internal <- HEX_dRBS_SSP3 - HEX_baseline
plot(HEX_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(HEX_loss_SSP3_internal, "HEX_loss_SSP3_internal.tif", overwrite=TRUE)

HEX_loss_SSP3_internal[HEX_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# HEX

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
HEX_baseline <- raster("HEX_external_SSP2.tif")
plot(HEX_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
HEX_dRBS_SSP2 <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_dRBS_SSP2)
HEX_loss_SSP2_external <- HEX_dRBS_SSP2 - HEX_baseline
plot(HEX_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(HEX_loss_SSP2_external, "HEX_loss_SSP2_external.tif", overwrite=TRUE)

HEX_loss_SSP2_external[HEX_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# HEX

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
HEX_baseline <- raster("HEX_external_SSP3.tif")
plot(HEX_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
HEX_dRBS_SSP3 <- raster("Hexactinellida_dRBS.t_base.tif")
plot(HEX_dRBS_SSP3)
HEX_loss_SSP3_external <- HEX_dRBS_SSP3 - HEX_baseline
plot(HEX_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(HEX_loss_SSP3_external, "HEX_loss_SSP3_external.tif", overwrite=TRUE)

HEX_loss_SSP3_external[HEX_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# PRI

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
PRI_baseline <- raster("PRI_internal_SSP2.tif")
plot(PRI_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PRI_dRBS_SSP2 <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_dRBS_SSP2)
PRI_loss_SSP2_internal <- PRI_dRBS_SSP2 - PRI_baseline
plot(PRI_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(PRI_loss_SSP2_internal, "PRI_loss_SSP2_internal.tif", overwrite=TRUE)

PRI_loss_SSP2_internal[PRI_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# PRI

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
PRI_baseline <- raster("PRI_internal_SSP3.tif")
plot(PRI_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PRI_dRBS_SSP3 <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_dRBS_SSP3)
PRI_loss_SSP3_internal <- PRI_dRBS_SSP3 - PRI_baseline
plot(PRI_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(PRI_loss_SSP3_internal, "PRI_loss_SSP3_internal.tif", overwrite=TRUE)

PRI_loss_SSP3_internal[PRI_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# PRI

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
PRI_baseline <- raster("PRI_external_SSP2.tif")
plot(PRI_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PRI_dRBS_SSP2 <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_dRBS_SSP2)
PRI_loss_SSP2_external <- PRI_dRBS_SSP2 - PRI_baseline
plot(PRI_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(PRI_loss_SSP2_external, "PRI_loss_SSP2_external.tif", overwrite=TRUE)

PRI_loss_SSP2_external[PRI_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# PRI

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
PRI_baseline <- raster("PRI_external_SSP3.tif")
plot(PRI_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PRI_dRBS_SSP3 <- raster("Primnoidae_dRBS.t_base.tif")
plot(PRI_dRBS_SSP3)
PRI_loss_SSP3_external <- PRI_dRBS_SSP3 - PRI_baseline
plot(PRI_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(PRI_loss_SSP3_external, "PRI_loss_SSP3_external.tif", overwrite=TRUE)

PRI_loss_SSP3_external[PRI_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# PTU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
PTU_baseline <- raster("PTU_internal_SSP2.tif")
plot(PTU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PTU_dRBS_SSP2 <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_dRBS_SSP2)
PTU_loss_SSP2_internal <- PTU_dRBS_SSP2 - PTU_baseline
plot(PTU_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(PTU_loss_SSP2_internal, "PTU_loss_SSP2_internal.tif", overwrite=TRUE)

PTU_loss_SSP2_internal[PTU_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# PTU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
PTU_baseline <- raster("PTU_internal_SSP3.tif")
plot(PTU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PTU_dRBS_SSP3 <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_dRBS_SSP3)
PTU_loss_SSP3_internal <- PTU_dRBS_SSP3 - PTU_baseline
plot(PTU_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(PTU_loss_SSP3_internal, "PTU_loss_SSP3_internal.tif", overwrite=TRUE)

PTU_loss_SSP3_internal[PTU_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# PTU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
PTU_baseline <- raster("PTU_external_SSP2.tif")
plot(PTU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PTU_dRBS_SSP2 <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_dRBS_SSP2)
PTU_loss_SSP2_external <- PTU_dRBS_SSP2 - PTU_baseline
plot(PTU_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(PTU_loss_SSP2_external, "PTU_loss_SSP2_external.tif", overwrite=TRUE)

PTU_loss_SSP2_external[PTU_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# PTU

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
PTU_baseline <- raster("PTU_external_SSP3.tif")
plot(PTU_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PTU_dRBS_SSP3 <- raster("Pennatulacea_dRBS.t_base.tif")
plot(PTU_dRBS_SSP3)
PTU_loss_SSP3_external <- PTU_dRBS_SSP3 - PTU_baseline
plot(PTU_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(PTU_loss_SSP3_external, "PTU_loss_SSP3_external.tif", overwrite=TRUE)

PTU_loss_SSP3_external[PTU_loss_SSP3_external >=0] <- NA


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


# RAD

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
RAD_baseline <- raster("RAD_internal_SSP2.tif")
plot(RAD_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
RAD_dRBS_SSP2 <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_dRBS_SSP2)
RAD_loss_SSP2_internal <- RAD_dRBS_SSP2 - RAD_baseline
plot(RAD_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(RAD_loss_SSP2_internal, "RAD_loss_SSP2_internal.tif", overwrite=TRUE)

RAD_loss_SSP2_internal[RAD_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# RAD

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
RAD_baseline <- raster("RAD_internal_SSP3.tif")
plot(RAD_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
RAD_dRBS_SSP3 <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_dRBS_SSP3)
RAD_loss_SSP3_internal <- RAD_dRBS_SSP3 - RAD_baseline
plot(RAD_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(RAD_loss_SSP3_internal, "RAD_loss_SSP3_internal.tif", overwrite=TRUE)

RAD_loss_SSP3_internal[RAD_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# RAD

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
RAD_baseline <- raster("RAD_external_SSP2.tif")
plot(RAD_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
RAD_dRBS_SSP2 <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_dRBS_SSP2)
RAD_loss_SSP2_external <- RAD_dRBS_SSP2 - RAD_baseline
plot(RAD_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(RAD_loss_SSP2_external, "RAD_loss_SSP2_external.tif", overwrite=TRUE)

RAD_loss_SSP2_external[RAD_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# RAD

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
RAD_baseline <- raster("RAD_external_SSP3.tif")
plot(RAD_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
RAD_dRBS_SSP3 <- raster("Radicipes_spp._dRBS.t_base.tif")
plot(RAD_dRBS_SSP3)
RAD_loss_SSP3_external <- RAD_dRBS_SSP3 - RAD_baseline
plot(RAD_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(RAD_loss_SSP3_external, "RAD_loss_SSP3_external.tif", overwrite=TRUE)

RAD_loss_SSP3_external[RAD_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


# STY

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
STY_baseline <- raster("STY_internal_SSP2.tif")
plot(STY_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
STY_dRBS_SSP2 <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_dRBS_SSP2)
STY_loss_SSP2_internal <- STY_dRBS_SSP2 - STY_baseline
plot(STY_loss_SSP2_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(STY_loss_SSP2_internal, "STY_loss_SSP2_internal.tif", overwrite=TRUE)

STY_loss_SSP2_internal[STY_loss_SSP2_internal >=0] <- NA

#### internal refugia SSP3

# STY

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
STY_baseline <- raster("STY_internal_SSP3.tif")
plot(STY_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
STY_dRBS_SSP3 <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_dRBS_SSP3)
STY_loss_SSP3_internal <- STY_dRBS_SSP3 - STY_baseline
plot(STY_loss_SSP3_internal)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(STY_loss_SSP3_internal, "STY_loss_SSP3_internal.tif", overwrite=TRUE)

STY_loss_SSP3_internal[STY_loss_SSP3_internal >=0] <- NA

#### external refugia SSP2

# STY

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP2")
STY_baseline <- raster("STY_external_SSP2.tif")
plot(STY_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
STY_dRBS_SSP2 <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_dRBS_SSP2)
STY_loss_SSP2_external <- STY_dRBS_SSP2 - STY_baseline
plot(STY_loss_SSP2_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP2")
writeRaster(STY_loss_SSP2_external, "STY_loss_SSP2_external.tif", overwrite=TRUE)

STY_loss_SSP2_external[STY_loss_SSP2_external >=0] <- NA

#### external refugia SSP3

# STY

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_external_SSP3")
STY_baseline <- raster("STY_external_SSP3.tif")
plot(STY_baseline)
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
STY_dRBS_SSP3 <- raster("Stylasteridae_dRBS.t_base.tif")
plot(STY_dRBS_SSP3)
STY_loss_SSP3_external <- STY_dRBS_SSP3 - STY_baseline
plot(STY_loss_SSP3_external)

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/loss/SSP3")
writeRaster(STY_loss_SSP3_external, "STY_loss_SSP3_external.tif", overwrite=TRUE)

STY_loss_SSP3_external[STY_loss_SSP3_external >=0] <- NA

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

############## SUMMARY TABLE - INTERNAL REFUGIA #############   

# SSP2

density_loss_matrix_internal_refugia_SSP2 <- array(0, c(10,3))
colnames(density_loss_matrix_internal_refugia_SSP2) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_internal_refugia_SSP2) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")

density_loss_matrix_internal_refugia_SSP2[1,1] <- sum(na.omit(values(CBR_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[1,2] <- mean(na.omit(values(CBR_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[1,3] <- min(na.omit(values(CBR_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[2,1] <- sum(na.omit(values(COB_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[2,2] <- mean(na.omit(values(COB_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[2,3] <- min(na.omit(values(COB_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[3,1] <- sum(na.omit(values(DEM_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[3,2] <- mean(na.omit(values(DEM_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[3,3] <- min(na.omit(values(DEM_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[4,1] <- sum(na.omit(values(GDU_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[4,2] <- mean(na.omit(values(GDU_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[4,3] <- min(na.omit(values(GDU_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[5,1] <- sum(na.omit(values(GOC_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[5,2] <- mean(na.omit(values(GOC_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[5,3] <- min(na.omit(values(GOC_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[6,1] <- sum(na.omit(values(HEX_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[6,2] <- mean(na.omit(values(HEX_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[6,3] <- min(na.omit(values(HEX_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[7,1] <- sum(na.omit(values(PRI_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[7,2] <- mean(na.omit(values(PRI_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[7,3] <- min(na.omit(values(PRI_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[8,1] <- sum(na.omit(values(PTU_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[8,2] <- mean(na.omit(values(PTU_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[8,3] <- min(na.omit(values(PTU_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[9,1] <- sum(na.omit(values(RAD_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[9,2] <- mean(na.omit(values(RAD_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[9,3] <- min(na.omit(values(RAD_loss_SSP2_internal)))

density_loss_matrix_internal_refugia_SSP2[10,1] <- sum(na.omit(values(STY_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[10,2] <- mean(na.omit(values(STY_loss_SSP2_internal)))
density_loss_matrix_internal_refugia_SSP2[10,3] <- min(na.omit(values(STY_loss_SSP2_internal)))


# SSP3

density_loss_matrix_internal_refugia_SSP3 <- array(0, c(10,3))
colnames(density_loss_matrix_internal_refugia_SSP3) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_internal_refugia_SSP3) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")

density_loss_matrix_internal_refugia_SSP3[1,1] <- sum(na.omit(values(CBR_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[1,2] <- mean(na.omit(values(CBR_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[1,3] <- min(na.omit(values(CBR_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[2,1] <- sum(na.omit(values(COB_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[2,2] <- mean(na.omit(values(COB_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[2,3] <- min(na.omit(values(COB_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[3,1] <- sum(na.omit(values(DEM_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[3,2] <- mean(na.omit(values(DEM_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[3,3] <- min(na.omit(values(DEM_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[4,1] <- sum(na.omit(values(GDU_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[4,2] <- mean(na.omit(values(GDU_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[4,3] <- min(na.omit(values(GDU_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[5,1] <- sum(na.omit(values(GOC_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[5,2] <- mean(na.omit(values(GOC_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[5,3] <- min(na.omit(values(GOC_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[6,1] <- sum(na.omit(values(HEX_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[6,2] <- mean(na.omit(values(HEX_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[6,3] <- min(na.omit(values(HEX_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[7,1] <- sum(na.omit(values(PRI_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[7,2] <- mean(na.omit(values(PRI_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[7,3] <- min(na.omit(values(PRI_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[8,1] <- sum(na.omit(values(PTU_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[8,2] <- mean(na.omit(values(PTU_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[8,3] <- min(na.omit(values(PTU_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[9,1] <- sum(na.omit(values(RAD_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[9,2] <- mean(na.omit(values(RAD_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[9,3] <- min(na.omit(values(RAD_loss_SSP3_internal)))

density_loss_matrix_internal_refugia_SSP3[10,1] <- sum(na.omit(values(STY_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[10,2] <- mean(na.omit(values(STY_loss_SSP3_internal)))
density_loss_matrix_internal_refugia_SSP3[10,3] <- min(na.omit(values(STY_loss_SSP3_internal)))

print(density_loss_matrix_internal_refugia_SSP2)
print(density_loss_matrix_internal_refugia_SSP3)


############# SUMMARY TABLE - EXTERNAL REFUGIA #############

# SSP2

density_loss_matrix_external_refugia_SSP2 <- array(0, c(10,3))
colnames(density_loss_matrix_external_refugia_SSP2) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_external_refugia_SSP2) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")

density_loss_matrix_external_refugia_SSP2[1,1] <- sum(na.omit(values(CBR_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[1,2] <- mean(na.omit(values(CBR_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[1,3] <- min(na.omit(values(CBR_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[2,1] <- sum(na.omit(values(COB_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[2,2] <- mean(na.omit(values(COB_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[2,3] <- min(na.omit(values(COB_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[3,1] <- sum(na.omit(values(DEM_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[3,2] <- mean(na.omit(values(DEM_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[3,3] <- min(na.omit(values(DEM_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[4,1] <- sum(na.omit(values(GDU_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[4,2] <- mean(na.omit(values(GDU_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[4,3] <- min(na.omit(values(GDU_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[5,1] <- sum(na.omit(values(GOC_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[5,2] <- mean(na.omit(values(GOC_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[5,3] <- min(na.omit(values(GOC_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[6,1] <- sum(na.omit(values(HEX_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[6,2] <- mean(na.omit(values(HEX_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[6,3] <- min(na.omit(values(HEX_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[7,1] <- sum(na.omit(values(PRI_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[7,2] <- mean(na.omit(values(PRI_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[7,3] <- min(na.omit(values(PRI_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[8,1] <- sum(na.omit(values(PTU_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[8,2] <- mean(na.omit(values(PTU_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[8,3] <- min(na.omit(values(PTU_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[9,1] <- sum(na.omit(values(RAD_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[9,2] <- mean(na.omit(values(RAD_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[9,3] <- min(na.omit(values(RAD_loss_SSP2_external)))

density_loss_matrix_external_refugia_SSP2[10,1] <- sum(na.omit(values(STY_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[10,2] <- mean(na.omit(values(STY_loss_SSP2_external)))
density_loss_matrix_external_refugia_SSP2[10,3] <- min(na.omit(values(STY_loss_SSP2_external)))


# SSP3

density_loss_matrix_external_refugia_SSP3 <- array(0, c(10,3))
colnames(density_loss_matrix_external_refugia_SSP3) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_external_refugia_SSP3) <- c("CBR", "COB", "DEM", "GDU", "GOC", "HEX", "PRI", "PTU", "RAD", "STY")

density_loss_matrix_external_refugia_SSP3[1,1] <- sum(na.omit(values(CBR_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[1,2] <- mean(na.omit(values(CBR_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[1,3] <- min(na.omit(values(CBR_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[2,1] <- sum(na.omit(values(COB_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[2,2] <- mean(na.omit(values(COB_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[2,3] <- min(na.omit(values(COB_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[3,1] <- sum(na.omit(values(DEM_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[3,2] <- mean(na.omit(values(DEM_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[3,3] <- min(na.omit(values(DEM_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[4,1] <- sum(na.omit(values(GDU_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[4,2] <- mean(na.omit(values(GDU_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[4,3] <- min(na.omit(values(GDU_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[5,1] <- sum(na.omit(values(GOC_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[5,2] <- mean(na.omit(values(GOC_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[5,3] <- min(na.omit(values(GOC_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[6,1] <- sum(na.omit(values(HEX_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[6,2] <- mean(na.omit(values(HEX_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[6,3] <- min(na.omit(values(HEX_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[7,1] <- sum(na.omit(values(PRI_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[7,2] <- mean(na.omit(values(PRI_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[7,3] <- min(na.omit(values(PRI_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[8,1] <- sum(na.omit(values(PTU_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[8,2] <- mean(na.omit(values(PTU_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[8,3] <- min(na.omit(values(PTU_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[9,1] <- sum(na.omit(values(RAD_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[9,2] <- mean(na.omit(values(RAD_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[9,3] <- min(na.omit(values(RAD_loss_SSP3_external)))

density_loss_matrix_external_refugia_SSP3[10,1] <- sum(na.omit(values(STY_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[10,2] <- mean(na.omit(values(STY_loss_SSP3_external)))
density_loss_matrix_external_refugia_SSP3[10,3] <- min(na.omit(values(STY_loss_SSP3_external)))

print(density_loss_matrix_external_refugia_SSP2)
print(density_loss_matrix_external_refugia_SSP3)


# recap 

print(density_loss_matrix_internal_refugia_SSP2)
print(density_loss_matrix_internal_refugia_SSP3)

print(density_loss_matrix_external_refugia_SSP2)
print(density_loss_matrix_external_refugia_SSP3)

################################################################################
#===============================================================================

library(rgdal); library(sf); library(raster); library(stringr)

# OVERALL AND PRIMARY HABITATS

# GDU

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
GDU_overall_baseline <- raster("GD.pred.AB_mean_present.tif") # overall
GDU_Q.D_baseline <- raster("GD.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
GDU_overall_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
GDU_Q.D_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif")

# loss
GDU_loss_overall <- GDU_overall_dRBS - GDU_overall_baseline
plot(GDU_loss_overall)

GDU_loss_Q.D <- GDU_Q.D_dRBS - GDU_Q.D_baseline
plot(GDU_loss_Q.D)

################################################################################

# CBR

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
CBR_overall_baseline <- raster("CBR.pred.AB_mean_present.tif") # overall
CBR_Q.D_baseline <- raster("CBR.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
CBR_overall_dRBS <- raster("Scleractinia_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
CBR_Q.D_dRBS <- raster("Scleractinia_dRBS.t_base.tif") # primary habitat

# loss
CBR_loss_overall <- CBR_overall_dRBS - CBR_overall_baseline
plot(CBR_loss_overall)

CBR_loss_Q.D <- CBR_Q.D_dRBS - CBR_Q.D_baseline
plot(CBR_loss_Q.D)

################################################################################

# COB

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
COB_overall_baseline <- raster("COB.pred.AB_mean_present.tif") # overall
COB_Q.D_baseline <- raster("COB.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
COB_overall_dRBS <- raster("Antipatharia_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
COB_Q.D_dRBS <- raster("Antipatharia_dRBS.t_base.tif") # primary habitat

# loss
COB_loss_overall <- COB_overall_dRBS - COB_overall_baseline
plot(COB_loss_overall)

COB_loss_Q.D <- COB_Q.D_dRBS - COB_Q.D_baseline
plot(COB_loss_Q.D)

################################################################################

# RAD

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
RAD_overall_baseline <- raster("RAD.pred.AB_mean_present.tif") # overall
RAD_Q.D_baseline <- raster("RAD.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
RAD_overall_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
RAD_Q.D_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif") # primary habitat

# loss
RAD_loss_overall <- RAD_overall_dRBS - RAD_overall_baseline
plot(RAD_loss_overall)

RAD_loss_Q.D <- RAD_Q.D_dRBS - RAD_Q.D_baseline
plot(RAD_loss_Q.D)

################################################################################

# PTU

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
PTU_overall_baseline <- raster("PTU.pred.AB_mean_present.tif") # overall
PTU_Q.D_baseline <- raster("PTU.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
PTU_overall_dRBS <- raster("Pennatulacea_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
PTU_Q.D_dRBS <- raster("Pennatulacea_dRBS.t_base.tif") # primary habitat

# loss
PTU_loss_overall <- PTU_overall_dRBS - PTU_overall_baseline
plot(PTU_loss_overall)

PTU_loss_Q.D <- PTU_Q.D_dRBS - PTU_Q.D_baseline
plot(PTU_loss_Q.D)

################################################################################

# GOC

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
GOC_overall_baseline <- raster("GOC.pred.AB_mean_present.tif") # overall
GOC_Q.D_baseline <- raster("GOC.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
GOC_overall_dRBS <- raster("Gorgonians_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
GOC_Q.D_dRBS <- raster("Gorgonians_dRBS.t_base.tif") # primary habitat

# loss
GOC_loss_overall <- GOC_overall_dRBS - GOC_overall_baseline
plot(GOC_loss_overall)

GOC_loss_Q.D <- GOC_Q.D_dRBS - GOC_Q.D_baseline
plot(GOC_loss_Q.D)

################################################################################

# PRI

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
PRI_overall_baseline <- raster("PRI.pred.AB_mean_present.tif") # overall
PRI_Q.D_baseline <- raster("PRI.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
PRI_overall_dRBS <- raster("Primnoidae_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
PRI_Q.D_dRBS <- raster("Primnoidae_dRBS.t_base.tif") # primary habitat

# loss
PRI_loss_overall <- PRI_overall_dRBS - PRI_overall_baseline
plot(PRI_loss_overall)

PRI_loss_Q.D <- PRI_Q.D_dRBS - PRI_Q.D_baseline
plot(PRI_loss_Q.D)

################################################################################

# STY

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
STY_overall_baseline <- raster("STY.pred.AB_mean_present.tif") # overall
STY_Q.D_baseline <- raster("STY.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
STY_overall_dRBS <- raster("Stylasteridae_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
STY_Q.D_dRBS <- raster("Stylasteridae_dRBS.t_base.tif") # primary habitat

# loss
STY_loss_overall <- STY_overall_dRBS - STY_overall_baseline
plot(STY_loss_overall)

STY_loss_Q.D <- STY_Q.D_dRBS - STY_Q.D_baseline
plot(STY_loss_Q.D)

################################################################################

# HEX

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
HEX_overall_baseline <- raster("HEX.pred.AB_mean_present.tif") # overall
HEX_Q.D_baseline <- raster("HEX.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
HEX_overall_dRBS <- raster("Hexactinellida_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
HEX_Q.D_dRBS <- raster("Hexactinellida_dRBS.t_base.tif") # primary habitat

# loss
HEX_loss_overall <- HEX_overall_dRBS - HEX_overall_baseline
plot(HEX_loss_overall)

HEX_loss_Q.D <- HEX_Q.D_dRBS - HEX_Q.D_baseline
plot(HEX_loss_Q.D)

################################################################################

# DEM

# Baseline

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
DEM_overall_baseline <- raster("DEM.pred.AB_mean_present.tif") # overall
DEM_Q.D_baseline <- raster("DEM.present.Q.D.tif") # primary habitat

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
DEM_overall_dRBS <- raster("Demospongiae_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
DEM_Q.D_dRBS <- raster("Demospongiae_dRBS.t_base.tif") # primary habitat

# loss
DEM_loss_overall <- DEM_overall_dRBS - DEM_overall_baseline
plot(DEM_loss_overall)

DEM_loss_Q.D <- DEM_Q.D_dRBS - DEM_Q.D_baseline
plot(DEM_loss_Q.D)


################################################################################
################################################################################
################################################################################
################################################################################

# Table Overall


density_loss_matrix_overall <- array(0, c(10,3))
colnames(density_loss_matrix_overall) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_overall) <- c("GDU", "CBR", "COB", "RAD", "PTU", "GOC", "PRI", "STY", "HEX", "DEM")

density_loss_matrix_overall[1,1] <- sum(na.omit(values(GDU_loss_overall)))
density_loss_matrix_overall[1,2] <- mean(na.omit(values(GDU_loss_overall)))
density_loss_matrix_overall[1,3] <- min(na.omit(values(GDU_loss_overall)))

density_loss_matrix_overall[2,1] <- sum(na.omit(values(CBR_loss_overall)))
density_loss_matrix_overall[2,2] <- mean(na.omit(values(CBR_loss_overall)))
density_loss_matrix_overall[2,3] <- min(na.omit(values(CBR_loss_overall)))

density_loss_matrix_overall[3,1] <- sum(na.omit(values(COB_loss_overall)))
density_loss_matrix_overall[3,2] <- mean(na.omit(values(COB_loss_overall)))
density_loss_matrix_overall[3,3] <- min(na.omit(values(COB_loss_overall)))

density_loss_matrix_overall[4,1] <- sum(na.omit(values(RAD_loss_overall)))
density_loss_matrix_overall[4,2] <- mean(na.omit(values(RAD_loss_overall)))
density_loss_matrix_overall[4,3] <- min(na.omit(values(RAD_loss_overall)))

density_loss_matrix_overall[5,1] <- sum(na.omit(values(PTU_loss_overall)))
density_loss_matrix_overall[5,2] <- mean(na.omit(values(PTU_loss_overall)))
density_loss_matrix_overall[5,3] <- min(na.omit(values(PTU_loss_overall)))

density_loss_matrix_overall[6,1] <- sum(na.omit(values(GOC_loss_overall)))
density_loss_matrix_overall[6,2] <- mean(na.omit(values(GOC_loss_overall)))
density_loss_matrix_overall[6,3] <- min(na.omit(values(GOC_loss_overall)))

density_loss_matrix_overall[7,1] <- sum(na.omit(values(PRI_loss_overall)))
density_loss_matrix_overall[7,2] <- mean(na.omit(values(PRI_loss_overall)))
density_loss_matrix_overall[7,3] <- min(na.omit(values(PRI_loss_overall)))

density_loss_matrix_overall[8,1] <- sum(na.omit(values(STY_loss_overall)))
density_loss_matrix_overall[8,2] <- mean(na.omit(values(STY_loss_overall)))
density_loss_matrix_overall[8,3] <- min(na.omit(values(STY_loss_overall)))

density_loss_matrix_overall[9,1] <- sum(na.omit(values(HEX_loss_overall)))
density_loss_matrix_overall[9,2] <- mean(na.omit(values(HEX_loss_overall)))
density_loss_matrix_overall[9,3] <- min(na.omit(values(HEX_loss_overall)))

density_loss_matrix_overall[10,1] <- sum(na.omit(values(DEM_loss_overall)))
density_loss_matrix_overall[10,2] <- mean(na.omit(values(DEM_loss_overall)))
density_loss_matrix_overall[10,3] <- min(na.omit(values(DEM_loss_overall)))


# Table dRBS

density_loss_matrix_Q.D <- array(0, c(10,3))
colnames(density_loss_matrix_Q.D) <- c("sum_loss","mean_loss","max_loss")
rownames(density_loss_matrix_Q.D) <- c("GDU", "CBR", "COB", "RAD", "PTU", "GOC", "PRI", "STY", "HEX", "DEM")

density_loss_matrix_Q.D[1,1] <- sum(na.omit(values(GDU_loss_Q.D)))
density_loss_matrix_Q.D[1,2] <- mean(na.omit(values(GDU_loss_Q.D)))
density_loss_matrix_Q.D[1,3] <- min(na.omit(values(GDU_loss_Q.D)))

density_loss_matrix_Q.D[2,1] <- sum(na.omit(values(CBR_loss_Q.D)))
density_loss_matrix_Q.D[2,2] <- mean(na.omit(values(CBR_loss_Q.D)))
density_loss_matrix_Q.D[2,3] <- min(na.omit(values(CBR_loss_Q.D)))

density_loss_matrix_Q.D[3,1] <- sum(na.omit(values(COB_loss_Q.D)))
density_loss_matrix_Q.D[3,2] <- mean(na.omit(values(COB_loss_Q.D)))
density_loss_matrix_Q.D[3,3] <- min(na.omit(values(COB_loss_Q.D)))

density_loss_matrix_Q.D[4,1] <- sum(na.omit(values(RAD_loss_Q.D)))
density_loss_matrix_Q.D[4,2] <- mean(na.omit(values(RAD_loss_Q.D)))
density_loss_matrix_Q.D[4,3] <- min(na.omit(values(RAD_loss_Q.D)))

density_loss_matrix_Q.D[5,1] <- sum(na.omit(values(PTU_loss_Q.D)))
density_loss_matrix_Q.D[5,2] <- mean(na.omit(values(PTU_loss_Q.D)))
density_loss_matrix_Q.D[5,3] <- min(na.omit(values(PTU_loss_Q.D)))

density_loss_matrix_Q.D[6,1] <- sum(na.omit(values(GOC_loss_Q.D)))
density_loss_matrix_Q.D[6,2] <- mean(na.omit(values(GOC_loss_Q.D)))
density_loss_matrix_Q.D[6,3] <- min(na.omit(values(GOC_loss_Q.D)))

density_loss_matrix_Q.D[7,1] <- sum(na.omit(values(PRI_loss_Q.D)))
density_loss_matrix_Q.D[7,2] <- mean(na.omit(values(PRI_loss_Q.D)))
density_loss_matrix_Q.D[7,3] <- min(na.omit(values(PRI_loss_Q.D)))

density_loss_matrix_Q.D[8,1] <- sum(na.omit(values(STY_loss_Q.D)))
density_loss_matrix_Q.D[8,2] <- mean(na.omit(values(STY_loss_Q.D)))
density_loss_matrix_Q.D[8,3] <- min(na.omit(values(STY_loss_Q.D)))

density_loss_matrix_Q.D[9,1] <- sum(na.omit(values(HEX_loss_Q.D)))
density_loss_matrix_Q.D[9,2] <- mean(na.omit(values(HEX_loss_Q.D)))
density_loss_matrix_Q.D[9,3] <- min(na.omit(values(HEX_loss_Q.D)))

density_loss_matrix_Q.D[10,1] <- sum(na.omit(values(DEM_loss_Q.D)))
density_loss_matrix_Q.D[10,2] <- mean(na.omit(values(DEM_loss_Q.D)))
density_loss_matrix_Q.D[10,3] <- min(na.omit(values(DEM_loss_Q.D)))

# recap 

print(density_loss_matrix_overall)
print(density_loss_matrix_Q.D)



#*******************************************************************************
#*******************************************************************************
#*******************************************************************************

# AGGREGATING TOTAL TAXA 


library(rgdal); library(sf); library(raster); library(stringr)

# Loading density layers

# CBR

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/CBR_final")
CBR_overall_baseline <- raster("CBR.pred.AB_mean_present.tif") # overall
CBR_Q.D_baseline <- raster("CBR.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
CBR_internal_baseline_SSP2 <- raster("CBR_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
CBR_external_baseline_SSP2 <- raster("CBR_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
CBR_internal_baseline_SSP3 <- raster("CBR_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
CBR_external_baseline_SSP3 <- raster("CBR_external_SSP3.tif") # external refugia SSP3

plot(CBR_overall_baseline)
plot(CBR_Q.D_baseline)
plot(CBR_internal_baseline_SSP2)
plot(CBR_internal_baseline_SSP3)
plot(CBR_external_baseline_SSP2)
plot(CBR_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
CBR_overall_dRBS <- raster("Scleractinia_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
CBR_Q.D_dRBS <- raster("Scleractinia_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
CBR_internal_dRBS_SSP2 <- raster("Scleractinia_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
CBR_external_dRBS_SSP2 <- raster("Scleractinia_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
CBR_internal_dRBS_SSP3 <- raster("Scleractinia_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
CBR_external_dRBS_SSP3 <- raster("Scleractinia_dRBS.t_base.tif") # external refugia SSP3

plot(CBR_overall_dRBS)
plot(CBR_Q.D_dRBS)
plot(CBR_internal_dRBS_SSP2)
plot(CBR_internal_dRBS_SSP3)
plot(CBR_external_dRBS_SSP2)
plot(CBR_external_dRBS_SSP3)


################################################################################
################################################################################
################################################################################

# COB

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/COB_final")
COB_overall_baseline <- raster("COB.pred.AB_mean_present.tif") # overall
COB_Q.D_baseline <- raster("COB.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
COB_internal_baseline_SSP2 <- raster("COB_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
COB_external_baseline_SSP2 <- raster("COB_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
COB_internal_baseline_SSP3 <- raster("COB_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
COB_external_baseline_SSP3 <- raster("COB_external_SSP3.tif") # external refugia SSP3

plot(COB_overall_baseline)
plot(COB_Q.D_baseline)
plot(COB_internal_baseline_SSP2)
plot(COB_internal_baseline_SSP3)
plot(COB_external_baseline_SSP2)
plot(COB_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
COB_overall_dRBS <- raster("Antipatharia_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
COB_Q.D_dRBS <- raster("Antipatharia_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
COB_internal_dRBS_SSP2 <- raster("Antipatharia_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
COB_external_dRBS_SSP2 <- raster("Antipatharia_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
COB_internal_dRBS_SSP3 <- raster("Antipatharia_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
COB_external_dRBS_SSP3 <- raster("Antipatharia_dRBS.t_base.tif") # external refugia SSP3

plot(COB_overall_dRBS)
plot(COB_Q.D_dRBS)
plot(COB_internal_dRBS_SSP2)
plot(COB_internal_dRBS_SSP3)
plot(COB_external_dRBS_SSP2)
plot(COB_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# DEM

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/DEM_final")
DEM_overall_baseline <- raster("DEM.pred.AB_mean_present.tif") # overall
DEM_Q.D_baseline <- raster("DEM.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
DEM_internal_baseline_SSP2 <- raster("DEM_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
DEM_external_baseline_SSP2 <- raster("DEM_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
DEM_internal_baseline_SSP3 <- raster("DEM_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
DEM_external_baseline_SSP3 <- raster("DEM_external_SSP3.tif") # external refugia SSP3

plot(DEM_overall_baseline)
plot(DEM_Q.D_baseline)
plot(DEM_internal_baseline_SSP2)
plot(DEM_internal_baseline_SSP3)
plot(DEM_external_baseline_SSP2)
plot(DEM_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
DEM_overall_dRBS <- raster("Demospongiae_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
DEM_Q.D_dRBS <- raster("Demospongiae_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
DEM_internal_dRBS_SSP2 <- raster("Demospongiae_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
DEM_external_dRBS_SSP2 <- raster("Demospongiae_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
DEM_internal_dRBS_SSP3 <- raster("Demospongiae_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
DEM_external_dRBS_SSP3 <- raster("Demospongiae_dRBS.t_base.tif") # external refugia SSP3

plot(DEM_overall_baseline)
plot(DEM_Q.D_baseline)
plot(DEM_internal_dRBS_SSP2)
plot(DEM_internal_dRBS_SSP3)
plot(DEM_external_dRBS_SSP2)
plot(DEM_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# GDU

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GD_final")
GDU_overall_baseline <- raster("GD.pred.AB_mean_present.tif") # overall
GDU_Q.D_baseline <- raster("GD.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
GDU_internal_baseline_SSP2 <- raster("GD_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
GDU_external_baseline_SSP2 <- raster("GD_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
GDU_internal_baseline_SSP3 <- raster("GD_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
GDU_external_baseline_SSP3 <- raster("GD_external_SSP3.tif") # external refugia SSP3

plot(GDU_overall_baseline)
plot(GDU_Q.D_baseline)
plot(GDU_internal_baseline_SSP2)
plot(GDU_internal_baseline_SSP3)
plot(GDU_external_baseline_SSP2)
plot(GDU_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
GDU_overall_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
GDU_Q.D_dRBS <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GDU_internal_dRBS_SSP2 <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GDU_external_dRBS_SSP2 <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GDU_internal_dRBS_SSP3 <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GDU_external_dRBS_SSP3 <- raster("Goniocorella_dumosa_dRBS.t_base.tif") # external refugia SSP3

plot(GDU_overall_dRBS)
plot(GDU_Q.D_dRBS)
plot(GDU_internal_dRBS_SSP2)
plot(GDU_internal_dRBS_SSP3)
plot(GDU_external_dRBS_SSP2)
plot(GDU_external_dRBS_SSP3)


################################################################################
################################################################################
################################################################################

# GOC

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/GOC_final")
GOC_overall_baseline <- raster("GOC.pred.AB_mean_present.tif") # overall
GOC_Q.D_baseline <- raster("GOC.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
GOC_internal_baseline_SSP2 <- raster("GOC_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
GOC_external_baseline_SSP2 <- raster("GOC_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
GOC_internal_baseline_SSP3 <- raster("GOC_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
GOC_external_baseline_SSP3 <- raster("GOC_external_SSP3.tif") # external refugia SSP3

plot(GOC_overall_baseline)
plot(GOC_Q.D_baseline)
plot(GOC_internal_baseline_SSP2)
plot(GOC_internal_baseline_SSP3)
plot(GOC_external_baseline_SSP2)
plot(GOC_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
GOC_overall_dRBS <- raster("Gorgonians_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
GOC_Q.D_dRBS <- raster("Gorgonians_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
GOC_internal_dRBS_SSP2 <- raster("Gorgonians_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
GOC_external_dRBS_SSP2 <- raster("Gorgonians_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
GOC_internal_dRBS_SSP3 <- raster("Gorgonians_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
GOC_external_dRBS_SSP3 <- raster("Gorgonians_dRBS.t_base.tif") # external refugia SSP3

plot(GOC_overall_baseline)
plot(GOC_Q.D_baseline)
plot(GOC_internal_dRBS_SSP2)
plot(GOC_internal_dRBS_SSP3)
plot(GOC_external_dRBS_SSP2)
plot(GOC_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# HEX

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/HEX_final")
HEX_overall_baseline <- raster("HEX.pred.AB_mean_present.tif") # overall
HEX_Q.D_baseline <- raster("HEX.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
HEX_internal_baseline_SSP2 <- raster("HEX_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
HEX_external_baseline_SSP2 <- raster("HEX_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
HEX_internal_baseline_SSP3 <- raster("HEX_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
HEX_external_baseline_SSP3 <- raster("HEX_external_SSP3.tif") # external refugia SSP3

plot(HEX_overall_baseline)
plot(HEX_Q.D_baseline)
plot(HEX_internal_baseline_SSP2)
plot(HEX_internal_baseline_SSP3)
plot(HEX_external_baseline_SSP2)
plot(HEX_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
HEX_overall_dRBS <- raster("Hexactinellida_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
HEX_Q.D_dRBS <- raster("Hexactinellida_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
HEX_internal_dRBS_SSP2 <- raster("Hexactinellida_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
HEX_external_dRBS_SSP2 <- raster("Hexactinellida_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
HEX_internal_dRBS_SSP3 <- raster("Hexactinellida_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
HEX_external_dRBS_SSP3 <- raster("Hexactinellida_dRBS.t_base.tif") # external refugia SSP3

plot(HEX_overall_baseline)
plot(HEX_Q.D_baseline)
plot(HEX_internal_dRBS_SSP2)
plot(HEX_internal_dRBS_SSP3)
plot(HEX_external_dRBS_SSP2)
plot(HEX_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# PRI

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PRI_final")
PRI_overall_baseline <- raster("PRI.pred.AB_mean_present.tif") # overall
PRI_Q.D_baseline <- raster("PRI.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
PRI_internal_baseline_SSP2 <- raster("PRI_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
PRI_external_baseline_SSP2 <- raster("PRI_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
PRI_internal_baseline_SSP3 <- raster("PRI_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
PRI_external_baseline_SSP3 <- raster("PRI_external_SSP3.tif") # external refugia SSP3

plot(PRI_overall_baseline)
plot(PRI_Q.D_baseline)
plot(PRI_internal_baseline_SSP2)
plot(PRI_internal_baseline_SSP3)
plot(PRI_external_baseline_SSP2)
plot(PRI_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
PRI_overall_dRBS <- raster("Primnoidae_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
PRI_Q.D_dRBS <- raster("Primnoidae_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PRI_internal_dRBS_SSP2 <- raster("Primnoidae_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PRI_external_dRBS_SSP2 <- raster("Primnoidae_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PRI_internal_dRBS_SSP3 <- raster("Primnoidae_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PRI_external_dRBS_SSP3 <- raster("Primnoidae_dRBS.t_base.tif") # external refugia SSP3

plot(PRI_overall_baseline)
plot(PRI_Q.D_baseline)
plot(PRI_internal_dRBS_SSP2)
plot(PRI_internal_dRBS_SSP3)
plot(PRI_external_dRBS_SSP2)
plot(PRI_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# PTU

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/PTU_final")
PTU_overall_baseline <- raster("PTU.pred.AB_mean_present.tif") # overall
PTU_Q.D_baseline <- raster("PTU.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
PTU_internal_baseline_SSP2 <- raster("PTU_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
PTU_external_baseline_SSP2 <- raster("PTU_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
PTU_internal_baseline_SSP3 <- raster("PTU_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
PTU_external_baseline_SSP3 <- raster("PTU_external_SSP3.tif") # external refugia SSP3

plot(PTU_overall_baseline)
plot(PTU_Q.D_baseline)
plot(PTU_internal_baseline_SSP2)
plot(PTU_internal_baseline_SSP3)
plot(PTU_external_baseline_SSP2)
plot(PTU_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
PTU_overall_dRBS <- raster("Pennatulacea_dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
PTU_Q.D_dRBS <- raster("Pennatulacea_dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
PTU_internal_dRBS_SSP2 <- raster("Pennatulacea_dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
PTU_external_dRBS_SSP2 <- raster("Pennatulacea_dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
PTU_internal_dRBS_SSP3 <- raster("Pennatulacea_dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
PTU_external_dRBS_SSP3 <- raster("Pennatulacea_dRBS.t_base.tif") # external refugia SSP3

plot(PTU_overall_baseline)
plot(PTU_Q.D_baseline)
plot(PTU_internal_dRBS_SSP2)
plot(PTU_internal_dRBS_SSP3)
plot(PTU_external_dRBS_SSP2)
plot(PTU_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# RAD

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/RAD_final")
RAD_overall_baseline <- raster("RAD.pred.AB_mean_present.tif") # overall
RAD_Q.D_baseline <- raster("RAD.present.Q.D.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
RAD_internal_baseline_SSP2 <- raster("RAD_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
RAD_external_baseline_SSP2 <- raster("RAD_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
RAD_internal_baseline_SSP3 <- raster("RAD_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
RAD_external_baseline_SSP3 <- raster("RAD_external_SSP3.tif") # external refugia SSP3

plot(RAD_overall_baseline)
plot(RAD_Q.D_baseline)
plot(RAD_internal_baseline_SSP2)
plot(RAD_internal_baseline_SSP3)
plot(RAD_external_baseline_SSP2)
plot(RAD_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
RAD_overall_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
RAD_Q.D_dRBS <- raster("Radicipes_spp._dRBS.t_base.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
RAD_internal_dRBS_SSP2 <- raster("Radicipes_spp._dRBS.t_base.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
RAD_external_dRBS_SSP2 <- raster("Radicipes_spp._dRBS.t_base.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
RAD_internal_dRBS_SSP3 <- raster("Radicipes_spp._dRBS.t_base.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
RAD_external_dRBS_SSP3 <- raster("Radicipes_spp._dRBS.t_base.tif") # external refugia SSP3

plot(RAD_overall_baseline)
plot(RAD_Q.D_baseline)
plot(RAD_internal_dRBS_SSP2)
plot(RAD_internal_dRBS_SSP3)
plot(RAD_external_dRBS_SSP2)
plot(RAD_external_dRBS_SSP3)

################################################################################
################################################################################
################################################################################

# STY

# BASELINE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 1/Training_Fabrice/R_files/STY_final")
STY_overall_baseline <- raster("STY.pred.AB_mean_present.tif") # overall
STY_Q.D_baseline <- raster("STY.present.Q.D.tif") # primary habitat
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP2")
STY_internal_baseline_SSP2 <- raster("STY_internal_SSP2.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP2")
STY_external_baseline_SSP2 <- raster("STY_external_SSP2.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_INTERNAL_SSP3")
STY_internal_baseline_SSP3 <- raster("STY_internal_SSP3.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/BASELINE/TAXA_SDM_EXTERNAL_SSP3")
STY_external_baseline_SSP3 <- raster("STY_external_SSP3.tif") # external refugia SSP3

plot(STY_overall_baseline)
plot(STY_Q.D_baseline)
plot(STY_internal_baseline_SSP2)
plot(STY_internal_baseline_SSP3)
plot(STY_external_baseline_SSP2)
plot(STY_external_baseline_SSP3)

# dRBS

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/overall")
STY_overall_dRBS <- raster("Stylasteridae_dRBS.t_best.tif") # overall
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/primary habitat")
STY_Q.D_dRBS <- raster("Stylasteridae_dRBS.t_best.tif") # primary habitat

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP2")
STY_internal_dRBS_SSP2 <- raster("Stylasteridae_dRBS.t_best.tif") # internal refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP2")
STY_external_dRBS_SSP2 <- raster("Stylasteridae_dRBS.t_best.tif") # external refugia SSP2
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/internal refugia_SSP3")
STY_internal_dRBS_SSP3 <- raster("Stylasteridae_dRBS.t_best.tif") # internal refugia SSP3
setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS/external refugia_SSP3")
STY_external_dRBS_SSP3 <- raster("Stylasteridae_dRBS.t_best.tif") # external refugia SSP3

plot(STY_overall_baseline)
plot(STY_Q.D_baseline)
plot(STY_internal_dRBS_SSP2)
plot(STY_internal_dRBS_SSP3)
plot(STY_external_dRBS_SSP2)
plot(STY_external_dRBS_SSP3)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
#===============================================================================
#===============================================================================
#===============================================================================
#===============================================================================
#===============================================================================
#===============================================================================
#===============================================================================
#===============================================================================

#=====================  CALCULATIONS ===========================================
#===============================================================================

######################### TOTAL VMEs taxa ######################################

# BASELINE

# overall

TOT_overall_baseline <- CBR_overall_baseline + 
  GDU_overall_baseline + 
  COB_overall_baseline + 
  DEM_overall_baseline +
  GOC_overall_baseline +
  HEX_overall_baseline +
  PRI_overall_baseline +
  PTU_overall_baseline +
  RAD_overall_baseline +
  STY_overall_baseline

plot(TOT_overall_baseline)

# primary habitats

TOT_primary_habitats_baseline <- CBR_Q.D_baseline + 
  GDU_Q.D_baseline + 
  COB_Q.D_baseline + 
  DEM_Q.D_baseline +
  GOC_Q.D_baseline +
  HEX_Q.D_baseline +
  PRI_Q.D_baseline +
  PTU_Q.D_baseline +
  RAD_Q.D_baseline +
  STY_Q.D_baseline

plot(TOT_primary_habitats_baseline)

# creating the mask file 

TOT_primary_habitats_baseline_mask <- CBR_Q.D_baseline + 
  GDU_Q.D_baseline + 
  COB_Q.D_baseline + 
  DEM_Q.D_baseline +
  GOC_Q.D_baseline +
  HEX_Q.D_baseline +
  PRI_Q.D_baseline +
  PTU_Q.D_baseline +
  RAD_Q.D_baseline +
  STY_Q.D_baseline

TOT_primary_habitats_baseline_mask[TOT_primary_habitats_baseline_mask>0] <- 1
plot(TOT_primary_habitats_baseline_mask)
TOT_primary_habitats_baseline_mask[TOT_primary_habitats_baseline_mask==0] <- 1


# creating raster files for internal refugia SSP2

CBR_internal_baseline_SSP2[is.na(CBR_internal_baseline_SSP2)] <- 0
CBR_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*CBR_internal_baseline_SSP2

GDU_internal_baseline_SSP2[is.na(GDU_internal_baseline_SSP2)] <- 0
GDU_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*GDU_internal_baseline_SSP2

COB_internal_baseline_SSP2[is.na(COB_internal_baseline_SSP2)] <- 0
COB_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*COB_internal_baseline_SSP2

GOC_internal_baseline_SSP2[is.na(GOC_internal_baseline_SSP2)] <- 0
GOC_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*GOC_internal_baseline_SSP2

DEM_internal_baseline_SSP2[is.na(DEM_internal_baseline_SSP2)] <- 0
DEM_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*DEM_internal_baseline_SSP2

HEX_internal_baseline_SSP2[is.na(HEX_internal_baseline_SSP2)] <- 0
HEX_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*HEX_internal_baseline_SSP2

PRI_internal_baseline_SSP2[is.na(PRI_internal_baseline_SSP2)] <- 0
PRI_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*PRI_internal_baseline_SSP2

PTU_internal_baseline_SSP2[is.na(PTU_internal_baseline_SSP2)] <- 0
PTU_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*PTU_internal_baseline_SSP2

RAD_internal_baseline_SSP2[is.na(RAD_internal_baseline_SSP2)] <- 0
RAD_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*RAD_internal_baseline_SSP2

STY_internal_baseline_SSP2[is.na(STY_internal_baseline_SSP2)] <- 0
STY_internal_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*STY_internal_baseline_SSP2

# creating raster files for internal refugia SSP3

CBR_internal_baseline_SSP3[is.na(CBR_internal_baseline_SSP3)] <- 0
CBR_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*CBR_internal_baseline_SSP3

GDU_internal_baseline_SSP3[is.na(GDU_internal_baseline_SSP3)] <- 0
GDU_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*GDU_internal_baseline_SSP3

COB_internal_baseline_SSP3[is.na(COB_internal_baseline_SSP3)] <- 0
COB_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*COB_internal_baseline_SSP3

GOC_internal_baseline_SSP3[is.na(GOC_internal_baseline_SSP3)] <- 0
GOC_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*GOC_internal_baseline_SSP3

DEM_internal_baseline_SSP3[is.na(DEM_internal_baseline_SSP3)] <- 0
DEM_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*DEM_internal_baseline_SSP3

HEX_internal_baseline_SSP3[is.na(HEX_internal_baseline_SSP3)] <- 0
HEX_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*HEX_internal_baseline_SSP3

PRI_internal_baseline_SSP3[is.na(PRI_internal_baseline_SSP3)] <- 0
PRI_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*PRI_internal_baseline_SSP3

PTU_internal_baseline_SSP3[is.na(PTU_internal_baseline_SSP3)] <- 0
PTU_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*PTU_internal_baseline_SSP3

RAD_internal_baseline_SSP3[is.na(RAD_internal_baseline_SSP3)] <- 0
RAD_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*RAD_internal_baseline_SSP3

STY_internal_baseline_SSP3[is.na(STY_internal_baseline_SSP3)] <- 0
STY_internal_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*STY_internal_baseline_SSP3


plot(CBR_internal_baseline_SSP2)
plot(GDU_internal_baseline_SSP2)
plot(COB_internal_baseline_SSP2)
plot(GOC_internal_baseline_SSP2)
plot(DEM_internal_baseline_SSP2)
plot(HEX_internal_baseline_SSP2)
plot(PRI_internal_baseline_SSP2)
plot(PTU_internal_baseline_SSP2)
plot(RAD_internal_baseline_SSP2)
plot(STY_internal_baseline_SSP2)

plot(CBR_internal_baseline_SSP3)
plot(GDU_internal_baseline_SSP3)
plot(COB_internal_baseline_SSP3)
plot(GOC_internal_baseline_SSP3)
plot(DEM_internal_baseline_SSP3)
plot(HEX_internal_baseline_SSP3)
plot(PRI_internal_baseline_SSP3)
plot(PTU_internal_baseline_SSP3)
plot(RAD_internal_baseline_SSP3)
plot(STY_internal_baseline_SSP3)


# internal refugia


TOT_internal_baseline_SSP2 <- CBR_internal_baseline_SSP2 + 
  GDU_internal_baseline_SSP2 + 
  COB_internal_baseline_SSP2 + 
  DEM_internal_baseline_SSP2 +
  GOC_internal_baseline_SSP2 +
  HEX_internal_baseline_SSP2 +
  PRI_internal_baseline_SSP2 +
  PTU_internal_baseline_SSP2 +
  RAD_internal_baseline_SSP2 +
  STY_internal_baseline_SSP2

TOT_internal_baseline_SSP3 <- CBR_internal_baseline_SSP3 + 
  GDU_internal_baseline_SSP3 + 
  COB_internal_baseline_SSP3 + 
  DEM_internal_baseline_SSP3 +
  GOC_internal_baseline_SSP3 +
  HEX_internal_baseline_SSP3 +
  PRI_internal_baseline_SSP3 +
  PTU_internal_baseline_SSP3 +
  RAD_internal_baseline_SSP3 +
  STY_internal_baseline_SSP3

plot(TOT_internal_baseline_SSP2)
plot(TOT_internal_baseline_SSP3)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# creating raster files for external refugia SSP2

CBR_external_baseline_SSP2[is.na(CBR_external_baseline_SSP2)] <- 0
CBR_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*CBR_external_baseline_SSP2

GDU_external_baseline_SSP2[is.na(GDU_external_baseline_SSP2)] <- 0
GDU_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*GDU_external_baseline_SSP2

COB_external_baseline_SSP2[is.na(COB_external_baseline_SSP2)] <- 0
COB_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*COB_external_baseline_SSP2

GOC_external_baseline_SSP2[is.na(GOC_external_baseline_SSP2)] <- 0
GOC_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*GOC_external_baseline_SSP2

DEM_external_baseline_SSP2[is.na(DEM_external_baseline_SSP2)] <- 0
DEM_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*DEM_external_baseline_SSP2

HEX_external_baseline_SSP2[is.na(HEX_external_baseline_SSP2)] <- 0
HEX_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*HEX_external_baseline_SSP2

PRI_external_baseline_SSP2[is.na(PRI_external_baseline_SSP2)] <- 0
PRI_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*PRI_external_baseline_SSP2

PTU_external_baseline_SSP2[is.na(PTU_external_baseline_SSP2)] <- 0
PTU_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*PTU_external_baseline_SSP2

RAD_external_baseline_SSP2[is.na(RAD_external_baseline_SSP2)] <- 0
RAD_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*RAD_external_baseline_SSP2

STY_external_baseline_SSP2[is.na(STY_external_baseline_SSP2)] <- 0
STY_external_baseline_SSP2 <- TOT_primary_habitats_baseline_mask*STY_external_baseline_SSP2

# creating raster files for external refugia SSP3

CBR_external_baseline_SSP3[is.na(CBR_external_baseline_SSP3)] <- 0
CBR_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*CBR_external_baseline_SSP3

GDU_external_baseline_SSP3[is.na(GDU_external_baseline_SSP3)] <- 0
GDU_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*GDU_external_baseline_SSP3

COB_external_baseline_SSP3[is.na(COB_external_baseline_SSP3)] <- 0
COB_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*COB_external_baseline_SSP3

GOC_external_baseline_SSP3[is.na(GOC_external_baseline_SSP3)] <- 0
GOC_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*GOC_external_baseline_SSP3

DEM_external_baseline_SSP3[is.na(DEM_external_baseline_SSP3)] <- 0
DEM_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*DEM_external_baseline_SSP3

HEX_external_baseline_SSP3[is.na(HEX_external_baseline_SSP3)] <- 0
HEX_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*HEX_external_baseline_SSP3

PRI_external_baseline_SSP3[is.na(PRI_external_baseline_SSP3)] <- 0
PRI_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*PRI_external_baseline_SSP3

PTU_external_baseline_SSP3[is.na(PTU_external_baseline_SSP3)] <- 0
PTU_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*PTU_external_baseline_SSP3

RAD_external_baseline_SSP3[is.na(RAD_external_baseline_SSP3)] <- 0
RAD_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*RAD_external_baseline_SSP3

STY_external_baseline_SSP3[is.na(STY_external_baseline_SSP3)] <- 0
STY_external_baseline_SSP3 <- TOT_primary_habitats_baseline_mask*STY_external_baseline_SSP3


plot(CBR_external_baseline_SSP2)
plot(GDU_external_baseline_SSP2)
plot(COB_external_baseline_SSP2)
plot(GOC_external_baseline_SSP2)
plot(DEM_external_baseline_SSP2)
plot(HEX_external_baseline_SSP2)
plot(PRI_external_baseline_SSP2)
plot(PTU_external_baseline_SSP2)
plot(RAD_external_baseline_SSP2)
plot(STY_external_baseline_SSP2)

plot(CBR_external_baseline_SSP3)
plot(GDU_external_baseline_SSP3)
plot(COB_external_baseline_SSP3)
plot(GOC_external_baseline_SSP3)
plot(DEM_external_baseline_SSP3)
plot(HEX_external_baseline_SSP3)
plot(PRI_external_baseline_SSP3)
plot(PTU_external_baseline_SSP3)
plot(RAD_external_baseline_SSP3)
plot(STY_external_baseline_SSP3)


# external refugia

TOT_external_baseline_SSP2 <- CBR_external_baseline_SSP2 + 
  GDU_external_baseline_SSP2 + 
  COB_external_baseline_SSP2 + 
  DEM_external_baseline_SSP2 +
  GOC_external_baseline_SSP2 +
  HEX_external_baseline_SSP2 +
  PRI_external_baseline_SSP2 +
  PTU_external_baseline_SSP2 +
  RAD_external_baseline_SSP2 +
  STY_external_baseline_SSP2

TOT_external_baseline_SSP3 <- CBR_external_baseline_SSP3 + 
  GDU_external_baseline_SSP3 + 
  COB_external_baseline_SSP3 + 
  DEM_external_baseline_SSP3 +
  GOC_external_baseline_SSP3 +
  HEX_external_baseline_SSP3 +
  PRI_external_baseline_SSP3 +
  PTU_external_baseline_SSP3 +
  RAD_external_baseline_SSP3 +
  STY_external_baseline_SSP3


plot(TOT_internal_baseline_SSP2)
plot(TOT_internal_baseline_SSP3)
plot(TOT_external_baseline_SSP2)
plot(TOT_external_baseline_SSP3)



################################################################################
################################################################################
################################################################################################################################################################
################################################################################
################################################################################
################################################################################################################################################################
################################################################################
################################################################################
################################################################################################################################################################
################################################################################
################################################################################
################################################################################

# dRBS

# overall

TOT_overall_dRBS <- CBR_overall_dRBS + 
  GDU_overall_dRBS + 
  COB_overall_dRBS + 
  DEM_overall_dRBS +
  GOC_overall_dRBS +
  HEX_overall_dRBS +
  PRI_overall_dRBS +
  PTU_overall_dRBS +
  RAD_overall_dRBS +
  STY_overall_dRBS

plot(TOT_overall_dRBS)

# primary habitats

# creating raster files for primary habitats

CBR_Q.D_dRBS[is.na(CBR_Q.D_dRBS)] <- 0
CBR_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*CBR_Q.D_dRBS

GDU_Q.D_dRBS[is.na(GDU_Q.D_dRBS)] <- 0
GDU_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*GDU_Q.D_dRBS

COB_Q.D_dRBS[is.na(COB_Q.D_dRBS)] <- 0
COB_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*COB_Q.D_dRBS

DEM_Q.D_dRBS[is.na(DEM_Q.D_dRBS)] <- 0
DEM_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*DEM_Q.D_dRBS

GOC_Q.D_dRBS[is.na(GOC_Q.D_dRBS)] <- 0
GOC_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*GOC_Q.D_dRBS

HEX_Q.D_dRBS[is.na(HEX_Q.D_dRBS)] <- 0
HEX_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*HEX_Q.D_dRBS

PTU_Q.D_dRBS[is.na(PTU_Q.D_dRBS)] <- 0
PTU_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*PTU_Q.D_dRBS

PRI_Q.D_dRBS[is.na(PRI_Q.D_dRBS)] <- 0
PRI_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*PRI_Q.D_dRBS

RAD_Q.D_dRBS[is.na(RAD_Q.D_dRBS)] <- 0
RAD_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*RAD_Q.D_dRBS

STY_Q.D_dRBS[is.na(STY_Q.D_dRBS)] <- 0
STY_Q.D_dRBS <- TOT_primary_habitats_baseline_mask*STY_Q.D_dRBS


TOT_primary_habitats_dRBS <- CBR_Q.D_dRBS + 
  GDU_Q.D_dRBS + 
  COB_Q.D_dRBS + 
  DEM_Q.D_dRBS +
  GOC_Q.D_dRBS +
  HEX_Q.D_dRBS +
  PRI_Q.D_dRBS +
  PTU_Q.D_dRBS +
  RAD_Q.D_dRBS +
  STY_Q.D_dRBS

plot(TOT_primary_habitats_dRBS)


# creating raster files for internal refugia SSP2

CBR_internal_dRBS_SSP2[is.na(CBR_internal_dRBS_SSP2)] <- 0
CBR_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*CBR_internal_dRBS_SSP2

GDU_internal_dRBS_SSP2[is.na(GDU_internal_dRBS_SSP2)] <- 0
GDU_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*GDU_internal_dRBS_SSP2

COB_internal_dRBS_SSP2[is.na(COB_internal_dRBS_SSP2)] <- 0
COB_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*COB_internal_dRBS_SSP2

GOC_internal_dRBS_SSP2[is.na(GOC_internal_dRBS_SSP2)] <- 0
GOC_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*GOC_internal_dRBS_SSP2

DEM_internal_dRBS_SSP2[is.na(DEM_internal_dRBS_SSP2)] <- 0
DEM_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*DEM_internal_dRBS_SSP2

HEX_internal_dRBS_SSP2[is.na(HEX_internal_dRBS_SSP2)] <- 0
HEX_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*HEX_internal_dRBS_SSP2

PRI_internal_dRBS_SSP2[is.na(PRI_internal_dRBS_SSP2)] <- 0
PRI_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*PRI_internal_dRBS_SSP2

PTU_internal_dRBS_SSP2[is.na(PTU_internal_dRBS_SSP2)] <- 0
PTU_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*PTU_internal_dRBS_SSP2

RAD_internal_dRBS_SSP2[is.na(RAD_internal_dRBS_SSP2)] <- 0
RAD_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*RAD_internal_dRBS_SSP2

STY_internal_dRBS_SSP2[is.na(STY_internal_dRBS_SSP2)] <- 0
STY_internal_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*STY_internal_dRBS_SSP2

# creating raster files for internal refugia SSP3

CBR_internal_dRBS_SSP3[is.na(CBR_internal_dRBS_SSP3)] <- 0
CBR_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*CBR_internal_dRBS_SSP3

GDU_internal_dRBS_SSP3[is.na(GDU_internal_dRBS_SSP3)] <- 0
GDU_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*GDU_internal_dRBS_SSP3

COB_internal_dRBS_SSP3[is.na(COB_internal_dRBS_SSP3)] <- 0
COB_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*COB_internal_dRBS_SSP3

GOC_internal_dRBS_SSP3[is.na(GOC_internal_dRBS_SSP3)] <- 0
GOC_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*GOC_internal_dRBS_SSP3

DEM_internal_dRBS_SSP3[is.na(DEM_internal_dRBS_SSP3)] <- 0
DEM_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*DEM_internal_dRBS_SSP3

HEX_internal_dRBS_SSP3[is.na(HEX_internal_dRBS_SSP3)] <- 0
HEX_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*HEX_internal_dRBS_SSP3

PRI_internal_dRBS_SSP3[is.na(PRI_internal_dRBS_SSP3)] <- 0
PRI_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*PRI_internal_dRBS_SSP3

PTU_internal_dRBS_SSP3[is.na(PTU_internal_dRBS_SSP3)] <- 0
PTU_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*PTU_internal_dRBS_SSP3

RAD_internal_dRBS_SSP3[is.na(RAD_internal_dRBS_SSP3)] <- 0
RAD_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*RAD_internal_dRBS_SSP3

STY_internal_dRBS_SSP3[is.na(STY_internal_dRBS_SSP3)] <- 0
STY_internal_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*STY_internal_dRBS_SSP3


plot(CBR_internal_dRBS_SSP2)
plot(GDU_internal_dRBS_SSP2)
plot(COB_internal_dRBS_SSP2)
plot(GOC_internal_dRBS_SSP2)
plot(DEM_internal_dRBS_SSP2)
plot(HEX_internal_dRBS_SSP2)
plot(PRI_internal_dRBS_SSP2)
plot(PTU_internal_dRBS_SSP2)
plot(RAD_internal_dRBS_SSP2)
plot(STY_internal_dRBS_SSP2)

plot(CBR_internal_dRBS_SSP3)
plot(GDU_internal_dRBS_SSP3)
plot(COB_internal_dRBS_SSP3)
plot(GOC_internal_dRBS_SSP3)
plot(DEM_internal_dRBS_SSP3)
plot(HEX_internal_dRBS_SSP3)
plot(PRI_internal_dRBS_SSP3)
plot(PTU_internal_dRBS_SSP3)
plot(RAD_internal_dRBS_SSP3)
plot(STY_internal_dRBS_SSP3)


# internal refugia


TOT_internal_dRBS_SSP2 <- CBR_internal_dRBS_SSP2 + 
  GDU_internal_dRBS_SSP2 + 
  COB_internal_dRBS_SSP2 + 
  DEM_internal_dRBS_SSP2 +
  GOC_internal_dRBS_SSP2 +
  HEX_internal_dRBS_SSP2 +
  PRI_internal_dRBS_SSP2 +
  PTU_internal_dRBS_SSP2 +
  RAD_internal_dRBS_SSP2 +
  STY_internal_dRBS_SSP2

TOT_internal_dRBS_SSP3 <- CBR_internal_dRBS_SSP3 + 
  GDU_internal_dRBS_SSP3 + 
  COB_internal_dRBS_SSP3 + 
  DEM_internal_dRBS_SSP3 +
  GOC_internal_dRBS_SSP3 +
  HEX_internal_dRBS_SSP3 +
  PRI_internal_dRBS_SSP3 +
  PTU_internal_dRBS_SSP3 +
  RAD_internal_dRBS_SSP3 +
  STY_internal_dRBS_SSP3

plot(TOT_internal_dRBS_SSP2)
plot(TOT_internal_dRBS_SSP3)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# creating raster files for external refugia SSP2

CBR_external_dRBS_SSP2[is.na(CBR_external_dRBS_SSP2)] <- 0
CBR_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*CBR_external_dRBS_SSP2

GDU_external_dRBS_SSP2[is.na(GDU_external_dRBS_SSP2)] <- 0
GDU_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*GDU_external_dRBS_SSP2

COB_external_dRBS_SSP2[is.na(COB_external_dRBS_SSP2)] <- 0
COB_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*COB_external_dRBS_SSP2

GOC_external_dRBS_SSP2[is.na(GOC_external_dRBS_SSP2)] <- 0
GOC_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*GOC_external_dRBS_SSP2

DEM_external_dRBS_SSP2[is.na(DEM_external_dRBS_SSP2)] <- 0
DEM_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*DEM_external_dRBS_SSP2

HEX_external_dRBS_SSP2[is.na(HEX_external_dRBS_SSP2)] <- 0
HEX_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*HEX_external_dRBS_SSP2

PRI_external_dRBS_SSP2[is.na(PRI_external_dRBS_SSP2)] <- 0
PRI_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*PRI_external_dRBS_SSP2

PTU_external_dRBS_SSP2[is.na(PTU_external_dRBS_SSP2)] <- 0
PTU_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*PTU_external_dRBS_SSP2

RAD_external_dRBS_SSP2[is.na(RAD_external_dRBS_SSP2)] <- 0
RAD_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*RAD_external_dRBS_SSP2

STY_external_dRBS_SSP2[is.na(STY_external_dRBS_SSP2)] <- 0
STY_external_dRBS_SSP2 <- TOT_primary_habitats_baseline_mask*STY_external_dRBS_SSP2

# creating raster files for external refugia SSP3

CBR_external_dRBS_SSP3[is.na(CBR_external_dRBS_SSP3)] <- 0
CBR_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*CBR_external_dRBS_SSP3

GDU_external_dRBS_SSP3[is.na(GDU_external_dRBS_SSP3)] <- 0
GDU_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*GDU_external_dRBS_SSP3

COB_external_dRBS_SSP3[is.na(COB_external_dRBS_SSP3)] <- 0
COB_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*COB_external_dRBS_SSP3

GOC_external_dRBS_SSP3[is.na(GOC_external_dRBS_SSP3)] <- 0
GOC_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*GOC_external_dRBS_SSP3

DEM_external_dRBS_SSP3[is.na(DEM_external_dRBS_SSP3)] <- 0
DEM_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*DEM_external_dRBS_SSP3

HEX_external_dRBS_SSP3[is.na(HEX_external_dRBS_SSP3)] <- 0
HEX_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*HEX_external_dRBS_SSP3

PRI_external_dRBS_SSP3[is.na(PRI_external_dRBS_SSP3)] <- 0
PRI_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*PRI_external_dRBS_SSP3

PTU_external_dRBS_SSP3[is.na(PTU_external_dRBS_SSP3)] <- 0
PTU_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*PTU_external_dRBS_SSP3

RAD_external_dRBS_SSP3[is.na(RAD_external_dRBS_SSP3)] <- 0
RAD_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*RAD_external_dRBS_SSP3

STY_external_dRBS_SSP3[is.na(STY_external_dRBS_SSP3)] <- 0
STY_external_dRBS_SSP3 <- TOT_primary_habitats_baseline_mask*STY_external_dRBS_SSP3


plot(CBR_external_dRBS_SSP2)
plot(GDU_external_dRBS_SSP2)
plot(COB_external_dRBS_SSP2)
plot(GOC_external_dRBS_SSP2)
plot(DEM_external_dRBS_SSP2)
plot(HEX_external_dRBS_SSP2)
plot(PRI_external_dRBS_SSP2)
plot(PTU_external_dRBS_SSP2)
plot(RAD_external_dRBS_SSP2)
plot(STY_external_dRBS_SSP2)

plot(CBR_external_dRBS_SSP3)
plot(GDU_external_dRBS_SSP3)
plot(COB_external_dRBS_SSP3)
plot(GOC_external_dRBS_SSP3)
plot(DEM_external_dRBS_SSP3)
plot(HEX_external_dRBS_SSP3)
plot(PRI_external_dRBS_SSP3)
plot(PTU_external_dRBS_SSP3)
plot(RAD_external_dRBS_SSP3)
plot(STY_external_dRBS_SSP3)


# external refugia

TOT_external_dRBS_SSP2 <- CBR_external_dRBS_SSP2 + 
  GDU_external_dRBS_SSP2 + 
  COB_external_dRBS_SSP2 + 
  DEM_external_dRBS_SSP2 +
  GOC_external_dRBS_SSP2 +
  HEX_external_dRBS_SSP2 +
  PRI_external_dRBS_SSP2 +
  PTU_external_dRBS_SSP2 +
  RAD_external_dRBS_SSP2 +
  STY_external_dRBS_SSP2

TOT_external_dRBS_SSP3 <- CBR_external_dRBS_SSP3 + 
  GDU_external_dRBS_SSP3 + 
  COB_external_dRBS_SSP3 + 
  DEM_external_dRBS_SSP3 +
  GOC_external_dRBS_SSP3 +
  HEX_external_dRBS_SSP3 +
  PRI_external_dRBS_SSP3 +
  PTU_external_dRBS_SSP3 +
  RAD_external_dRBS_SSP3 +
  STY_external_dRBS_SSP3

plot(TOT_external_dRBS_SSP2)
plot(TOT_external_dRBS_SSP3)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# RECAP

plot(TOT_overall_baseline)
plot(TOT_overall_dRBS)
plot(TOT_primary_habitats_baseline)
plot(TOT_primary_habitats_dRBS)
plot(TOT_internal_baseline_SSP2)
plot(TOT_internal_dRBS_SSP2)
plot(TOT_internal_baseline_SSP3)
plot(TOT_internal_dRBS_SSP3)
plot(TOT_external_baseline_SSP2)
plot(TOT_external_dRBS_SSP2)
plot(TOT_external_baseline_SSP3)
plot(TOT_external_dRBS_SSP3)

# SAVE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/VMEs")
writeRaster(TOT_overall_baseline, "TOT_overall_baseline.tif", overwrite=TRUE)
writeRaster(TOT_overall_dRBS, "TOT_overall_dRBS.tif", overwrite=TRUE)
writeRaster(TOT_primary_habitats_baseline, "TOT_primary_habitats_baseline.tif", overwrite=TRUE)
writeRaster(TOT_primary_habitats_dRBS, "TOT_primary_habitats_dRBS.tif", overwrite=TRUE)
writeRaster(TOT_internal_baseline_SSP2, "TOT_internal_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_internal_dRBS_SSP2, "TOT_internal_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_internal_baseline_SSP3, "TOT_internal_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(TOT_internal_dRBS_SSP3, "TOT_internal_dRBS_SSP3.tif", overwrite=TRUE)
writeRaster(TOT_external_baseline_SSP2, "TOT_external_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_external_dRBS_SSP2, "TOT_external_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_external_baseline_SSP3, "TOT_external_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(TOT_external_dRBS_SSP3, "TOT_external_dRBS_SSP3.tif", overwrite=TRUE)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################


################################ LOSS  #########################################

# overall

loss_CBR_overall <- CBR_overall_dRBS - CBR_overall_baseline 
loss_GDU_overall <- GDU_overall_dRBS - GDU_overall_baseline
loss_COB_overall <- COB_overall_dRBS - COB_overall_baseline
loss_GOC_overall <- GOC_overall_dRBS - GOC_overall_baseline
loss_DEM_overall <- DEM_overall_dRBS - DEM_overall_baseline
loss_HEX_overall <- HEX_overall_dRBS - HEX_overall_baseline
loss_PRI_overall <- PRI_overall_dRBS - PRI_overall_baseline
loss_PTU_overall <- PTU_overall_dRBS - PTU_overall_baseline
loss_RAD_overall <- RAD_overall_dRBS - RAD_overall_baseline
loss_STY_overall <- STY_overall_dRBS - STY_overall_baseline

TOT_loss_overall <- loss_CBR_overall + 
  loss_GDU_overall +
  loss_COB_overall +
  loss_GOC_overall +
  loss_DEM_overall +
  loss_HEX_overall +
  loss_PRI_overall +
  loss_PTU_overall +
  loss_RAD_overall +
  loss_STY_overall

plot(TOT_loss_overall)


# primary habitats

loss_CBR_primary_habitats <- CBR_Q.D_dRBS - CBR_Q.D_baseline 
loss_GDU_primary_habitats <- GDU_Q.D_dRBS - GDU_Q.D_baseline
loss_COB_primary_habitats <- COB_Q.D_dRBS - COB_Q.D_baseline
loss_GOC_primary_habitats <- GOC_Q.D_dRBS - GOC_Q.D_baseline
loss_DEM_primary_habitats <- DEM_Q.D_dRBS - DEM_Q.D_baseline
loss_HEX_primary_habitats <- HEX_Q.D_dRBS - HEX_Q.D_baseline
loss_PRI_primary_habitats <- PRI_Q.D_dRBS - PRI_Q.D_baseline
loss_PTU_primary_habitats <- PTU_Q.D_dRBS - PTU_Q.D_baseline
loss_RAD_primary_habitats <- RAD_Q.D_dRBS - RAD_Q.D_baseline
loss_STY_primary_habitats <- STY_Q.D_dRBS - STY_Q.D_baseline

TOT_loss_primary_habitats <- loss_CBR_primary_habitats + 
  loss_GDU_primary_habitats + 
  loss_COB_primary_habitats + 
  loss_GOC_primary_habitats +
  loss_DEM_primary_habitats +
  loss_HEX_primary_habitats +
  loss_PRI_primary_habitats +
  loss_PTU_primary_habitats +
  loss_RAD_primary_habitats +
  loss_STY_primary_habitats

plot(TOT_loss_primary_habitats)


# internal refugia SSP2

loss_CBR_internal_SSP2 <- CBR_internal_dRBS_SSP2 - CBR_internal_baseline_SSP2 
loss_GDU_internal_SSP2 <- GDU_internal_dRBS_SSP2 - GDU_internal_baseline_SSP2
loss_COB_internal_SSP2 <- COB_internal_dRBS_SSP2 - COB_internal_baseline_SSP2
loss_GOC_internal_SSP2 <- GOC_internal_dRBS_SSP2 - GOC_internal_baseline_SSP2
loss_DEM_internal_SSP2 <- DEM_internal_dRBS_SSP2 - DEM_internal_baseline_SSP2
loss_HEX_internal_SSP2 <- HEX_internal_dRBS_SSP2 - HEX_internal_baseline_SSP2
loss_PRI_internal_SSP2 <- PRI_internal_dRBS_SSP2 - PRI_internal_baseline_SSP2
loss_PTU_internal_SSP2 <- PTU_internal_dRBS_SSP2 - PTU_internal_baseline_SSP2
loss_RAD_internal_SSP2 <- RAD_internal_dRBS_SSP2 - RAD_internal_baseline_SSP2
loss_STY_internal_SSP2 <- STY_internal_dRBS_SSP2 - STY_internal_baseline_SSP2

TOT_loss_internal_SSP2 <- loss_CBR_internal_SSP2 + 
  loss_GDU_internal_SSP2 + 
  loss_COB_internal_SSP2 + 
  loss_GOC_internal_SSP2 +
  loss_DEM_internal_SSP2 +
  loss_HEX_internal_SSP2 +
  loss_PRI_internal_SSP2 +
  loss_PTU_internal_SSP2 +
  loss_RAD_internal_SSP2 +
  loss_STY_internal_SSP2

plot(TOT_loss_internal_SSP2)

# internal refugia SSP3

loss_CBR_internal_SSP3 <- CBR_internal_dRBS_SSP3 - CBR_internal_baseline_SSP3 
loss_GDU_internal_SSP3 <- GDU_internal_dRBS_SSP3 - GDU_internal_baseline_SSP3
loss_COB_internal_SSP3 <- COB_internal_dRBS_SSP3 - COB_internal_baseline_SSP3
loss_GOC_internal_SSP3 <- GOC_internal_dRBS_SSP3 - GOC_internal_baseline_SSP3
loss_DEM_internal_SSP3 <- DEM_internal_dRBS_SSP3 - DEM_internal_baseline_SSP3
loss_HEX_internal_SSP3 <- HEX_internal_dRBS_SSP3 - HEX_internal_baseline_SSP3
loss_PRI_internal_SSP3 <- PRI_internal_dRBS_SSP3 - PRI_internal_baseline_SSP3
loss_PTU_internal_SSP3 <- PTU_internal_dRBS_SSP3 - PTU_internal_baseline_SSP3
loss_RAD_internal_SSP3 <- RAD_internal_dRBS_SSP3 - RAD_internal_baseline_SSP3
loss_STY_internal_SSP3 <- STY_internal_dRBS_SSP3 - STY_internal_baseline_SSP3

TOT_loss_internal_SSP3 <- loss_CBR_internal_SSP3 + 
  loss_GDU_internal_SSP3 + 
  loss_COB_internal_SSP3 + 
  loss_GOC_internal_SSP3 +
  loss_DEM_internal_SSP3 +
  loss_HEX_internal_SSP3 +
  loss_PRI_internal_SSP3 +
  loss_PTU_internal_SSP3 +
  loss_RAD_internal_SSP3 +
  loss_STY_internal_SSP3

plot(TOT_loss_internal_SSP3)

################################################################################

# external refugia SSP2

loss_CBR_external_SSP2 <- CBR_external_dRBS_SSP2 - CBR_external_baseline_SSP2 
loss_GDU_external_SSP2 <- GDU_external_dRBS_SSP2 - GDU_external_baseline_SSP2
loss_COB_external_SSP2 <- COB_external_dRBS_SSP2 - COB_external_baseline_SSP2
loss_GOC_external_SSP2 <- GOC_external_dRBS_SSP2 - GOC_external_baseline_SSP2
loss_DEM_external_SSP2 <- DEM_external_dRBS_SSP2 - DEM_external_baseline_SSP2
loss_HEX_external_SSP2 <- HEX_external_dRBS_SSP2 - HEX_external_baseline_SSP2
loss_PRI_external_SSP2 <- PRI_external_dRBS_SSP2 - PRI_external_baseline_SSP2
loss_PTU_external_SSP2 <- PTU_external_dRBS_SSP2 - PTU_external_baseline_SSP2
loss_RAD_external_SSP2 <- RAD_external_dRBS_SSP2 - RAD_external_baseline_SSP2
loss_STY_external_SSP2 <- STY_external_dRBS_SSP2 - STY_external_baseline_SSP2

TOT_loss_external_SSP2 <- loss_CBR_external_SSP2 + 
  loss_GDU_external_SSP2 + 
  loss_COB_external_SSP2 + 
  loss_GOC_external_SSP2 +
  loss_DEM_external_SSP2 +
  loss_HEX_external_SSP2 +
  loss_PRI_external_SSP2 +
  loss_PTU_external_SSP2 +
  loss_RAD_external_SSP2 +
  loss_STY_external_SSP2

plot(TOT_loss_external_SSP2)

# external refugia SSP3

loss_CBR_external_SSP3 <- CBR_external_dRBS_SSP3 - CBR_external_baseline_SSP3 
loss_GDU_external_SSP3 <- GDU_external_dRBS_SSP3 - GDU_external_baseline_SSP3
loss_COB_external_SSP3 <- COB_external_dRBS_SSP3 - COB_external_baseline_SSP3
loss_GOC_external_SSP3 <- GOC_external_dRBS_SSP3 - GOC_external_baseline_SSP3
loss_DEM_external_SSP3 <- DEM_external_dRBS_SSP3 - DEM_external_baseline_SSP3
loss_HEX_external_SSP3 <- HEX_external_dRBS_SSP3 - HEX_external_baseline_SSP3
loss_PRI_external_SSP3 <- PRI_external_dRBS_SSP3 - PRI_external_baseline_SSP3
loss_PTU_external_SSP3 <- PTU_external_dRBS_SSP3 - PTU_external_baseline_SSP3
loss_RAD_external_SSP3 <- RAD_external_dRBS_SSP3 - RAD_external_baseline_SSP3
loss_STY_external_SSP3 <- STY_external_dRBS_SSP3 - STY_external_baseline_SSP3

TOT_loss_external_SSP3 <- loss_CBR_external_SSP3 + 
  loss_GDU_external_SSP3 + 
  loss_COB_external_SSP3 + 
  loss_GOC_external_SSP3 +
  loss_DEM_external_SSP3 +
  loss_HEX_external_SSP3 +
  loss_PRI_external_SSP3 +
  loss_PTU_external_SSP3 +
  loss_RAD_external_SSP3 +
  loss_STY_external_SSP3

plot(TOT_loss_external_SSP3)


# SAVE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/VMEs/loss")
writeRaster(TOT_loss_overall, "TOT_loss_overall.tif", overwrite=TRUE)
writeRaster(TOT_loss_primary_habitats, "TOT_loss_primary_habitats.tif", overwrite=TRUE)
writeRaster(TOT_loss_internal_SSP2, "TOT_loss_internal_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_loss_internal_SSP3, "TOT_loss_internal_SSP3.tif", overwrite=TRUE)
writeRaster(TOT_loss_external_SSP2, "TOT_loss_external_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_loss_external_SSP3, "TOT_loss_external_SSP3.tif", overwrite=TRUE)



##############################################################################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# WORKSHOP (DIFFERENT TAXA GROUP AGGREGATION, CWC, SPONGES, HYDROZOA)


# CWCs

# overall

CWCs_overall_baseline <- CBR_overall_baseline + 
  GDU_overall_baseline + 
  COB_overall_baseline + 
  GOC_overall_baseline +
  PRI_overall_baseline +
  PTU_overall_baseline +
  RAD_overall_baseline

plot(CWCs_overall_baseline)

CWCs_overall_dRBS <- CBR_overall_dRBS + 
  GDU_overall_dRBS + 
  COB_overall_dRBS + 
  GOC_overall_dRBS +
  PRI_overall_dRBS +
  PTU_overall_dRBS +
  RAD_overall_dRBS

plot(CWCs_overall_dRBS)

# primary habitats

CWCs_Q.D_baseline <- CBR_Q.D_baseline + 
  GDU_Q.D_baseline + 
  COB_Q.D_baseline + 
  GOC_Q.D_baseline +
  PRI_Q.D_baseline +
  PTU_Q.D_baseline +
  RAD_Q.D_baseline +
  STY_Q.D_baseline

plot(CWCs_Q.D_baseline)

CWCs_Q.D_dRBS <- CBR_Q.D_dRBS + 
  GDU_Q.D_dRBS + 
  COB_Q.D_dRBS + 
  GOC_Q.D_dRBS +
  PRI_Q.D_dRBS +
  PTU_Q.D_dRBS +
  RAD_Q.D_dRBS +
  STY_Q.D_dRBS

plot(CWCs_Q.D_dRBS)

# internal

CWCs_internal_baseline_SSP2 <- CBR_internal_baseline_SSP2 + 
  GDU_internal_baseline_SSP2 + 
  COB_internal_baseline_SSP2 + 
  GOC_internal_baseline_SSP2 +
  PRI_internal_baseline_SSP2 +
  PTU_internal_baseline_SSP2 +
  RAD_internal_baseline_SSP2 +
  STY_internal_baseline_SSP2

plot(CWCs_internal_baseline_SSP2)

CWCs_internal_dRBS_SSP2 <- CBR_internal_dRBS_SSP2 + 
  GDU_internal_dRBS_SSP2 + 
  COB_internal_dRBS_SSP2 + 
  GOC_internal_dRBS_SSP2 +
  PRI_internal_dRBS_SSP2 +
  PTU_internal_dRBS_SSP2 +
  RAD_internal_dRBS_SSP2 +
  STY_internal_dRBS_SSP2

plot(CWCs_internal_dRBS_SSP2)

CWCs_internal_baseline_SSP3 <- CBR_internal_baseline_SSP3 + 
  GDU_internal_baseline_SSP3 + 
  COB_internal_baseline_SSP3 + 
  GOC_internal_baseline_SSP3 +
  PRI_internal_baseline_SSP3 +
  PTU_internal_baseline_SSP3 +
  RAD_internal_baseline_SSP3 +
  STY_internal_baseline_SSP3

plot(CWCs_internal_baseline_SSP3)

CWCs_internal_dRBS_SSP3 <- CBR_internal_dRBS_SSP3 + 
  GDU_internal_dRBS_SSP3 + 
  COB_internal_dRBS_SSP3 + 
  GOC_internal_dRBS_SSP3 +
  PRI_internal_dRBS_SSP3 +
  PTU_internal_dRBS_SSP3 +
  RAD_internal_dRBS_SSP3 +
  STY_internal_dRBS_SSP3

plot(CWCs_internal_dRBS_SSP3)

# external

CWCs_external_baseline_SSP2 <- CBR_external_baseline_SSP2 + 
  GDU_external_baseline_SSP2 + 
  COB_external_baseline_SSP2 + 
  GOC_external_baseline_SSP2 +
  PRI_external_baseline_SSP2 +
  PTU_external_baseline_SSP2 +
  RAD_external_baseline_SSP2 +
  STY_external_baseline_SSP2

plot(CWCs_external_baseline_SSP2)

CWCs_external_dRBS_SSP2 <- CBR_external_dRBS_SSP2 + 
  GDU_external_dRBS_SSP2 + 
  COB_external_dRBS_SSP2 + 
  GOC_external_dRBS_SSP2 +
  PRI_external_dRBS_SSP2 +
  PTU_external_dRBS_SSP2 +
  RAD_external_dRBS_SSP2 +
  STY_external_dRBS_SSP2

plot(CWCs_external_dRBS_SSP2)

CWCs_external_baseline_SSP3 <- CBR_external_baseline_SSP3 + 
  GDU_external_baseline_SSP3 + 
  COB_external_baseline_SSP3 + 
  GOC_external_baseline_SSP3 +
  PRI_external_baseline_SSP3 +
  PTU_external_baseline_SSP3 +
  RAD_external_baseline_SSP3 +
  STY_external_baseline_SSP3

plot(CWCs_external_baseline_SSP3)

CWCs_external_dRBS_SSP3 <- CBR_external_dRBS_SSP3 + 
  GDU_external_dRBS_SSP3 + 
  COB_external_dRBS_SSP3 + 
  GOC_external_dRBS_SSP3 +
  PRI_external_dRBS_SSP3 +
  PTU_external_dRBS_SSP3 +
  RAD_external_dRBS_SSP3 +
  STY_external_dRBS_SSP3

plot(CWCs_external_dRBS_SSP3)

################################################################################

# Sponges

# overall

Sponges_overall_baseline <- DEM_overall_baseline + HEX_overall_baseline
plot(Sponges_overall_baseline)

Sponges_overall_dRBS <- DEM_overall_dRBS + HEX_overall_dRBS
plot(Sponges_overall_dRBS)

# primary habitats

Sponges_Q.D_baseline <- DEM_Q.D_baseline + HEX_Q.D_baseline
plot(Sponges_Q.D_baseline)

Sponges_Q.D_dRBS <- DEM_Q.D_dRBS + HEX_Q.D_dRBS
plot(Sponges_Q.D_dRBS)

# internal
Sponges_internal_baseline_SSP2 <- DEM_internal_baseline_SSP2 + HEX_internal_baseline_SSP2
plot(Sponges_internal_baseline_SSP2)

Sponges_internal_baseline_SSP3 <- DEM_internal_baseline_SSP3 + HEX_internal_baseline_SSP3
plot(Sponges_internal_baseline_SSP3)

Sponges_internal_dRBS_SSP2 <- DEM_internal_dRBS_SSP2 + HEX_internal_dRBS_SSP2
plot(Sponges_internal_dRBS_SSP2)

Sponges_internal_dRBS_SSP3 <- DEM_internal_dRBS_SSP3 + HEX_internal_dRBS_SSP3
plot(Sponges_internal_dRBS_SSP3)

# external
Sponges_external_baseline_SSP2 <- DEM_external_baseline_SSP2 + HEX_external_baseline_SSP2
plot(Sponges_external_baseline_SSP2)

Sponges_external_baseline_SSP3 <- DEM_external_baseline_SSP3 + HEX_external_baseline_SSP3
plot(Sponges_external_baseline_SSP3)

Sponges_external_dRBS_SSP2 <- DEM_external_dRBS_SSP2 + HEX_external_dRBS_SSP2
plot(Sponges_external_dRBS_SSP2)

Sponges_external_dRBS_SSP3 <- DEM_external_dRBS_SSP3 + HEX_external_dRBS_SSP3
plot(Sponges_external_dRBS_SSP3)


# Hydrozoa

# overall

# HYD_overall_dRBS <- STY_overall_dRBS

# plot(HYD_overall_dRBS)

# primary habitats

# HYD_Q.D_dRBS <- STY_Q.D_dRBS

# plot(HYD_Q.D_dRBS)


# refugia total (internal + external)



# SAVE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/Desktop/Chapter 3_workshop/dRBS_TAXA")
writeRaster(CWCs_overall_dRBS, "CWCs_overall_dRBS.tif", overwrite=TRUE)
writeRaster(Sponges_overall_dRBS, "Sponges_overall_dRBS.tif", overwrite=TRUE)

writeRaster(CWCs_Q.D_dRBS, "CWCs_Q.D_dRBS.tif", overwrite=TRUE)
writeRaster(Sponges_Q.D_dRBS, "Sponges_Q.D_dRBS.tif", overwrite=TRUE)

writeRaster(CWCs_internal_baseline_SSP2, "CWCs_internal_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_internal_baseline_SSP3, "CWCs_internal_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(Sponges_internal_baseline_SSP2, "Sponges_internal_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_internal_baseline_SSP3, "Sponges_internal_baseline_SSP3.tif", overwrite=TRUE)

writeRaster(CWCs_external_baseline_SSP2, "CWCs_external_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_external_baseline_SSP3, "CWCs_external_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(Sponges_external_baseline_SSP2, "Sponges_external_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_external_baseline_SSP3, "Sponges_external_baseline_SSP3.tif", overwrite=TRUE)

writeRaster(CWCs_internal_dRBS_SSP2, "CWCs_internal_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_internal_dRBS_SSP3, "CWCs_internal_dRBS_SSP3.tif", overwrite=TRUE)
writeRaster(Sponges_internal_dRBS_SSP2, "Sponges_internal_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_internal_dRBS_SSP3, "Sponges_internal_dRBS_SSP3.tif", overwrite=TRUE)

writeRaster(CWCs_external_dRBS_SSP2, "CWCs_external_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_external_dRBS_SSP3, "CWCs_external_dRBS_SSP3.tif", overwrite=TRUE)
writeRaster(Sponges_external_dRBS_SSP2, "Sponges_external_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_external_dRBS_SSP3, "Sponges_external_dRBS_SSP3.tif", overwrite=TRUE)


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################

# crating (total: internal + external) refugia maps

# CWCs

CWCs_refugia_baseline_SSP2 <- CWCs_internal_baseline_SSP2 + CWCs_external_baseline_SSP2
plot(CWCs_refugia_baseline_SSP2)
CWCs_refugia_dRBS_SSP2 <- CWCs_internal_dRBS_SSP2 + CWCs_external_dRBS_SSP2
plot(CWCs_refugia_dRBS_SSP2)

CWCs_refugia_baseline_SSP3 <- CWCs_internal_baseline_SSP3 + CWCs_external_baseline_SSP3
plot(CWCs_refugia_baseline_SSP3)
CWCs_refugia_dRBS_SSP3 <- CWCs_internal_dRBS_SSP3 + CWCs_external_dRBS_SSP3
plot(CWCs_refugia_dRBS_SSP3)

# difference (loss)

loss_CwCs_overall <- CWCs_overall_dRBS - CWCs_overall_baseline 
plot(loss_CwCs_overall) # overall

loss_CwCs_primary_habitats <- CWCs_Q.D_dRBS - CWCs_Q.D_baseline 
plot(loss_CwCs_primary_habitats) # primary habitats


loss_CWCs_refugia_SSP2 <-  CWCs_refugia_dRBS_SSP2 - CWCs_refugia_baseline_SSP2
plot(loss_CWCs_refugia_SSP2) # total refugia SSP2

loss_CWCs_refugia_SSP3 <-  CWCs_refugia_dRBS_SSP3 - CWCs_refugia_baseline_SSP3
plot(loss_CWCs_refugia_SSP3) # total refugia SSP3


##########################################################################################


# Sponges

Sponges_refugia_baseline_SSP2 <- Sponges_internal_baseline_SSP2 + Sponges_external_baseline_SSP2
plot(Sponges_refugia_baseline_SSP2)
Sponges_refugia_dRBS_SSP2 <- Sponges_internal_dRBS_SSP2 + Sponges_external_dRBS_SSP2
plot(Sponges_refugia_dRBS_SSP2)

Sponges_refugia_baseline_SSP3 <- Sponges_internal_baseline_SSP3 + Sponges_external_baseline_SSP3
plot(Sponges_refugia_baseline_SSP3)
Sponges_refugia_dRBS_SSP3 <- Sponges_internal_dRBS_SSP3 + Sponges_external_dRBS_SSP3
plot(Sponges_refugia_dRBS_SSP3)

# difference (loss)

loss_Sponges_overall <- Sponges_overall_dRBS - Sponges_overall_baseline 
plot(loss_Sponges_overall) # overall

loss_Sponges_primary_habitats <- Sponges_Q.D_dRBS - Sponges_Q.D_baseline 
plot(loss_Sponges_primary_habitats) # primary habitats


loss_Sponges_refugia_SSP2 <-  Sponges_refugia_dRBS_SSP2 - Sponges_refugia_baseline_SSP2
plot(loss_Sponges_refugia_SSP2) # total refugia SSP2

loss_Sponges_refugia_SSP3 <-  Sponges_refugia_dRBS_SSP3 - Sponges_refugia_baseline_SSP3
plot(loss_Sponges_refugia_SSP3) # total refugia SSP3

####################################################################################################


# STY

STY_refugia_baseline_SSP2 <- STY_internal_baseline_SSP2 + STY_external_baseline_SSP2
plot(STY_refugia_baseline_SSP2)
STY_refugia_dRBS_SSP2 <- STY_internal_dRBS_SSP2 + STY_external_dRBS_SSP2
plot(STY_refugia_dRBS_SSP2)

STY_refugia_baseline_SSP3 <- STY_internal_baseline_SSP3 + STY_external_baseline_SSP3
plot(STY_refugia_baseline_SSP3)
STY_refugia_dRBS_SSP3 <- STY_internal_dRBS_SSP3 + STY_external_dRBS_SSP3
plot(STY_refugia_dRBS_SSP3)

# difference (loss)

loss_STY_overall <- STY_overall_dRBS - STY_overall_baseline 
plot(loss_STY_overall) # overall

loss_STY_primary_habitats <- STY_Q.D_dRBS - STY_Q.D_baseline 
plot(loss_STY_primary_habitats) # primary habitats


loss_STY_refugia_SSP2 <-  STY_refugia_dRBS_SSP2 - STY_refugia_baseline_SSP2
plot(loss_STY_refugia_SSP2) # total refugia SSP2

loss_STY_refugia_SSP3 <-  STY_refugia_dRBS_SSP3 - STY_refugia_baseline_SSP3
plot(loss_STY_refugia_SSP3) # total refugia SSP3


#####################################################################################


# overall


# TOT

TOT_refugia_baseline_SSP2 <- TOT_internal_baseline_SSP2 + TOT_external_baseline_SSP2
plot(TOT_refugia_baseline_SSP2)
TOT_refugia_dRBS_SSP2 <- TOT_internal_dRBS_SSP2 + TOT_external_dRBS_SSP2
plot(TOT_refugia_dRBS_SSP2)

TOT_refugia_baseline_SSP3 <- TOT_internal_baseline_SSP3 + TOT_external_baseline_SSP3
plot(TOT_refugia_baseline_SSP3)
TOT_refugia_dRBS_SSP3 <- TOT_internal_dRBS_SSP3 + TOT_external_dRBS_SSP3
plot(TOT_refugia_dRBS_SSP3)

# difference (loss)

loss_TOT_overall <- TOT_overall_dRBS - TOT_overall_baseline 
plot(loss_TOT_overall) # overall

loss_TOT_primary_habitats <- TOT_primary_habitats_dRBS - TOT_primary_habitats_baseline 
plot(loss_TOT_primary_habitats) # primary habitats


loss_TOT_refugia_SSP2 <-  TOT_refugia_dRBS_SSP2 - TOT_refugia_baseline_SSP2
plot(loss_TOT_refugia_SSP2) # total refugia SSP2

loss_TOT_refugia_SSP3 <-  TOT_refugia_dRBS_SSP3 - TOT_refugia_baseline_SSP3
plot(loss_TOT_refugia_SSP3) # total refugia SSP3


#######################################################################################

# SAVE

setwd("C:/Users/ez14/OneDrive - The University of Waikato/Desktop/Chapter 3_workshop/dRBS_TAXA")

# TOTAL REFUGIA
writeRaster(CWCs_refugia_baseline_SSP2, "CWCs_refugia_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_refugia_dRBS_SSP2, "CWCs_refugia_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(CWCs_refugia_baseline_SSP3, "CWCs_refugia_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(CWCs_refugia_dRBS_SSP3, "CWCs_refugia_dRBS_SSP3.tif", overwrite=TRUE)

# LOSS
writeRaster(loss_CwCs_overall, "loss_CwCs_overall.tif", overwrite=TRUE)
writeRaster(loss_CwCs_primary_habitats, "loss_CwCs_primary_habitats.tif", overwrite=TRUE)
writeRaster(loss_CWCs_refugia_SSP2, "loss_CWCs_refugia_SSP2.tif", overwrite=TRUE)
writeRaster(loss_CWCs_refugia_SSP3, "loss_CWCs_refugia_SSP3.tif", overwrite=TRUE)

# TOTAL REFUGIA
writeRaster(Sponges_refugia_baseline_SSP2, "Sponges_refugia_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_refugia_dRBS_SSP2, "Sponges_refugia_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(Sponges_refugia_baseline_SSP3, "Sponges_refugia_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(Sponges_refugia_dRBS_SSP3, "Sponges_refugia_dRBS_SSP3.tif", overwrite=TRUE)

# LOSS
writeRaster(loss_Sponges_overall, "loss_Sponges_overall.tif", overwrite=TRUE)
writeRaster(loss_Sponges_primary_habitats, "loss_Sponges_primary_habitats.tif", overwrite=TRUE)
writeRaster(loss_Sponges_refugia_SSP2, "loss_Sponges_refugia_SSP2.tif", overwrite=TRUE)
writeRaster(loss_Sponges_refugia_SSP3, "loss_Sponges_refugia_SSP3.tif", overwrite=TRUE)

# TOTAL REFUGIA
writeRaster(STY_refugia_baseline_SSP2, "STY_refugia_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(STY_refugia_dRBS_SSP2, "STY_refugia_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(STY_refugia_baseline_SSP3, "STY_refugia_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(STY_refugia_dRBS_SSP3, "STY_refugia_dRBS_SSP3.tif", overwrite=TRUE)

# LOSS
writeRaster(loss_STY_overall, "loss_STY_overall.tif", overwrite=TRUE)
writeRaster(loss_STY_primary_habitats, "loss_STY_primary_habitats.tif", overwrite=TRUE)
writeRaster(loss_STY_refugia_SSP2, "loss_STY_refugia_SSP2.tif", overwrite=TRUE)
writeRaster(loss_STY_refugia_SSP3, "loss_STY_refugia_SSP3.tif", overwrite=TRUE)

# TOTAL REFUGIA
writeRaster(TOT_refugia_baseline_SSP2, "TOT_refugia_baseline_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_refugia_dRBS_SSP2, "TOT_refugia_dRBS_SSP2.tif", overwrite=TRUE)
writeRaster(TOT_refugia_baseline_SSP3, "TOT_refugia_baseline_SSP3.tif", overwrite=TRUE)
writeRaster(TOT_refugia_dRBS_SSP3, "TOT_refugia_dRBS_SSP3.tif", overwrite=TRUE)

# LOSS
writeRaster(loss_TOT_overall, "loss_TOT_overall.tif", overwrite=TRUE)
writeRaster(loss_TOT_primary_habitats, "loss_TOT_primary_habitats.tif", overwrite=TRUE)
writeRaster(loss_TOT_refugia_SSP2, "loss_TOT_refugia_SSP2.tif", overwrite=TRUE)
writeRaster(loss_TOT_refugia_SSP3, "loss_TOT_refugia_SSP3.tif", overwrite=TRUE)

# save.image("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 3/1.SCRIPT")
# load("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 3/1.SCRIPT")


#*******************************************************************************
#*******************************************************************************
#*******************************************************************************
#*#*****************************************************************************
#*******************************************************************************
#*******************************************************************************
#*#*****************************************************************************
#*******************************************************************************
#*******************************************************************************


library(rgdal); library(sf); library(raster); library(stringr)

home <- "C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/"
# setwd(home)
# save.image("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS.SCRIPT")
# load("C:/Users/ez14/OneDrive - The University of Waikato/EDO/Chapter 2/dRBS_documents/dRBS.SCRIPT")
