# LAB-4

# Señales electromiográficas EMG 

## Asignatura

Procesamiento Digital de Señales

## Programa

Ingeniería Biomédica – Universidad Militar Nueva Granada

## Práctica de laboratorio

**Señales electromiográficas EMG**

## Integrantes

Andrea Carolina Amórtegui Carrillo – Código 5600963


---

## Descripción

El laboratorio se centra en el análisis de señales electromiográficas (EMG) para la identificación de la fatiga muscular mediante herramientas de procesamiento digital de señales. Se emplean tanto señales emuladas como señales reales adquiridas a partir de una contracción muscular sostenida hasta alcanzar la fatiga, con el fin de estudiar sus características en el dominio del tiempo y de la frecuencia.

A partir de estas señales, se realiza su adquisición, filtrado y segmentación, permitiendo analizar la evolución temporal de la actividad muscular durante el esfuerzo continuo. Se aplica la Transformada Rápida de Fourier (FFT) con el objetivo de obtener el contenido espectral de la señal y calcular parámetros característicos como la frecuencia media y la frecuencia mediana.

Adicionalmente, se evalúa cómo estos parámetros cambian a lo largo del tiempo durante la contracción sostenida, lo que permite identificar la aparición de la fatiga muscular, evidenciada principalmente por el desplazamiento del contenido frecuencial hacia componentes de menor frecuencia. Finalmente, se comparan los resultados obtenidos entre señales simuladas y reales, con el propósito de comprender el comportamiento fisiológico del músculo bajo condiciones de esfuerzo prolongado.

---


## Metodología

El desarrollo del laboratorio se dividió en dos partes principales. En cada etapa se emplearon herramientas de programación en Python para el procesamiento y análisis de señales electromiográficas (EMG).

En primer lugar, se realizó la adquisición y el acondicionamiento de la señal, tanto emulada como real, obtenida a partir de una contracción muscular sostenida hasta alcanzar la fatiga. A estas señales se les aplicó un filtrado pasa banda (20–450 Hz) con el fin de eliminar ruido y artefactos, garantizando así una mejor calidad para su posterior análisis.

Posteriormente, se llevó a cabo el análisis de la señal en el dominio del tiempo y de la frecuencia. Se segmentó la señal en diferentes intervalos representativos a lo largo de la contracción sostenida, permitiendo observar la evolución de la actividad muscular. Para cada segmento, se aplicó la Transformada Rápida de Fourier (FFT), obteniendo su espectro de amplitud y permitiendo identificar la distribución de frecuencias presente en la señal.

Finalmente, se calcularon parámetros espectrales relevantes como la frecuencia media y la frecuencia mediana para cada segmento analizado. Estos parámetros se representaron gráficamente con el fin de evaluar su comportamiento a lo largo del tiempo y evidenciar el efecto de la fatiga muscular, caracterizado por el desplazamiento del contenido frecuencial hacia bajas frecuencias. Asimismo, se compararon los resultados entre la señal emulada y la señal real para analizar diferencias en su comportamiento fisiológico.

---

## Explicación del código

En esta sección se explica el funcionamiento del código, en el cual se emplean herramientas de programación en Python para el procesamiento y análisis de señales electromiográficas (EMG). Se destaca la importancia del análisis espectral mediante la Transformada Rápida de Fourier (FFT) y métodos como Welch, así como la aplicación de filtros digitales pasa banda implementados con funciones de la librería scipy.signal. Adicionalmente, se utilizan librerías como NumPy, Pandas y Matplotlib para la manipulación de datos, el cálculo de parámetros relevantes en el dominio de la frecuencia y la visualización de la señal, permitiendo evaluar el comportamiento espectral y su relación con la fatiga muscular.

### Importación de librerías

Primero se importan las librerías necesarias para la lectura, procesamiento y análisis de las señales electromiográficas:

* `numpy `: Se utiliza para el manejo de arreglos numéricos y la realización de operaciones matemáticas como promedios, sumas, aplicación de ventanas (Hamming) y cálculos espectrales.

* `matplotlib.pyplot `: Se emplea para la generación de gráficas en el dominio del tiempo y de la frecuencia, permitiendo visualizar la señal EMG original, filtrada y sus espectros.

* `pandas `: Permite la lectura y manipulación de archivos de datos, especialmente en formato `.txt `, facilitando la organización y extracción de la señal adquirida.

* `scipy.fft (fft, fftfreq) `: Se utiliza para calcular la Transformada Rápida de Fourier (FFT) y obtener el espectro de frecuencias de la señal.

* `scipy.signal (butter, filtfilt, welch) `:

* `butter `:Se usa para diseñar filtros digitales tipo Butterworth, tanto pasa bajos como pasa banda, adecuados para el procesamiento de señales EMG.

* `filtfilt `: Aplica el filtrado de forma bidireccional, evitando desfases en la señal.

* `welch `: Permite estimar la densidad espectral de potencia (PSD), útil para el análisis comparativo del contenido frecuencial en diferentes segmentos de la señal.

Estas herramientas son fundamentales para el procesamiento digital de señales electromiográficas, ya que permiten el acondicionamiento de la señal, su análisis en el dominio del tiempo y la frecuencia, y la extracción de características relevantes para evaluar la fatiga muscular.

<p align="center">

</p>
<p align="center">
  <em>Diagrama de flujo del codigo</em></p


---
### Parte A

En esta sección se analizó una señal electromiográfica (EMG) simulada, almacenada en un archivo en formato .txt, con el objetivo de estudiar su comportamiento en el dominio del tiempo y de la frecuencia, así como identificar posibles cambios asociados a la fatiga muscular.

La señal fue cargada mediante numpy, extrayendo el vector de tiempo y la amplitud. A partir de estos datos se calculó la frecuencia de muestreo utilizando el intervalo entre muestras. Para mejorar la calidad de la señal, se eliminó el valor medio con el fin de centrarla en cero y se aplicó un filtro pasabajos de 410 Hz que reduce el ruido de alta frecuencia.

Se realizó una representación gráfica de la señal original y la señal filtrada, lo que permitió apreciar con claridad el efecto del filtrado y la mejora en la definición de la señal.

<p align="center">
<img width="1547" height="662" alt="image" src="https://github.com/user-attachments/assets/ae4412a0-cded-495f-9441-e0337e110903" />
</p>
<p align="center">
  <em>Señal original vs Señal filtrada</em></p

La señal filtrada se dividió en ventanas de corta duración para analizar su comportamiento a lo largo del tiempo. A cada segmento se le aplicó una ventana de Hamming, lo que ayuda a reducir efectos no deseados en el análisis espectral. Sobre cada uno de estos segmentos se calculó la Transformada Rápida de Fourier (FFT), obteniendo así su contenido en frecuencia. Con esta información se calcularon la frecuencia media y la frecuencia mediana.

Estos parámetros se representaron en función del tiempo, lo que permitió observar su evolución durante toda la señal. Se ajustó una regresión lineal a estos valores para identificar tendencias, aportando una forma cuantitativa de analizar posibles cambios relacionados con la fatiga muscular.

También se calculó la FFT de la señal completa para tener una visión general de su contenido espectral. El espectro se representó en escala logarítmica, incluyendo la ubicación de la frecuencia media y mediana, lo que facilita la interpretación de la distribución de energía en la señal.

Además, se aplicó la Transformada Rápida de Fourier (FFT) a la señal con el fin de obtener su representación en el dominio de la frecuencia. Este procedimiento permitió analizar la distribución de energía en las diferentes componentes frecuenciales, lo cual es fundamental para el estudio de señales electromiográficas.

```python
X = np.abs(fft(x_filtrada))
frecuencias = fftfreq(N, 1/fs)
```

A partir de este análisis, se trabajó únicamente con las frecuencias positivas dentro del rango de interés (20–450 Hz), correspondiente a la actividad muscular relevante.

Se calcularon parámetros espectrales característicos de la señal. La frecuencia media se obtuvo como el promedio ponderado de las frecuencias, lo que permite identificar el centro de masa del espectro.

```python
corr = np.correlate(signal, signal, mode='full')
corr = corr[len(corr)//2:]
```
La frecuencia media o centroide espectral se calculó como el promedio ponderado de las frecuencias presentes en la señal, indicando el “centro de masa” del espectro.

```python
f_media = np.sum(freqs * X) / np.sum(X)
```
La frecuencia mediana se determinó como la frecuencia que divide el espectro en dos partes con igual contenido de energía, proporcionando una medida robusta del comportamiento frecuencial de la señal.

```python
acumulada = np.cumsum(X)
mitad = acumulada[-1] / 2
f_mediana = freqs[np.where(acumulada >= mitad)[0][0]]
```
Estos parámetros se calcularon para diferentes segmentos de la señal, lo que permitió analizar su evolución a lo largo del tiempo. Este enfoque resulta especialmente útil para identificar cambios en el contenido frecuencial asociados a la fatiga muscular.


### Representación gráfica de las señales

Las gráficas obtenidas permiten visualizar el comportamiento de la señal electromiográfica tanto en el dominio del tiempo como en el dominio de la frecuencia. En el dominio temporal se observan variaciones en la amplitud asociadas a la actividad muscular durante la contracción, mientras que en el dominio frecuencial se identifican las principales componentes de energía de la señal.

A partir de estas representaciones, es posible evidenciar cambios en la distribución de frecuencias a lo largo del tiempo. En particular, se observa una tendencia a la disminución de las componentes de alta frecuencia y un desplazamiento del contenido espectral hacia frecuencias más bajas, lo cual es característico del proceso de fatiga muscular.


### Resultado parte A

El análisis espectral permitió caracterizar la señal electromiográfica mediante parámetros relevantes como la frecuencia media y la frecuencia mediana, los cuales describen la distribución de energía en el dominio de la frecuencia.

Se observó que, a medida que avanza la contracción muscular, ambos parámetros tienden a disminuir de forma progresiva. Esta variación indica un desplazamiento del contenido espectral hacia frecuencias más bajas, lo que es consistente con la aparición de la fatiga muscular. La tendencia se evidencia tanto en las gráficas de evolución temporal como en el ajuste de regresión lineal, donde se obtienen pendientes negativas.

Además, al comparar los espectros de diferentes segmentos de la señal (inicio, mitad y final), se identifica una reducción en las componentes de alta frecuencia y un cambio en la frecuencia pico hacia valores menores. Este comportamiento refleja cambios fisiológicos en el músculo, como la disminución en la velocidad de conducción de las fibras musculares y la fatiga de las unidades motoras.

Estos resultados confirman la utilidad del análisis en el dominio de la frecuencia como una herramienta efectiva para la detección de fatiga muscular a partir de señales electromiográficas.

---

### Parte B

En esta sección se realizó el análisis de una señal electromiográfica (EMG) real obtenida a partir de una contracción muscular sostenida hasta la fatiga, con el objetivo de evaluar su comportamiento espectral a lo largo del tiempo.

Inicialmente, la señal fue cargada desde un archivo utilizando la librería pandas, seleccionando el canal correspondiente a la medición EMG. Se asumió una frecuencia de muestreo de 1000 Hz y se construyó el eje temporal para su análisis.

Para el acondicionamiento de la señal, se eliminó el valor medio con el fin de centrarla en cero y se aplicó un filtro pasabanda entre 20 y 450 Hz, rango característico de las señales electromiográficas. Este filtrado permitió reducir el ruido y conservar únicamente la información relevante de la actividad muscular.

```python
x = x - np.mean(x)
x_filtrada = filtro_pasabanda(x, fs, 20, 450)
```
<p align="center">
<img width="1523" height="632" alt="image" src="https://github.com/user-attachments/assets/03c16d7d-741b-4b9c-a288-0c23f4aa2b60" />
</p>
<p align="center">
  <em>Señal original vs Señal filtrada</em></p

Se generó una representación gráfica de la señal original y la señal filtrada, lo que permitió evidenciar la mejora en la calidad de la señal tras el proceso de filtrado.

Posteriormente, la señal fue segmentada en ventanas con solapamiento, lo que permitió analizar su evolución durante toda la contracción. En cada segmento se aplicó la Transformada Rápida de Fourier (FFT) para obtener su contenido en frecuencia.

```python
fm, fmed = calcular_frecuencias(xi, fs)
```
<p align="center">
<img width="1294" height="647" alt="image" src="https://github.com/user-attachments/assets/dad21b15-341f-45e5-a9cf-7ffb78e2d639" />
</p>
<p align="center">
  <em>Transformada de fourier</em></p

A partir de este análisis se calcularon parámetros espectrales como la frecuencia media y la frecuencia mediana, los cuales fueron representados en función del tiempo. Esto permitió observar la evolución de estas frecuencias a medida que el músculo se aproxima a la fatiga.

<p align="center">
<img width="1286" height="647" alt="image" src="https://github.com/user-attachments/assets/a0673bff-b550-43e1-84b6-03bb801f7263" />
</p>
<p align="center">
  <em>Frecuencia media y mediana</em></p

Adicionalmente, se realizó un ajuste mediante regresión lineal sobre estos parámetros, con el fin de identificar tendencias en su comportamiento. La pendiente obtenida proporciona una medida cuantitativa del cambio en el contenido frecuencial de la señal.

Para complementar el análisis, se seleccionaron tres segmentos representativos de la señal (inicio, mitad y final), sobre los cuales se calculó la FFT. Esto permitió comparar directamente el contenido espectral en diferentes momentos de la contracción.

```python
X_seg = np.abs(fft(xi))
```
<p align="center">
<img width="1297" height="621" alt="image" src="https://github.com/user-attachments/assets/0a66fea1-e741-46e0-b7de-52e7cea56a1f" />
</p>
<p align="center">
  <em>Transformada de fourier en segmento</em></p
 
Se identificó la frecuencia pico en cada uno de estos segmentos, evidenciando un desplazamiento hacia frecuencias más bajas a medida que avanza la contracción. Este comportamiento es característico de la fatiga muscular y refleja cambios en la activación de las fibras musculares.

<p align="center">
<img width="902" height="647" alt="image" src="https://github.com/user-attachments/assets/efaf64dc-759b-453a-b9a7-fa467fabe9bc" />
</p>
<p align="center">
  <em>Señal original vs Señal filtrada</em></p


#### Medición del Jitter (variación en la frecuencia fundamental)

El jitter mide la variación en el periodo de la señal de voz entre ciclos consecutivos. Para su cálculo, se detectaron los picos de la señal, los cuales representan los ciclos de vibración. A partir de estos picos, se calcularon los periodos \( T_i \) y sus diferencias sucesivas.

El jitter absoluto se obtuvo como el promedio de las diferencias entre periodos consecutivos, mientras que el jitter relativo se calculó como el porcentaje de esta variación respecto al periodo promedio.

Los resultados obtenidos muestran valores elevados de jitter en varias señales, especialmente en las voces masculinas. Por ejemplo, la señal *hombre1.wav* presenta un jitter de 13.9308%, mientras que *mujer3.wav* alcanza un valor de 12.4154%. Estos valores se encuentran por encima del rango típico (menor al 1%), lo que indica una alta variabilidad en la frecuencia de la señal.

#### Medición del Shimmer (variación en la amplitud)

El shimmer mide la variación en la amplitud de la señal entre ciclos consecutivos. Para su cálculo, se tomaron las amplitudes en los picos detectados y se analizaron las diferencias entre valores consecutivos.

El shimmer absoluto corresponde al promedio de estas diferencias, mientras que el shimmer relativo se expresa como un porcentaje respecto a la amplitud promedio.

En los resultados obtenidos, se observan valores de shimmer superiores a los rangos típicos (3%–5%). Por ejemplo, la señal *hombre1.wav* presenta un shimmer de 17.6272%, y *hombre2.wav* alcanza 15.1376%. Incluso en señales femeninas como *mujer3.wav*, el valor es de 10.0855%, lo cual indica una variabilidad significativa en la amplitud de la señal.

#### Análisis de los resultados

Los valores obtenidos de jitter y shimmer evidencian una alta variabilidad en varias de las señales analizadas. Esto puede explicarse por diferentes factores:

- Presencia de ruido en las grabaciones.
- Segmentos de voz que no son completamente periódicos.
- Variaciones naturales en la producción vocal de los hablantes.
- Limitaciones en la detección automática de picos.
- Condiciones no controladas durante la adquisición de las señales.

Además, es importante considerar que el cálculo de estos parámetros depende fuertemente de la correcta identificación de los ciclos de la señal. Si la señal no presenta una periodicidad clara, los valores de jitter y shimmer pueden aumentar considerablemente.

#### Resultados obtenidos

Los valores finales de jitter y shimmer se resumen en la siguiente tabla:

| Archivo     | Genero | Jitter (%) | Shimmer (%) |
|------------|--------|------------|-------------|
| mujer1.wav | Mujer  | 3.1462     | 4.9545      |
| mujer2.wav | Mujer  | 2.2534     | 5.5305      |
| mujer3.wav | Mujer  | 12.4154    | 10.0855     |
| hombre1.wav| Hombre | 13.9308    | 17.6272     |
| hombre2.wav| Hombre | 11.5165    | 15.1376     |
| hombre3.wav| Hombre | 11.6516    | 12.5142     |

A partir de estos resultados, se observa que las señales masculinas presentan, en general, mayores valores de jitter y shimmer en comparación con las señales femeninas, lo cual indica una mayor variabilidad en la frecuencia y amplitud de estas señales bajo las condiciones de análisis realizadas.

---

### Parte C – Comparación y conclusiones

#### 1. ¿Qué diferencias se observan en la frecuencia fundamental?

A partir de los resultados obtenidos, se observa una diferencia clara entre las voces masculinas y femeninas en términos de frecuencia fundamental (F0).

Las voces femeninas presentan valores de F0 más altos:
- mujer1: 229.67 Hz  
- mujer2: 178.44 Hz  
- mujer3: 181.13 Hz  

Mientras que las voces masculinas presentan valores más bajos:
- hombre1: 113.74 Hz  
- hombre2: 109.43 Hz  
- hombre3: 154.84 Hz  

Esto confirma el comportamiento esperado, ya que las voces masculinas tienen frecuencias fundamentales menores debido a que las cuerdas vocales son más largas y gruesas, generando vibraciones más lentas. En contraste, las voces femeninas presentan frecuencias más altas debido a cuerdas vocales más cortas y delgadas.

---

#### 2. ¿Qué otras diferencias notan en términos de brillo, media o intensidad?

En cuanto a la frecuencia media y el brillo (centroide espectral), se observa que en general las voces femeninas tienden a presentar valores elevados, como en el caso de:
- mujer2: 4337.16 Hz  
- mujer3: 3353.4 Hz  

Sin embargo, también se observa que una señal masculina (hombre3) presenta un valor alto (4712.82 Hz), lo cual indica que este parámetro no depende únicamente del género, sino también del contenido espectral específico de la señal y la forma de pronunciación.

En términos de energía e intensidad (RMS), no se observa una relación directa con el género. Por ejemplo:
- mujer2 presenta una intensidad alta (5071.45)
- hombre2 presenta una intensidad baja (1367.55)

Esto indica que estos parámetros dependen más de la fuerza de la voz, la distancia al micrófono y las condiciones de grabación, más que del género del hablante.

---

#### 3. Conclusiones sobre el comportamiento de la voz en hombres y mujeres

El análisis realizado permite concluir que la frecuencia fundamental es el parámetro más confiable para diferenciar entre voces masculinas y femeninas, ya que presenta una separación clara entre ambos grupos.

Por otro lado, parámetros como el brillo y la frecuencia media pueden mostrar tendencias generales, pero no son determinantes por sí solos, ya que pueden variar dependiendo del contenido espectral de la señal.

En cuanto a la energía y la intensidad, estos parámetros no permiten diferenciar el género de forma directa, ya que dependen principalmente de la forma en que se emite la voz y de las condiciones de grabación.

Adicionalmente, el análisis de jitter y shimmer mostró valores elevados en varias señales, especialmente en las masculinas:
- hombre1: jitter 13.93%, shimmer 17.62%
- hombre2: jitter 11.51%, shimmer 15.13%

Estos valores indican una alta variabilidad en la señal, lo cual puede deberse a ruido, falta de periodicidad o condiciones no controladas durante la grabación.

---

#### 4. Importancia clínica del jitter y shimmer en el análisis de la voz

El jitter y el shimmer son parámetros fundamentales en el análisis clínico de la voz, ya que permiten evaluar la estabilidad de la vibración de las cuerdas vocales.

El jitter mide las variaciones en la frecuencia entre ciclos consecutivos, mientras que el shimmer mide las variaciones en la amplitud. En condiciones normales, estos valores suelen ser bajos (jitter < 1% y shimmer < 3–5%).

En los resultados obtenidos, muchos valores superan estos rangos, lo cual puede deberse a:
- Ruido en las señales
- Segmentos no periódicos
- Errores en la detección de picos
- Condiciones de grabación no controladas

En el ámbito clínico, valores elevados de jitter y shimmer pueden estar asociados a patologías vocales como disfonías o alteraciones en las cuerdas vocales. Sin embargo, en este caso no se puede concluir la presencia de una patología, ya que los valores también pueden estar influenciados por factores externos.

Por lo tanto, estos parámetros son herramientas útiles para el análisis de la voz, pero deben ser interpretados en conjunto con otros estudios y en condiciones controladas.

---

## Discusión y analisis de resultados

Las señales de voz en el laboratorio, la idea era meternos de lleno en cómo se comportan distintas características acústicas, tanto en el tiempo como en la frecuencia, y de paso mirar unos parámetros que miden la estabilidad de la voz, como el jitter y el shimmer.

Lo primero que saltó a la vista fue lo de siempre: la frecuencia fundamental (esa que asociamos con el tono de la voz) es claramente distinta entre hombres y mujeres. En las voces femeninas andaba entre 178 Hz y 229 Hz, mientras que en las masculinas estaba más abajo, entre 109 Hz y 154 Hz. Nada nuevo bajo el sol, la teoría lo explica: cuerdas vocales más largas y gruesas vibran más lento (hombres), y las más cortas y delgadas vibran más rápido (mujeres).

Después nos pusimos a ver otros aspectos, como el centroide espectral o el brillo, que básicamente te dicen dónde se concentra la energía en el espectro. Aquí las mujeres, en general, apuntan más hacia frecuencias altas. Pero ojo, no es una regla fija. Por ejemplo, en el archivo hombre3.wav los valores de frecuencia media salieron bastante altos. Eso te hace pensar que el asunto no es solo cuestión de género, también influye cómo pronuncia cada quien, la entonación, la intensidad y hasta lo que está diciendo en ese momento.

Con el RMS, que viene siendo la intensidad promedio de la señal, no encontramos ningún patrón claro ligado al género. Había mujeres con RMS alto y hombres con RMS bajo, y viceversa. La explicación más sensata es que la intensidad depende más de cosas como si la persona habló cerca o lejos del micrófono, cómo estaba configurada la grabación, o el ruido del entorno, que de si es hombre o mujer.

Ahora, el tema del jitter y el shimmer sí que dio para pensar. El jitter mide las variaciones en el periodo (la frecuencia) de un ciclo a otro, y el shimmer hace lo mismo pero con la amplitud. En una voz estable, estos valores suelen ser bajos. Pero cuando vimos los resultados, algunos eran altísimos. En voces masculinas, por ejemplo, encontramos jitter por encima del 10% y shimmer llegando al 17%. Para que te hagas una idea, lo que se considera normal suele ser jitter menor al 1% y shimmer entre 3% y 5% más o menos.

Uno podría pensar que esos números tan altos son señal de algún problema vocal, pero no hay que apresurarse. Resulta que estos parámetros son muy sensibles. Si la señal tiene ruido, si hay partes donde la voz no es tan periódica, o si el algoritmo que usamos para detectar los picos falla un poco, los valores se disparan. Y como nuestras grabaciones no fueron en un entorno súper controlado, pues es probable que eso haya pasado. De hecho, para poder estimarlos bien tuvimos que filtrar y elegir ventanas donde la voz se viera más estable.

En el mundo clínico, el jitter y el shimmer sí se usan para evaluar la voz, sobre todo en casos de disfonías o problemas en las cuerdas vocales. Pero si hablamos de patologías más complejas, como las afasias (que afectan el lenguaje, no la parte motora de la voz), pues estos parámetros no dicen mucho. En la disartria, que sí afecta el control muscular del habla, pueden tener más sentido, pero igual hay que combinarlos con otras pruebas.

Al final, lo que queda claro es que estas herramientas son útiles, pero no son la verdad absoluta. Sirven para dar pistas, pero un diagnóstico clínico requiere más cosas: otros análisis acústicos, la opinión de especialistas, evaluaciones más completas.

En resumen, el laboratorio nos sirvió para ver en la práctica cómo el procesamiento de señales (con Fourier, autocorrelación, filtros, etc.) permite describir la voz con números y gráficas. También aprendimos que los resultados dependen un montón de cómo se tomen las muestras y cómo se procesen. Y sí, aunque hay diferencias generales entre voces de hombres y mujeres, al final cada señal es única y está llena de matices.

---

## Conclusiones

- Se logró implementar correctamente el procesamiento digital de señales de voz mediante herramientas como la Transformada de Fourier y la autocorrelación, permitiendo analizar las señales tanto en el dominio del tiempo como en el dominio de la frecuencia.

- La frecuencia fundamental (F0) demostró ser el parámetro más confiable para diferenciar entre voces masculinas y femeninas, evidenciando valores más altos en las voces femeninas y más bajos en las masculinas, en concordancia con las características fisiológicas de las cuerdas vocales.

- El análisis del centroide espectral (frecuencia media) y el brillo mostró que las voces femeninas tienden a presentar mayor contenido en frecuencias altas; sin embargo, estos parámetros no son completamente determinantes, ya que dependen del contenido espectral específico de cada señal.

- La energía y la intensidad (RMS) no presentaron una relación directa con el género, lo que indica que estos parámetros están más influenciados por factores como la forma de emisión de la voz, la intensidad del hablante y las condiciones de grabación.

- Los parámetros de jitter y shimmer permitieron evaluar la estabilidad de la señal de voz; sin embargo, los valores obtenidos fueron en muchos casos superiores a los rangos típicos, evidenciando la sensibilidad de estos indicadores frente al ruido, la falta de periodicidad y posibles errores en la detección de picos.

- Se evidenció la importancia del preprocesamiento de la señal, especialmente el filtrado y la selección de ventanas periódicas, ya que estos procesos influyen significativamente en la precisión de los resultados obtenidos.

- Se permitió comprender la relevancia del procesamiento digital de señales en aplicaciones como el análisis biomédico y el reconocimiento de voz, destacando la necesidad de trabajar con señales de buena calidad y condiciones controladas para obtener resultados más precisos

