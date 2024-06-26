<div align= 'center'>
  
![Static Badge](https://img.shields.io/badge/PowerBI-gray?style=flat&logo=powerbi)
![Static Badge](https://img.shields.io/badge/Python-gray?style=flat&logo=python)
![Static Badge](https://img.shields.io/badge/-Pandas-gray?style=flat&logo=pandas)
![Static Badge](https://img.shields.io/badge/-Matplotlib-gray?style=flat&logo=matplotlib)
![Static Badge](https://img.shields.io/badge/-Seaborn-gray?style=flat&logo=seaborn)
![Static Badge](https://img.shields.io/badge/-Jupyter_Notebook-gray?style=flat&logo=jupyter)
![Static Badge](https://img.shields.io/badge/Visual_Studio_Code-gray?style=flat&logo=visual%20studio%20code&logoColor=white)

</div>


<h1 align ='center'>SINIESTROS VIALES</h1>
<p align='center'> <img src= 'https://ahorraseguros.mx/wp-content/uploads/2022/12/siniestro.jpg'> </p>

<h1 align='left'>INTRODUCCIÓN</h1>

<p align= 'justify'>Los siniestros viales, también conocidos como accidentes viales, de tránsito o tráfico, son sucesos que ocurren por lo general cuando un vehiculo colisiona contra uno o más sectores de la vialidad (estos pueden ser otro vehículo, una persona, animal o escombros del camino) u otra obstruccion estacionaria como un poste, edificio o árbol, etc.</p>

<p align= 'justify'>Estos no son aleatorios y usualmente están acomáñados por corresponsabilidades cómo pueden ser ajenas o propias del conductor o conductora.
En este informe se pretende generar la información que permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales.</p>

<p align= 'justify'>La seguridad vial es una problemática a nivel mundial, en Argentina, la inseguridad vial supera las 10 vícimas fatales por cada 100 mil habitantes, la inseguridad vial es una de las principales causas de muerte por enfermedades no transmisibles entre los menores de 35 años (Dirección Nacional de Observatorio Vial, 2023).</p>

<p align= 'justify'>En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, esta sigue siendo la principal causa de muertes violentas en el país. Los informes del Sistema Nacional de Información Criminal (SNIC), del Ministerio de Seguridad de la Nación, revelan que entre 2018 y 2022 se registraron 19.630 muertes en siniestros viales en todo el país. Estas cifras equivalen a 11 personas por día que resultaron víctimas fatales por accidentes de tránsito.</p>

<p align= 'justify'>Solo en 2022, se contabilizaron 3.828 muertes fatales en este tipo de hechos. Los expertos en la materia indican que en Argentina es dos o tres veces más alta la probabilidad de que una persona muera en un siniestro vial que en un hecho de inseguridad delictiva.</p>

<p align= 'justify'>Debido a esto es que se tiene como objetivo generar información para proveer a las autoridads locales las medidas adecuadas para disminuir la cantidad de víctimas fatales de los siniestros viales.</p>

<h1 align='left'>DATOS</h1>

<p align= 'justify'>Para el desarrollo de este proyecto se utilizó un dataset sobre siniestros viales llamado 'homicidios.xlsx' obtenido de la data de Buenos Aires. Se decidió utilizar los siguientes datos:</p>

<p align ='justify'><b>HECHOS:</b> contiene una fila de hecho con id único y las variables temporales, espaciales y participantes asociadas al mismo</p>
<p align ='justify'><b>VICTIMAS:</b>  contiene una fila por cada víctima de los hechos y las variables edad, sexo y modo de desplazamiento asociadas a cada víctima.
En el sigueinte link se encuentran los archivos utilizados así como el pdf donde se proporciona la información pertinente sobre los <a href= https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales>datasets</a>.</p>

<h1 align='left'>ETL</h1>
<p align= 'justify'>Para realizar el proceso de Extracción, transformacion y carga de los datos, se obtuvo el dataset 'homicidios.xlsx' con 4 solapas, se decidió utilizar las hojas con el nombre de 'HECHOS' y 'VICTIMAS' ya que estas contenian los datos a utilizar, una vez que se convirtieron a un data frame se procedió a realizar un 'merge' de los dos dataframe por medio de la columna en común 'ID', posterior a eso capitalizamos todos los datos que poseen nuestras columnas con esto volvemos la primer letra en mayusculas y las demás en minúsculas, eliminamos columnas duplicadas e irrelevantes, también se agrego una columna en la que se mostrara el semestre correspondiente del año.</p>

<p align= 'left'><b>Nulos</b></p>
<p align= 'justify'>Los datos nulos que se encontraron en el DF estaban representados por 'Sd' o 'SD' el cual hace referencia a 'SinDato', se decidió eliminar las filas que tuvieran 'Sd' en las columnas 'VICTIMAS' 'ACUSADO' y 'PARTICIPANTES', se encontraron accidentes pero no había personas encontradas. Para los 'SinDato' encontrados en la columna de 'EDAD' se decidió realizar un 'fillna' con la media de las edades en dicha columna, al igual que para 'HORA_SINIESTRO'</p>

<p align= 'left'><b>Duplicados</b></p>
<p align= 'justify'>Se encontraron algunos duplicados en la columna 'ID' después de eliminar el año al inicio del ID, así que se decidió reemplazar los duplicados por valores 'NaN' y posterior a eso llenarlos con el indice en el que se encontraban</p>

<p align= 'left'><b>Outliers</b></p>
<p align= 'justify'>Durante el EDA no se encontraron outliers, pero considerando que había víctimas conduciendo que tenían más de 65 años se puede considerar cómo un valor atípico, ya que consultando la pagina de la Agencia Nacional de Seguridad Vial la vigencia de la licencia disminuye con forme a la edad y la clase de licencia.</p>

<h1 align= 'left'><b>EDA</b></h1>
<p align= 'justify'>Una vez que se realizó el ETL del dataset 'Homicidios.xlsx, se procedió a llevar a cabo el EDA, en la cual tenemos una visión gráfica de los datos y se puede realizar un análisis de estos.</p>

<p align= 'left'><b>Número de víctimas por año</b></p>

![Descripción de la imagen](Graficos/grafico_1.png)

<p align= 'justify'>En el gráfico podemos observar que el número de víctimas en el año 2020 disminuyó, esto probablemente por las reestricciones por la pandemia de COVID-19</p>

<p align= 'left'><b>Porcentaje de Víctimas por Rol</b></p>

![Descripción de la imagen](Graficos/grafico_2.png)

<p align= 'justify'>Podemos ver que en este gráfico las víctimas al momento del accidente eran principalmente conductores.</p>

<p align= 'left'><b>Porcentaje de víctimas por sexo</b></p>

![Descripción de la imagen](Graficos/grafico_3.png)
<p align= 'justify'>Vemos que la cantidad de víctimas que son hombres tienen mayor incidencia que el sexo femenino.</p>

<p align= 'left'><b>Porcentaje de víctimas por año y sexo</b></p>

![Descripción de la imagen](Graficos/grafico_4.png)

<p align= 'justify'>En este gráfico igual podemos observar que los Hombres tienen mayor incidencia cómo víctimas en los siniestros viales, siendo el año 2020 el que más víctimas masculinas presentó.</p>

<p align= 'left'><b>Número de víctimas por rango etario</b></p>

![Descripción de la imagen](Graficos/grafico_5.png)

<p align= 'justify'>Aquí podemos observar que la mayor cantidad de víctimas se encuentran en el rango etario de 21 a 40 años.</p>

<p align= 'left'><b>Rol por rango etario</b></p>

![Descripción de la imagen](Graficos/grafico_6.png)

<p align= 'justify'>Aquí podemos observer que de igual forma la mayor cantidad de víctimas se encuentran en el rango etario de 21 a 40 años y a su vez observamos que en su mayoria las víctimas se encuentran en el rol de conductores para el mismo rango etario.</p>

<p align= 'left'><b>Número de accidentes por comuna a través de los años</b></p>

![Descripción de la imagen](Graficos/grafico_7.png)

<p align= 'justify'>Podemos observar que los accidentes por comuna disminuyeron para el año 2020 y en el año 2019 en varias comunas se redujeron los accidentes viales</p>

<p align= 'left'><b>Dashboard</b></p>

![Descripción de la imagen](Graficos/Siniestrosviales.png)

<p align= 'justify'>Cómo podemos ver en la imagen las víctimas en total, desde 2016 al 2021, fueron 734. Otro aspecto que se puede observar que las víctimas masculinas estaban en mayor proporción comparado con las vícitimas femeninas, así como podemos observar, en el mapa, las zonas en que están presentes estos accidentes.</p>


![Descripción de la imagen](Graficos/Promediodevíctimas.png)


<p align= 'justify'>En la imagen anterior podemos observar el promedio de víctimas por edad y por comuna</p>


![Descripción de la imagen](Graficos/KPI1.png)


<p align= 'justify'>En esta imagen se buscó reducir el 10% de los homicidios en siniestros viales en los ultimos seis meses, cómo podemos ver en el gráfico de la reducción de homicidios este objetivo se logró, al igual que podemos verlo en la tarjeta del indicador de desempeño, de igual forma podemos ver los gráficos de víctimas por semestre en cada año.</p>


![Descripción de la imagen](Graficos/KPI2.png)

<p align= 'justify'>En la imagen anterior se muestra la reducción del 7% en las víctimas en moto para el año actual con respecto al año anterior, así como el promedio de víctimas en moto por año y un filtro por año para poder mostrar el promedio de víctimas para dicho año.</p>

<p align= 'left'><b>Conclusión</b></p>
<p align= 'justify'>Una vez terminado el ETL, EDA y realizar el Dashboard, nos dimos cuenta que para el año 2020 los siniestros viales, se redujeron de manera notable se cree que esto es debido a las restricciones por COVID-19. Así mismo podemos notar que las víctimas son en su mayoría conductores y se encuentran en un rango etario de 21 a 40 años, siendo un aproximado de 200 víctimas en total para esta categoría. También podemos obsevar que las víctimas son en su mayoría hombres con un 75% en total en el periodo de 2016 a 2021.</p>

<p align= 'left'><b>Referencias</b></p>
<p align= 'justify'> https://www.argentina.gob.ar/sites/default/files/2018/12/ansv_victimas_fatales_zoom_en_los_usuarios_de_las_vias_2022.pdf 
  
https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales</p>

<p align= 'left'><b>Autor</b></p>
<p align= 'justify'>Github: https://github.com/Bethcosima
  
Linkedin: www.linkedin.com/in/elizabeth-fraire-a830bb234</p>


