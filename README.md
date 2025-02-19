# TC2008B-Revision1-Respaldo

# *Propuesta Formal: Simulación Multiagente de Distribución de Oxígeno en una Colonia Espacial*
### INTEGRANTES
* A01733551 Lou Parra Camargo
* A01425183 Luis Adrian Dias santana Gonzales
* A01734547 Ithandehui Joselyn Espinoza Mazón
* A01660520 Kevin Alfredo Martínez Catalán

#### Liga jira https://towytech.atlassian.net/jira/software/projects/TC2038/boards/4
#### Liga repo https://towytech-admin@bitbucket.org/towytech/tc2005b-actividades.git


## **Conformación del Equipo**

El equipo de trabajo está conformado por los siguientes integrantes:

| Matrícula   | Nombre Completo                                |
|-------------|--------------------------------------------------|
| A01733551  | Lou Parra Camargo                                |
| A01425183  | Luis Adrián Díaz Santana González                |
| A01734547  | Ithandehui Joselyn Espinoza Mazón                |
| A01660520  | Kevin Alfredo Martínez Catalán                   |


### **Fortalezas y Áreas de Oportunidad**

| Integrante | Fortalezas | Áreas de Oportunidad |
|------------|------------|-----------------------|
| **Lou Parra Camargo** | Scrum, habilidades de liderazgo, diseño, manejo de Unity | Profundizar en integración de simulaciones con API REST y WebGL. |
| **Luis Adrián Díaz Santana González** | Pensamiento lógico, resolución de problemas, manejo de Python | Mejorar conocimientos en visualización y Unity. |
| **Ithandehui Joselyn Espinoza Mazón** | Programación orientada a objetos, manejo de estructuras de datos, fundamentos en desarrollo web | Ampliar conocimientos en modelación multiagente y simulación. |
| **Kevin Alfredo Martínez Catalán** | Desarrollo de software, integración de sistemas, fundamentos en desarrollo web  | Reforzar conocimientos sobre Flask y servicios REST. |



### **Expectativas del Bloque**

Como equipo, nuestras expectativas respecto al presente bloque son:

1. **Fortalecer conocimientos prácticos sobre simulación multiagente:** Implementar un modelo funcional que nos permita comprender mejor la interacción entre agentes autónomos en entornos parcialmente observables.
2. **Aplicar habilidades de integración de sistemas:** Lograr la comunicación fluida entre **Python (AgentPy)**, **API REST (Flask)** y **Unity**.
3. **Consolidar la capacidad de trabajar en equipo bajo metodologías ágiles:** Aplicar enfoques como **Scrum** para distribuir tareas y garantizar entregables semanales.
4. **Desarrollar una solución visual y funcionalmente atractiva:** Aprovechar **Unity** y la exportación a **WebGL** para crear una simulación accesible y comprensible para usuarios externos.
5. **Adquirir experiencia en el despliegue de aplicaciones web interactivas:** Publicar exitosamente el sistema en línea y validar su funcionamiento en entorno web.



### **Logros Esperados como Equipo**

- Implementar exitosamente el sistema multiagente de distribución de oxígeno en una colonia espacial.
- Integrar los módulos de simulación, API REST, visualización en Unity y despliegue WebGL.
- Generar un producto final que no solo sea funcional, sino también visualmente atractivo e interactivo.
- Desarrollar un flujo de trabajo eficiente basado en la colaboración interdisciplinaria, aprovechando las fortalezas individuales.
- Presentar un proyecto que demuestre comprensión profunda de los sistemas multiagente y su aplicación en escenarios críticos.

---

### **Compromisos del Equipo**

- **Comunicación constante:** Mantener reuniones periódicas para evaluar avances, detectar obstáculos y ajustar el plan de trabajo.
- **Cumplimiento de entregables:** Asegurarnos de completar las actividades asignadas en los tiempos establecidos.
- **Apoyo mutuo:** Brindar soporte entre los integrantes cuando se presenten dificultades técnicas.
- **Aprendizaje colectivo:** Compartir conocimientos sobre las tecnologías y metodologías empleadas durante el desarrollo del proyecto.
- **Calidad del producto final:** Enfocarnos no solo en cumplir los requisitos mínimos, sino en garantizar que el resultado final sea robusto, funcional y visualmente destacable.







### *Descripción General del Sistema*
Se propone el desarrollo de una simulación multiagente utilizando el lenguaje de programación *Python* con la biblioteca *AgentPy* para la modelación del comportamiento de los agentes y *Unity* para la visualización del entorno. La simulación representará la dinámica de distribución y consumo de oxígeno en una colonia espacial, considerando las restricciones y necesidades de supervivencia de los habitantes (astronautas) en un entorno hostil.

El sistema se centrará en la interacción entre los diferentes agentes involucrados en la distribución de oxígeno desde los centros de producción hacia los habitantes, empleando puntos de acceso como intermediarios. La colonia evolucionará en función del desempeño del sistema: podrá expandirse con la creación de nuevas estructuras habitacionales o colapsar ante fallas en el suministro.



### *Objetivos de la Simulación*
- *Evaluar la eficiencia y adaptabilidad* de un sistema de distribución de oxígeno en condiciones dinámicas.
- *Explorar la relación entre el abastecimiento oportuno* y el crecimiento o colapso de la colonia.
- *Analizar las estrategias de navegación y decisión* de agentes autónomos bajo restricciones críticas de recursos.



# *Entidades y Agentes*
El modelo considera la interacción de las siguientes entidades, definidas como agentes o elementos del entorno:


### 1. _Astronauta (Habitante)_

- **Rol y Función:** Representa a un colono que requiere oxígeno para sobrevivir.
- **Dinámica y Comportamiento:**
    - Ciclo diurno: realiza trayectorias de desplazamiento aleatorio dentro de la colonia.
    - Ciclo nocturno: retorna a su estructura habitacional (domo) a descansar.
    - Si sus niveles de oxígeno son críticos, se dirige al punto de acceso más cercano para recargar.
    - Si no logra abastecerse a tiempo, muere.



### 2. _Repartidor (Vehículo de Transporte)_

- **Rol y Función:** Vehículo autónomo encargado de la distribución de oxígeno desde las plataformas de despegue hacia los puntos de acceso de la colonia.
- **Dinámica y Comportamiento:**
    - Inicia con un suministro completo de oxígeno en la plataforma.
    - Despliega un recorrido por la colonia y rellena los puntos de acceso con niveles bajos.
    - Si agota su suministro o completa la ronda, regresa a la plataforma de recarga.
    - El proceso de recarga en la plataforma toma _N iteraciones_, durante las cuales el vehículo permanece inactivo.
    - Prioriza la atención a puntos de acceso con niveles críticos y puede ajustar su recorrido si recibe señales de emergencia.



### 3. _Punto de Acceso (Nodo de Distribución)_

- **Rol y Función:** Depósito intermedio de oxígeno al que acuden los astronautas para recargar sus suministros.
- **Dinámica y Comportamiento:**
    - Recibe oxígeno del repartidor.
    - Si su nivel de oxígeno baja de un umbral crítico, emite una señal de recarga al repartidor.



### 4. _Domo (Estructura Habitacional)_

- **Rol y Función:** Refugio de astronautas, representa su hogar y punto de descanso.
- **Dinámica y Comportamiento:**
    - Los astronautas inician y finalizan sus recorridos en estos puntos.
    - Si todos los astronautas asignados a un domo mueren, la estructura colapsa (es removida del entorno).



### 5. _Plataforma de Recarga_

- **Rol y Función:** Punto estático donde el repartidor recarga oxígeno antes de reiniciar sus rondas.
- **Dinámica y Comportamiento:**
    - La recarga del repartidor toma _N iteraciones_, durante las cuales el vehículo no está disponible para la distribución.


### *Ciclo de Actividad*
#### *Etapa Diurna*
- Los astronautas se desplazan por la colonia, siguiendo trayectorias simples o aleatorias.
- El repartidor distribuye oxígeno a los puntos de acceso según sus niveles.
- Los puntos de acceso emiten señales al repartidor si sus reservas se agotan.
- Los astronautas acuden a los puntos de acceso cercanos si su oxígeno es insuficiente.

#### *Etapa Nocturna*
- Los astronautas regresan a sus respectivos domos a descansar.
- El repartidor puede continuar operaciones si no está en proceso de recarga.
- Los astronautas que no logran retornar a tiempo o se quedan sin oxígeno, mueren.



### *Eventos de Expansión y Colapso*
- *Expansión:* Cada *M iteraciones sin muertes* se construirá un nuevo domo y se integrarán nuevos astronautas a la colonia.
- *Colapso:* Si todos los astronautas de un domo mueren, la estructura colapsa y es removida del entorno. Este colapso visualmente simboliza el deterioro de la colonia y la pérdida de capacidad habitacional.



### *Heurísticas y Estrategias Decisionales*
#### *Astronautas:*
- Patrón de exploración aleatorio durante el día.
- Monitoreo constante de nivel de oxígeno.
- Búsqueda del punto de acceso más cercano si el oxígeno es bajo.
- Retorno al domo al inicio de la etapa nocturna.

#### *Repartidor:*
- Ronda inicial por los puntos de acceso.
- Evaluación continua de niveles de oxígeno en puntos de acceso.
- Priorización de puntos críticos (niveles bajos o señales de emergencia).
- Retorno a plataforma de recarga cuando se agota el suministro.
- Tiempo de recarga *N iteraciones*, luego reanuda operaciones.

#### *Puntos de Acceso:*
- Monitoreo de sus niveles de oxígeno.
- Emisión de señal de emergencia si el nivel es crítico.

#### *Domo:*
- Punto estático que sirve como referencia espacial.
- Puede colapsar si mueren todos sus habitantes.



### *Aspectos Visuales en Unity*
Para resaltar las dinámicas del sistema, se integrarán los siguientes elementos visuales:
- *Ciclo Día/Noche:* Cambio en iluminación y actividad.
- *Visualización de niveles de oxígeno:* Barras flotantes sobre astronautas y puntos de acceso.
- *Eventos Críticos:* Colapso de estructuras con efectos visuales al morir los astronautas asignados.
- *Expansión:* Aparición progresiva de nuevos domos como resultado del éxito en la gestión.



### *Implicaciones del Tiempo de Recarga del Repartidor*
- Introduce períodos en los que el sistema de distribución es vulnerable.
- Obliga a priorizar puntos de acceso críticos antes de iniciar recargas.
- Posible acumulación de demanda durante el tiempo de recarga, generando picos de estrés en la red de distribución.
- Puede derivar en eventos de colapso si el periodo de recarga coincide con múltiples astronautas en niveles críticos.



### *Resultados Esperados*
La simulación permitirá:
- Observar el comportamiento emergente en la gestión de recursos vitales bajo restricciones espaciales y temporales.
- Analizar el impacto de la indisponibilidad temporal del repartidor sobre la supervivencia de los habitantes.
- Evaluar la sostenibilidad y adaptabilidad del sistema frente al crecimiento progresivo de la colonia.


## *Definición de PEAS*

El análisis PEAS (Performance, Environment, Actuators, Sensors) proporciona un marco conceptual para definir los elementos que intervienen en el comportamiento y desempeño de los agentes dentro del sistema de simulación multiagente. A continuación, se detallan estos elementos para cada uno de los principales agentes modelados en la simulación:



### *Agente: Astronauta (Habitante)*

| Elemento   | Descripción                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------|
| *Performance (Desempeño)* | La eficiencia del agente astronauta se medirá en función de su capacidad de *mantenerse con vida* durante el mayor número de iteraciones posible, lo cual implica gestionar adecuadamente sus niveles de oxígeno y retornar a su domo al final del ciclo diurno. La supervivencia sostenida de la población será un indicador agregado del desempeño colectivo de estos agentes. |
| *Environment (Ambiente)*  | Los astronautas se desplazan en una colonia espacial representada en una cuadrícula discreta. Los objetos relevantes son: *puntos de acceso (para recarga de oxígeno), **otros astronautas* (como parte de la población), *domos* (puntos de descanso nocturno y origen), y el espacio vacío que representa las áreas transitables. La disponibilidad y ubicación de los puntos de acceso determinarán las decisiones de desplazamiento. |
| *Actuators (Actuadores)*  | Los actuadores permitirán al agente realizar las siguientes acciones: *desplazarse* en las cuatro direcciones cardinales dentro de la cuadrícula (norte, sur, este, oeste) y *recargar oxígeno* al situarse sobre un punto de acceso. Además, *regresará a su domo* durante el ciclo nocturno. |
| *Sensors (Sensores)*      | Los astronautas contarán con sensores que les permitirán percibir su *nivel interno de oxígeno, **la posición de los puntos de acceso cercanos, y **su posición relativa al domo* asignado. También podrán detectar si están *ubicados en un punto de acceso* para proceder con la recarga. |



### *Agente: Repartidor (Vehículo de Transporte)*

| Elemento   | Descripción                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------|
| *Performance (Desempeño)* | El desempeño del repartidor se evaluará mediante dos métricas principales: (1) *la continuidad del suministro de oxígeno* a los puntos de acceso, minimizando los períodos en que estos se encuentren vacíos, y (2) *la capacidad de respuesta ante emergencias* (solicitudes de recarga por niveles críticos de oxígeno). La eficiencia en la recarga antes de que se produzcan muertes será clave en su evaluación. |
| *Environment (Ambiente)*  | El vehículo repartidor opera sobre la misma cuadrícula que los astronautas. Los elementos relevantes incluyen: *planta de recarga (punto de reabastecimiento de oxígeno), **puntos de acceso (nodos de distribución), **domos* (referencia espacial) y *espacios transitables*. Las distancias entre la plataforma de recarga y los puntos de acceso son críticas, ya que el tiempo de desplazamiento condiciona la continuidad del servicio. |
| *Actuators (Actuadores)*  | El repartidor podrá ejecutar las siguientes acciones: *desplazarse* en las cuatro direcciones cardinales, *recargar oxígeno en la plataforma* tras estacionarse durante *N iteraciones, y **depositar oxígeno* en los puntos de acceso al posicionarse sobre ellos. |
| *Sensors (Sensores)*      | Este agente contará con sensores para detectar su *nivel actual de oxígeno, **el nivel de oxígeno en los puntos de acceso cercanos, **solicitudes de emergencia* generadas por puntos de acceso con niveles críticos, y *su posición respecto a la plataforma de recarga* y los nodos de distribución. |



### *Agente: Punto de Acceso (Nodo de Distribución)*

| Elemento   | Descripción                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------|
| *Performance (Desempeño)* | El desempeño de los puntos de acceso se valorará en términos de *la disponibilidad de oxígeno* que ofrecen a los astronautas. La frecuencia con la que se quedan vacíos o no logran abastecer a los astronautas en situación crítica será indicativa de su eficiencia como intermediarios en la red de suministro. |
| *Environment (Ambiente)*  | Operan en una posición fija dentro de la cuadrícula. Los elementos relevantes incluyen: *astronautas que se aproximan para recargar* y *el repartidor que los abastece*. Su interacción se limita a estos agentes en su posición espacial. |
| *Actuators (Actuadores)*  | Los puntos de acceso *almacenan y liberan oxígeno* hacia los astronautas que se posicionen sobre ellos. Además, *pueden emitir señales de emergencia* cuando su nivel de oxígeno cae por debajo de un umbral crítico. |
| *Sensors (Sensores)*      | Estos nodos perciben *su propio nivel de oxígeno, **la presencia de astronautas en su casilla, y **la llegada del repartidor* para reabastecimiento. Detectan cuando *su nivel desciende por debajo del umbral crítico*, lo que activa la señal de emergencia. |



### *Agente: Domo (Estructura Habitacional)*

| Elemento   | Descripción                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------|
| *Performance (Desempeño)* | Su desempeño se mide de manera indirecta a través de *la supervivencia de los astronautas que aloja*. El colapso de un domo indica la falla total en el soporte vital de sus ocupantes. |
| *Environment (Ambiente)*  | Es una estructura estática ubicada en la cuadrícula. Su interacción se restringe a los astronautas que inician y finalizan sus trayectorias en él. |
| *Actuators (Actuadores)*  | No posee actuadores, ya que es un elemento pasivo. Su única "acción" es *desaparecer* si todos sus astronautas perecen. |
| *Sensors (Sensores)*      | Monitorea *la cantidad de astronautas vivos* que tiene asignados. Detecta la *muerte de sus ocupantes* y activa su colapso si se extingue su población. |



## *Síntesis General del Marco PEAS*
| Agente         | Performance                                         | Environment                            | Actuators                                | Sensors                                      |
|----------------|-----------------------------------------------------|------------------------------------------|--------------------------------------------|-----------------------------------------------|
| Astronauta     | Supervivencia sostenida                             | Cuadrícula; puntos de acceso; domos     | Desplazarse, recargar, retornar           | Nivel de oxígeno, posición, detección de nodos|
| Repartidor     | Continuidad y rapidez en suministro                 | Cuadrícula; plataforma; puntos de acceso| Desplazarse, recargar, depositar oxígeno  | Nivel de oxígeno, solicitudes, posición      |
| Punto de Acceso| Disponibilidad constante de oxígeno                  | Estático; astronautas y repartidor      | Almacenar oxígeno, emitir señal           | Nivel de oxígeno, presencia de astronautas   |
| Domo           | Permanencia (ausencia de colapso)                   | Estático; astronautas asignados         | Colapsar (remoción del entorno)           | Número de astronautas vivos                  |




# *Plan de Trabajo y Aprendizaje Adquirido*

## *Plan de Trabajo*

### *Distribución General del Proyecto*
El proyecto se dividirá en *cuatro bloques de trabajo, que progresarán de manera **parcialmente paralela*:

1. *Modelado y Simulación Multiagente (Python con AgentPy)*.
2. *Desarrollo de API REST (Flask) para la conexión entre simulación y visualización*.
3. *Visualización de la simulación en Unity*.
4. *Exportación a WebGL y despliegue en línea*.

Cada integrante asumirá *un rol principal, pero se promoverá la **colaboración cruzada* en los momentos clave de integración y validación.



## *Cronograma General (3 Semanas)*

| Semana | Actividades principales | Resultados esperados | Participantes principales |
|--------|---------------------------|----------------------|----------------------------|
| *Semana 1 (18-24 febrero)* | - Implementación del modelo multiagente en Python con AgentPy (agentes, entorno, reglas y eventos). <br> - Diseño de arquitectura API REST (Flask). <br> - Prototipo base del entorno visual en Unity (importación de assets y estructura básica de la colonia). | Simulación multiagente funcional sin visualización. <br> API con primer endpoint de prueba. <br> Escena básica en Unity. | *AgentePy:* Ing. 1 e Ing. 2 <br> *API REST:* Ing. 3 <br> *Unity:* Ing. 4 |
| *Semana 2 (25 febrero - 3 marzo)* | - Finalizar comportamiento de los agentes e integrar eventos dinámicos (colapso y expansión) en AgentPy. <br> - Desarrollo completo de la API REST para intercambio de estados. <br> - Integración de API con Unity (visualización de datos en tiempo real). | Simulación multiagente estable con eventos. <br> API REST funcional para comunicar estados. <br> Integración parcial AgentPy-Unity. | *AgentPy:* Ing. 1 <br> *API:* Ing. 3 <br> *Unity:* Ing. 2 e Ing. 4 |
| *Semana 3 (4-10 marzo)* | - Ajustes y validaciones finales en el comportamiento de agentes. <br> - Finalizar integración API-Unity. <br> - Exportación del proyecto Unity a WebGL. <br> - Publicación y pruebas del sistema en línea. <br> - Preparación de documentación y presentación final. | Simulación multiagente conectada con Unity, desplegada en WebGL y accesible en línea. | *AgentPy:* Ing. 1 <br> *API:* Ing. 3 <br> *Unity y WebGL:* Ing. 2 e Ing. 4 |



## *Actividades Pendientes y Fechas Tentativas*

| Actividad | Responsable(s) | Fecha de inicio | Fecha de término | Esfuerzo estimado (horas) |
|-----------|-----------------|-----------------|------------------|-----------------------------|
| Modelado y codificación de agentes y entorno en AgentPy | Ing. 1 e Ing. 2 | 18 febrero | 24 febrero | 12 - 15 h |
| Implementación de eventos dinámicos (colapso, expansión) | Ing. 1 e Ing. 2 | 22 febrero | 27 febrero | 6 - 8 h |
| Desarrollo de endpoints básicos en Flask | Ing. 3 | 19 febrero | 23 febrero | 8 - 10 h |
| Extensión de la API REST (estado de agentes, acciones) | Ing. 3 | 24 febrero | 29 febrero | 6 - 8 h |
| Configuración inicial de Unity (assets, entorno) | Ing. 4 | 20 febrero | 24 febrero | 6 - 8 h |
| Consumo de API desde Unity | Ing. 2 e Ing. 4 | 26 febrero | 3 marzo | 10 - 12 h |
| Ajustes visuales y animación básica en Unity | Ing. 4 | 3 marzo | 7 marzo | 6 - 8 h |
| Exportación a WebGL | Ing. 2 e Ing. 4 | 8 marzo | 9 marzo | 4 - 6 h |
| Subida a servidor y pruebas en línea | Ing. 3 | 9 marzo | 10 marzo | 4 - 6 h |
| Integración final, validación conjunta | Todo el equipo | 8 marzo | 10 marzo | 8 - 10 h |



## *Distribución de Roles (Primera Revisión - Semana 1)*

| Actividad | Responsable(s) | Fecha | Esfuerzo estimado |
|-----------|-----------------|--------|--------------------|
| Implementar estructura básica del entorno y agentes (AgentPy) | Ing. 1 e Ing. 2 | 18-24 febrero | 12-15 h |
| Crear API REST básica con Flask | Ing. 3 | 19-24 febrero | 8-10 h |
| Crear escena inicial en Unity con assets de la colonia | Ing. 4 | 20-24 febrero | 6-8 h |

*Integración ligera:* Al final de la primera semana, se hará una *prueba simple* de comunicación *AgentPy -> API REST -> Unity* para verificar el flujo general, aunque los módulos no estarán finalizados.



## *Aprendizaje Adquirido  
Hasta el momento, el equipo ha adquirido conocimientos y habilidades en:

- *Modelado multiagente en entornos parcialmente observables:* Familiarización con *AgentPy* y la configuración de entornos discreto-espaciales para modelar dinámicas de distribución de recursos en un sistema autónomo de agentes.
- *Gestión de recursos y eventos adaptativos:* Definición de heurísticas para agentes repartidores y habitantes bajo restricciones críticas como el oxígeno, así como el diseño de mecanismos de emergencia y adaptabilidad en el entorno (colapso y expansión).
- *Comunicación entre sistemas heterogéneos:* Primera aproximación a la creación de *API REST con Flask* para permitir la conexión entre el modelo de simulación y entornos de visualización en *Unity*.
- *Desarrollo de entornos virtuales:* Experimentación con *Unity* y la integración de assets 3D para representar sistemas dinámicos.

En conjunto, este aprendizaje ha permitido al equipo fortalecer sus competencias en la *integración de sistemas complejos* que combinan *simulación multiagente, **interoperabilidad vía API* y *visualización interactiva*.



## *Nota Final sobre Coordinación*

Cada integrante es responsable de liderar su bloque, pero *habrá revisiones conjuntas cada semana (viernes por la tarde)* para sincronizar avances e identificar bloqueos. Estas sesiones también permitirán *redistribuir esfuerzos* si alguno de los bloques experimenta retrasos.

- *Viernes 23 de febrero:* Revisión Semana 1 → Verificar modelo base, API inicial y entorno Unity.
- *Viernes 1 de marzo:* Revisión Semana 2 → Conectar API con Unity y testear comunicación.
- *Viernes 8 de marzo:* Revisión Semana 3 → Validar simulación integrada y despliegue WebGL.



## *Resumen Visual del Plan*

- *Semana 1:* Implementación de componentes por separado (AgentPy, Flask, Unity).
- *Semana 2:* Finalización de lógica de agentes, API completa e integración inicial.
- *Semana 3:* Ajustes finales, integración total y despliegue WebGL.

