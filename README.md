# Diseño y Construcción de una Incubadora Neonatal a Escala

## Objetivos

El objetivo general de este proyecto es reconocer la importancia de las incubadoras neonatales en la salud del recién nacido, comprendiendo de manera práctica los principios físicos y de instrumentación que rigen su funcionamiento.

De este objetivo se desprenden tres propósitos específicos. En primer lugar, identificar las partes principales que componen una incubadora neonatal y entender la función que cumple cada una dentro del sistema. En segundo lugar, desarrollar un sistema funcional a escala que emule el modo de operación de una incubadora, integrando sensores, actuadores y un microcontrolador. En tercer lugar, evaluar de qué manera el control de variables como la temperatura, la humedad relativa y el flujo de aire incide directamente en la supervivencia y el desarrollo adecuado del neonato.

---

## Marco Teórico y Simulaciones

### Incubadora Neonatal: Partes Principales y Funciones

Una incubadora neonatal es un dispositivo médico cuyo propósito central es reproducir, en la medida de lo posible, las condiciones del vientre materno fuera del cuerpo de la madre. Su diseño responde a una necesidad clínica concreta: garantizar la supervivencia y el desarrollo óptimo del recién nacido en condiciones de vulnerabilidad, especialmente en los casos de prematuridad [1, 2]. Para lograrlo, el dispositivo debe controlar de forma continua y precisa un conjunto de variables fisiológicas y ambientales que el neonato, por sí solo, no puede regular.

El parámetro más crítico es la temperatura interior, que debe mantenerse alrededor de los 37 °C [3]. Este control se logra haciendo circular el aire que ingresa desde el exterior a través de un elemento calefactor —generalmente una resistencia eléctrica o un bombillo incandescente— impulsado por un ventilador de baja potencia. En neonatos prematuros, este control cobra una importancia aún mayor, dado que su piel delgada y su sistema nervioso inmaduro limitan gravemente la capacidad de termorregulación autónoma [4]. La exposición a temperaturas fuera del rango seguro puede derivar en hipotermia o hipertermia, ambas con consecuencias clínicas serias. Cabe señalar que en regiones de clima cálido, donde la temperatura ambiente puede superar los 40 °C, la incubadora también debe contar con un sistema de enfriamiento activo, lo que incrementa considerablemente su complejidad y costo [5].

Las partes principales que componen una incubadora neonatal, junto con la función específica de cada una, se presentan en la siguiente tabla:

| Componente | Función |
|---|---|
| Cubierta transparente | Permite la visibilidad del neonato y reduce la pérdida de calor por convección |
| Ventilador | Circula el aire caliente de forma uniforme dentro de la cabina |
| Elemento calefactor | Eleva la temperatura del aire que ingresa al sistema |
| Sensor de temperatura | Monitorea la temperatura interna de forma continua |
| Sensor de humedad | Controla el nivel de humedad relativa dentro de la cabina |
| Sensor de peso (galga extensométrica) | Estima el peso del recién nacido sin necesidad de retirarlo del entorno controlado |
| Pantalla LCD / display | Presenta las variables monitoreadas al personal médico en tiempo real |
| Sistema de control | Regula los actuadores para mantener las variables dentro de los rangos clínicamente seguros |

---

### Simulación: Circuito Control de Temperatura

Para validar el principio de funcionamiento del sistema de calefacción antes de construirlo físicamente, se diseñó y simuló un circuito eléctrico de lazo cerrado capaz de mantener la temperatura interior de la incubadora dentro del rango clínicamente seguro de 36 °C a 37,5 °C [3].

El circuito emplea un termistor como elemento sensor. Cuando la temperatura cae por debajo del límite inferior del rango, el sistema activa el elemento calefactor a través de un relé. Para ofrecer retroalimentación visual al operador sobre el estado térmico del sistema, se incorporó un panel de tres LEDs: uno verde para indicar que la temperatura se encuentra dentro del rango seguro, y dos rojos para señalar, respectivamente, que la temperatura está por debajo o por encima de los límites establecidos.

<img width="762" height="530" alt="image" src="https://github.com/user-attachments/assets/42ffd8ff-d0e0-4a2f-938f-9ee938dcbe34" />

---

### Simulación: Balanza de Peso del Neonato

De forma paralela, se diseñó y simuló el sistema de pesaje, cuya función es estimar la masa del recién nacido sin necesidad de retirarlo del entorno controlado de la incubadora. El sistema emplea una galga extensométrica de 5 kg como elemento transductor. Dado que la señal eléctrica generada por la galga es de muy baja amplitud, se requiere el módulo amplificador HX711 para acondicionar la señal antes de enviarla al microcontrolador ESP32, que se encarga de procesarla y presentar el valor de peso en una pantalla LCD o en displays de siete segmentos.

Este tipo de medición resulta especialmente relevante en el contexto clínico, ya que el seguimiento del peso del neonato es uno de los indicadores más directos de su evolución nutricional y de su estado general de salud.

<img width="960" height="684" alt="Captura de pantalla 2026-04-23 141752" src="https://github.com/user-attachments/assets/797f1dde-18dc-438d-9ad0-8b4fc68def0c" />


---

## Construcción de la Incubadora

### Materiales y Costos

La selección de materiales respondió a un criterio de bajo costo sin sacrificar la funcionalidad mínima necesaria para demostrar el principio de operación del dispositivo. La estructura física se construyó con cartón piedra y palos de balso, mientras que el aislamiento térmico se logró con espuma de poliestireno expandido. Para la instrumentación electrónica se utilizaron componentes comerciales de uso común en prototipado. El costo total del sistema fue de $219.450 COP, lo que equivale aproximadamente a 55 USD. Todos los precios están expresados en pesos colombianos (COP).

| Cantidad | Material | Precio Unitario | Precio Total |
|:---:|---|---:|---:|
| 3 | Cartón piedra | $4.000 | $12.000 |
| 4 | Palos de balso | $2.000 | $8.000 |
| 1 | Láminas de acetato (paquete) | $11.400 | $11.400 |
| 1 | Galga extensométrica 5 kg | $11.000 | $11.000 |
| 1 | Módulo HX711 | $7.000 | $7.000 |
| 1 | Ventilador 5 V | $8.000 | $8.000 |
| 1 | Relé | $10.000 | $10.000 |
| 1 | Bombillo incandescente | $8.000 | $8.000 |
| 1 | ESP32 | $35.000 | $35.000 |
| 1 | Jumpers (paquete) | $3.000 | $3.000 |
| 3 | LEDs | $700 | $2.100 |
| 3 | Resistencias | $50 | $150 |
| 1 | Pantalla OLED | $18.000 | $18.000 |
| 1 | Pantalla LCD | $12.000 | $12.000 |
| 1 | Sensor DHT11 | $8.500 | $8.500 |
| 1 | Espuma de poliestireno (metro) | $9.800 | $9.800 |
| 1 | Pegante de todo uso | $8.000 | $8.000 |
| 1 | Cinta de enmascarar | $5.000 | $5.000 |
| 4 | Tornillos | $2.000 | $8.000 |
| 2 | Imanes (tapa superior ajustable) | $3.000 | $6.000 |
| 1 | Cartulina | $500 | $500 |
| 2 | Fuentes de 5 V (construidas con cargadores USB) | $10.000 | $20.000 |
| 2 | Cables USB C | $4.000 | $8.000 |
| | **TOTAL** | | **$219.450** |

Las fuentes de alimentación de 5 V se obtuvieron reutilizando cargadores de celular, lo que permitió reducir el costo sin comprometer la estabilidad del suministro eléctrico para los módulos de baja potencia.

---

### Proceso de Armado

La estructura principal de la incubadora se formó cortando y ensamblando piezas de cartón piedra y palos de balso, con dimensiones aproximadas de 40 cm × 25 cm × 20 cm conforme a las especificaciones de la guía de laboratorio. Sobre esta base se instaló la cubierta transparente, fabricada con láminas de acetato en la tapa y las paredes laterales visibles, lo que permite observar el interior sin necesidad de abrir el dispositivo. La tapa superior se aseguró con imanes para facilitar su apertura y cierre de forma repetida sin dañar la estructura.

El interior se recubrió con espuma de poliestireno expandido para reducir las pérdidas de calor por conducción y convección hacia el ambiente externo. A continuación se instaló el sistema de calefacción y ventilación, compuesto por un ventilador de 5 V y un bombillo incandescente como elemento calefactor, el bombillo siendo controlado mediante el relé conectado al ESP32. En una etapa posterior se integró el sistema de pesaje, formado por la galga extensométrica de 5 kg, el módulo HX711 y el ESP32, con la pantalla LCD mostrando el valor en tiempo real. Finalmente, se completó el panel de monitoreo con el sensor DHT11 para temperatura, las pantallas OLED y LCD, y el panel de LEDs indicadores del estado térmico del sistema.

![Detección de peso]<img width="1600" height="1204" alt="image" src="https://github.com/user-attachments/assets/408a090d-0dba-4992-9551-20ffe78128f6" />



![Circuito con la oled, que indica temperatura]<img width="1600" height="1204" alt="temperatura" src="https://github.com/user-attachments/assets/dcd9692b-cb06-463c-b24e-de526a5ccbfb" />

![Armazón de la incubadora]<img width="1600" height="1204" alt="foto incubadora" src="https://github.com/user-attachments/assets/90821b76-0c20-44bd-9b96-4873f8773a44" />

---

### Comparación con Soluciones Comerciales

Comparar el prototipo desarrollado con equipos disponibles en el mercado permite dimensionar con precisión las limitaciones del sistema y entender qué factores determinan el costo de una incubadora clínica real. El costo total del prototipo fue de aproximadamente 55 USD, frente a los 10.000 USD o más que puede costar un equipo comercial certificado. Esta diferencia no se explica únicamente por los materiales, sino por el conjunto de características que hacen apto a un dispositivo para uso clínico real: precisión metrológica, control activo de múltiples variables, sistemas de alarma, cumplimiento normativo y materiales biocompatibles de fácil desinfección.

| Proveedor | Modelo (referencia) | Precio estimado (USD) | Características destacadas |
|---|---|:---:|---|
| Este trabajo | Incubadora a escala — ESP32 | ~55 | Prototipo educativo, control básico de temperatura y peso |
| Dräger | Caleo / Isolette | 10.000 – 30.000+ | Control preciso de temperatura, humedad y O₂; alarmas clínicas; certificación médica |
| Instrumentalia S.A.S. | Equipos neonatales importados | Variable según modelo | Distribución nacional de equipos certificados para UCI neonatal |
| LEEX Medical | Incubadoras neonatales | Variable según modelo | Soluciones para entornos hospitalarios en Colombia |

El sistema construido representa un prototipo educativo funcional, no un dispositivo médico. Su valor radica en la comprensión práctica de los principios de diseño y control, no en la replicación de las prestaciones clínicas de un equipo certificado.

---

## Análisis de Resultados

### Resultados Esperados vs. Obtenidos

#### Control de temperatura


El sistema de calefacción no logró alcanzar el rango de temperatura establecido de 36 °C a 37,5 °C. La temperatura máxima registrada en el interior de la cabina fue de aproximadamente 32 °C, lo que representa una diferencia de al menos 4 °C respecto al límite inferior del rango objetivo. Este resultado puede atribuirse a dos causas que operan de manera simultánea: por un lado, el bombillo incandescente utilizado no generó la potencia calorífica suficiente para elevar la temperatura de un volumen de aire del tamaño de la cabina hasta el nivel requerido; por otro lado, el aislamiento térmico provisto por la espuma de poliestireno no fue suficiente para retener el calor generado, de modo que las pérdidas hacia el ambiente externo compensaron parcialmente el calor aportado por el elemento calefactor.

Para superar estas limitaciones en versiones futuras del prototipo, se propone reemplazar el bombillo por un elemento calefactor de mayor potencia, como las resistencias utilizadas en impresoras 3D, y aumentar el espesor del aislante en todas las paredes de la cabina, prestando especial atención a las esquinas y juntas, que son los puntos de mayor fuga térmica.

#### Medición de peso


La galga extensométrica entregó valores aproximados del peso, pero con un error que la hace insuficiente para aplicaciones donde se requiera precisión. Las causas más probables de este comportamiento son una calibración incompleta del sistema y la sensibilidad del módulo HX711 a vibraciones mecánicas externas, así como a la rigidez insuficiente de la plataforma de apoyo de la galga, que puede introducir deformaciones parásitas en la medición. Para mejorar este resultado, se propone realizar una calibración rigurosa con pesas patrón de masa conocida y rediseñar la plataforma de soporte con un material más rígido y una superficie nivelada, condiciones necesarias para que la galga trabaje dentro de su rango lineal de operación.

---

### Preguntas para la Discusión

**Pregunta 1: ¿Qué otras variables, y por qué, además de las aquí mencionadas son críticas en el monitoreo neonatal?**

El monitoreo neonatal no se limita al control de temperatura y humedad. Existen otras variables fisiológicas y ambientales cuya vigilancia continua resulta indispensable para garantizar la seguridad del recién nacido. La concentración de oxígeno en la cabina (FiO₂) es una de las más importantes, dado que los neonatos prematuros con frecuencia requieren oxigenoterapia controlada; sin embargo, niveles excesivos de oxígeno pueden provocar retinopatía del prematuro, una condición que puede llevar a la pérdida de visión [4]. La frecuencia cardíaca y la frecuencia respiratoria son indicadores directos del estado vital del recién nacido y permiten detectar de forma temprana eventos como bradicardia o apnea. La saturación de oxígeno en sangre (SpO₂), medida mediante pulsioximetría, complementa esta vigilancia al reflejar la eficiencia del intercambio gaseoso. Finalmente, variables ambientales como el nivel de ruido y la intensidad de la iluminación también tienen relevancia clínica, pues la exposición sostenida a estímulos sensoriales intensos puede interferir con el desarrollo neurológico y los ciclos de sueño del neonato.

**Pregunta 2: ¿Qué haría falta para convertir el sistema desarrollado en una incubadora neonatal real?**

La transición de un prototipo educativo a un dispositivo médico implica una serie de requisitos que van mucho más allá de los componentes electrónicos. En primer lugar, el dispositivo debería obtener la certificación del INVIMA en Colombia y cumplir con normas internacionales como la IEC 60601-2-19, específica para incubadoras de recién nacidos. En segundo lugar, el sistema necesitaría incorporar un control preciso de humedad relativa —idealmente entre el 50 % y el 70 %— mediante un humidificador activo, así como un sistema de regulación de la concentración de oxígeno para neonatos con necesidades respiratorias. Un sistema de alarmas audibles y visuales sería indispensable para alertar al personal médico ante cualquier condición fuera de rango, incluyendo desconexión de sensores o fallo en el suministro eléctrico. Los materiales de todas las superficies de contacto deberían ser biocompatibles, no porosos y resistentes a los agentes de limpieza y desinfección hospitalaria. Por último, el dispositivo debería someterse a pruebas clínicas controladas que validen su seguridad y eficacia antes de cualquier uso con pacientes [1].

**Pregunta 3: ¿Qué semejanzas hay entre una incubadora neonatal y una servo-cuna?**

Tanto la incubadora neonatal como la servo-cuna —también denominada cuna de calor radiante— comparten el objetivo clínico fundamental de mantener la termorregulación del recién nacido dentro de rangos seguros. En ambos casos se utilizan sensores de temperatura para monitorear el ambiente térmico de forma continua, y los dos dispositivos cuentan con sistemas de calefacción controlados que responden automáticamente a las variaciones de temperatura. Ambos también están diseñados para facilitar el acceso del personal médico al neonato sin interrumpir el control ambiental.

La diferencia principal reside en el mecanismo de transferencia de calor: la incubadora utiliza convección forzada de aire caliente circulante dentro de una cabina cerrada, mientras que la servo-cuna emplea calor radiante emitido desde un panel ubicado por encima del neonato, en un entorno abierto. Esta diferencia tiene implicaciones clínicas relevantes: la servo-cuna facilita la realización de procedimientos médicos sobre el recién nacido, pero al no contar con una cabina cerrada, lo expone en mayor medida a las condiciones del ambiente exterior, lo que puede dificultar el mantenimiento de una temperatura estable.

---

### Conclusiones

La construcción de este prototipo de incubadora neonatal a escala permitió abordar de manera práctica y concreta los principios de diseño, instrumentación y control propios de los dispositivos biomédicos. A lo largo del proceso se evidenció que el control preciso de la temperatura es técnicamente alcanzable con componentes de bajo costo, pero exige una selección cuidadosa del elemento calefactor y un diseño de aislamiento térmico adecuado al volumen de la cabina. En este proyecto, el bombillo incandescente utilizado resultó insuficiente para alcanzar el rango objetivo de 36 °C a 37,5 °C, lo que pone de manifiesto que la potencia del actuador y la calidad del aislante son factores determinantes en el desempeño del sistema.

En cuanto al sistema de pesaje, la galga extensométrica de bajo costo demostró ser viable como aproximación funcional, aunque la exactitud obtenida fue limitada. Para aplicaciones clínicas reales, este subsistema requeriría una celda de carga con mayor resolución, una calibración rigurosa y una plataforma de soporte mecánico más robusta.

Desde una perspectiva más amplia, la diferencia de costo entre el prototipo desarrollado (~$219.450 COP, aproximadamente 55 USD) y una incubadora comercial certificada (desde ~10.000 USD) ilustra de forma clara la brecha que existe entre un prototipo educativo y un dispositivo médico real, en términos de precisión, seguridad, durabilidad y cumplimiento normativo. Sin embargo, iniciativas de este tipo tienen un valor formativo indudable y pueden constituir un punto de partida válido para el desarrollo de soluciones de bajo costo orientadas a contextos de recursos limitados [1, 2].

---

## Referencias


[1] C. G. K. Tran, A. Gibson, D. Wong, D. Tilahun, N. Selock, T. Good, y G. Rao, "Designing a low-cost multifunctional infant incubator," *J. Lab. Autom.*, vol. 19, no. 3, pp. 332–337, Jun. 2014. https://doi.org/10.1177/2211068214530391

[2] L. Restrepo-Pérez, N. Durango-Londoño, N. E. Gómez-Suárez, F. González-Ramírez, y N. Rivera-Bonilla, "Prototipo de incubadora neonatal," *Revista Ingeniería Biomédica*, vol. 1, no. 1, pp. 55–59, 2007. Disponible en: http://www.scielo.org.co/pdf/rinbi/v1n1/v1n1a12.pdf

[3] M. van Leeuwen *et al.*, *European Standards of Care for Newborn Health: Temperature management in newborn infants*. European Foundation for the Care of Newborn Infants (EFCNI), Nov. 2018. Disponible en: https://newborn-health-standards.org/standards/standards-english/care-procedures/temperature-management-in-newborn-infants/

[4] R. B. Knobel-Dail, "Role of effective thermoregulation in premature neonates," *Research and Reports in Neonatology*, vol. 4, pp. 147–156, 2014. https://doi.org/10.2147/RRN.S52377

[5] R. E. Black, S. Cousens, H. L. Johnson *et al.*, "Global, regional, and national causes of child mortality in 2008: a systematic analysis," *Lancet*, vol. 375, pp. 1969–1987, Jun. 2010. https://doi.org/10.1016/S0140-6736(10)60549-1
