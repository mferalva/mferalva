install.packages("sf")
install.packages("ggplot2")
install.packages("sp")

library(sf)
library(ggplot2)
library(sp)

install.packages("readxl")
library(readxl)
#tobit
library(ggplot2)
#install.packages("GGally")
#install.packages("VGAM")
library(GGally)
library(VGAM)
library(tmap)
library(haven)
install.packages("devtools")
library("devtools")
install_github("diegovalle/mxmaps")
library("dyplr")
library("mxmaps")


mexico <- read_excel("/Users/mariafernandaalvaradomarin/Documents/OTOÑO 2024/Desarrollo Economico/Parar.xlsx") 
summary(mexico)
unique(mexico$ENTIDAD)

mexicomap <- st_read("/Users/mariafernandaalvaradomarin/Downloads/702825296520_s/32_Entidades_Federativas/ESTADOS.shp")

#primer intento
mapa <- ggplot(data = mexicomap) + geom_sf(aes(fill=FGT1)) + theme_minimal() + labs(title = "Nivel de Pobreza por Entidad")
print(mapa)


#segundo intento
mapa.p <- mxstate_choropleth(mexico, num_colors = 4, title = "Nivel de Pobreza por Entidad", legend = "FGT0") + theme(plot.title = element_text(hjust = 0.5))
print(mapa.p)
