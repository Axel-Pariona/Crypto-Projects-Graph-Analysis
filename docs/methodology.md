# Methodology

Este documento describe la metodología utilizada en el proyecto **Crypto Projects Graph Analysis**.

El objetivo del análisis es obtener información de proyectos de criptomonedas desde CoinMarketCap, clasificar los proyectos según sus categorías y construir un grafo que represente relaciones entre ellos.

## 1. Obtención de datos

La fuente principal de datos es la API de CoinMarketCap.

El notebook realiza una solicitud HTTP utilizando la librería `requests`. La autenticación se realiza mediante una API key almacenada en una variable de entorno:

```env
COINMARKETCAP_API_KEY=your_api_key_here
```

La API key no debe escribirse directamente en el notebook ni subirse al repositorio.

## 2. Carga de credenciales

Para cargar la credencial se utiliza `python-dotenv`.

Ejemplo general:

```python
import os
from dotenv import load_dotenv

load_dotenv()

API_KEY = os.getenv("COINMARKETCAP_API_KEY")
```

Si la variable no existe, el notebook debe detenerse o mostrar un mensaje indicando que falta configurar la clave.

## 3. Consulta a la API

La solicitud a la API permite obtener información de proyectos cripto, incluyendo datos como:

- Nombre del proyecto.
- Símbolo.
- Categorías.
- Capitalización.
- Volumen.
- Precio.
- Posición en el ranking.
- Cambios porcentuales.

La disponibilidad exacta de campos puede depender del endpoint usado y de la respuesta actual de CoinMarketCap.

## 4. Normalización de datos

La respuesta de la API suele recibirse en formato JSON.

Para facilitar el análisis, los datos se transforman a una estructura tabular usando Pandas.

Proceso general:

```txt
JSON response
  ↓
Extracción de campos relevantes
  ↓
DataFrame de Pandas
  ↓
Limpieza y selección de columnas
```

## 5. Clasificación de proyectos

Los proyectos se clasifican usando reglas basadas en categorías o palabras clave.

Ejemplos de posibles grupos:

- Meme coins.
- DeFi.
- Gaming.
- Metaverse.
- Layer 1.
- Layer 2.
- Stablecoins.
- AI tokens.
- Exchange tokens.

Esta clasificación es orientativa y depende de la información categórica disponible para cada proyecto.

## 6. Construcción de nodos

Cada proyecto cripto se representa como un nodo dentro del grafo.

Un nodo puede incluir atributos como:

- `name`
- `symbol`
- `categories`
- `rank`
- `market_cap`
- `volume_24h`

Estos atributos permiten enriquecer el análisis y facilitar visualizaciones o filtros posteriores.

## 7. Construcción de aristas

Las aristas representan relaciones entre dos proyectos.

Una relación puede crearse cuando dos proyectos comparten una o más categorías.

Ejemplo:

```txt
Proyecto A: DeFi, Layer 1
Proyecto B: DeFi, Governance

Relación: comparten la categoría DeFi
```

## 8. Peso de las relaciones

El peso de una arista puede calcularse según la cantidad de categorías compartidas.

Ejemplo:

```txt
weight = número de categorías compartidas
```

Mientras mayor sea el peso, mayor será la similitud categórica entre dos proyectos.

## 9. Construcción del grafo

Con NetworkX se construye el grafo:

```python
import networkx as nx

G = nx.Graph()
```

Luego se agregan nodos y aristas con sus atributos correspondientes.

Flujo general:

```txt
DataFrame de proyectos
  ↓
Agregar nodos
  ↓
Comparar categorías entre proyectos
  ↓
Agregar aristas ponderadas
  ↓
Visualizar grafo
```

## 10. Visualización

La visualización se realiza con NetworkX y Matplotlib.

Las visualizaciones pueden incluir:

- Grafo general de proyectos.
- Subgrafo por categoría.
- Grafo reducido de muestra.
- Nodos con etiquetas.
- Aristas con pesos.

Cuando el número de proyectos es grande, se recomienda limitar la cantidad de nodos o filtrar por categorías para evitar gráficos saturados.

## 11. Análisis de resultados

El análisis permite observar:

- Proyectos con más conexiones.
- Categorías con mayor presencia.
- Agrupaciones de proyectos similares.
- Relaciones fuertes entre proyectos.
- Posibles comunidades dentro del ecosistema cripto.

## 12. Limitaciones metodológicas

El análisis tiene algunas limitaciones:

- Los datos dependen de la API y pueden cambiar con el tiempo.
- Las categorías pueden no estar completas para todos los proyectos.
- La clasificación se basa en reglas, no en aprendizaje supervisado.
- El peso de las relaciones es una aproximación simple.
- Los grafos grandes pueden ser difíciles de interpretar visualmente.

## 13. Posibles mejoras metodológicas

Se podrían implementar mejoras como:

- Cálculo de centralidad de grado.
- Cálculo de betweenness centrality.
- Detección de comunidades.
- Clustering no supervisado.
- Comparación temporal entre snapshots.
- Visualizaciones interactivas.
- Exportación automática de resultados.
- Uso de métricas financieras como atributos del grafo.

## Conclusión

La metodología permite transformar datos de proyectos cripto en una estructura de red para analizar similitudes y relaciones categóricas. Aunque el enfoque es exploratorio y académico, proporciona una base útil para aplicar análisis de grafos y técnicas de ciencia de datos sobre información del mercado de criptomonedas.
