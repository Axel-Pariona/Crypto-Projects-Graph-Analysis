# Figures

Esta carpeta está destinada a almacenar las visualizaciones generadas por el notebook del proyecto **Crypto Projects Graph Analysis**.

## Propósito

Las figuras permiten documentar visualmente los resultados del análisis de grafos aplicado a proyectos de criptomonedas.

## Posibles salidas

En esta carpeta se pueden guardar imágenes como:

- Grafo general de proyectos cripto.
- Subgrafo de una categoría específica.
- Grafo reducido de muestra.
- Visualización de comunidades.
- Comparación entre proyectos por categorías.
- Gráficos auxiliares generados durante el análisis.

## Formatos recomendados

Se recomienda guardar las visualizaciones en formatos como:

```txt
.png
.jpg
.svg
.pdf
```

Para GitHub, el formato `.png` suele ser suficiente para mostrar capturas o gráficos en el README.

## Recomendación

No es necesario subir figuras pesadas si pueden regenerarse ejecutando el notebook.

Si se agregan imágenes al repositorio, se recomienda usar nombres descriptivos, por ejemplo:

```txt
crypto_graph_general.png
meme_projects_subgraph.png
defi_projects_subgraph.png
sample_graph.png
```

## Regeneración de figuras

Las figuras pueden regenerarse ejecutando el notebook principal:

```txt
notebooks/crypto_graph_analysis.ipynb
```

El notebook contiene el flujo completo para obtener datos, procesarlos, construir grafos y generar visualizaciones.
