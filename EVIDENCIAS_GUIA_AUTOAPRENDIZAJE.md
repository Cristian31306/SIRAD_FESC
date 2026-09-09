# GUÍA DE AUTOAPRENDIZAJE · DISEÑO Y PRIMERA CONSTRUCCIÓN WEB
## UNIDAD 2: DESARROLLO BÁSICO DE APLICACIONES EN RED
**Fecha de Entrega:** 01 de septiembre de 2026  
**Estudiante / Desarrollador:** Cristian Alexander Durán Medina  
**Proyecto Individual:** SIRAD (Sistema de Control y Trazabilidad Interna de Radicados)  
**Entidad de Implementación:** Secretaría de Programas y Proyectos Estratégicos y Especiales — Gobernación de Norte de Santander  
**Tecnología Base:** HTML5 Semántico y PHP Básico Nativo (Entorno Escolar sin Frameworks)

---

## 1. PRESENTACIÓN DEL PROYECTO Y CONTEXTO DE TRABAJO

El proyecto individual que vengo desarrollando se denomina **SIRAD** (*Sistema de Control y Trazabilidad Interna de Radicados*). Este sistema nace de una necesidad operativa real dentro de la **Secretaría de Programas y Proyectos Estratégicos y Especiales de la Gobernación de Norte de Santander**, donde diariamente se reciben solicitudes ciudadanas, conceptos técnicos de proyectos de infraestructura, convenios interadministrativos y traslados presupuestales.

Para el desarrollo de esta actividad escolar de la Unidad 2, he diseñado e implementado la **primera página web del proyecto**, aplicando una arquitectura limpia, estructurada en HTML5 y respaldada con lógica básica en PHP nativo. De acuerdo con las orientaciones académicas, se prescindió del uso de frameworks pesados como Laravel y de librerías complejas de correo, enfocando el esfuerzo en la correcta maquetación, semántica, selección crítica de metadatos y en la conexión con el modelo cliente-servidor.

---

## 2. PASO 1 · RECUPERA TU PROYECTO

### ¿Quién es el usuario principal?
El usuario principal de esta primera interfaz es el **operador de radicación de ventanilla única** y los **profesionales especializados de la Secretaría** (ingenieros, arquitectos, abogados y economistas). Estos funcionarios necesitan revisar diariamente qué trámites tienen bajo su custodia, cuál es su fecha de ingreso y cuánto tiempo legal les queda para emitir respuesta.

### ¿Qué necesidad debe atender la página?
La página debe atender la necesidad de **consultar de manera inmediata la trazabilidad de un documento y supervisar los términos de ley** (amparados bajo la Ley 1755 de 2015 sobre derecho de petición). La página debe permitir al funcionario saber en cuestión de segundos quién tiene el radicado, en qué estado se encuentra y alertarlo si el plazo legal está próximo a expirar.

### ¿Qué debe encontrar primero ese usuario?
El usuario debe encontrar de primera vista dos elementos clave:
1. **El Semáforo de Control de Términos:** Tarjetas de estado que muestran de inmediato cuántos trámites están al día, cuántos están en alerta amarilla y cuántos tienen término vencido.
2. **El Buscador Rápido de Radicados:** Un formulario directo donde puede escribir el código de radicado (por ejemplo `RAD-2026-0089`) o el nombre del remitente sin tener que navegar por menús complejos.

### ¿Qué información es indispensable y cuál puede quedar en segundo plano?
* **Información Indispensable:** Código del radicado, nombre del remitente, asunto resumido, profesional responsable asignado, días hábiles restantes de plazo y el indicador visual de estado (semáforo verde, amarillo o rojo).
* **Información en Segundo Plano:** El historial exhaustivo de traslados previos, la tipología archivística detallada, la normativa jurídica completa y los datos de contacto institucionales de la Gobernación, los cuales se ubican ordenadamente en el pie de página (*footer*).

### ¿Cómo se relaciona esta página con el cliente web que identificaste?
Esta página se ejecuta en el **navegador web del usuario** (el cliente web, como Google Chrome, Mozilla Firefox o Microsoft Edge). El cliente web es el responsable de interpretar las etiquetas HTML5, aplicar los estilos CSS para brindar una jerarquía visual clara y gestionar la interacción del usuario. Cuando el usuario escribe un código en el buscador y presiona el botón, el cliente web captura ese evento, genera una solicitud HTTP utilizando el método `GET` hacia el servidor web y finalmente renderiza la respuesta devuelta por el motor PHP.

---

## 3. PASO 2 · DISEÑA LA MAQUETACIÓN ANTES DEL CÓDIGO

Antes de escribir código HTML o PHP, elaboré el boceto de distribución de contenidos teniendo en cuenta la ergonomía visual del funcionario público. Se diseñó un wireframe estructurado en 6 zonas clave, el cual se encuentra disponible en formato vectorial en el archivo `Desarrollo/boceto_wireframe.svg`.

### Descripción de las 6 zonas mínimas del boceto:

1. **[1] Encabezado / Identificación del Proyecto (`<header>`):**  
   Ubicado en la parte superior. Contiene el logotipo representativo de SIRAD, el título principal del aplicativo, la identificación institucional de la Secretaría de Programas y Proyectos Estratégicos (Gobernación de Norte de Santander) y la tarjeta de sesión del operador activo.
2. **[2] Elementos de Navegación (`<nav>`):**  
   Barra de navegación horizontal con enlaces semánticos a las secciones fundamentales: *Inicio*, *Consultar Radicado*, *Semáforo de Términos*, *Guía Multimedia* e *Información Entidad*.
3. **[3] Zona Principal de Contenido (`<main>` / `<section id="consulta">`):**  
   Espacio protagonista que alberga el formulario de búsqueda de radicados y la tabla de resultados con los datos de correspondencia, profesional responsable y estado actual.
4. **[4] Espacio para Información Relevante (`<section id="semaforo">`):**  
   Tablero de métricas operativas estilo semáforo (*KPI Cards*) que categoriza los radicados en: *Total en Gestión*, *Al Día (> 5 días)*, *En Alerta (1-4 días)* y *Vencidos (< 0 días)*.
5. **[5] Lugar Previsto para Recurso Multimedia (`<section id="capacitacion">`):**  
   Módulo de capacitación con un reproductor de video nativo en HTML5 (`<video controls>`) y un listado de pasos guía que explica a los nuevos funcionarios cómo se realiza la radicación y el seguimiento sin duplicidad de documentos.
6. **[6] Pie de Página / Información Complementaria (`<footer>`):**  
   Zona final que incluye la dirección física oficial de la Cúpula Chata en Cúcuta, horarios de atención de la ventanilla única, marco normativo (Ley 1755 de 2015) y los créditos de desarrollo del estudiante.

---

## 4. PASO 3 · HTML5 Y XHTML: COMPARA PARA TOMAR DECISIONES

Para fundamentar técnicamente la construcción de la página, investigué las diferencias estructurales, sintácticas y de procesamiento entre HTML5 y XHTML:

### Cuadro Comparativo Técnico: HTML5 vs XHTML

| Aspecto a Comparar | HTML5 | XHTML (1.0 / 1.1) |
| :--- | :--- | :--- |
| **Definición y Origen** | Estándar moderno desarrollado por WHATWG y W3C. Es una evolución flexible de HTML pensada para aplicaciones web interactivas. | Reformulación de HTML 4 bajo las reglas estrictas de XML 1.0 creado por el W3C a principios de los años 2000. |
| **Declaración DOCTYPE** | Extremadamente simple y fácil de recordar: `<!DOCTYPE html>`. No requiere referencia a ningún DTD externo. | Largo y complejo; exige referenciar un DTD externo formal (Strict, Transitional o Frameset), por ejemplo: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">`. |
| **Sensibilidad a Mayúsculas (Case Sensitivity)** | Insensible a mayúsculas. Se pueden escribir etiquetas en mayúsculas o minúsculas (aunque la buena práctica recomienda minúsculas). | Sensible a mayúsculas y minúsculas (*case-sensitive*). Todas las etiquetas y atributos deben escribirse obligatoriamente en minúsculas. |
| **Cierre de Etiquetas Vacías (*Void Elements*)** | Elementos como `<meta>`, `<input>`, `<br>`, `<img>` no requieren cierre ni barra diagonal final: `<meta charset="UTF-8">`. | Todo elemento debe cerrarse obligatoriamente. Los elementos vacíos exigen autoclusuras con espacio y barra: `<meta charset="UTF-8" />`, `<br />`. |
| **Manejo de Errores por el Navegador (*Parsing*)** | Parser tolerante y estandarizado. Si hay un error menor de sintaxis, el navegador lo corrige de manera predecible sin detener la página. | Procesamiento dracónico de XML. Si existe un solo error de sintaxis o etiqueta sin cerrar, el navegador bloquea la página y muestra un error XML fatal. |
| **Soporte Multimedia** | Soporte multimedia nativo con etiquetas semánticas dedicadas: `<video>`, `<audio>` y `<canvas>`, sin requerir plugins de terceros. | No cuenta con etiquetas multimedia nativas. Dependía de plugins externos (como Adobe Flash Player) o de etiquetas genéricas `<object>`. |
| **Semántica Estructural** | Introduce etiquetas semánticas nativas de alto nivel: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`. | Carece de estas etiquetas estructurales. Toda la maquetación se realizaba utilizando divisiones genéricas `<div>` y `<span>` con IDs y clases. |
| **MIME Type en Servidor** | Habitualmente servido como `text/html`. | Debía servirse como `application/xhtml+xml` para que el navegador aplicara las reglas XML reales (lo cual causaba incompatibilidades). |

### ¿Qué diferencias de sintaxis o estructura consideras más importantes?
Desde mi perspectiva como estudiante, las diferencias más importantes son:
1. **La tolerancia y robustez del parser:** Mientras que en XHTML un despiste tan simple como olvidar cerrar una etiqueta `<input />` o escribir un atributo en mayúscula provocaba que el navegador detuviera el renderizado y mostrara una pantalla de error XML (lo que inutilizaría el sistema para un funcionario), HTML5 define un algoritmo de recuperación de errores claro que asegura la operatividad de la página.
2. **La riqueza semántica y multimedia nativa:** HTML5 eliminó la necesidad de anidar múltiples etiquetas `<div>` con nombres arbitrarios para crear la cabecera, la navegación y el pie de página, proporcionando etiquetas con significado propio (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`) y permitiendo insertar video institucional mediante `<video>` sin depender de software obsoleto o plugins externos.

### ¿Cuál enfoque resulta más conveniente para tu ejercicio y por qué?
Para el proyecto SIRAD, **el enfoque de HTML5 resulta indiscutiblemente más conveniente**. 
* **Justificación:** Nuestro sistema requiere una interfaz institucional ágil, limpia y adaptable a pantallas de diferentes resoluciones. HTML5 nos permite escribir un código mucho más limpio y legible, facilita la integración de estilos CSS modernos y nos da soporte nativo para incluir el video de capacitación mediante la etiqueta `<video>`. Además, al trabajar con PHP nativo para la generación dinámica de tablas y resultados, la sintaxis flexible de HTML5 reduce el riesgo de inconsistencias que en XHTML habrían bloqueado completamente el aplicativo.

---

## 5. PASO 4 · METADATOS: IDENTIFICA, DIFERENCIA Y DECIDE

### ¿Qué información describen los metadatos?
Los metadatos son datos estructurados sobre el propio documento web que se ubican dentro de la etiqueta `<head>`. No se muestran de manera gráfica en el cuerpo de la página, pero describen información vital para el navegador web, los motores de búsqueda y los servidores, tales como:
* El juego o codificación de caracteres utilizado para representar textos.
* La configuración de la ventana de visualización (*viewport*) para diseño responsivo.
* El título y la descripción del contenido para buscadores y pestañas del navegador.
* La autoría y los derechos de autor del proyecto.
* Pautas de rastreo para indexadores web (*robots*).
* Metadatos de integración social (*Open Graph*) y color de interfaz para navegadores móviles.

### ¿Qué metadatos consideras necesarios para tu proyecto?
Para la primera página de SIRAD considero indispensables los siguientes metadatos:
1. **`charset="UTF-8"`:** Para garantizar la representación correcta de acentos, eñes y caracteres del idioma español en los nombres de funcionarios y remitentes de Norte de Santander.
2. **`viewport`:** Para asegurar que la página se adapte de forma fluida tanto a pantallas de escritorio de oficina como a dispositivos móviles y tabletas.
3. **`title`:** Para identificar con claridad el aplicativo en las pestañas del navegador del funcionario.
4. **`description`:** Para resumir el propósito institucional del sistema (control de correspondencia y plazos).
5. **`keywords`:** Palabras clave asociadas a la gestión documental y a la Gobernación.
6. **`author`:** Para registrar formalmente la autoría del estudiante desarrollador (Cristian Alexander Durán Medina).
7. **`theme-color`:** Para personalizar la barra superior en navegadores móviles con el color azul institucional.
8. **Metadatos Open Graph (`og:title`, `og:description`, `og:type`):** Para estandarizar la forma en que se previsualiza el enlace si es compartido por canales institucionales.

### ¿Qué diferencias encontraste al trabajar con HTML5 y XHTML?
* **Sintaxis de cierre:** En XHTML la etiqueta `<meta>` es un elemento vacío que obligatoriamente debía cerrarse con una barra al final (`<meta ... />`), mientras que en HTML5 se escribe de forma natural sin barra de cierre (`<meta ...>`).
* **Declaración del Charset:** En XHTML la especificación del juego de caracteres requería una sintaxis engorrosa:  
  `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />`  
  En cambio, HTML5 la simplificó notablemente a un atributo directo:  
  `<meta charset="UTF-8">`.
* **Uso de espacios de nombres (Namespaces):** En XHTML era necesario declarar atributos `xmlns` en la etiqueta `<html>`, mientras que HTML5 prescinde de ellos para documentos estándar.

### ¿Qué metadatos incluirías en la primera página de tu proyecto y por qué?
En el `<head>` de `Desarrollo/index.php` incluí:
* `<meta charset="UTF-8">`: Porque en la Gobernación se manejan nombres de municipios como *Chinácota*, *Ábrego*, *Cúcuta*, y términos como *radicación* o *petición*; sin este metadato aparecerían caracteres extraños (mojibake).
* `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Porque los supervisores y secretarios de despacho consultan frecuentemente el estado de los radicados desde sus teléfonos móviles.
* `<meta name="description" content="SIRAD: Sistema web para el control de flujo interno, seguimiento de términos legales y semáforo de plazos de correspondencia oficial...">`: Permite que cualquier auditor o usuario identifique de inmediato la función del sistema.
* `<meta name="author" content="Cristian Alexander Durán Medina">`: Certifica la autoría del estudiante en el desarrollo de la obra.
* `<meta name="robots" content="index, follow">`: Facilita la indexación controlada en la red local de la entidad.
* `<meta name="theme-color" content="#1e3a8a">`: Aplica el tono azul oscuro institucional al navegador.

---

## 6. PASO 5 · DEFINE LA ESTRUCTURA DE TU PÁGINA

A partir del boceto preliminar, estructuré la página en 6 bloques semánticos con propósitos específicos para el usuario:

| Sección / Elemento Semántico | Contenido Previsto | Propósito para el Usuario |
| :--- | :--- | :--- |
| **1. Encabezado (`<header>`)** | Logotipo de SIRAD, título institucional, nombre de la Secretaría de Programas y Proyectos Especiales y credencial del operador en turno. | Identificar visualmente la aplicación oficial, validar que se encuentra en el entorno de la Gobernación y saber con qué perfil de usuario se está operando. |
| **2. Navegación Principal (`<nav>`)** | Enlaces accesibles a las secciones: Inicio, Consultar Radicado, Semáforo de Términos, Guía Multimedia e Información Entidad. | Permitir al usuario desplazarse con rapidez a las diferentes áreas de trabajo de la página sin tener que desplazarse manualmente por todo el documento. |
| **3. Tablero de Términos (`<section id="semaforo">`)** | 4 tarjetas métricas (*KPIs*): Radicados Totales, Trámites al Día (Verde), Trámites en Alerta (Amarillo) y Trámites Vencidos (Rojo). | Brindar un diagnóstico visual inmediato al inicio de la jornada laboral para que el funcionario priorice aquellos radicados cuyos plazos legales están por expirar. |
| **4. Zona Principal de Consulta (`<section id="consulta">`)** | Campo de búsqueda de texto, selector de filtro por estado, botón de búsqueda y tabla semántica con los datos del radicado (código, remitente, asunto, asignado, días restantes y badge de estado). | Atender la necesidad operativa fundamental: consultar si un radicado existe, verificar qué funcionario lo está gestionando y calcular cuántos días hábiles quedan de respuesta. |
| **5. Módulo Multimedia (`<section id="capacitacion">`)** | Reproductor de video nativo HTML5 (`<video controls>`), carátula previa (*poster*), subtítulos descriptivos y lista de los 4 pasos clave de radicación. | Capacitar e inducir a los funcionarios sobre el correcto flujo de radicación digital, reduciendo errores operativos y duplicidad de radicados. |
| **6. Pie de Página (`<footer>`)** | Dirección física de la Gobernación en Cúcuta, horarios oficiales de ventanilla, referencia a la Ley 1755 de 2015 y ficha técnica de la versión académica. | Proveer información complementaria institucional, respaldo jurídico del servicio y claridad sobre la versión del software implementada. |

---

## 7. PASO 6 · CONSTRUYE LA PRIMERA VERSIÓN

La primera página del proyecto fue construida en la carpeta `Desarrollo/` en dos archivos complementarios:
* `Desarrollo/index.php`: Código fuente interactivo que utiliza PHP básico nativo para procesar las búsquedas por parámetro GET (`?q=...&estado=...`), calcular dinámicamente las cantidades del semáforo y renderizar las filas de la tabla de forma limpia.
* `Desarrollo/index.html`: Versión estática compilada que permite abrir y visualizar el prototipo directamente en cualquier navegador web haciendo doble clic, sin necesidad de iniciar previamente un servidor.

### Características implementadas:
* **Marcado HTML5 Válido:** Cumple con la estructura de elementos semánticos recomendados (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<video>`, `<footer>`).
* **Estilos CSS Integrados:** Sistema de diseño visual sobrio, con paleta institucional gubernamental (azules, grises y colores de semáforo normalizados), diseño en cuadrícula responsiva (*CSS Grid* y *Flexbox*), tipografía del sistema legible y microinteracciones en botones y tarjetas.
* **Componente Multimedia Operativo:** Etiqueta `<video>` con controles de reproducción nativos, contenedor con relación de aspecto adaptada y texto de soporte para accesibilidad.

---

## 8. PASO 7 · COMPRUEBA LO QUE CONSTRUISTE

Tras abrir la página construida en el navegador web (Google Chrome / Firefox) y contrastarla con el boceto inicial, doy respuesta a las preguntas de comprobación:

### ¿La página quedó organizada como la diseñaste?
**Sí.** La distribución guarda estricta fidelidad con el boceto del wireframe. El encabezado y la barra de navegación se ubican arriba; inmediatamente después se visualizan las métricas del semáforo para impacto visual, seguido por el buscador central con su tabla de radicados, el área de video tutorial y el pie de página institucional.

### ¿El contenido principal es fácil de identificar?
**Totalmente.** Gracias a la jerarquía visual de tamaños y contrastes, la vista del usuario se dirige naturalmente al buscador de radicados y a los números grandes de las tarjetas del semáforo. La tabla utiliza bordes suaves y distintivos de colores (*badges*) para que sea inmediato reconocer si un trámite está en verde, amarillo o rojo.

### ¿La estructura responde a la necesidad del usuario?
**Sí responde a su necesidad cotidiana.** Un funcionario de la Gobernación no necesita pantallas sobrecargadas; necesita saber qué radicados tiene asignados y cuáles están en riesgo de vencimiento. La estructura construida permite realizar esa consulta en un solo paso.

### ¿Encontraste algún problema de sintaxis o estructura?
Al realizar la revisión inicial con el linter de PHP (`php -l`) y validar las etiquetas HTML5, no se presentaron errores de sintaxis ni etiquetas sin cerrar. Un detalle observado fue la necesidad de garantizar que el contenedor del video tuviera un ancho máximo adaptativo para que en pantallas pequeñas de teléfono no desbordara el ancho horizontal de la página, lo cual se resolvió agregando `max-width: 100%` en las reglas CSS.

### ¿Qué cambiarías en una segunda versión?
En una segunda versión considero conveniente:
1. Conectar la tabla directamente a una base de datos MySQL mediante PDO en PHP (en lugar del array de prueba actual).
2. Añadir un botón para exportar el listado de radicados filtrados a formato PDF o Excel.
3. Incorporar paginación para cuando la Secretaría maneje cientos de radicados simultáneos.

---

## 9. PASO 10 · CONTROL DE CALIDAD INICIAL

Para garantizar la calidad técnica de la página web en las próximas fases del proyecto, he definido la siguiente **lista de 8 criterios de calidad medibles y aplicables**:

1. **Validación de Estándares W3C:** La página no debe presentar errores críticos ni advertencias graves en el validador oficial de HTML5 del W3C (*The Nu HTML Checker*).
2. **Jerarquía Semántica de Encabezados:** Existencia de un único encabezado principal `<h1>` por página, seguido de niveles subordinados lógicos (`<h2>`, `<h3>`) sin saltos de nivel injustificados (por ejemplo, pasar de `h1` directamente a `h4`).
3. **Adaptabilidad Responsiva (Diseño Móvil):** La página debe adaptarse correctamente a diferentes anchos de pantalla (móvil de 360px, tableta de 768px y escritorio de 1200px) sin generar desbordamiento horizontal (*scroll horizontal*).
4. **Contraste de Color y Legibilidad (Accesibilidad WCAG AA):** Todo texto debe mantener una relación de contraste mínima de 4.5:1 respecto a su fondo para facilitar la lectura a personas con baja agudeza visual.
5. **Accesibilidad en Formularios:** Todos los campos de entrada (`<input>`, `<select>`) deben contar con etiquetas explícitas (`<label>`) o atributos descriptivos accesibles (`aria-label`), además de indicadores visuales claros al recibir foco (`:focus`).
6. **Integridad de Enlaces y Recursos Externos:** Verificación de que no existan enlaces rotos (código HTTP 404), que las imágenes cuenten con su atributo `alt` obligatorio y que el video contenga un texto de respaldo si el formato no es soportado.
7. **Rendimiento de Carga y Peso del Documento:** El peso del documento HTML y sus recursos locales debe optimizarse para cargar en menos de 2 segundos en una conexión de red estándar institucional.
8. **Consistencia en la Codificación UTF-8:** Verificación visual y técnica de que todos los textos, acentos y signos de puntuación se visualicen sin alteraciones en cualquier navegador.

---

## 10. PASO 11 · CONECTA CON LA ARQUITECTURA WEB

Recordemos el modelo arquitectónico fundamental estudiado en clase:  
$$\text{Usuario} \longrightarrow \text{Cliente} \longrightarrow \text{Solicitud} \longrightarrow \text{Servidor} \longrightarrow \text{Respuesta}$$

A continuación analizo cómo opera este ciclo en el contexto real de SIRAD:

### ¿Qué parte de tu página responde directamente a una necesidad del usuario?
La **sección central de consulta y la tabla de radicados con su semáforo** responden directamente a la necesidad primordial del usuario. Cuando el funcionario necesita saber el estado del trámite `RAD-2026-0089`, esta sección le presenta de forma consolidada el asunto, a qué profesional fue derivado y si le quedan 4 días de término legal, mitigando el riesgo de que la entidad incurra en silencios administrativos o sanciones por mora.

### ¿Qué papel cumple el cliente web al mostrar tu página?
El cliente web (el navegador del funcionario) cumple tres funciones fundamentales:
1. **Peticionario:** Recolecta la entrada del usuario en el formulario y la envía codificada mediante una solicitud HTTP `GET` hacia la URL correspondiente.
2. **Motor de Renderizado:** Recibe el documento HTML generado por el servidor, construye el árbol de objetos del documento (*DOM*), aplica las reglas de cascada de estilos (*CSSOM*) y dibuja los elementos gráficos en la pantalla.
3. **Intérprete de Multimedia e Interacción:** Se encarga de decodificar el archivo multimedia mediante su reproductor nativo y maneja los estados interactivos (como el cambio de color al pasar el cursor sobre los botones o filas).

### ¿Qué información podría solicitar el usuario posteriormente?
Posteriormente, el usuario podría solicitar:
* El historial detallado de actuaciones de un radicado específico (bitácora de derivaciones internas entre funcionarios).
* La descarga del archivo PDF oficial adjunto que fue escaneado en ventanilla.
* La generación de un nuevo radicado mediante un formulario de registro.
* Un reporte estadístico consolidado de trámites atendidos versus radicados vencidos en el mes.

### ¿Qué respuesta esperaría recibir?
* **En el caso de consultar el historial:** El servidor respondería con un documento HTML o una vista modal que muestre la cronología de movimientos con fecha, hora y funcionario que recibió el documento.
* **En el caso de solicitar el PDF:** El servidor respondería con una cabecera HTTP `Content-Type: application/pdf` acompañada de los datos binarios del documento para su previsualización o descarga inmediata en el navegador.
* **En el caso de un nuevo registro:** Esperaría recibir un código HTTP `200 OK` (o redirección `302/303`) mostrando una notificación de éxito con el número de radicado asignado automáticamente (por ejemplo: `RAD-2026-0091`).

---

## 11. LISTA DE VERIFICACIÓN Y AUTOEVALUACIÓN

| Criterio de Verificación | Estado | Evidencia en el Proyecto |
| :--- | :---: | :--- |
| **Partí de mi proyecto individual** |  Cumplido | Basado 100% en SIRAD (Gobernación de Norte de Santander / Secretaría de Programas y Proyectos). |
| **Diseñé la maquetación antes de programar** |  Cumplido | Wireframe estructurado en `Desarrollo/boceto_wireframe.svg` con las 6 zonas requeridas. |
| **Comparé HTML5 y XHTML** |  Cumplido | Cuadro comparativo riguroso con 8 criterios técnicos en el Paso 3. |
| **Diferencié sus características de sintaxis relevantes** |  Cumplido | Análisis de DOCTYPE, reglas de cierre, case-sensitivity, parsing dracónico vs tolerante y multimedia nativa. |
| **Analicé los metadatos** |  Cumplido | Estudio detallado de la etiqueta `<head>` y sus diferencias entre estándares en el Paso 4. |
| **Justifiqué qué metadatos utilizaré** |  Cumplido | Justificación argumentada de los metadatos `charset`, `viewport`, `description`, `author`, `theme-color` y `Open Graph`. |
| **Construí una primera versión HTML** |  Cumplido | Implementado en `Desarrollo/index.php` y `Desarrollo/index.html` con PHP nativo y HTML5 semántico. |
| **Comprobé la página en el navegador** |  Cumplido | Evaluación visual y funcional realizada en Google Chrome y Firefox (Paso 7). |
| **Relacioné el resultado con las necesidades del usuario y el proyecto** |  Cumplido | Conexión explícita con el modelo Usuario-Cliente-Solicitud-Servidor-Respuesta y las necesidades de la ventanilla única. |

---
**Elaborado por:** Cristian Alexander Durán Medina  
**Proyecto SIRAD · Desarrollo Básico de Aplicaciones en Red**  
Septiembre de 2026
