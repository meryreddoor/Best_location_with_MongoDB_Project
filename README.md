# Proyecto Mongo DB

El propósito de este proyecto es determinar el mejor lugar para localizar una compañía de videjuegos.

## Requisitos

Se necesitará importar las siguientes librerías:

```
import pandas as pd
import numpy as np
import requests
import math
import os
from dotenv import load_dotenv

from pymongo import MongoClient

import geopandas as gpd
from geopy.distance import distance
from geopy.distance import geodesic 
from shapely.geometry import Point
from geopy.distance import great_circle
from descartes import PolygonPatch

import matplotlib.pyplot as plt
%matplotlib inline

import folium
from folium import plugins
from folium import Choropleth, Circle, Marker
from folium.plugins import HeatMap, MarkerCluster
```

## Acciones sobre las Bases de Datos

1. Se ha importado el archivo 'companies' desde Mongo DB para poder acceder a las coordenadas y la información de las distintas empresas de videojuegos.

2. Después de dicha importación, se ha procedido a limpiar el dataset - Eliminando duplicados, elementos 'Nan' y columnas innecesarias como la de 'offices'.

3. Antes de eliminar la columna 'offices' se procedió a 'expandir' la información que ésta contenía.

4. Después, se procedió a extraer la información del dataset 'companies', y se compararon las ciudades donde más compañías de videojuegos había según la columna 'city'.

5. Tras esto, se analizaron las correspondientes coordenadas de estas ciudades a través de GEOQUERIES para encontrar el número de empresas de videojuegos cercanas a cada ciudad, y así poder evaluar si la información que contenía la columna 'city' era la correcta. Se encontraron algunas discrepancias, por ejemplo, Paris no devolvió tantos resultados como se esperaba, ya que el número de empresas devuelto fue muy bajo.

6. Para terminar con la comparación, se midió la distancia en km entre los principales aeropuertos de cada ciudad.

7. Finalmente, la ciudad con mejor puntuación en ambas comparaciones fue Santa Monica.

8. Es por ello que se procedió a analizar más en profundidad dicha ciudad y se extrajeron más puntos clave para la empresa, como por ejemplo:

* Universidades: posibilidad de poder captar talentos nuevos para la empresa, asistir a charlas (entre otras de diseño) y para los hijos de los empleados.

* Lugar de Ocio (Parque de Atracciones): para que los empleados puedas disfrutar de su tiempo libre, tanto con familia, amigos o los propios colegas del trabajo. Este punto puede ayudar a incrementar el compañerismo y la atmósfera de trabajo en equipo.

* Colegios para los niños de los trabajadores.

* Clubs de Noche

* Parque de atracciones para toda la familia

* Bares

## Mapa

![alt text](https://github.com/meryreddoor/mongodb/blob/master/img/Map.png)


## Built With

* [Folium](https://python-visualization.github.io/folium/) - Web utilizada para presentar los gráficos.
* [Google API](https://developers.google.com/apis-explorer) - Web utilizada para extraer sitios y coordenadas desde Google
* [Geocode](https://geocode.xyz) - Web utilizada para extraer las coordenadas de las ciudades.
* [Crunchbase](https://www.crunchbase.com) - Web utilizada para analizar las empresas de videjuegos.

