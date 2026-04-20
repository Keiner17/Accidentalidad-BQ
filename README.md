# Accidentalidad Barranquilla

Dashboard de análisis de vehículos involucrados en accidentes de tránsito en Barranquilla, construido con HTML, CSS y JavaScript vanilla. Los datos son consumidos en tiempo real desde el portal oficial de datos abiertos del gobierno colombiano.
<img width="1366" height="651" alt="image" src="https://github.com/user-attachments/assets/792f7c16-6122-4517-bee5-d23bf449bacd" />



---

<!-- Reemplaza esta línea con tu imagen: ![Dashboard](./tu-captura.png) -->

---

## Tabla de contenidos

- [Descripción](#descripción)
- [Características](#características)
- [Tecnologías](#tecnologías)
- [Instalación](#instalación)
- [Fuente de datos](#fuente-de-datos)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Autores](#autores)

---

## Descripción

Este proyecto es una página web estática que visualiza estadísticas de accidentalidad vial en Barranquilla. Al cargar, consulta la API pública SODA (Socrata Open Data API) del dataset oficial del gobierno y construye automáticamente los indicadores, gráficas y tabla de registros a partir de los campos disponibles en el dataset.

No requiere servidor, base de datos ni dependencias externas más allá de la librería de gráficas.

---

## Características

- **Indicadores clave (KPIs):** total de registros documentados, tipos de vehículo distintos, rango de años disponibles y mes con mayor accidentalidad.
- **Gráfica de barras horizontal:** top 10 tipos de vehículo ordenados por frecuencia de accidentes.
- **Gráfica de dona:** distribución porcentual por gravedad del accidente o clase de accidente según los campos disponibles en el dataset.
- **Tabla de registros:** muestra los 200 incidentes más recientes con columnas priorizadas (tipo de vehículo, gravedad, año, mes, barrio, vía, etc.) y scroll interno.
- **Detección dinámica de campos:** el código lee los nombres de columna del dataset y mapea automáticamente los campos relevantes, por lo que es tolerante a cambios en la estructura del API.
- **Animación de contadores:** los KPIs numéricos se animan al cargarse.
- **Diseño responsive:** adaptado para móvil, tablet y escritorio.
- **Pantalla de carga:** loader animado mientras se obtienen los datos.
- **Manejo de errores:** si la API falla, se muestra un mensaje descriptivo en pantalla.
<img width="1366" height="651" alt="image" src="https://github.com/user-attachments/assets/df691c87-4eaf-423c-82c9-53ce265b3d43" />
<img width="1366" height="651" alt="image" src="https://github.com/user-attachments/assets/17cd9f5a-bb44-4bb2-b6c1-ca5037de2ff8" />

---

## Tecnologías

| Tecnología | Uso |
|---|---|
| HTML5| Estructura, estilos y diseño responsivo |
| JavaScript  | Lógica de consumo de API, procesamiento de datos y renderizado |
| [Plotly.js 2.27](https://plotly.com/javascript/) | Gráficas interactivas (barras y dona) |
| [API SODA ](https://dev.socrata.com/) | Fuente de datos de accidentalidad |

---

> **Recomendación:** usar la extensión [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) de VS Code para evitar posibles bloqueos CORS al hacer las peticiones a la API desde el sistema de archivos local.

---

## Fuente de datos

Los datos provienen del dataset **Accidentalidad Barranquilla — Detalle de Vehículos**, publicado en el portal de datos abiertos del gobierno colombiano.

- **Portal:** [datos.gov.co](https://www.datos.gov.co/Transporte/Accidentalidad-Barranquilla-detalle-de-Veh-culos/nfa3-wgxy/about_data)
- **Endpoint API:**
  ```
  https://www.datos.gov.co/resource/nfa3-wgxy.json

### `index.html`

Contiene todo el proyecto en un solo archivo: estilos, estructura HTML y lógica JavaScript. Al cargar ejecuta la función `init()`, que:

1. Hace una petición de muestra para detectar los campos disponibles en el dataset.
2. Lanza en paralelo todas las consultas necesarias (conteo total, últimos 500 registros, agrupaciones por tipo de vehículo, gravedad, año y mes).
3. Construye los KPIs, renderiza las gráficas con Plotly y genera la tabla de registros dinámicamente.

---

## Autores

Desarrollado por **Keiner Fontalvo** y **Oscar Llanos** — Tecnologías Web.

Los datos son provistos por [datos.gov.co](https://www.datos.gov.co) bajo licencia de datos abiertos.
