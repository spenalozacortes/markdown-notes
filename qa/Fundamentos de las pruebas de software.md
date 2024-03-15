# Módulo 1

## Fundamentos y principios de la prueba

### Fundamentos

- La prueba exhaustiva no es posible en sistemas complejos
- Decidir cuándo es suficiente
- Prueba y depuración
- Prueba estática y dinámica
- Proceso de prueba

### Siete principios de la prueba

- La prueba muestra la presencia de defectos, no su ausencia
- La prueba exhaustiva es imposible
- Beneficio de la prueba temprana
- Agrupación de defectos
- Paradoja del pesticida
- La prueba depende del contexto
- La falacia de la ausencia de errores

## Independencia de la prueba
La prueba puede ser más efectiva si no es llevada a cabo por parte de individuos que escriben un código, debido a que el creador de cualquier cosa (ya sean trabajos de software o bien artísticos) mantiene una relación especial con el objeto creado.

El siguiente listado muestra diferentes personas o grupos de personas ordenados de menor a mayor independencia de la autoría del código:

- Aquellas que escriben el código.
- Miembros del mismo equipo de desarrollo.
- Miembros de un grupo diferente (al equipo de desarrollo).
- Miembros de una empresa diferente (por ejemplo, un consultor de pruebas/externalizado).

Por este motivo, a mayor lejanía con la autoría del código, mayor grado de independencia.

## Código ético
Los probadores de software deben adherirse a un código ético o deontológico y se les requiere que actúen de forma profesional. El código ético se aplica a las siguientes áreas:

- **Pública**: los probadores de software certificados deben considerar unos intereses públicos generales en sus acciones.
- **Cliente y empleador**: los probadores de software certificados deben actuar velando por los intereses de sus clientes (y en consonancia con el interés público general).
- **Producto**: los probadores de software certificados deben asegurase de que los lanzamientos que proveen (de cualquier producto o sistema en el cual trabajan) forman parte de unos estándares de la más alta calidad posible.
- **Juicio o criterio**: los probadores de software certificados deben mantener su integridad e independencia en su juicio profesional.
- **Gestión**: los jefes y líderes de pruebas de software certificados deben suscribir y promover una aproximación ética a la gestión del testo de software.
- **Profesión**: los probadores de software certificados deben mostrar una integridad y reputación de la profesión en consonancia con el interés público general.
- **Colegas**: los probadores de software certificados deben ser fieles y brindar apoyo a sus colegas de sector, promoviendo la cooperación con los desarrolladores de software.
- **Uno mismo**: los probadores de software certificados deben participar en un aprendizaje y reciclaje continuo propio de su profesión, y deben promover una aproximación ética a la práctica profesional.

## Psicología de la prueba
Durante cada proceso de la prueba los miembros del equipo deben comunicarse por diferentes tipos de motivos como, por ejemplo, acordar qué pruebas realizar a un objeto de pruebas o reportar incidencias encontradas durante una ejecución de prueba.

La comunicación debe ser **objetiva y expresada de formas impersonales**:

- El objetivo es trabajar juntos y no enfrentados. Hay que mantener el foco en el desarrollo de la calidad del producto.  
- Los resultados deberían ser mostrados de una forma impersonal.
- Hay que procurar comprender cómo se sienten los demás y dialogar sobre los problemas de forma positiva.
- Al final de los debates, es recomendable confirmar que ambas partes de un diálogo se han entendido entre ellos, han comprendido lo mismo y se han hecho entender.

# Módulo 2

## Las pruebas como un proceso

1. Planificación y control
2. Análisis y diseño
3. Implementación y ejecución
4. Evaluación criterios salida e informes
5. Actividades de cierre de pruebas

### Planificación y control

**Plan de pruebas**
- Objetivos y criterios de salida
- Alcance
- Recursos necesarios
- Actividades
- Plazos establecidos de tiempo para las pruebas
- Riesgos y estrategias a seguir

**Monitorización y control**

### Análisis y diseño

- Análisis de requisitos presentes en el software
- Creación de casos de prueba
- Los casos deben cubrir diferentes escenarios y condiciones de prueba
- Qué probar y tipos de prueba, en función del software y del contexto

### Implementación y ejecución

- Ejecución de las pruebas
- Registro de resultados y documentación de defectos encontrados
- Informes de progresos y resultados
- Entornos operativos y correctamente configurados
- Priorización y orden lógico de los casos de prueba

#### Prueba de confirmación

- Repetición de los test que fallaron en la versión anterior a la modificación
- Confirmar la corrección de los defectos detectados
- Prueba áreas del software que han sido modificadas durante la corrección

#### Prueba de regresión

- Comprueba áreas no modificadas del software
- Es frecuente que modificaciones en determinadas áreas de software tengan repercusión en otras zonas
- Ayudan a verificar que no se han introducido nuevos defectos después de una modificación del software

### Evaluación de criterios de salida e informes

- Cumplimiento de criterios de salida
- Revisión de informes de pruebas
- Se determina si el software cumple los criterios de calidad para su entrega

### Actividades de cierre de pruebas

- Cerrar y guardar los entornos de prueba e infraestructura utilizada
- Revisar que la documentación está en orden
- Todos estos elementos conforman el "testware" que será entregado al equipo de mantenimiento
- Proceso de mejora continua, con aspectos de mejora que aplicaremos en próximos proyectos

## Ciclo de vida del software y niveles de prueba

### Ciclo de vida de software

- Describe actividades de cada etapa del desarrollo
- Las actividades se relacionan entre sí de manera lógica y cronológica
- Los modelos establecen pasos en tareas que permiten asignar, completar y medir

#### Modelos secuenciales

##### Modelo en cascada

- Especificación requerimientos
- Análisis funcional
- Diseño
- Codificación
- Pruebas

##### Modelo en V

- Especificación requerimiento -> Nivel aceptación
- Especificación funcional -> Nivel sistema
- Especificación técnica -> Nivel integración
- Especificación de programa -> Nivel componente
- Codificación

#### Modelos iterativos e incrementales

Scrum
Kanban

### Niveles de prueba

- Componente, unidad o programa
- Integración
- Sistema
- Aceptación
#### Nivel de pruebas de integración

- **Stub**: Simula al componente que es llamado en el flujo descendente de ejecución
- **Driver**: Simula al componente que llama en el flujo ascendente de ejecución

#### Nivel de pruebas de sistema

- Pruebas funcionales
- Pruebas no funcionales

#### Nivel de pruebas de aceptación

- Pruebas de aceptación de usuario (UAT)
	- Crear confianza en el uso del sistema
	- Cumplimiento de los requisitos definidos
- Pruebas de aceptación operacionales
	- Pruebas de copia de seguridad y restauración
	- Pruebas de instalación, actualización y desinstalación
	- Pruebas de recuperación ante desastres y fallos
	- Pruebas de gestión de usuarios en el sistema
	- Pruebas de mantenimiento
	- Pruebas de carga y migración de datos
	- Pruebas de seguridad y procedimientos
	- Pruebas de rendimiento
- Pruebas de aceptación contractuales y de normativa
- Pruebas Alfa y Beta

# Módulo 3

## Pruebas estáticas

- No requieren la ejecución del software sometido a pruebas
- Evaluación de productos de trabajo
	- Documentos de especificaciones
	- Planes de prueba
	- Documentos técnicos o funcionales
	- Guías de usuario
	- Código
	- Contratos
	- Presupuestos

### Revisiones

- Revisión informal
- Revisión guiada o walkthrough
- Revisión técnica
- Inspección

- Ad hoc
- Listas de comprobación
- Escenarios y ensayos
- Basada en roles
- Basada en perspectiva

### Análisis estático

- Código inalcanzable o código muerto
- Variables no utilizadas en el código
- Interfaces inconsistentes entre módulos
- Defectos de seguridad
- Errores de sintaxis
- Complejidad del código

# Módulo 4

## Pruebas dinámicas de caja negra

- Partición de equivalencia
- Análisis de valores límite
- Prueba de tabla de decisión
- Prueba de transición de estado
- Prueba de caso de uso

### Particiones de equivalencia

- Valores de entrada o de salida
- Se pueden agrupar debido a su comportamiento equivalente entre sí
- Podemos tener particiones válidas y no válidas

### Análisis de valores frontera o límite

- Extensión de la técnica de partición de equivalencia
- Aplicable si tenemos datos numéricos o secuenciales
- El valor mínimo y máximo de la partición serán los valores frontera

### Prueba de tabla de decisión

- Sistemas basados en reglas de negocio
- Las filas corresponden a condiciones y acciones o resultados
- Cada columna corresponderá a una regla de decisión

![[Pasted image 20240311153434.png]]

### Prueba de transición de estado

- Diferentes entradas producirán salidas esperadas para diferentes estados
- Para sistemas basados en estados y transiciones entre ellos
- Trabajaremos con diagramas de transición de estados o tablas de estados

![[Pasted image 20240311153843.png]]

### Prueba de caso de uso

- Permiten diseñar y probar los usos típicos de un sistema
- Se asocian a actores (usuarios humanos, hardware o sistemas)
- Representa funciones o requisitos
- Son muy utilizados en las pruebas de aceptación
- Definen interacción entre usuarios (actores) con el sistema y sus resultados esperados

![[Pasted image 20240311154226.png]]

![[Pasted image 20240311154320.png]]

## Pruebas dinámicas de caja blanca

- Prueba de sentencia
- Prueba de decisión

### Prueba de sentencia y de decisión

- Cobertura de sentencia
- Cobertura de decisión

100% cobertura de decisión incluye 100% cobertura de sentencia

# Módulo 5

## El riesgo y las pruebas

Riesgo = Probabilidad x Impacto

- Riesgos de producto
	- Funcionamiento
	- Seguridad
	- Rendimiento
	- Usabilidad
- Riesgos de proyecto
	- Recursos insuficientes
		- Tiempo
		- Personal
		- Herramientas
		- Presupuesto
	- Planificación / Estimación

- Mitigación
- Contingencia

## Incidencias y reporte de defectos

- Incidencia: Ocurrencia de un suceso que requiere investigación.
- Defecto: Imperfección o deficiencia en un producto de trabajo donde no se cumplen sus requisitos o especificaciones.

**Informe de defecto**

- Identificador
- Título
- Fecha
- Autor
- ID elemento
- Fase
- Detalle
- Resultados esperados
- Resultados reales
- Impacto
- Prioridad
- Estado
- Conclusiones
- Comentarios
- Historial de cambios
- Referencias

## Reporte de defectos e incidencias

### Por qué reportar defectos
El equipo de desarrollo tendrá la necesidad de solucionar los problemas que se encuentren en la aplicación, la página web o el objeto en pruebas.

Para que los desarrolladores acudan de forma directa al problema concreto que se ha de solucionar, el probador debe identificar y reportar correctamente el problema detectado.

Un buen reporte de la incidencia puede ayudar al desarrollador a encontrar más rápidamente la incidencia y le dará los datos necesarios para conocerla y resolverla.

### Qué se debe reportar
En algunas empresas se trabaja con herramientas para reportar y hacer un seguimiento de las incidencias (ticketing). No obstante, no en todas las empresas se utilizan este tipo de aplicaciones, entre otras razones porque las que ofrecen mayores ventajas no suelen ser gratuitas o porque aprender a utilizar una nueva herramienta y adaptarse para usarla únicamente durante una temporada toma un tiempo del que no disponen todos los equipos de trabajo, por ejemplo.

Si no existe una norma contractual que lo contradiga, se deberían registrar todas las incidencias sucedidas durante las ejecuciones de las pruebas y que estén directamente relacionadas con el objeto de pruebas, no reportando las incidencias que únicamente tengan que ver con el entorno sin la interacción del objeto de pruebas.

### Cómo se debe reportar
No siempre se deben seguir estas instrucciones.

Cada cliente u organización tendrá su modo de reportar y utilizará sus herramientas, tanto alguna aplicación de ticketing como otro tipo de sistema de seguimiento de incidencias.

### Elementos que componen un reporte
Los campos que contemplan las aplicaciones de ticketing suelen ser los mismos que los que aquí veremos. Cada cliente añadirá más campos personalizados o eliminará campos en la medida en la que lo necesiten.

#### Documento de pruebas
Contiene una descripción por campos de todas las pruebas a realizar. Este documento tendrá una versión o fecha que identificará cuándo fue creado o a qué configuración o versión del elemento a probar ha de ser aplicada.

También puede contener una tabla de contenidos para acceder de forma rápida al contenido deseado desde este índice.

Puede estar compuesto por tablas que contienen los siguientes elementos:

**Identificador de prueba**: Es un elemento que diferencia a una prueba del resto.

**Categoría**: Categoría (tipo de prueba) a la que pertenece la prueba.

**Título/ Objetivo**: Breve descripción de la prueba.

**Descripción**: Descripción más amplia de la prueba.

**Requisitos**: Pasos previos, pruebas previas… que se deben haber realizado anteriormente. Elementos a tener en cuenta que sean necesarios para poder llevar a cabo la prueba. Por ejemplo, sistemas operativos concretos instalados, navegadores, configuraciones…

**Pasos a seguir**: Descripción paso a paso para realizar la prueba.

**Resultados esperados**: es la forma en la que se espera que el objeto de pruebas responda al realizar los pasos anteriores.

**Comentarios**: posibles notas a tener en cuenta a la hora de ejecutar la prueba.

#### Archivo de seguimiento de pruebas
Permite controlar las pruebas que se han realizado y las que todavía no, y diferenciar las pruebas fallidas y no fallidas dentro de las pruebas que se han realizado.

Puede estar compuesto por tablas que contienen los siguientes elementos:

**Identificador de prueba**: se trata del mismo identificador del documento de pruebas.

**Fecha**: fecha en la que se realiza la prueba.

**Estado**: estado de la prueba; si se ha realizado sin incidencias (OK, Pasado, etc), si se ha realizado, pero se han encontrado incidencias (KO, Fallido, etc.)…

**Resultado**: (campo opcional) descripción del resultado de la prueba, sobre todo si se trata de un resultado no esperado. Si el resultado de la prueba es correcto, este campo se suele omitir o pasar al estado “OK”. Es opcional porque la información que pueda contener este campo suele ser transmitida en el reporte del error.

**Incidencias**: enumeración de todos los identificadores de errores e incidencias reportados en el reporte de incidencias y relacionados con esta prueba.

#### Archivo de registro de incidencias o reporte de errores
Colección de reportes de errores e incidencias encontrados durante la ejecución de las pruebas. Este documento será de utilidad a las personas que deban realizar las modificaciones para corregir defectos.

**Identificador de incidencia**: elemento que diferencia una incidencia del resto de incidencias.

**Fecha**: fecha en la que se detectó el error.

**Descripción**: descripción detallada del error. Es aconsejable adjuntar capturas de pantalla siempre que sea posible.

**Gravedad/Importancia**: cada equipo de trabajo puede tener una escala diferente para referenciar la gravedad. Puede ser numérica (1, 2, 3… donde el 1 es el grado de mayor gravedad, o viceversa), con colores (por ejemplo, donde el rojo es el nivel más grave, en naranja algo menos, el amarillo algo menos, el verde no es de importancia…), con letras (A más grave, B menos grave…), etc.

**Pasos para reproducirlo**: Un paso a paso detallado para poder reproducir el error.

**Estado**: Este campo se observa, sobre todo, en las aplicaciones de gestión de incidencias. Indica el estado en el que se encuentra el error: si todavía está abierto y pendiente de resolución, si está asignado a algún miembro del equipo para resolverlo, si está resuelto…

**Categoría**: Categoría de la incidencia o área del personal que debe atenderla. Este campo se encuentra, sobre todo, en las aplicaciones de ticketing.

**Propietario**: Este campo se observa cuando se trabaja en equipo en el mismo archivo de reporte de incidencias, para conocer quién abrió la incidencia o a quién ha sido asignada.

#### Informe de pruebas
Documento de texto donde se expone levemente el proceso de pruebas llevado a cabo y los resultados obtenidos.

Este documento puede tener una sección inicial de presentación en la que se explique de forma breve qué tipo de pruebas se han llevado a cabo y cómo ha sido el proceso de pruebas. Además, en otra sección se hablará de qué grupos de errores se han encontrado, incidencias a tener en cuenta y se listarán también de forma breve los errores detectados concretamente.

En ocasiones, este documento también puede contener sugerencias de modificación o mejora.

