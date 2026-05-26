# lending-club-data-cleaning
  Lending Club — Limpieza y Análisis de Datos

**Universidad Tecnológica de Bolívar · Ciencia de Datos**

> Proyecto de limpieza, exploración y análisis del dataset de préstamos aprobados de Lending Club (2007–2018), como base para futuros modelos de predicción de riesgo crediticio.

---

##  Autores

| Nombre | Programa |
|--------|----------|
| Gabriel David Torres Montiel | ciencias de datos · UTB |
| Jose Angel Gomez Agamez | ciencias de datos · UTB |


##  Descripción del proyecto

Lending Club fue la plataforma de préstamos entre personas (P2P) más grande de EE. UU. Este proyecto trabaja con su dataset público de **2.26 millones de préstamos** aprobados entre 2007 y 2018, disponible en Kaggle.

El objetivo es dejar el dataset limpio, documentado en español y listo para ser usado en modelos de machine learning que predigan la probabilidad de impago de un préstamo.

---

##  Objetivos

- Descargar y explorar el dataset original (151 columnas × 2.26M filas)
- Detectar y tratar valores nulos
- Eliminar duplicados
- Traducir todas las columnas al español con descripción
- Realizar análisis exploratorio con visualizaciones
- Exportar el dataset limpio


##  Resultados del proceso de limpieza

| Métrica | Antes | Después |
|---------|-------|---------|
| Filas | 2,260,701 | 2,260,668 |
| Columnas | 151 | 107 |
| Columnas con nulos | 87 | 0 |
| Duplicados | 0 | 0 |

### Tratamiento de nulos

| Estrategia | Columnas | Criterio |
|------------|----------|----------|
| Eliminadas | 44 | Más del 50% de valores nulos |
| Imputadas con mediana | 29 | Columnas numéricas con nulos bajos/moderados |
| Imputadas con moda | 14 | Columnas de texto con nulos bajos/moderados |


##  Estructura del repositorio

```
lending-club-data-cleaning/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── Proyecto_corte3.ipynb        # Notebook principal con todo el proceso
│
├── dashboard/
│   └── Dashboard_LendingClub.html   # Dashboard interactivo de resultados
│
└── data/
    └── data_sample.csv              # Muestra de 2,000 filas del dataset limpio
```


## ⚙️ Metodología paso a paso

**1. Descarga del dataset**
- Usando `kagglehub` se descarga automáticamente el dataset desde Kaggle
- Dataset: `wordsforthewise/lending-club`

**2. Exploración inicial**
- Revisión de dimensiones, tipos de datos y estadísticas descriptivas
- Identificación de columnas problemáticas

**3. Detección y tratamiento de nulos**
- Cálculo del porcentaje de nulos por columna
- Eliminación de columnas con >50% de nulos (44 columnas)
- Imputación con mediana para columnas numéricas
- Imputación con moda para columnas de texto

**4. Detección de duplicados**
- Revisión de duplicados exactos con `df.duplicated()`
- Revisión por ID único con `subset=['id']`
- Resultado: 0 duplicados encontrados

**5. Traducción y documentación**
- Las 107 columnas finales fueron renombradas al español
- Organizadas en 5 categorías: Préstamo, Pagos, Crédito, Prestatario, Otros

**6. Análisis exploratorio**
- Distribución de montos solicitados
- Estado de los préstamos
- Propósito del crédito
- Calificación de riesgo (A–G)

---

##  Cómo reproducir el proyecto

### 1. Clona el repositorio
```bash
git clone https://github.com/TU_USUARIO/lending-club-data-cleaning.git
cd lending-club-data-cleaning
```

### 2. Instala las dependencias
```bash
pip install -r requirements.txt
```

### 3. Configura tu API key de Kaggle
- Ve a [kaggle.com/settings](https://www.kaggle.com/settings) → API → Create New Token
- Descarga el archivo `kaggle.json`
- Colócalo en `~/.kaggle/kaggle.json`

### 4. Ejecuta el notebook
```bash
jupyter notebook notebooks/Proyecto_corte3.ipynb
```

>  El dataset pesa ~1.26 GB. La descarga puede tardar varios minutos dependiendo de tu conexión.


##  Dashboard interactivo

El archivo `dashboard/Dashboard_LendingClub.html` es un dashboard interactivo que puedes abrir directamente en el navegador. Incluye:

- Resumen general del proceso de limpieza
- Análisis de valores nulos
- Verificación de duplicados
- Análisis exploratorio de préstamos
- Tabla completa de columnas traducidas
- Información del proyecto, autores y consideraciones éticas


##  Fuente de datos

- **Dataset:** [Lending Club Loan Data — Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club)
- **Período:** 2007 – 2018
- **Registros:** 2,260,701 préstamos aprobados
- **Licencia:** Uso público/académico


##  Ética y limitaciones

- Los datos son públicos y anónimos; no permiten identificar personas individuales
- El dataset puede contener sesgos históricos en la aprobación de créditos (por estado, ingreso, tipo de empleo)
- Los datos cubren 2007–2018 y no reflejan el mercado crediticio actual
- Este proyecto es exclusivamente académico; no se toman decisiones crediticias reales con estos resultados
- Cualquier modelo predictivo derivado debe evaluarse con criterios de equidad antes de aplicarse en contextos reales

---
