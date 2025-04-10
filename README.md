# GENE500

R codes that were used to visualise the expression genes from a single-cell RNA seq dataset

# 1. Install R Studio
https://posit.co/download/rstudio-desktop/

# 2. Install the following packages
install.packages(‘ggplot2’)

install.packages(‘Seurat’)

install.packages(‘cowplot’)

install.packages(‘Matrix’)

# 3. Load the libraries
library(ggplot2

library(Seurat)

library(cowplot)

library(Matrix)

# 4. Set the directory
On R, set your working directory to the esmo.combine.rds (WBR dataset) or emso.rds (Adult daatset) file location
The code below will work if your folder is on the desktop and inside the Single_cell_codes_of_B_diegensis of Adult_single_cell_data folder

Setwd(“~/Desktop/Single_cell_codes_of_B_diegensis”)
Setwd(“~/Desktop/Adult_single_cell_data”)

# 5. Load the rds data
Double-click on esmo.combined.rds or emso.rds to open with Rstudio or you can load with the code below

emso.combined <- readRDS("~/Desktop/Single- cell_codes_of_B_diegensis/emso.combined.rds") 
emso <- readRDS("~/Desktop/Adult_single_cell_data/emso.rds") 

# Visualisation of target gene expression
To visualise the expression of the target gene using scRNA seq dataset.


# 1. Load the whole dataset with the code below
Dimplot(esmo.combined, reduction = “umap”, label = T)

# 2. Set the assay to RNA with the code below
DefaultAssay(esmo.combined)<-“RNA

# 3. Open the Stringtie_annotations excel file and look for channel of interest
For example, look for a MSTRG with the gene ID of your target gene (e.g., g03374)

# 4. Once you have obtained the MSTRG of interest. Enter the code below to visualise the UMAP plot

WBR

ggpubr::annotate_figure(
  p = FeaturePlot(emso.combined, features = "MSTRG.11700", order=TRUE),
  top = ggpubr::text_grob(label = 'MSTRG.11700/Wnt5a', face = 'bold',))

Adult

ggpubr::annotate_figure(
  p = FeaturePlot(emso, features = "MSTRG.11700", order=TRUE),
  top = ggpubr::text_grob(label = 'MSTRG.11700/Wnt5a', face = 'bold',))

# 5. We can then load the violin plot of out gene of interest with the code below.


WBR
  ggpubr::annotate_figure(
   p = VlnPlot(emso.combined, features = "MSTRG.11700"),
   top = ggpubr::text_grob(label = 'MSTRG.11700/Wnt5a', face = 'bold'))

Adult
  ggpubr::annotate_figure(
   p = VlnPlot(emso, features = "MSTRG.11700"),
   top = ggpubr::text_grob(label = '11700.3661/Wnt5a', face = 'bold'))

# 6. To compare the expression of the different genes and look at which clusters they are expressed, we can create a dot plot by using the code below.
For example:

features <- c("MSTRG.3661", "MSTRG.4954", "MSTRG.3368")

DotPlot(emso.combined, features = features) + RotatedAxis()

DotPlot(emso, features = features) + RotatedAxis()
