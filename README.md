# Crypto Projects Graph Analysis

Crypto Projects Graph Analysis es un proyecto académico de análisis de datos aplicado a proyectos de criptomonedas. El trabajo utiliza datos obtenidos desde la API de CoinMarketCap, procesamiento con Python y construcción de grafos con NetworkX para representar relaciones entre proyectos según categorías compartidas.

El proyecto fue desarrollado como parte de una práctica académica del curso de Machine Learning. Aunque no implementa un modelo supervisado tradicional, aplica técnicas de análisis, clasificación basada en reglas y visualización de redes para estudiar patrones entre proyectos cripto.

## Objetivo del proyecto

El objetivo principal es analizar proyectos de criptomonedas mediante sus categorías, construir una red de relaciones entre ellos y visualizar agrupaciones o conexiones relevantes dentro del ecosistema cripto.

El proyecto busca demostrar:

- Consumo de datos desde una API externa.
- Normalización y análisis de datos con Pandas.
- Clasificación de proyectos por categorías.
- Construcción de grafos con NetworkX.
- Definición de nodos y aristas según similitud categórica.
- Visualización de relaciones entre proyectos.
- Análisis exploratorio aplicado a datos del mercado cripto.

## Tecnologías utilizadas

- Python
- Jupyter Notebook
- Pandas
- Requests
- NetworkX
- Matplotlib
- python-dotenv
- CoinMarketCap API

## Fuente de datos

Los datos son obtenidos desde la API de CoinMarketCap. Para ejecutar el notebook se requiere una API key personal.

La clave no debe escribirse directamente en el notebook. En su lugar, debe configurarse mediante un archivo `.env`.

Ejemplo:

```env
COINMARKETCAP_API_KEY=your_api_key_here
```

## Estructura del proyecto

```txt
Crypto-Projects-Graph-Analysis/
  README.md
  .gitignore
  .env.example
  requirements.txt

  notebooks/
    crypto_graph_analysis.ipynb

  docs/
    methodology.md

  outputs/
    figures/
      README.md
```

## Descripción de carpetas

### `notebooks/`

Contiene el notebook principal del proyecto:

```txt
crypto_graph_analysis.ipynb
```

En este notebook se realiza la obtención de datos, procesamiento, clasificación, construcción del grafo y visualización de resultados.

### `docs/`

Contiene documentación complementaria del proyecto.

- [`methodology.md`](docs/methodology.md): explica la metodología utilizada para obtener datos, clasificar proyectos y construir los grafos.

### `outputs/figures/`

Carpeta destinada a almacenar visualizaciones generadas por el notebook, como grafos generales o subgrafos por categoría.

## Instalación

Clonar el repositorio:

```bash
git clone <url-del-repositorio>
cd Crypto-Projects-Graph-Analysis
```

Crear un entorno virtual:

```bash
python -m venv .venv
```

Activar el entorno virtual en Windows PowerShell:

```powershell
.venv\Scripts\activate
```

Activar el entorno virtual en Linux o WSL:

```bash
source .venv/bin/activate
```

Instalar dependencias:

```bash
pip install -r requirements.txt
```

## Configuración de variables de entorno

Crear un archivo `.env` a partir de `.env.example`:

```bash
cp .env.example .env
```

En Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Luego agregar la API key real de CoinMarketCap:

```env
COINMARKETCAP_API_KEY=your_real_api_key
```

El archivo `.env` no debe subirse al repositorio.

## Ejecución

Abrir el notebook:

```txt
notebooks/crypto_graph_analysis.ipynb
```

Ejecutar las celdas en orden para:

1. Cargar la API key desde variables de entorno.
2. Consultar datos desde CoinMarketCap.
3. Convertir la respuesta JSON a estructuras tabulares.
4. Clasificar proyectos según categorías.
5. Construir el grafo de relaciones.
6. Visualizar el grafo general y subgrafos.

## Flujo general del análisis

```txt
CoinMarketCap API
  ↓
Extracción de datos
  ↓
Normalización con Pandas
  ↓
Clasificación por categorías
  ↓
Construcción de nodos
  ↓
Cálculo de relaciones
  ↓
Construcción de aristas
  ↓
Visualización con NetworkX y Matplotlib
```

## Metodología resumida

El análisis se basa en representar cada proyecto cripto como un nodo. Luego, se crean relaciones entre proyectos cuando comparten categorías o características similares.

El peso de una arista representa el grado de relación entre dos proyectos según las categorías compartidas. A mayor cantidad de coincidencias, mayor peso en la relación.

Para más detalle, revisar:

[`docs/methodology.md`](docs/methodology.md)

## Resultados esperados

El notebook permite generar visualizaciones como:

- Grafo general de proyectos cripto.
- Relaciones entre proyectos según categorías.
- Subgrafos por tipo de proyecto.
- Visualización de conexiones entre proyectos similares.
- Exploración de agrupamientos dentro del ecosistema cripto.

## Seguridad y manejo de credenciales

Este repositorio no debe contener API keys reales.

Buenas prácticas aplicadas:

- Uso de `.env` para credenciales locales.
- Inclusión de `.env.example` como plantilla.
- Exclusión de `.env` mediante `.gitignore`.
- Eliminación de claves sensibles del notebook.

Si una API key fue subida anteriormente al repositorio, se recomienda revocarla y generar una nueva desde la plataforma correspondiente.

## Alcance del proyecto

Este proyecto corresponde a una práctica académica de análisis de datos.

Incluye:

- Consumo de API externa.
- Procesamiento de datos.
- Clasificación basada en reglas.
- Construcción de grafos.
- Visualización de relaciones.
- Análisis exploratorio.

## Limitaciones

- Depende de la disponibilidad y límites de la API de CoinMarketCap.
- No implementa un modelo de Machine Learning supervisado.
- La clasificación se basa en reglas y categorías disponibles.
- Los datos pueden variar con el tiempo.
- El análisis depende de la calidad de la información devuelta por la API.
- Las visualizaciones pueden requerir ajustes si aumenta mucho el número de nodos.

## Posibles mejoras

- Agregar métricas de centralidad del grafo.
- Detectar comunidades dentro de la red.
- Comparar proyectos por capitalización, volumen o variación de precio.
- Exportar figuras automáticamente a `outputs/figures/`.
- Implementar clustering no supervisado.
- Crear un dashboard interactivo.
- Agregar pruebas de validación para las funciones de procesamiento.
- Guardar snapshots de datos para reproducibilidad.

## Estado del proyecto

Proyecto académico funcional y reorganizado para presentación en GitHub.

## Autor

Desarrollado por Axel Pariona como práctica académica de análisis de datos y grafos aplicada a proyectos de criptomonedas.
