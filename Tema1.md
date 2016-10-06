#Tema 1#

##Ejercicio 1##

###Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años.###

Para calcular el coste de amortización se ha elegido el servidor [HP ProLiant ML110 Gen9 E5-2620v3/8GB/1TB](http://www.pccomponentes.com/hp_proliant_ml110_gen9_e5_2620v3_8gb_1tb.html) a la venta en PcComponentes y su precio es 1311€, sin IVA 1083.47€.

Según las tablas oficiales de amortización lineal publicadas en la [Ley 27/2014, de 27 de noviembre](http://www.boe.es/buscar/act.php?id=BOE-A-2014-12328&tn=1&p=20150922&vd=#a12), se establece un coeficiente lineal máximo de amortización del **25%** para equipos *Equipos para procesos de información* para un periodo de 8 años máximo.

####Para el caso de la estimación de la vida útil del producto en 4 años:####

Suponemos un valor residual de 250€, por tanto la **Base de amortización** = 1083.47 - 250 = **833.47€**

Usando el método de amortización según tablas oficiales de amortización lineal obtenemos una **cuota de amortización anual** = 833.47 / 4 = **208.37€**


|Año|Base de amortización|Coef. de amortización|Amortización acumulada|Valor neto|
|---|--------------------|---------------------|----------------------|----------|
|1  |833.47€             |25%                  |208.37€               |875,1     |
|2  |833.47€             |25%                  |416.74€               |666,73    |
|3  |833.47€             |25%                  |625.11€               |458,36    |
|4  |833.47€             |25%                  |833.47€               |**250**   | **= Valor residual**|


####Para el caso de la estimación de la vida útil del producto en 7 años:####

Suponiendo un valor residual de 150€, por tanto la **Base de amortización** = 1083.47 - 150 = **933.47€**

Para este caso se usara un método de amortización más realista, que tiene en cuenta que el valor del equipo no se degrada de forma homogénea a lo largo de su vida útil, este es el **método de los números dígitos**.

Dado que el valor del equipo descenderá en mayor medida cuanto más antigüedad tenga, calculamos la suma de dígitos de forma creciente empezando por la unidad para el primer año: **1+2+3+4+5+6+7 = 28**.

La **cuota por dígito** sería 933,47/28 = 33.34€****

|Año|Dígitos|Base de amortización|Amortización         |Amortización acumulada|Valor neto|
|---|-------|--------------------|---------------------|----------------------|----------|
|1  |1      |933.47€             |1x33.34 = 33.34      |33.34                 |1050.13   |
|2  |2      |933.47€             |2x33.34 = 66.68      |100.02                |983.45    |
|3  |3      |933.47€             |3x33.34 = 100.02     |200.04                |883.43    |
|4  |4      |933.47€             |4x33.34 = 133.36     |333.4                 |750.07    |
|5  |5      |933.47€             |5x33.34 = 166.7      |500.1                 |583.37    |
|6  |6      |933.47€             |6x33.34 = 200.04     |700.14                |383.33    |
|7  |7      |933.47€             |7x33.34 = 233.38     |933.47                |**150**   | **= Valor residual**|

##Ejercicio 2##

###Usando las tablas de precios de servicios de alojamiento en Internet y de proveedores de servicios en la nube, Comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del tiempo.###
Para la comparativa he escogido [Azure](www.azure.microsoft.com) de Microsoft como proveedor de servicios en la nube y a [Hostalia](http://www.hostalia.com/) para el servicio de servidor dedicado.

####Azure
Ofrece una máquina virtual (D3) con 4 núcleos, 14GB de RAM y 200GB de disco duro SSD por un precio de [0.283€/h](https://azure.microsoft.com/es-es/pricing/calculator/). En el caso de que se usara las 24 horas del día costaría **210,81€** al mes.
####Hostalia
Por [99€](http://www.hostalia.com/dedicados/) al mes obtenemos un servidor dedicado Dell PowerEdge R220 con 4 núcleos, 16GB de memoria RAM y dos discos duros SATA de 1TB.

####Supuesto del 1% de uso de la infraestructura
En el caso del servidor dedicado de Hostalia independientemente del uso que se haga el precio será fijo, en total **99€ \* 12 meses = 1188€ al año**

Sin embargo en el caso de Azure si varía el precio **210,81€ \* 12 meses \* 0,01 = 25,30€ al año**

####Supuesto del 10% de uso de la infraestructura
Al igual que en el supuesto anterior el servidor de Hostalia costaría **1188€** al año.

Para Azure tenemos **210,81€ \* 12 meses \* 0,1 = 252,97€ al año**

####Conclusión
A menos que hagamos un gran uso de las infraestructura, superior al 50% más o menos, la opción de contratar proveedores de servicios en la nube es mucho más rentable que el alquiler de un servidor dedicado.
