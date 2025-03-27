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


### 1.2. Motores Corriente Alterna - Asíncronos
El motor funciona mediante un campo magnético giratorio generado en el devanado inductor del estator. Al atravesar el devanado del rotor, induce fuerzas electromagnéticas que generan corrientes, provocando una reacción que hace girar el motor a una velocidad inferior a la de sincronismo.
  
En cuestiones industriales estos tipos de motores tienen varias aplicaciones, por lo que podemos resaltas las siguientes ventajas y desventajas:

| **Ventajas**                                 | **Desventajas**                                                           |
|----------------------------------------------|---------------------------------------------------------------------------|
| • Poco mantenimiento                         | • Baja eficiencia en aplicaciones pequeñas                                |
| • Excelente resistencia al entorno           |  Control más complicado que el DC por las señales de potencia             |
| • Alta velocidad y alto torque               | • Puede sufrir cambios en sus características debido a temperaturas       |
| • Alta eficiencia en aplicaciones grandes    |                                                                           |
| • Estructura robusta                         |                                                                           |

Tabla 2. Motores AC Asíncronicos

### 1.3. Motores Corriente Alterna - Síncronos
Son máquinas eléctricas cuya velocidad de rotación depende de la frecuencia de la red AC, manteniendo igual velocidad entre el rotor y el campo magnético del estator. Los imanes de campo se montan en el rotor y se excitan con corriente continua, mientras que las bobinas de armadura, divididas en tres partes, se alimentan con corriente trifásica. Estos motores contienen las siguientes caracteristicas fisicas:
* Estator:  Bobinado trifásico para producir el campo magnético giratorio.
* Rotor: Tiene unos imanes o bobinas de excitación recorridas por una corriente continua. Gira a la velocidad del campo magnético.
* Anillos Rozantes: Son anillos metálicos que sirven para alimentar de corriente continua al rotor.

Se debe tener en cuenta que para iniciar el motor síncronico se debe aplica una señal alterna trifásica al estator y una señal DC al rotor, generando un campo magnético con polaridad. El campo del estator atrae al del rotor, provocando su giro a velocidad de sincronismo.
  
En cuestiones industriales estos tipos de motores tienen varias aplicaciones, por lo que podemos resaltas las siguientes ventajas y desventajas:

| **Ventajas**                                     | **Desventajas**                                                           |
|--------------------------------------------------|---------------------------------------------------------------------------|
| • Muy poco mantenimiento                         | • Control de dificultad intermedia                                        |
| • Excelente resistencia al entorno               | • Se requiere respuesta 1:1 entre driver motor                            |
| • Compactos y ligeros                            | • Sus imanes pueden sufrir desmagnetización con el tiempo                 |
| • Alta eficiencia en todo tipo de aplicaciones   |                                                                           |

Tabla 3. Motores AC Síncronicos

### 1.4. Servomotores
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
