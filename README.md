# Explorador de vehículos usados con Streamlit

## Resumen

Construí una aplicación para explorar anuncios de vehículos usados y comparar sus precios de forma interactiva. La desarrollé con **Streamlit, pandas y Plotly**, como parte del **Sprint 7 del bootcamp de Data Science de TripleTen**.

**Autor:** [Luis Eduardo Aguilar Castellanos](https://github.com/EdAgZer03)

## Objetivo

Permitir que una persona explore las características de los anuncios y compare marcas sin tener que ejecutar un notebook. La aplicación trabaja con **51 525 anuncios** del archivo `vehicles_us.csv`.

**[Abrir la aplicación en Render](https://edag-proyect-7.onrender.com/)**

## Qué hice

- Cargué los datos y extraje la marca desde el nombre del modelo.
- Agregué una vista de la tabla y una opción para mostrar marcas con más de 10 000 anuncios.
- Construí gráficos interactivos de precios, tipos de vehículo, condición, año y odómetro.
- Incorporé la selección de dos marcas para comparar la distribución de sus precios.

## Cómo usar la aplicación

| Control | Qué permite explorar |
|---|---|
| Vista de datos y filtro de marcas | Revisar los anuncios incluidos en la selección. |
| Precio promedio por tipo | Comparar los precios anunciados entre tipos de vehículo. |
| Dispersión de odómetro y precio | Observar la relación entre ambas variables y detectar valores extremos. |
| Histogramas de condición y año | Comparar las edades de los vehículos según su condición. |
| Histograma de odómetro | Revisar la distribución de sus lecturas. |
| Comparación de dos marcas | Contrastar las distribuciones de precios dentro de la selección activa. |

Selecciona las opciones y utiliza el botón de cada sección para generar su gráfico. El filtro de marcas también se aplica a la comparación final. Los gráficos de Plotly permiten acercar, consultar valores y ocultar series desde la leyenda.

## Tecnologías

**Python · Streamlit · pandas · Plotly · Jupyter Notebook**

- [Aplicación](app.py): interfaz y gráficos interactivos.
- [Notebook](Notebooks/EDA.ipynb): exploración y construcción de los gráficos.
- [Datos](data/README.md): descripción del archivo y configuración de su ruta.
- [Dependencias de la aplicación](requirements.txt) y [dependencias para el notebook](requirements-notebook.txt).

## Cómo ejecutar

Entorno de referencia: **Python 3.10.21 · Windows**, con Streamlit **1.63.0**, pandas **2.3.3** y Plotly **6.9.0**.

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

La aplicación busca `data/vehicles_us.csv` y, como alternativa, el archivo `vehicles_us.csv` incluido en la raíz. Para usar otra ubicación, configura la ruta antes de iniciar:

```powershell
$env:VEHICLES_DATA_PATH = 'C:\datos\vehicles_us.csv'
python -m streamlit run app.py
```

Para ejecutar el notebook con su script:

```powershell
python -m pip install -r requirements-notebook.txt
python scripts/execute_notebook.py
```

El [archivo de dependencias completo](requirements-lock.txt) corresponde al entorno de referencia en Windows e incluye las herramientas de notebook.

## Conclusiones y alcance

Lo más útil de este proyecto fue convertir gráficos de un notebook en una herramienta que se puede explorar con botones y filtros. El promedio por tipo y los histogramas ayudan a comparar los anuncios desde distintos ángulos.

La aplicación muestra **precios anunciados**, no precios de venta confirmados. Los promedios pueden verse afectados por valores extremos y las variables con datos ausentes se omiten en los gráficos que las necesitan. Mantengo la unidad original del odómetro; no aplico una conversión a kilómetros.

El filtro de marcas con mayor número de anuncios cambia el conjunto comparado. Los resultados describen este dataset y no representan una valoración automática ni todo el mercado de vehículos.
