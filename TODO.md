Voy a revisar la estructura real de todos los `.tex`, localizar los `TODO` y leer especialmente `Implementacion.tex`, `Conclusions.tex` y los capítulos que describen requisitos, diseño, pruebas y despliegue. Después te devolveré una propuesta de contenido centrada solo en Implementación y Conclusiones, señalando también qué añadiría fuera de los `TODO` si falta para cerrar el relato técnico.

Searched for regex `TODO|\\chapter|\\section|\\subsection|\\include|\\input` (`**/*.tex`), 195 results

Read 

Search complete: Analizar estructura LaTeX

Read 

Read 

Searched codebase for "TFG sport league paper structure chapters sections TODOs", no results

Searched codebase for "implementation testing deployment sections missing", no results

Searched for files matching `**/*.tex`, 18 matches

Searched for files matching `**/Implementacion*.tex`, 1 match

Searched for files matching `**/Conclusions*.tex`, 1 match

Searched for files matching `**/MemoriaTFG.tex`, 1 match

Searched for regex `TODO|todo|TOD`, 67 results

Searched for regex `Implementacion|Conclusions|pruebas|despliegue`, 15 results

Read 

Read 

Read , lines 220 to 259

Searched for regex `despliegue|despliegue escalable|docker|AWS|GCP|empaquetado|Expo`, 20 results

Searched for regex `pruebas|pruebas automatizadas|pruebas unitarias|pruebas de integración|testcontainers`, 4 results

Searched for text `Implementacion`, 1 result

Searched for text `Conclusions`, 4 results

Searched for files matching `**/*.tex`, 18 matches

Searched codebase for "despliegue escalable robusta estrategia docker compose", 26 results

Searched codebase for "pruebas automatizadas unitarias integración testcontainers", 23 results

Searched for files matching `**/docker-compose.yaml`, no matches

Searched for files matching `**/*.yaml`, no matches

Searched for text `docker-compose`, 1 result

Searched for text `Despliegue`, 6 results

Searched for regex `pruebas automatizadas|pruebas unitarias|pruebas de integración|testcontainers`, 2 results

Read , lines 1 to 260

Ya se ve el patrón principal: `Proceso.tex` concentra análisis y diseño, `Tecnologia.tex` documenta las elecciones técnicas, mientras `Implementacion.tex` apenas empieza a trasladar esas decisiones al código y `Conclusions.tex` todavía no cierra resultados ni límites. Haré una segunda lectura acotada de `Resultado.tex`, el final de análisis/diseño y el resto del estado tecnológico para separar contenido que pertenece a Implementación de contenido que convendría dejar en capítulos 7 y 8.

Read 

Read , lines 1 to 380

Read , lines 470 to 474

Read , lines 80 to 174

Read 

Read 

He revisado la estructura de los archivos `.tex`, los `TODO` y las referencias entre capítulos. La conclusión principal es que el proyecto tiene una base sólida en análisis y diseño, pero falta explicar cómo se transformó ese diseño en un sistema funcional y qué resultados concretos se obtuvieron.

**Observación estructural importante**

Actualmente `MemoriaTFG.tex` incluye:

1. Introducción
2. Gestión del proyecto
3. Análisis y diseño
4. Estado del arte tecnológico
5. Implementación
6. Conclusiones

Sin embargo, según la estructura propuesta por tu tutor faltan capítulos explícitos de:

- Pruebas
- Despliegue
- Resultados

Además, `Resultado.tex` no está incluido en `MemoriaTFG.tex:229-234`, por lo que actualmente su contenido no aparece en el documento final. Este archivo podría convertirse en el capítulo de resultados, o integrarse parcialmente en Implementación, Pruebas y Conclusiones.

## Implementación

El capítulo `Implementacion.tex` debería responder principalmente a esta pregunta:

> ¿Cómo se construyó realmente el sistema diseñado?

La estructura actual es correcta como punto de partida, pero hay varios apartados incompletos y falta describir decisiones concretas de implementación.

### 1. Entorno de desarrollo

Ya explicas los editores utilizados, pero añadiría:

- Versiones concretas de Kotlin, Spring Boot, Node.js, Expo, PostgreSQL, MinIO y Docker.
- Sistema operativo o sistemas utilizados.
- Organización de los repositorios.
- Flujo de trabajo con Git.
- Gestión de variables de entorno.
- Diferencias entre entorno de desarrollo y producción.
- Comandos principales para levantar el sistema.

El apartado `Ejecución y despliegue` debería centrarse en la preparación del entorno local. Si finalmente existe un capítulo independiente de Despliegue, convendría reservar allí la instalación en producción, configuración del servidor, dominios, HTTPS y copias de seguridad.

### 2. Migraciones de base de datos

El apartado de migración está incompleto:

```tex
Para mantener una correcta gestión de migraciones para la base de datos relacional
```

Deberías explicar:

- Por qué se utiliza Flyway.
- Cómo se nombran las migraciones.
- En qué orden se ejecutan.
- Qué ocurre cuando se inicia el sistema por primera vez.
- Cómo se actualiza una base de datos existente.
- Qué datos pertenecen al esquema y cuáles son datos iniciales.
- Cómo se evita modificar manualmente la base de datos.
- Cómo se gestionan errores o migraciones incompatibles.

También convendría aclarar que las migraciones deben ser acumulativas y no modificarse después de haber sido aplicadas en un entorno compartido.

### 3. Servidor back-end

Este debería ser uno de los apartados principales del capítulo. La implementación debería describir:

- Organización real de paquetes y módulos.
- Separación vertical por entidad o funcionalidad.
- Diferencias entre módulos de tres capas y módulos hexagonales.
- Responsabilidad de controladores, servicios, repositorios y adaptadores.
- Gestión de errores y respuestas HTTP.
- Validación de datos recibidos.
- Autenticación mediante JWT.
- Autorización por roles y pertenencia a una liga.
- Gestión de transacciones.
- Uso de DTOs generados desde OpenAPI.
- Generación automática de partidos.
- Gestión de solicitudes entre jugadores, capitanes y administradores.
- Cálculo de clasificaciones.
- Tratamiento de actas, periodos y eventos de partido.
- Gestión de archivos mediante MinIO.

El `TODO` de la estructura de carpetas debería sustituirse por una figura real, pero la imagen debe ir acompañada de una explicación. No basta con mostrar el árbol de directorios: debes justificar qué responsabilidad tiene cada zona.

Podrías organizarlo así:

```tex
\section{Servidor back-end}

\subsection{Estructura modular}
\subsection{Implementación de la seguridad}
\subsection{Implementación de la lógica de ligas}
\subsection{Generación de fases, rondas y partidos}
\subsection{Gestión de resultados y actas}
\subsection{Contrato API y generación de DTOs}
\subsection{Gestión de errores y validaciones}
```

No es necesario explicar todas las clases. Es mejor escoger dos o tres flujos representativos y explicar su recorrido completo, por ejemplo:

- Crear una liga.
- Solicitar la creación de un equipo.
- Cerrar el acta de un partido.
- Consultar la clasificación.

### 4. Vista de clasificación

El `TODO` de la vista de clasificación es importante porque representa una decisión técnica relevante.

Deberías explicar:

- Qué datos utiliza la vista.
- Cómo se calculan partidos jugados, victorias, derrotas, sets y puntos.
- Cómo se agrupan los resultados por liga, fase, grupo o jornada.
- Por qué se utiliza una vista en la base de datos.
- Qué ventajas aporta frente a calcularlo todo en Kotlin.
- Cómo se garantiza que no se muestran resultados de otra liga.
- Si es una vista normal o materializada.

Aquí hay una incoherencia que deberías revisar: en `Implementacion.tex:38-44` se habla de una vista, pero en los requisitos se menciona una “vista materializada”. Debes indicar cuál de las dos se implementó realmente.

### 5. Base de datos

El contenido actual menciona PostgreSQL y las migraciones, pero sería conveniente añadir:

- Cómo se aplican las restricciones de integridad.
- Claves primarias y foráneas.
- Restricciones de unicidad.
- Relaciones muchos a muchos mediante entidades asociativas.
- Borrado lógico y sus disparadores.
- Tratamiento de la multitenencia por liga.
- Motivo de no almacenar imágenes y documentos directamente en PostgreSQL.
- Ejemplo de una operación transaccional compleja.

La explicación de `Participante` y de las actas ya aparece en el capítulo de diseño. En Implementación deberías explicar cómo se trasladaron esas decisiones a tablas, entidades JPA, repositorios y consultas.

### 6. Almacenamiento de objetos

Actualmente está vacío:

```tex
\section{Almacenamiento de objetos}
```

Deberías mencionar:

- Qué tipos de archivos se almacenan.
- Qué estructura de nombres o carpetas se utiliza.
- Cómo se generan las claves de los objetos.
- Cómo se suben y descargan los archivos.
- Cómo se controlan los tipos y tamaños permitidos.
- Cómo se aplican las restricciones de 200 KB.
- Cómo se evita guardar credenciales de MinIO en el código.
- Cómo se diferencia el almacenamiento local del de producción.
- Si los archivos se sirven directamente o mediante URLs temporales.
- Qué ocurre cuando se elimina una entidad que tiene archivos asociados.

### 7. Interfaz multiplataforma

También está prácticamente vacío. Deberías explicar:

- Estructura de navegación.
- Organización de pantallas y componentes.
- Gestión del estado.
- Comunicación con la API.
- Uso de los DTOs generados.
- Gestión de carga, errores y estados vacíos.
- Persistencia de sesión y tokens.
- Formularios y validaciones.
- Gestión de imágenes.
- Flujo de firma de actas.
- Diseño específico para árbitros en tabletas.
- Cómo se cumple el requisito de registrar un evento en pocos clics.
- Qué partes son comunes y cuáles dependen del rol.

Sería interesante elegir una pantalla compleja y explicar su implementación completa, por ejemplo la pantalla de gestión del acta o la negociación de la fecha de un partido.

## Pruebas

No existe actualmente un capítulo específico de pruebas. Según los requisitos de `Proceso.tex:372-380`, debería documentarse:

- Pruebas unitarias de lógica de negocio.
- Pruebas de integración de endpoints.
- Pruebas de repositorios y consultas.
- Pruebas de autorización.
- Pruebas de generación de partidos.
- Pruebas del cálculo de clasificación.
- Pruebas del cierre transaccional de actas.
- Pruebas de subida de imágenes.
- Pruebas manuales de los flujos principales.
- Dispositivos utilizados para probar la aplicación móvil.
- Resultados obtenidos.
- Limitaciones de las pruebas.

Para cada prueba convendría indicar:

- Qué se comprueba.
- Qué datos se utilizan.
- Qué resultado se esperaba.
- Qué resultado se obtuvo.
- Si la prueba se ejecuta automáticamente o manualmente.

Si no has desarrollado suficientes pruebas automatizadas, no deberías afirmar que se cumple completamente `RNF-DES-3` y `RNF-DES-4`. En ese caso, puedes documentar honestamente qué pruebas existen y qué queda pendiente.

## Despliegue

Actualmente el despliegue solo aparece mencionado en el entorno de desarrollo. Deberías documentar aparte:

- Requisitos del servidor.
- Servicios necesarios.
- Configuración de Docker Compose.
- Variables de entorno.
- Creación de volúmenes persistentes.
- Configuración de PostgreSQL.
- Configuración de MinIO.
- Ejecución de las migraciones.
- Construcción de las imágenes.
- Publicación de la API.
- Publicación o distribución de la aplicación móvil.
- Configuración de HTTPS.
- Gestión de secretos.
- Copias de seguridad.
- Actualización a nuevas versiones.
- Recuperación ante errores.
- Limitaciones del despliegue actual.

La posibilidad de autoalojamiento es una de las mejoras importantes del proyecto, por lo que debería demostrarse con una descripción concreta del proceso, no solo mencionarse en Conclusiones.

## Resultados

`Resultado.tex` debería desarrollarse o integrarse en capítulos separados. Sus apartados actuales son adecuados:

- Cambios respecto a los requisitos iniciales.
- Desviaciones respecto a la planificación.
- Funcionalidades añadidas.
- Ejemplos de código relevantes.

Añadiría también:

- Funcionalidades implementadas completamente.
- Funcionalidades implementadas parcialmente.
- Funcionalidades no implementadas.
- Requisitos no funcionales cumplidos.
- Requisitos no funcionales pendientes.
- Estado actual del sistema.
- Capturas o flujos principales.
- Limitaciones conocidas.

El algoritmo de generación de partidos es un buen ejemplo de código, pero no debería ser el único. También podrías explicar brevemente:

- La generación de una clasificación.
- La asignación automática de árbitros.
- La negociación de fechas.
- El cierre transaccional de un acta.
- La autorización basada en el rol dentro de una liga.

## Conclusiones

El capítulo `Conclusions.tex` tiene una base válida, pero necesita relacionar explícitamente el resultado con los objetivos definidos en `Introduccio.tex:118-132`.

### 1. Aprendizaje

Mantendría esta sección, pero la dividiría por áreas:

- Ingeniería de requisitos.
- Diseño de arquitectura.
- Desarrollo de una API REST.
- Kotlin y Spring Boot.
- React Native y Expo.
- PostgreSQL y Flyway.
- MinIO y almacenamiento de objetos.
- Docker y despliegue.
- Seguridad y gestión de roles.
- Pruebas y depuración.
- Organización de un proyecto individual.

También corregiría la frase sobre Instagram y Netflix: las tecnologías pueden servir como ejemplos, pero no es necesario afirmar que sus sistemas concretos están implementados exactamente con esas tecnologías si no se aporta una referencia.

### 2. Mejoras aportadas

La sección debería ser más concreta y comparar cada mejora con Winner y Clupik:

- Gestión centralizada en una única aplicación.
- Múltiples roles dentro de una misma liga.
- Reparto del trabajo entre administradores.
- Gestión de árbitros.
- Firmas digitales de capitanes y árbitros.
- Gestión detallada de actas.
- Personalización de equipos y jugadores.
- Negociación de fechas entre capitanes.
- Configuración de fases y formatos.
- Clasificación calculada automáticamente.
- Posibilidad de ampliar el sistema a otros deportes.
- Autoalojamiento y control de los datos.
- Menor dependencia de planes de pago.
- Contrato API compartido entre front-end y back-end.

No conviene presentar como implementada una funcionalidad que únicamente está diseñada. Cada punto debería clasificarse como:

- Implementado.
- Implementado parcialmente.
- Diseñado, pero pendiente.
- No incluido en el alcance.

### 3. Cumplimiento de objetivos

Añadiría una sección explícita:

```tex
\section{Cumplimiento de objetivos}
```

Para cada objetivo específico deberías indicar:

- Qué trabajo se realizó.
- Qué evidencia existe.
- Si se cumplió completamente.
- Qué limitaciones quedaron.

Por ejemplo:

- Recopilación de necesidades mediante 26 respuestas y reuniones con la OUSIS.
- Diseño basado en los requisitos extraídos.
- Implementación del sistema cliente-servidor multiplataforma.
- Preparación de un entorno reproducible mediante Docker.
- Estado real del despliegue y qué queda pendiente para producción.

Esta sección será probablemente más útil para el tutor que una conclusión genérica.

### 4. Limitaciones

Añadiría:

```tex
\section{Limitaciones}
```

Deberías mencionar:

- Tamaño reducido de la muestra de encuestas.
- Solo dos respuestas de árbitros y dos de administradores.
- Ausencia de actas formales de las reuniones con la OUSIS.
- Posibles funcionalidades todavía no implementadas.
- Falta de validación prolongada en una temporada real.
- Falta de certificación o auditoría ENS.
- Dependencia de una futura integración con la autenticación de la UIB.
- Necesidad de mejorar observabilidad, copias de seguridad y mantenimiento.
- Posible necesidad de adaptar el sistema a otros deportes.

Esto fortalece las conclusiones porque muestra una evaluación crítica del resultado.

### 5. Trabajo futuro

El contenido actual es razonable, pero corregiría varios puntos:

- `Graphana` debe ser `Grafana`.
- `SLF4J` sirve principalmente como fachada de logging; por sí solo no proporciona auditoría ni telemetría completa.
- La certificación ENS no debería presentarse simplemente como “adquirir un certificado”. Habría que hablar de cumplimiento del Esquema Nacional de Seguridad, análisis de riesgos, medidas de seguridad, auditoría y, según corresponda, certificación o declaración de conformidad.
- La autenticación de la UIB mediante OAuth debería explicarse como una integración condicionada a que exista una API o proveedor autorizado.
- La exigencia de credenciales UIB debería quedar como una política configurable por liga, tal como ya indicas.

También añadiría como trabajo futuro:

- Notificaciones push y por correo.
- Panel de estadísticas para administradores.
- Gestión de temporadas.
- Soporte para más deportes.
- Aplicación web administrativa.
- Copias de seguridad automáticas.
- Monitorización con métricas y alertas.
- Pipeline de integración y despliegue continuo.
- Pruebas de carga.
- Control de permisos más granular.
- Internacionalización.
- Accesibilidad avanzada.
- Migración opcional a servicios cloud.

## Recomendación final de contenido

Centrado en los capítulos que tienes más vacíos, la estructura mínima que desarrollaría sería:

```tex
\chapter{Implementación}

\section{Entorno de desarrollo}
\subsection{Herramientas y versiones}
\subsection{Ejecución local}
\subsection{Migraciones}

\section{Servidor back-end}
\subsection{Estructura modular}
\subsection{Seguridad y autorización}
\subsection{Lógica de negocio}
\subsection{Gestión de partidos y actas}
\subsection{Contrato API y DTOs}

\section{Base de datos}
\subsection{Implementación del modelo}
\subsection{Borrado lógico}
\subsection{Vista de clasificación}

\section{Almacenamiento de objetos}

\section{Interfaz multiplataforma}
\subsection{Navegación y pantallas}
\subsection{Comunicación con la API}
\subsection{Flujos por rol}
```

Y para las conclusiones:

```tex
\chapter{Conclusiones}

\section{Cumplimiento de objetivos}
\section{Resultados obtenidos}
\section{Mejoras respecto a las alternativas}
\section{Limitaciones}
\section{Aprendizaje}
\section{Trabajo futuro}
```

La carencia más importante ahora mismo no es añadir más teoría, sino demostrar el vínculo entre requisitos, implementación y resultados. Cada funcionalidad relevante debería poder seguirse desde un requisito de `Proceso.tex`, hasta su implementación en `Implementacion.tex`, y finalmente hasta una prueba o resultado documentado.