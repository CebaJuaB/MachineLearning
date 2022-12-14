# Introducci贸n al agrupamiento

El agrupamiento (clustering) es un tipo de [aprendizaje no supervisado](https://wikipedia.org/wiki/Unsupervised_learning) que supone que un conjunto de datos est谩 sin etiquetar o que sus entradas no est谩n emparejadas con salidas predefinidas. Usa varios algoritmos para ordenar datos sin etiquetar y provee agrupaciones de acuerdo a patrones que discierne en los datos.

[![No One Like You de PSquare](https://img.youtube.com/vi/ty2advRiWJM/0.jpg)](https://youtu.be/ty2advRiWJM "No One Like You de PSquare")

> 馃帴 Haz clic en la imagen de arriba para ver el video. Mientras estudias aprendizaje autom谩tico con agrupamiento, disfruta de algunas canciones Dance Hall Nigerianas - esta es una canci贸n muy popular del 2014 de PSquare.

## [Examen previo a la lecci贸n](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/27?loc=es)

### Introducci贸n

El [agrupamiento](https://link.springer.com/referenceworkentry/10.1007%2F978-0-387-30164-8_124) es muy 煤til para la exploraci贸n de datos. Veamos si nos puede ayudar a descubrir tendencias y patrones en la forma en que la audiencia Nigeriana consume m煤sica.

鉁? Piensa por un minuto acerca de los usos del agrupamiento. En la vida real, el agrupamiento sucede siempre que tienes un mont贸n de ropa sucia y necesitas ordenar las prendas de los miembros de la familia 馃Е馃憰馃憱馃┎. En la ciencia de datos, el agrupamiento ocurre cuando intentamos analizar las preferencias de los usuarios, o determinar las caracter铆sticas de cualquier conjunto de datos no etiquetado. El agrupamiento, de cierta forma, ayuda a dar sentido al caos, como un caj贸n de calcetines.

[![introducci贸n al agrupamiento](https://img.youtube.com/vi/esmzYhuFnds/0.jpg)](https://youtu.be/esmzYhuFnds "introducci贸n al agrupamiento")

> 馃帴 Haz clic en la imagen de arriba para ver el video: John Guttag del MIT presenta el agrupamiento

En el 谩mbito profesional, el agrupamiento puede ser usado para determinar temas como la segmentaci贸n de mercado, qu茅 grupos de edad compran qu茅 cosas, por citar algunos. Otro uso ser铆a la detecci贸n de anomal铆as, quiz谩 para detectar el fraude de un conjunto de datos de transacciones de tarjetas de cr茅dito. O podr铆as usar el agrupamiento para determinar tumores en un lote de escaneos m茅dicos.

鉁? Piensa un poco acerca de c贸mo encontrar铆as el agrupamiento 'en la naturaleza', en un entorno bancario, de comercio electr贸nico o de negocio.

> 馃帗 Curiosamente, el an谩lisis de agrupamiento se origin贸 en los campos de la Antropolog铆a y Psicolog铆a en los a帽os 1930. 驴Puedes imaginar c贸mo fue usado?

Alternativamente, puedes usarlo para agrupar resultados de b煤squeda - por enlaces de compra, im谩genes o rese帽as, por citar algunos. El agrupamiento es 煤til cuando tienes un gran conjunto de datos el cual quieres reducir y sobre el cual deseas realizar un an谩lisis m谩s granular, as铆 la t茅cnica puede ser usada para aprender acerca de los datos antes que se construyan otros modelos.

鉁? Una vez que tus datos est谩n organizados en grupos , asignale un Id de grupo, y esta t茅cnica puede ser 煤til cuando conservas la privacidad de un conjunto de datos; en su lugar te puedes referir a un punto de datos por su id de grupo, en vez de sus datos identificables m谩s reveladores. 驴Puedes pensar en otras razones del por qu茅 preferir铆as un Id de grupo en lugar de otros elementos del grupo para identificarlo?

Profundiza tu compresi贸n de las t茅cnicas de agrupamiento en este [m贸dulo de aprendizaje](https://docs.microsoft.com/learn/modules/train-evaluate-cluster-models?WT.mc_id=academic-77952-leestott)

## Empezando con el agrupamiento

[Scikit-learn ofrece un gran arreglo](https://scikit-learn.org/stable/modules/clustering.html) de m茅todos para realizar agrupamiento. El tipo que elijas depender谩 de tu caso de uso. De acuerdo a la documentaci贸n, cada m茅todo tiene varios beneficios. Aqu铆 tienes una tabla simplificada de los m茅todos soportados por Scikit-learn y sus casos de uso apropiados:

| Nombre del m茅todo            | Caso de uso                                                               |
| :--------------------------- | :-------------------------------------------------------------------------|
| K-Medias                     | prop贸sito general, inductivo                                              |
| Propagaci贸n de afinidad      | Muchos, grupos desiguales, inductivo                                      |
| Desplazamiento medio         | Muchos, grupos desiguales, inductivo                                      |
| Agrupamiento espectral       | Pocos, grupos iguales, transductivo                                       |
| Agrupaci贸n jer谩rquica Ward   | Muchos, grupos restringidos, transductivo                                 |
| Agrupaci贸n aglomerativa      | Muchos, restringidos, distancia no Euclidianas, transductivo              |
| DBSCAN                       | Geometr铆a no plana, grupos desiguales, transductivo                       |
| OPTICS                       | Geometr铆a no plana, grupos desiguales con densidad variable, transductivo |
| Mezclas Gaussianas           | Geometr铆a plana, inductivo                                                |
| BIRCH                        | Gran conjunto de datos con valores at铆picos, inductivo                    |

> 馃帗 El c贸mo creamos los grupos tiene mucho que ver con c贸mo recopilamos los puntos de datos en grupos. Desempaquemos algo de vocabulario:
>
> 馃帗 ['Transductivo' vs. 'inductivo'](https://wikipedia.org/wiki/Transduction_(machine_learning))
>
> La inferencia transductiva se deriva de los casos de entrenamiento observados que se asignan a casos de prueba espec铆ficos. La inferencia inductiva se deriva de los casos de entrenamiento que se asignan a reglas generales las cuales s贸lo aplican a los casos de prueba.
>
> Un ejemplo: Imagina que tienes un conjunto de datos que est谩 parcialmente etiquetado. Algunas cosas son 'records', otras 'cds' y unas m谩s est谩n en blanco. Tu trabajo es proveer las etiquetas para los blancos. Si eliges un enfoque inductivo, entrenar铆as un modelo buscando 'records' y 'cds' y aplicar铆as esas etiquetas a tus datos sin etiquetar. Este enfoque tendr谩 problemas clasificando como que en realidad con 'cassettes'. Por otro lado, un enfoque transductivo, maneja estos datos desconocidos de forma m谩s efectiva ya que funciona para agrupar elementos similares y luego aplica una etiqueta a un grupo. En este caso, los agrupamientos reflejan 'cosas musicales redondas' y 'cosas musicales cuadradas'.
>
> 馃帗 [Geometr铆a 'no plana' vs 'plana'](https://datascience.stackexchange.com/questions/52260/terminology-flat-geometry-in-the-context-of-clustering)
>
> Derivada de la terminolog铆a matem谩tica, la geometr铆a no plana versus plana se refiere a la medida de distancias entre puntos ya sea por m茅todos geom茅tricos 'planos' ([Euclidianos](https://wikipedia.org/wiki/Euclidean_geometry)) o 'no planos' (no Euclidianos).
>
> En este contexto 'Plano' se refiere a la geometr铆a Euclidiana (partes de las cuales se ense帽an como geometr铆a 'plana'), y no plana se refiere a la geometr铆a no Euclidiana. 驴Qu茅 tiene que ver la geometr铆a con el aprendizaje autom谩tico? Bien, como dos campos que tienen sus ra铆ces en las matem谩ticas, debe haber una forma com煤n de medir las distancias entre puntos en los grupos, y eso puede hacerse de forma 'plana' o 'no plana', dependiendo de la naturaleza de los datos. Las [distancias Euclidianas](https://wikipedia.org/wiki/Euclidean_distance) se miden como la longitud de un segmento de l铆nea entre dos puntos. Las [distancias no Euclidianas](https://wikipedia.org/wiki/Non-Euclidean_geometry) se miden como a lo largo de la curva. Si tus datos visualizados parecen no existir en un plano, podr铆as necesitar usar un algoritmo especializado para realizarlo.
>
![Infograf铆a de geometr铆a plana vs no plana](../images/flat-nonflat.png)
> Infograf铆a de [Dasani Madipalli](https://twitter.com/dasani_decoded)
>
> 馃帗 ['Distancias'](https://web.stanford.edu/class/cs345a/slides/12-clustering.pdf)
>
> Los agrupamientos se definen por su matriz de distancia, por ejemplo, las distancias entre puntos. Esta distancia puede ser medida de varias formas. Los agrupamientos Euclidianos se definen por el promedio de los valores de los puntos, y contienen un 'centroide' o punto central. por lo tanto, las distancias son medidas por la distancia al centroide. Las distancias no Euclidianas se refieren a 'clustroides', el punto m谩s cercano a otros puntos. Los clustroides en turno pueden ser definidos de varias formas.
>
> 馃帗 ['Restringido'](https://wikipedia.org/wiki/Constrained_clustering)
> 
> El [agrupamiento restringido](https://web.cs.ucdavis.edu/~davidson/Publications/ICDMTutorial.pdf) presenta el t茅rmino aprendizaje 'semi-supervisado' en este m茅todo no supervisado. Las relaciones entre los puntos son marcadas como 'cannot link' o 'must-link' por lo que algunas reglas son forzadas en el conjunto de datos.
>
> Un ejemplo: Si se libera un algoritmo en un lote de datos no etiquetados o semi-etiquetados, los agrupamientos que produce pueden ser de baja calidad. En el ejemplo de arriba, los agrupamientos pueden reunir 'round music things' y 'square music things' y 'triangular things' y 'cookies'. Si se proporcionan algunas restricciones o reglas a seguir ("el elemento debe estar hecho de pl谩stico", "el elemento necesita ser capaz de reproducir m煤sica") esto puede ayudar a 'restringir' al algoritmo para que realice mejores elecciones.
>
> 馃帗 'Densidad'
>
> Los datos que son 'ruidosos' se consideran como 'densos'. Las distancias entre los puntos en cada uno de sus grupos puede probar, al examinarse, ser m谩s o menos densos, o 'atestados' y por lo tanto estos datos necesitan ser analizados con los m茅todos de agrupamiento apropiados. [Este art铆culo](https://www.kdnuggets.com/2020/02/understanding-density-based-clustering.html) demuestra la diferencia entre usar los algoritmos K-Medias vs HDBSCAN para explorar un conjunto de datos ruidosos con densidad de agrupamiento desigual.

## Algoritmos de agrupamiento

Existen m谩s de 100 algoritmos de agrupamiento, y sus usos dependen de la naturaleza de los datos que se te presentan. Discutamos algunos de los m谩s importantes:

- **Agrupamiento jer谩rquico** Si un objeto se clasifica por su proximidad a un objeto cercano, en lugar de uno m谩s lejano, los grupos se forman basados en las distancias de sus miembros hacia y desde otros objetos. El agrupamiento aglomerativo de Scikit-learn es jer谩rquico.

   ![Infograf铆a de agrupamiento jer谩rquico](../images/hierarchical.png)
   > Infograf铆a de [Dasani Madipalli](https://twitter.com/dasani_decoded)

- **Agrupamiento de centroide**. Este popular algoritmo require la elecci贸n de 'k', o el n煤mero de grupos a formar, tras lo cua el algoritmo determina el punto central de un grupo y re煤ne datos alrededor de ese punto. [El agrupamiento K-Medias](https://wikipedia.org/wiki/K-means_clustering) es una versi贸n popular de agrupamiento de centroide. El centro se determina por la media m谩s cercana, por eso el nombre. La distancia al cuadrado desde el grupo se minimiza.

   ![Infograf铆a de agrupamiento de centroide](../images/centroid.png)
   > Infograf铆a de [Dasani Madipalli](https://twitter.com/dasani_decoded)

- **Agrupamiento basado en distribuci贸n**. Se basa en el modelado estad铆stico, el agrupamiento basado en distribuci贸n se centra en determinar la probabilidad de los puntos de datos de pertenecer a un grupo, y los asigna en consecuencia. Los m茅todos de mezcla Gaussiana pertenecen a este tipo.

- **Agrupamiento basado en densidad**. Los puntos de datos se asignan a grupos basado en su densidad, o su agrupaci贸n unos alrededor de otros. Los puntos de datos lejanos del grupo se consideran valores at铆picos o ruido. DBSCAN, desplazamiento medio y OPTICS pertenecen a este tipo de agrupamiento.

- **Agrupamiento basado en cuadr铆cula**. Para conjuntos de datos multi-dimensionales, se crea una cuadr铆cula y los datos se dividen entre las celdas de la cuadr铆cula, creando as铆 los grupos.

## Ejercicio - agrupa tus datos

El agrupamiento como t茅cnica recibe mucha ayuda de una buena visualizaci贸n, as铆 que empecemos por visualizar nuestros datos de m煤sica. Este ejercicio nos ayudar谩 a decidir cu谩l de los m茅todos de agrupamiento deber铆amos usar de forma m谩s efectiva de acuerdo a la naturaleza de estos datos.

1. Abre el archivo _notebook.ipynb_ en este directorio.

1. Importa el paquete `Seaborn` para una buena visualizaci贸n de datos.

    ```python
    !pip install seaborn
    ```

1. Adjunta los datos de la canci贸n del archivo _nigerian-songs.csv_. Carga un dataframe con algunos datos de las canciones. Prep谩rate para explorar estos datos al importar las bibliotecas y volcar los datos: 

    ```python
    import matplotlib.pyplot as plt
    import pandas as pd
    
    df = pd.read_csv("../data/nigerian-songs.csv")
    df.head()
    ```

    Revisa las primeras l铆neas de datos:

    |     | name                     | album                        | artist              | artist_top_genre | release_date | length | popularity | danceability | acousticness | energy | instrumentalness | liveness | loudness | speechiness | tempo   | time_signature |
    | --- | ------------------------ | ---------------------------- | ------------------- | ---------------- | ------------ | ------ | ---------- | ------------ | ------------ | ------ | ---------------- | -------- | -------- | ----------- | ------- | -------------- |
    | 0   | Sparky                   | Mandy & The Jungle           | Cruel Santino       | alternative r&b  | 2019         | 144000 | 48         | 0.666        | 0.851        | 0.42   | 0.534            | 0.11     | -6.699   | 0.0829      | 133.015 | 5              |
    | 1   | shuga rush               | EVERYTHING YOU HEARD IS TRUE | Odunsi (The Engine) | afropop          | 2020         | 89488  | 30         | 0.71         | 0.0822       | 0.683  | 0.000169         | 0.101    | -5.64    | 0.36        | 129.993 | 3              |
    | 2   | LITT!                    | LITT!                        | AYL脴                | indie r&b        | 2018         | 207758 | 40         | 0.836        | 0.272        | 0.564  | 0.000537         | 0.11     | -7.127   | 0.0424      | 130.005 | 4              |
    | 3   | Confident / Feeling Cool | Enjoy Your Life              | Lady Donli          | nigerian pop     | 2019         | 175135 | 14         | 0.894        | 0.798        | 0.611  | 0.000187         | 0.0964   | -4.961   | 0.113       | 111.087 | 4              |
    | 4   | wanted you               | rare.                        | Odunsi (The Engine) | afropop          | 2018         | 152049 | 25         | 0.702        | 0.116        | 0.833  | 0.91             | 0.348    | -6.044   | 0.0447      | 105.115 | 4              |

1. Obt茅n informaci贸n acerca del dataframe, llamando a `info()`:

    ```python
    df.info()
    ```

   La salida luce as铆:

    ```output
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 530 entries, 0 to 529
    Data columns (total 16 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   name              530 non-null    object 
     1   album             530 non-null    object 
     2   artist            530 non-null    object 
     3   artist_top_genre  530 non-null    object 
     4   release_date      530 non-null    int64  
     5   length            530 non-null    int64  
     6   popularity        530 non-null    int64  
     7   danceability      530 non-null    float64
     8   acousticness      530 non-null    float64
     9   energy            530 non-null    float64
     10  instrumentalness  530 non-null    float64
     11  liveness          530 non-null    float64
     12  loudness          530 non-null    float64
     13  speechiness       530 non-null    float64
     14  tempo             530 non-null    float64
     15  time_signature    530 non-null    int64  
    dtypes: float64(8), int64(4), object(4)
    memory usage: 66.4+ KB
    ```

1. Vuelve a revisar los valores nulos, al llamar a `isnull()` y verifica que la suma sea 0:

    ```python
    df.isnull().sum()
    ```

    Se ve bien:

    ```output
    name                0
    album               0
    artist              0
    artist_top_genre    0
    release_date        0
    length              0
    popularity          0
    danceability        0
    acousticness        0
    energy              0
    instrumentalness    0
    liveness            0
    loudness            0
    speechiness         0
    tempo               0
    time_signature      0
    dtype: int64
    ```

1. Describe los datos:

    ```python
    df.describe()
    ```

    |       | release_date | length      | popularity | danceability | acousticness | energy   | instrumentalness | liveness | loudness  | speechiness | tempo      | time_signature |
    | ----- | ------------ | ----------- | ---------- | ------------ | ------------ | -------- | ---------------- | -------- | --------- | ----------- | ---------- | -------------- |
    | count | 530          | 530         | 530        | 530          | 530          | 530      | 530              | 530      | 530       | 530         | 530        | 530            |
    | mean  | 2015.390566  | 222298.1698 | 17.507547  | 0.741619     | 0.265412     | 0.760623 | 0.016305         | 0.147308 | -4.953011 | 0.130748    | 116.487864 | 3.986792       |
    | std   | 3.131688     | 39696.82226 | 18.992212  | 0.117522     | 0.208342     | 0.148533 | 0.090321         | 0.123588 | 2.464186  | 0.092939    | 23.518601  | 0.333701       |
    | min   | 1998         | 89488       | 0          | 0.255        | 0.000665     | 0.111    | 0                | 0.0283   | -19.362   | 0.0278      | 61.695     | 3              |
    | 25%   | 2014         | 199305      | 0          | 0.681        | 0.089525     | 0.669    | 0                | 0.07565  | -6.29875  | 0.0591      | 102.96125  | 4              |
    | 50%   | 2016         | 218509      | 13         | 0.761        | 0.2205       | 0.7845   | 0.000004         | 0.1035   | -4.5585   | 0.09795     | 112.7145   | 4              |
    | 75%   | 2017         | 242098.5    | 31         | 0.8295       | 0.403        | 0.87575  | 0.000234         | 0.164    | -3.331    | 0.177       | 125.03925  | 4              |
    | max   | 2020         | 511738      | 73         | 0.966        | 0.954        | 0.995    | 0.91             | 0.811    | 0.582     | 0.514       | 206.007    | 5              |

> 馃 Si estamos trabajando con el agrupamiento, un m茅todo no supervisado que no requiere datos etiquetados. 驴Por qu茅 mostramos estos datos con etiquetas? En la fase de exploraci贸n de datos, son 煤tiles, pero no son necesarias para que el algoritmo de agrupamiento funcione.  Podr铆as s贸lo eliminar los encabezados de columna y referirte a los datos por el n煤mero de columna.

Observa los valores generales de los datos. Nota que 'popularity' puede ser '0', lo cual muestra las canciones que no tienen clasificaci贸n. Eliminemos esas.

1. Usa un gr谩fico de barras para descubrir los g茅neros m谩s populares:

    ```python
    import seaborn as sns
    
    top = df['artist_top_genre'].value_counts()
    plt.figure(figsize=(10,7))
    sns.barplot(x=top[:5].index,y=top[:5].values)
    plt.xticks(rotation=45)
    plt.title('Top genres',color = 'blue')
    ```

    ![Los m谩s populares](../images/popular.png)

鉁? Si te gustar铆a ver los mejores valores, cambia el valor top `[:5]` por uno mayor, o elim铆nalo para verlos todos.

Nota, cuando el g茅nero superior se describe como 'Missing', que significa que Spotify no lo clasific贸, as铆 que deshag谩monos de 茅l.

1. Deshazte de los datos faltantes al filtrarlos

    ```python
    df = df[df['artist_top_genre'] != 'Missing']
    top = df['artist_top_genre'].value_counts()
    plt.figure(figsize=(10,7))
    sns.barplot(x=top.index,y=top.values)
    plt.xticks(rotation=45)
    plt.title('Top genres',color = 'blue')
    ```

    Ahora revisa nuevamente los g茅neros:

    ![Los m谩s populares](../images/all-genres.png)

1. Por mucho, los mejores tres g茅neros dominan este conjunto de datos. Concentr茅monos en `afro dancehall`, `afropop`, y `nigerian pop`, adicionalmente filtra el conjunto de datos para remover todo lo que tenga un valor de popularidad de 0 (lo que significa no fue clasificado con una popularidad en el conjunto de datos y puede ser considerado ruido para nuestros prop贸sitos):

    ```python
    df = df[(df['artist_top_genre'] == 'afro dancehall') | (df['artist_top_genre'] == 'afropop') | (df['artist_top_genre'] == 'nigerian pop')]
    df = df[(df['popularity'] > 0)]
    top = df['artist_top_genre'].value_counts()
    plt.figure(figsize=(10,7))
    sns.barplot(x=top.index,y=top.values)
    plt.xticks(rotation=45)
    plt.title('Top genres',color = 'blue')
    ```

1. Haz una prueba r谩pida para ver si los datos se correlacionan de alguna forma particularmente fuerte:

    ```python
    corrmat = df.corr()
    f, ax = plt.subplots(figsize=(12, 9))
    sns.heatmap(corrmat, vmax=.8, square=True)
    ```

    ![Correlaciones](../images/correlation.png)

    La 煤nica correlaci贸n fuerte es entre `energy` y `loudness`, lo cual no es de sorprender, dado que la m煤sica a todo volumen es usualmente muy energ茅tica. De lo contrario, las correlaciones son relativamente d茅biles. Ser谩 interesante ver lo que un algoritmo de agrupamiento puede hacer con estos datos.

    > 馃帗 隆Nota que la correlaci贸n no implica causalidad! Tenemos prueba de la correlaci贸n pero no de la causalidad. Un [sitio web divertido](https://tylervigen.com/spurious-correlations) tiene algunas im谩genes que enfatizan este punto.

驴Hay convergencia alguna en este conjunto de datos en torno a la popularidad percibida y bailabilidad de la canci贸n? Una rejilla frontal muestra que hay c铆rculos conc茅ntricos que se al铆nean, sin importar el g茅nero. 驴Podr铆a ser que los gustos Nigerianos converjan a cierto nivel con la bailabilidad de este g茅nero?

鉁? Prueba distintos puntos de datos (energy, loudness, speechiness) y m谩s o distintos g茅neros musicales. 驴Qu茅 puedes descubrir? Da un vistazo a la table `df.describe()` para ver la propagaci贸n general de los puntos de datos.

### Ejercicio - distribuci贸n de datos

驴Son significativamente diferentes estos tres g茅neros en la percepci贸 nde su bailabilidad, basados en su popularidad?

1. Examina nuestra distribuci贸n de datos de los tres mejores g茅neros por popularidad y bailabilidad junto con un eje x e y dados.

    ```python
    sns.set_theme(style="ticks")
    
    g = sns.jointplot(
        data=df,
        x="popularity", y="danceability", hue="artist_top_genre",
        kind="kde",
    )
    ```

    Puedes descubrir c铆rculos conc茅ntricos entorno alrededor de un punto general de convergencia, mostrando la distribuci贸n de los puntos.

    > 馃帗 Nota que este ejemplo usa KDE (Estimaci贸n de la Densidad del Kernel), gr谩fico que representa los datos usando una curva de densidad de probabilidad continua. Esto nos permite interpretar los dato al trabajar con distribuciones m煤ltilples.

    En general, los tres g茅neros se alinean libremente en t茅rminos de su probabilidad y bailabilidad. Determinar los grupos en estos datos libremente alineados ser谩 un desaf铆o:

    ![Distribuci贸n](../images/distribution.png)

1. Crea un gr谩fico de dispersi贸n:

    ```python
    sns.FacetGrid(df, hue="artist_top_genre", size=5) \
       .map(plt.scatter, "popularity", "danceability") \
       .add_legend()
    ```

    Un gr谩fico de dispersi贸n de los mismos ejes muestra un patr贸n similar de convergencia

    ![Cadr铆cula de facetas](../images/facetgrid.png)

En general, para el agrupamiento, puedes usar gr谩ficos de dispersi贸n para mostrar grupos de datos, por lo que dominar este tipo de visualizaciones es muy 煤til. En la siguiente lecci贸n, tomaremos estos datos filtrados y usaremos el agrupamiento k-medias para descubrir grupos en estos datos que se vean superpuestos de formas interesantes.

---

## 馃殌Desaf铆o

En preparaci贸n para la siguiente lecci贸n, realiza una gr谩fica acerca de los diverso algoritmos de agrupamiento que puedes descubrir y usar en un ambiente de producci贸n. 驴Qu茅 tipo de problemas trata de abordar el agrupamiento?

## [Examen porterior a la lecci贸n](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/28?loc=es)

## Revisi贸n y auto-estudio

Antes que apliques los algoritmos de agrupamiento, como aprendimos, es buena idea entender la naturaleza de tu conjunto de datos. Lee m谩s sobre este tema [aqu铆](https://www.kdnuggets.com/2019/10/right-clustering-algorithm.html)

[Este 煤til art铆culo](https://www.freecodecamp.org/news/8-clustering-algorithms-in-machine-learning-that-all-data-scientists-should-know/) te gu铆a a trav茅s de las distintas formas en que se comportan los distintos algoritmos de agrupamiento, dadas distintas formas de los datos.

## Asignaci贸n

[Investiga otras visualizaciones para agrupamiento](assignment.es.md)
