##Ejercicio1: Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años. ##
La tienda de informática que he consultado ha sido pccomponentes y el servidor que he seleccionado es un 
[HP ProLiant ML310e](http://www.pccomponentes.com/hp_proliant_ml310e_g8_xe_e3_1220_8gb_2tb.html) que tiene 
un precio de **729€** (**602.48€ sin IVA**). Suponiendo que el servidor lo he comprado en Enero de el año 2015 
la amortización sería la siguiente:

A 4 años (25% cada año):
  - 2015: 150.62€
  - 2016: 150.62€
  - 2017: 150.62€
  - 2018: 150.62€
  

A 7 años (14.3% cada año):
  - 2015: 86.15464€
  - 2016: 86.15464€
  - 2017: 86.15464€
  - 2018: 86.15464€
  - 2019: 86.15464€
  - 2020: 86.15464€
  - 2021: 85.55216€


##Ejercicio 2: Usando las tablas de precios de servicios de alojamiento en Internet y de proveedores de servicios en la nube, Comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del tiempo. ##

Como proveedor de servicios en la nube he escogido [Microsoft Azure](https://azure.microsoft.com/es-es/pricing/) con 1.75 GB de RAM	y 224 GB de SSD y como servicio de alojamiento en Internet un VPS de [dinahosting](https://dinahosting.com/vps) con 1.5 GB de RAM, 120GB de almacenamiento y una tasa de transferencia de 1TB que tiene un precio de 53€ al mes si lo administra el proveedor de servicios y 44€ si lo administra el propio cliente.
El problema de no usar todo el tiempo de un año es que en el caso de los VPS da igual el tiempo que lo usemos ya que se contrata todo el tiempo de un mes o de un año, mientras que con Azure la ventaja es que contratas el servicio por tiempo.

**1 % del tiempo en un año:**
Esto es unas 88 horas al año, en el caso del servidor en la nube de Azure esto tendría un precio de 5,94€ al mes, como podemos ver bastante más bajo que el VPS que como mínimo nos costaría 44€ al mes.

**10% del tiempo en un año:**
Esto serían 876 horas al año, en el caso de Azure, estas horas nos costarían 58,7€ que tendría un precio más elevado en este caso que un VPS.

Como conclusión resulta más barato un VPS si vas a usarlo más del 9% del tiempo de un año, mientras que si el uso que le vas a dar es menor del 9% del tiempo de un año te sale más rentable un proveedor de servicios en la nube.
