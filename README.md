# Apuntes-Séptima y Octava semana
Apuntes control de movimiento - Segundo Corte-Séptima y Octava Semana

# PERFILES DE MOVIMIENTO
En esta clase se abordó el diseño de perfiles en el entorno virtual de Simscape, con énfasis en las diversas conexiones posibles y su comportamiento dinámico según la configuración seleccionada. Se profundizó en la asignación y funcionamiento de cada eje, analizando su movimiento, rango de rotación, y las interacciones mecánicas asociadas. Asimismo, se exploró el diseño detallado de cada perfil, destacando la posibilidad de ajustar el tamaño de los ejes y simular desplazamientos mediante los efectores proporcionados por el sistema, optimizando así la precisión y funcionalidad del modelo virtual.

## 1. Definición movimiento de perfil
El movimiento de un perfil está determinado como el movimiento dentro de una trayectoría para cumplir el recorrido de un punto A a un punto B. Existen diferentes casos dentro del movimiento de perfil que está dado por la cantidad de ejes que se quieran mover al tiempo.

>🔑 *Caso 1:* Es el caso más simple en el cual se mueve un solo eje por lo que el movimiento se observará como una línea recta.
>
>🔑 *Caso 2:* Para el manejo de diferentes ejes se requiere una combinación de diferentes perfiles para lograr una tarea específica; para entender el movimiento de cada eje se debe tener en cuenta la posición, velocidad y aceleración de cada etapa.
>

## Conceptos básicos de la Cinemática de Movimiento
### Cálculos de Perfil de Movimiento:
* Posición (X(t)):  Determina la ubicación del sistema o efector final en función del tiempo.
* Velocidad  $v(\tau): \frac{d\chi }{d\tau}$ : Evalúa la tasa de cambio de posición y permite definir un movimiento suave y eficiente. La anterior ecuación se puede reescribir en cuestión de integrales de la siguiente manera: $s=\int v(\tau )d\tau$.
* Aceleración $a(\tau): \frac{dv}{d\tau}$ : Controla la aceleración máxima para evitar esfuerzos mecánicos excesivos. La anterior ecuación se puede reescribir en cuestión de integrales de la siguiente manera: $s=\int a(\tau )d\tau$.

La siguiente imagen refleja el comportamiento gráfico de la posición, velocidad y aceleración. 

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/0a3b3c05c17711da2cf50962724627c729bb02ea/perfil%20de%20movimiento.png)


## 2. Reglas Geométricas
Para el desarrollo y movimiento de perfiles se deben tener en cuenta diferentes conceptos frente a la dinámica de cada uno de los ejes del perfil. A continuación realizaremos una breve explicación de los puntos a tener en cuenta.
* Cualquier punto de la posición del movimiento del sistema está dado por el área bajo la curva de velocidad hasta el instante de tiempo a analizar.
* La aceleración se puede denotar como la pendiente de la curva de velocidad.
* Este análisis está dado por las siguientes ecuaciones:
  $v= v_{0} + a(t-t_{0})$

  $s=s_{0}+\frac{1}{2}(t-t_{0})(v_{0}+a(t-t_{0}))$

En las anteriores ecuaciones el parámetro $t_{0}$ es el tiempo inicial del movimiento del intervalo donde se calculará, $v_{0}$ es la velocidad inicial del sistema del intervalo donde se calculará y $s_{0}$ la posición inicial en la que se encontrará el sistema.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/0d7817a8221d6b92206eb80cb93a1d519e691503/area%20bajo%20la%20curva.png)

## 3. Tipos de Perfiles

En sistemas mecánicos y de control, el movimiento se describe mediante cambios en la posición de un objeto a lo largo del tiempo. Dependiendo de cómo varíen la velocidad y la aceleración, se pueden clasificar en distintos tipos, cada uno con aplicaciones específicas en robótica, automatización y maquinaria industrial.

Los perfiles de movimiento más comunes incluyen:

**Perfil Trapezoidal**:  Es uno de los más utilizados en control de movimiento porque proporciona un equilibrio entre rapidez y suavidad. Se llama así porque la forma de la gráfica de velocidad en función del tiempo tiene un aspecto de trapezoide.

El movimiento se divide en tres fases principales:

*Aceleración constante*

* El sistema inicia desde el reposo y aumenta su velocidad de manera uniforme hasta alcanzar una velocidad máxima.

* La aceleración es constante en esta etapa.

*Velocidad constante*

* El sistema se mueve a velocidad máxima sin cambios.

* No hay aceleración ni desaceleración en esta fase.

*Desaceleración constante*

* El sistema reduce su velocidad de manera uniforme hasta detenerse o alcanzar el nuevo punto de destino.

* La desaceleración es constante y de la misma magnitud que la aceleración.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/7049ff48ecd31d96b365c153e34da52d09cd3c59/perfil%20trapezoidal.png)

**Curva en S**: Es una evolución del perfil trapezoidal que suaviza los cambios bruscos en aceleración y desaceleración. Se llama así porque su gráfica de posición en función del tiempo tiene una forma similar a una letra "S".

Este tipo de movimiento es ideal cuando se busca minimizar vibraciones, reducir el impacto mecánico y mejorar la estabilidad en sistemas de control de movimiento.

El movimiento se divide en cinco fases principales:

*Aceleración progresiva*

* En lugar de iniciar con una aceleración constante, esta aumenta gradualmente, lo que suaviza el arranque.

*Aceleración constante*

* El sistema mantiene una aceleración estable hasta alcanzar la velocidad máxima.

*Velocidad constante*

* El sistema se desplaza sin cambios en la velocidad.

*Desaceleración constante*

* Se inicia la fase de frenado, reduciendo la velocidad de manera controlada.

*Desaceleración progresiva*

* En vez de frenar bruscamente, la desaceleración disminuye de manera gradual hasta el reposo.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Sexta-Semana/blob/77a85765182e09a1f234fc1bdefb7dcf80b80b5d/curva%20s.png)

*Modelo Matemático Curva en S*

* Según la cantidad de segmentos curvos que presente la velocidad, esta está dada por un modelo de polinomio de segundo orden.

$$v(t)=C_{1}t^{2} + C_{2}t + C{3}$$

  En la fórmula anterior $C_{1}$, $C_{2}$ y $C_{3}$ son coeficientes que están determinadas por las condiciones de frontera.

## 4. Movimiento Multi-eje
Se refiere a la coordinación de varios ejes de movimiento (X, Y, Z, rotación, etc.) para lograr trayectorias complejas y precisas en sistemas mecánicos y robóticos. Es fundamental en aplicaciones donde un solo eje no es suficiente para realizar una tarea, como en robots industriales, máquinas CNC y brazos manipuladores.

A continuación explicaremos 3 tipos de movimiento multi-eje:

*Movimiento Secuencial*

* Cada eje se mueve por separado, uno tras otro.

* Es simple de programar pero más lento.

*Movimiento Coordinado*

* Los ejes se mueven simultáneamente siguiendo una trayectoria planificada.

* Evita movimientos bruscos y reduce el tiempo de operación.

*Interpolación Multieje*

* Lineal: Mueve varios ejes a velocidad constante en línea recta.

* Circular: Crea trayectorias circulares coordinando dos ejes.

* Helicoidal: Combina movimiento circular con desplazamiento en otro eje.

* Spline: Usa curvas suaves para trayectorias precisas.


## 5. Ejercicios

### A partir del perfil de velocidad, obtenga la posición del eje (axis) transcurridos 120 ms.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes_-Septima-y-Octava-Semana/blob/e228ab61be56aace3489af93800206a81f0eb4c7/ejercicio%201.png)

Tiempo total: 120 ms

Tiempo de aceleración: 40 ms

Tiempo de velocidad constante: 50 ms

Tiempo de desaceleración: 30 ms

Velocidad máxima: 40 cts/ms

$$V_{a}(t) = \frac{2V_{m}}{t^{2}_{a}}*t^{2}$$

$V_{a}(t) = \frac{2*40}{40^{2}}*t^{2}$

$V_{a}(t) = 0.05 t^{2}$

$S_{a}(t) = \int_{0}^{40} 0.05 t^{2} dt$

$S_{a}(t) = 1066.67 cts$

### Velocidad constante:

$V_{B}(t)=V_{m} = 40$

$S_{B}=40*50$

$S_{B}=2000 cts$

### Desaceleración:

$V_{c}(t) = V_{m} - \frac{2V_{m}}{t_{d}^{2}}(t-t_{d})^{2}$

$V_{c}(t)=40-\frac{2*40}{30^{2}}(t-30)^{2}$

$V_{c}(t)= 40-\frac{80}{900} (t-30)^{2}$

$S_{c}(t)=\int_{0}^{30} (40-\frac{80}{900} (t-30)^{2})dt$

*Usamos un cambio de variable u=t−30⇒du=dt:*

$S_{c}=\int_{0}^{30}(40-\frac{80}{900} u^{2}) du$

$S_{c} = 400 cts$}

### Posición total del eje a los 120 ms

$S(120)=S_{a} + S_{b} + S_{c}$

$S(120)= 1066.67 + 2000 + 400$

$S(120)= 3466.67 cts$

## Un actuador lineal debe moverse desde una posición inicial de 0 mm hasta 120 mm en 6 segundos. Se desea usar un perfil de velocidad trapezoidal con aceleración constante de 10 mm/s².

* ¿Cuál será la velocidad máxima alcanzada durante el movimiento?

En un perfil trapezoidal simétrico (aceleración constante y desaceleración igual), el movimiento se divide en 3 fases:

* Aceleración hasta $V_{max}$
​
* Movimiento a $V_{max}$

* Desaceleración a 0

Sea $t_{\alpha}$ el tiempo de aceleración (y también de desaceleración), y $t_{c}$ el tiempo de velocidad constante.

Sabemos que: $V_{max} = a*t_{\alpha}$

La distancia total recorrida es: $s=s_{1} + s_{2} + s_{3}$

donde:

**$S{1}= \frac{1}{2} at_{\alpha}^{2}$**

**$S{2}= V_{max} + t_{c}$**

**$S{3}= \frac{1}{2} at_{\alpha}^{2}$**

Y el tiempo total:

$T_{total}= 2t_{\alpha} + t_{c}$

$t_{c}=T_{total}-2t_{\alpha}$

Sustituyendo:

$s=at_{\alpha}^{2} + at_{\alpha} (t_{tota}-at_{\alpha})$

$s=at_{\alpha}[t_{tota}-t_{\alpha}]$

Ahora sustituyo:

$120=10*t_{\alpha} (6-t_{\alpha})$

$10t_{\alpha}^{2} - 60t_{\alpha} + 120 =0$

$t_{\alpha}^{2} - 6t_{\alpha} + 12=0$

$t_{\alpha} = \frac{6\pm\sqrt{(-6)^{2}-4*(1)(12)}}{2(1)}$

$t_{\alpha} = \frac{6\pm\sqrt{36-48}}{2}$

**No tiene solución real**

Esto significa que el perfil trapezoidal no tiene fase de velocidad constante.

Entonces el perfil es en realidad triangular, con aceleración y luego desaceleración directamente.

* Perfil Triangular (sin velocidad constante)
En este caso:

La distancia se reparte simétricamente:

$S=2*\frac{1}{2} at_{\alpha}^{2}$

$120=10t_{\alpha}^{2}$

$t_{\alpha}=\sqrt{12} \approx 3.464 s$

Cada fase dura $t_{\alpha}= 3.464 s$

* ¿Cuánto dura cada fase del movimiento (aceleración, velocidad constante, desaceleración)?

> Aceleración: 3.464 s

> Desaceleración: 3.464 s

> Velocidad constante: 0 s (no hay)


## Dada una curva de velocidad que sigue la ecuación: $V(t) = 4t$ en el intervalo de $t = 0$ a $t = 5$ s

*  Calcula el desplazamiento total usando el área bajo la curva.

$S=\int_{0}^{5} v(t) dt$

$S=\int_{0}^{5} 4 dt$

Resolviendo la integral:

$S=4*(\frac{5^{2}}{2} - \frac{0^{2}}{2}$

$S=50$

El desplazamiento total es: $S=50$

## 6. Conclusiones

* El diseño adecuado de perfiles de movimiento en entornos virtuales como Simscape permite optimizar la eficiencia y precisión de los sistemas mecánicos, facilitando la simulación de trayectorias y desplazamientos controlados.

* El análisis de posición, velocidad y aceleración es fundamental para garantizar movimientos suaves y eficientes, evitando esfuerzos mecánicos excesivos y optimizando el rendimiento del sistema.

*Ventajas de los Perfiles de Movimiento Comunes*

* Perfil trapezoidal: Proporciona un equilibrio entre rapidez y suavidad, siendo ideal para aplicaciones que requieren eficiencia sin excesiva complejidad.

* Perfil en S: Reduce vibraciones y esfuerzos mecánicos al suavizar los cambios de aceleración y desaceleración, mejorando la estabilidad del sistema.

* La coordinación de múltiples ejes permite lograr trayectorias complejas en robótica, CNC y sistemas automatizados. Diferentes estrategias, como el movimiento secuencial, coordinado e interpolación multieje, permiten adaptar el sistema según los requisitos de la aplicación.

## 7. Referencias

* Craig, J. J. (2005). Introduction to Robotics: Mechanics and Control (3rd ed.). Pearson Prentice Hall.

* Groover, M. P. (2020). Automation, Production Systems, and Computer-Integrated Manufacturing (5th ed.). Pearson.

* Sciavicco, L., & Siciliano, B. (2000). Modeling and Control of Robot Manipulators (2nd ed.). Springer.

* Norton, R. L. (2020). Design of Machinery: An Introduction to the Synthesis and Analysis of Mechanisms and Machines (6th ed.). McGraw-Hill Education.

* MathWorks. (n.d.). Modeling Mechanical Systems in Simscape. Recuperado de https://www.mathworks.com/help/physmod/simscape/

* MathWorks. (n.d.). Motion Profiles. Recuperado de https://www.mathworks.com/help/sm/ug/motion-profiles.html

* Spong, M. W., Hutchinson, S., & Vidyasagar, M. (2006). Robot Modeling and Control. Wiley.
