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

La frecuencia media inicia alrededor de valores cercanos a 120–125 Hz y presenta una disminución progresiva hasta valores próximos a 115 Hz. Esta tendencia se confirma con la pendiente negativa de la regresión lineal (-0.06 Hz/s), lo que indica una reducción gradual del contenido frecuencial de la señal.

Por su parte, la frecuencia mediana presenta una disminución más pronunciada, pasando aproximadamente de 90 Hz a valores cercanos a 80 Hz. La pendiente de la regresión (-0.11 Hz/s) es más negativa que la de la frecuencia media, lo que sugiere que este parámetro es más sensible a los cambios asociados a la fatiga.

Además de la tendencia general, se observan fluctuaciones locales en ambas curvas, las cuales pueden atribuirse a variaciones en la activación de las unidades motoras durante la contracción. Sin embargo, estas variaciones no afectan la tendencia global descendente.

Desde el punto de vista fisiológico, este comportamiento se relaciona con la disminución en la velocidad de conducción de las fibras musculares y la fatiga progresiva de las unidades motoras. Como consecuencia, el contenido espectral de la señal se desplaza hacia frecuencias más bajas, lo cual se refleja directamente en la disminución de la frecuencia media y mediana.

En conjunto, estos resultados evidencian que el análisis espectral de la señal EMG permite identificar de manera efectiva la aparición de fatiga muscular durante contracciones sostenidas.

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


#### Análisis de los resultados

Los resultados obtenidos a partir del análisis espectral de la señal electromiográfica evidencian una variación progresiva en los parámetros de frecuencia media y frecuencia mediana a lo largo del tiempo. Esta variación se manifiesta principalmente como una tendencia decreciente, lo que indica un desplazamiento del contenido espectral hacia frecuencias más bajas.

Este comportamiento puede explicarse por diferentes factores asociados a la fisiología de la fatiga muscular:

- Disminución en la velocidad de conducción de las fibras musculares.
- Fatiga progresiva de las unidades motoras durante la contracción sostenida.
- Cambios en el reclutamiento y sincronización de las fibras musculares.
- Acumulación de metabolitos como el lactato, que afectan la eficiencia del músculo.

Además, se observaron fluctuaciones en los valores de frecuencia a lo largo del tiempo, las cuales pueden atribuirse a:

- Variabilidad natural en la activación muscular.
- Presencia de ruido en la señal, incluso después del filtrado.
- Movimiento o leve variación en la posición de los electrodos.
- Limitaciones propias del proceso de segmentación de la señal.

Es importante considerar que el cálculo de la frecuencia media y mediana depende de la calidad del espectro obtenido. Factores como la longitud de las ventanas, el solapamiento y el filtrado aplicado pueden influir en la precisión de estos parámetros.

En conjunto, los resultados muestran que el análisis en el dominio de la frecuencia es una herramienta útil para identificar la fatiga muscular, permitiendo observar de manera objetiva la disminución del contenido de altas frecuencias en la señal EMG durante contracciones sostenidas.

---

### Parte C 
En esta sección se realizó un análisis espectral detallado de la señal electromiográfica (EMG) mediante la aplicación de la Transformada Rápida de Fourier (FFT), con el objetivo de observar cómo varía el contenido frecuencial a lo largo de una contracción muscular sostenida.

Se seleccionaron segmentos representativos de la señal correspondientes al inicio, la mitad y el final de la contracción. A cada uno de estos segmentos se le aplicó una ventana de Hamming para reducir efectos de fuga espectral y mejorar la estimación del contenido en frecuencia.

```python
xi = xi * np.hamming(N_seg)
X_seg = np.abs(fft(xi))
```

Para cada segmento se calculó el espectro de magnitud considerando únicamente el rango de frecuencias entre 20 y 450 Hz, correspondiente a la actividad muscular. Estos espectros fueron representados en escala logarítmica, lo que permitió una mejor visualización de las diferencias en la distribución de energía.

La comparación entre los espectros mostró una disminución progresiva del contenido de altas frecuencias a medida que avanza la contracción. En el segmento inicial se observa una mayor presencia de componentes de alta frecuencia, mientras que en el segmento final estas componentes se reducen notablemente.

Adicionalmente, se identificó la frecuencia pico en cada segmento, evidenciando un desplazamiento hacia valores más bajos con el paso del tiempo. Este comportamiento es consistente con la aparición de fatiga muscular.

```python
f_pico = freqs_s[np.argmax(X_seg)]
```
Estos resultados reflejan cambios fisiológicos en el músculo, como la disminución en la velocidad de conducción de las fibras musculares y la fatiga de las unidades motoras, lo cual provoca una redistribución del contenido espectral hacia frecuencias más bajas.

En conjunto, el análisis mediante FFT confirma que el estudio en el dominio de la frecuencia es una herramienta eficaz para detectar y caracterizar la fatiga muscular en señales electromiográficas.

<p align="center">
<img width="889" height="650" alt="image" src="https://github.com/user-attachments/assets/152a0590-d05f-4898-8665-7e8b1db76e07" />
</p>
<p align="center">
  <em>Desplazamiento del pico espectral</em></p
                                              
La gráfica muestra la variación de la frecuencia pico de la señal electromiográfica en tres momentos representativos de la contracción muscular: inicio, mitad y final. Se observa una disminución marcada desde aproximadamente 83.7 Hz al inicio hasta valores cercanos a 47 Hz en la mitad y el final de la contracción.

Este comportamiento evidencia un desplazamiento significativo del contenido espectral hacia frecuencias más bajas, especialmente en la primera mitad del esfuerzo. La caída abrupta entre el inicio y la mitad sugiere que el proceso de fatiga muscular comienza de forma temprana durante la contracción sostenida.

Entre la mitad y el final, la frecuencia pico se mantiene relativamente estable (47.3 Hz a 47.0 Hz), lo que indica que el músculo ya se encuentra en un estado de fatiga más avanzado, donde los cambios en la actividad eléctrica son menos pronunciados.

Desde el punto de vista fisiológico, este fenómeno se asocia con:

- La disminución en la velocidad de conducción de las fibras musculares.
- La fatiga de las unidades motoras activas.
- Una mayor sincronización de las fibras, lo que favorece componentes de menor frecuencia.

En conjunto, la gráfica confirma que la frecuencia pico es un indicador sensible de la fatiga muscular, mostrando una reducción clara a medida que progresa la contracción. Además, complementa los resultados obtenidos con la frecuencia media y mediana, reforzando la evidencia del desplazamiento espectral hacia bajas frecuencias.

---
### Preguntas para la discusión

#### 1. ¿Cambian los valores de frecuencia media y mediana a medida que el músculo se acerca a la fatiga? ¿A qué podría atribuirse este cambio?

Sí, los valores de frecuencia media y frecuencia mediana presentan una disminución progresiva a medida que el músculo se acerca a la fatiga. Este comportamiento se evidencia en las gráficas obtenidas, donde ambas frecuencias muestran una tendencia descendente a lo largo del tiempo.

Este cambio se atribuye principalmente a factores fisiológicos asociados al proceso de fatiga muscular, entre los que se destacan:

- La disminución en la velocidad de conducción de las fibras musculares.
- La fatiga de las unidades motoras, que reduce su capacidad de activación eficiente.
- La acumulación de metabolitos (como el lactato), que afecta el funcionamiento del músculo.
- Cambios en el reclutamiento y sincronización de las fibras musculares.

Como consecuencia, el contenido espectral de la señal electromiográfica se desplaza hacia frecuencias más bajas, lo que se refleja directamente en la reducción de la frecuencia media y mediana.


---

#### 2. ¿Cómo justifica el uso de herramientas como la transformada de Fourier en escenarios como, por ejemplo, terapias de rehabilitación?

El uso de herramientas como la Transformada de Fourier se justifica porque permite analizar la señal en el dominio de la frecuencia, proporcionando información que no es fácilmente observable en el dominio del tiempo.

En el contexto de terapias de rehabilitación, este tipo de análisis resulta especialmente útil, ya que permite detectar la fatiga muscular de forma objetiva mediante el estudio de cambios en las frecuencias de la señal. Asimismo, facilita el seguimiento del progreso del paciente al evaluar cómo varía la respuesta muscular a lo largo del tiempo.

De igual manera, este análisis contribuye a ajustar la intensidad y duración de los ejercicios, evitando sobrecargas o posibles lesiones. Además, brinda información sobre la activación muscular, lo que resulta útil para diseñar programas de rehabilitación más personalizados y eficientes.

En este sentido, la Transformada de Fourier se convierte en una herramienta clave dentro del procesamiento de señales biomédicas, ya que permite extraer características relevantes que apoyan la toma de decisiones clínicas.

---

## Discusión y analisis de resultados

El análisis de la señal electromiográfica permitió evidenciar cambios significativos tanto en el dominio del tiempo como en el dominio de la frecuencia durante una contracción muscular sostenida hasta la fatiga. En el dominio temporal se observaron variaciones en la amplitud de la señal asociadas a la actividad muscular, mientras que en el dominio frecuencial se identificaron transformaciones relevantes en la distribución de energía.

Los resultados obtenidos a partir del cálculo de la frecuencia media y la frecuencia mediana muestran una tendencia decreciente a lo largo del tiempo. Esta disminución indica un desplazamiento progresivo del contenido espectral hacia frecuencias más bajas, lo cual es un comportamiento característico de la fatiga muscular. La pendiente negativa observada en ambas curvas confirma esta tendencia, siendo más pronunciada en la frecuencia mediana, lo que sugiere una mayor sensibilidad de este parámetro frente a los cambios fisiológicos del músculo.

El análisis por segmentos refuerza este comportamiento. Al comparar el espectro en diferentes momentos de la contracción (inicio, mitad y final), se evidencia una reducción del contenido de altas frecuencias y un cambio en la distribución espectral hacia componentes de menor frecuencia. Este fenómeno se confirma mediante el desplazamiento de la frecuencia pico, que presenta una disminución considerable desde el inicio hasta la mitad del ejercicio, estabilizándose posteriormente en valores más bajos. Esto sugiere que la fatiga comienza a manifestarse de manera temprana durante la contracción sostenida.

Desde el punto de vista fisiológico, estos resultados pueden explicarse por la disminución en la velocidad de conducción de las fibras musculares, la fatiga progresiva de las unidades motoras y la acumulación de metabolitos que afectan el desempeño muscular. Estos factores provocan una modificación en la señal EMG, reflejada en la pérdida de componentes de alta frecuencia.

A pesar de la tendencia general observada, también se presentan fluctuaciones en los valores de frecuencia, las cuales pueden atribuirse a variaciones en la activación muscular, presencia de ruido en la señal, pequeñas alteraciones en la posición de los electrodos y limitaciones propias del proceso de segmentación y análisis.

El uso de herramientas como la Transformada de Fourier se justifica porque permite analizar la señal en el dominio de la frecuencia, proporcionando información que no es fácilmente observable en el dominio del tiempo. En el contexto de terapias de rehabilitación, este tipo de análisis resulta especialmente útil, ya que permite detectar la fatiga muscular de forma objetiva mediante el estudio de cambios en las frecuencias de la señal. Asimismo, facilita el seguimiento del progreso del paciente al evaluar cómo varía la respuesta muscular a lo largo del tiempo.

De igual manera, este análisis contribuye a ajustar la intensidad y duración de los ejercicios, evitando sobrecargas o posibles lesiones. Además, brinda información sobre la activación muscular, lo que resulta útil para diseñar programas de rehabilitación más personalizados y eficientes. En este sentido, la Transformada de Fourier se convierte en una herramienta clave dentro del procesamiento de señales biomédicas, ya que permite extraer características relevantes que apoyan la toma de decisiones clínicas.

En conjunto, los resultados obtenidos demuestran que el análisis espectral de señales EMG es una herramienta eficaz para la identificación y caracterización de la fatiga muscular, integrando de manera coherente los hallazgos observados en las diferentes representaciones y parámetros analizados.

---

## Conclusiones

- El análisis de la señal electromiográfica permitió evidenciar de manera clara la presencia de fatiga muscular durante una contracción sostenida, manifestada a través de la disminución progresiva de la frecuencia media y la frecuencia mediana.

- El desplazamiento del contenido espectral hacia frecuencias más bajas, así como la reducción de la frecuencia pico, confirman que los parámetros en el dominio de la frecuencia son indicadores sensibles y confiables de la fatiga muscular.

- La Transformada de Fourier demostró ser una herramienta fundamental para el análisis de señales biomédicas, al permitir identificar características que no son evidentes en el dominio del tiempo.

- Los resultados obtenidos resaltan la utilidad del análisis espectral en aplicaciones clínicas, especialmente en el monitoreo de la actividad muscular y el diseño de estrategias de rehabilitación más precisas y seguras.

