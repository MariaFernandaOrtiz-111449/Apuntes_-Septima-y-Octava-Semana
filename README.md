# Apuntes-Sexta semana
Apuntes control de movimiento - Segundo Corte-Sexta Semana

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

*En lugar de iniciar con una aceleración constante, esta aumenta gradualmente, lo que suaviza el arranque.

*Aceleración constante*

*El sistema mantiene una aceleración estable hasta alcanzar la velocidad máxima.

*Velocidad constante*

*El sistema se desplaza sin cambios en la velocidad.

*Desaceleración constante*

*Se inicia la fase de frenado, reduciendo la velocidad de manera controlada.

*Desaceleración progresiva*

*En vez de frenar bruscamente, la desaceleración disminuye de manera gradual hasta el reposo.

![]()

**Modelo por corriente de armadura**
* Parte Eléctrica: $\upsilon a= La*Ia + Ra*Ia + Vb$
* Parte Magnética: $Tm = ( Ka*Kc*Ic )*Ia( t ) = K\tau *Ia( t )$  $Vb = Ke* \omega$  $Tm = Tc + Tp$
* Parte Mecánica: $J*\frac{\partial^2 \theta }{\partial t^2  } + b*\frac{\mathrm{d} \theta }{\mathrm{d} t} + R\theta = \tau ( t )$
$La * \frac{\mathrm{d} ( \frac{J \theta   + b\theta  + K\theta }{K\tau } )}{\mathrm{d} t} + Ra * ( \frac{J \theta   + b\theta  + K\theta }{K\tau } ) + Ke \theta  = \upsilon a$

## 2. SENSORES
Un sensores un dispositivo que detecta cambios en una magnitud física o química, como temperatura, presión o luz, y los convierte en señales eléctricas para su procesamiento. Se usa en diversos sistemas para monitoreo y automatización.

>🔑 *Encoder:* Un encoder es un sensor que convierte el movimiento (rotación o desplazamiento) en señales eléctricas para medir posición, velocidad o dirección en motores y sistemas automatizados.
>
>🔑 *Resolver:* Es un sensor electromecánico que mide la posición angular y la velocidad de un eje, utilizando señales eléctricas sin necesidad de componentes electrónicos en el rotor, lo que lo hace resistente y preciso. 

Los servomecanismos utilizan sensores para medir corriente (torque), posición y velocidad, asegurando el cumplimiento de las rutinas de movimiento necesarias para diversas aplicaciones. Sin estas mediciones, no se puede garantizar un control preciso.
Se analizarán algunos tipos de sensores que existen, especialmente los encoder u otros sensores que nos permitan hacer mediciones de pulsos de un motor.

### 2.1. Encoders
Generalmente son usados para medir tanto la posición como la velocidad del eje de cualquier tipo de motor.
* Encoders Absolutos: Tienen un Código digital de posición absoluta para una sola revolución y un contador de revoluciones.
* Encoders Incrementales: Generan un número específico de pulsos por unidad de longitud de movimiento lineal.

Comparandos ambos tipos de encoders, tenemos que:

| **Elemento**              | **Encoder Incremental**                 |  **Encoder Absoluto**                                                     |
|---------------------------|-----------------------------------------|---------------------------------------------------------------------------|
| Salida                    | Salida aumenta incrementalmente         | Hay posiciones absolutas en una revolución                                |
| Reinicialización          | Operación de retorno durante encendido  | No require ninguna operación de retorno ya que se sabe siempre su posición dentro de una revolución   |
| Precio                    | Bajo                                    |Alto                                                                        |
| Estructura                | ![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/7c772e8d44d86a24e2e5148ac6cf6bbda825b5d9/Encoder%20incremental.png)  |  ![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/b67c06e9965e10d66c7d25e072653e2fdb2df51d/Encoder%20Absoluto.png)            |
|Adicionales                |  Solamente se detectan pulsos           | Hay un Código perforado en el encoder. El mas usado es gray                |

Tabla 4. MEncoders

### 2.2. Resolver
Un resolver es un sensor analógico de posición angular con un rotor y un estator embobinados. Su funcionamiento es similar al de un transformador, donde la amplitud inducida en el rotor varía según la posición relativa. Existen modelos con y sin escobillas.
* **Voltajes del resolver**: entre 2V RMS y 40V RMS.  
* **Frecuencia de operación**: 50 Hz a 20 kHz.  
* **Relación de transformación**: 0.2 V/V a 1 V/V.

### 2.3. Medición de Torque
torque se infiere a partir de la corriente, debido a su relación aproximadamente lineal.   
* **Shunt**: Usa una pequeña resistencia para medir voltaje y aplicar la ley de Ohm.  
* **Efecto Hall**: Detecta cambios en el campo magnético y, por la ley de Faraday, permite obtener la corriente.

## 3. DRIVERS DE POTENCIA
Un driver es un amplificador que convierte señales de control de baja potencia en señales de alta potencia (voltaje y/o corriente) para alimentar actuadores como motores, por lo que también se le conoce como amplificador. Cada eje requiere su propio driver y controlador. En los servomotores modernos, el controlador gestiona la retroalimentación de posición y velocidad, mientras que el driver maneja la retroalimentación de corriente.
El manejo del driver se realiza mediante PWM (modulación por ancho de pulso), el estándar industrial para motores DC y AC, debido a su alta eficiencia. Algunos de los ejemplos de drivers de potencia que se pueden encontrar en el mercado, y que son bastante usados son:

* Puente H
* L293 y L298 (AN240/1288)

## 4. Ejercicios
**Validación de Modelo**

En primera medida se realiza un montaje de un motor deseado para la estimación de parámetros faltantes dentro del datasheet del mismo. Se obsera la entrada y salida del mismo mediante el osciloscopio. Todo este proceso se ralizará dentro de un espacio simulado para no desgastar los componentes físico y poder realizar las pruebas necesarias sin un alto gasto económico.

 ![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/d6e6914ec354cdf12eba0cc78fcfb4d78b20ab08/Montaje.jpg)

En segunda medida, se especifican los parámtros que tendrá nuestro motor, identificando con el nombre de una variable los datos restantes a calcular.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/19f1970097cd354a2adfe8c3de00d11f888ff097/parametros.jpg)

Además, se debe tener en cuenta un motor estándar para tomar en cuenta la respuesta de un motor a una entrada escalón. Una vez teniendo las 2 gráficas del sistema, tanto la del motor de referencia y nuetro motor seleccionado, se realiza un contraste de ambas respuestas.
![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/7f7f518c4866c9cb6369a220ca7803f549a9a937/Simulacion.jpg)

Por último, se realiza la estimación de parámetros de nuestro motor y con esto completar la información faltante del funcionamiento del motor seleccionado.

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/aa328692bd5aad8d0854940948ad1e2ec0514aa9/estimaci%C3%B3n.jpg)

En la siguiente imagen podemos observar la respuesta del motoro con la estimación de parámtros faltantes; se observa un seguimiento a la referencia de la entrada con la que se alimenta al motor. 

![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/6272ebc703a4665d498ee1e5b2a2bb38e9ef1e22/datos%20iniciales.jpg)

## 5. Conclusiones
Los motores eléctricos, junto con los sensores y drivers, forman la base de innumerables aplicaciones industriales y tecnológicas. Su correcto funcionamiento depende de una integración efectiva de los diferentes componentes, desde la generación del movimiento hasta su regulación mediante señales de control y retroalimentación.
El uso de tecnologías como PWM en los drivers y la incorporación de sensores de posición y corriente han permitido aumentar la eficiencia y precisión de los sistemas de automatización. Comprender estos conceptos es esencial para diseñar y optimizar motores en diversas aplicaciones, desde robótica hasta maquinaria industrial, garantizando un desempeño confiable y eficiente.

## 6. Referencias
* CHAPMAN. 2005. Maquinas eléctricas. Madrid: McGraw-Hill Interamericana
* LANGSDORF. 1968. Principios de las maquinas de corriente continua. McGrawHill
* SERRANO IRIBARNEGARAY. 1989: Fundamentos de maquinas eléctricas rotativas. Marcombo.
* https://www.swe.siemens.com/spain/web/es/industry/drive_tech/variadores /Pages/Variadores.aspx
