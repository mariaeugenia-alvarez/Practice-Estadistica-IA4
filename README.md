# Práctica de Estadística e IA4 - Análisis de Datos de Airbnb Madrid

## 📋 Descripción del Proyecto

Este proyecto realiza un análisis estadístico completo de datos de Airbnb en Madrid, con el objetivo de predecir los metros cuadrados de los apartamentos utilizando técnicas de machine learning y análisis estadístico. El estudio incluye limpieza de datos, análisis exploratorio, clustering de barrios y modelado predictivo.

## 🎯 Objetivos

- Analizar el dataset de Airbnb de Madrid
- Limpiar y preprocesar los datos de metros cuadrados
- Agrupar barrios por similitud en metros cuadrados usando clustering jerárquico
- Crear un modelo de regresión lineal para predecir metros cuadrados
- Evaluar la calidad del modelo y rellenar valores faltantes

## 📊 Dataset

Los datos provienen de [OpenDataSoft](https://public.opendatasoft.com/explore/dataset/airbnb-listings/), específicamente filtrados para:
- **Ciudad**: Madrid
- **Tipo de habitación**: Apartamento completo ("Entire home/apt")
- **Variables principales**: Barrio, número de huéspedes, baños, habitaciones, camas, precio, metros cuadrados, etc.

## 🔧 Metodología

### 1. Preprocesamiento de Datos
- Filtrado de datos relevantes (Madrid, apartamentos completos)
- Conversión de pies cuadrados a metros cuadrados (1 ft² = 0.092903 m²)
- Identificación y tratamiento de valores NA (93.8% de valores faltantes iniciales)
- Eliminación de outliers (<20 m² y >250 m²)

### 2. Análisis Estadístico
- **Test de Shapiro-Wilk**: Evaluación de normalidad de la distribución
- **Test de Kruskal-Wallis**: Comparación de medias entre barrios
- **Análisis de Tukey**: Matriz de similaridad entre barrios

### 3. Clustering de Barrios
- Creación de matriz de distancias basada en p-valores de Tukey
- Dendrograma jerárquico con corte en h=0.25
- Identificación de **3 clusters principales** de barrios

### 4. Modelado Predictivo
- **Variables predictoras**: Baños, habitaciones, precio, cluster de barrio
- **Modelo de regresión lineal**: `Square.Meters ~ Bathrooms + Bedrooms + Price + neighb_id`
- **División**: 70% entrenamiento, 30% prueba

## 📈 Resultados

### Rendimiento del Modelo
- **R² (entrenamiento)**: 0.70
- **R² (prueba)**: 0.68
- **RMSE**: ~17.2 m²
- **Error promedio**: ±19.1 m²

### Variables Más Significativas
1. **Número de habitaciones** (Bedrooms)
2. **Precio por noche** (Price)
3. **Cluster de barrio** (neighb_id)
4. **Número de baños** (Bathrooms)

### Ejemplo de Predicción
Para un apartamento en el barrio de Sol con:
- 6 huéspedes
- 1 baño
- 3 habitaciones
- 3 camas
- 80€/noche

**Predicción**: ~95.6 m²

Cada habitación adicional aumenta aproximadamente **15.4** m².

## 🛠️ Tecnologías Utilizadas

- **R**: Lenguaje principal de análisis
- **Tidyverse**: Manipulación y transformación de datos
- **GGally**: Matrices de correlación y visualización
- **Dendextend**: Análisis de clustering y dendrogramas
- **Caret**: Evaluación de modelos de machine learning
- **Quarto**: Documentación reproducible

## 📁 Estructura del Proyecto

```
Practice-Estadistica-IA4/
├── README.md
├── Practica-MEugeniaAlvarez.qmd  # Análisis principal en Quarto
└── descargar.png                  # Imagen del dataset
```

## 🚀 Cómo Ejecutar

1. **Requisitos previos**:
   ```r
   install.packages(c("tidyverse", "GGally", "dendextend", "caret"))
   ```

2. **Ejecutar el análisis**:
   - Abrir `Practica-MEugeniaAlvarez.qmd` en RStudio o VS Code
   - Ejecutar los chunks de código secuencialmente
   - O renderizar todo el documento con Quarto

3. **Dataset**:
   - Descargar el dataset de Airbnb desde el enlace proporcionado
   - Ajustar la ruta del archivo CSV en el código

## 📊 Principales Hallazgos

1. **Alta cantidad de valores faltantes**: 93.8% de apartamentos sin datos de metros cuadrados
2. **Agrupación efectiva de barrios**: 3 clusters principales basados en similaridad de tamaños
3. **Modelo predictivo robusto**: R² de 0.68 en datos de prueba
4. **Variables clave**: Habitaciones y precio son los mejores predictores

## 🔍 Análisis de Calidad

- **Residuos**: Distribución aproximadamente normal con algunos outliers
- **Homocedasticidad**: Verificada mediante gráficos de residuos
- **Generalización**: Rendimiento similar entre entrenamiento y prueba

## 👨‍💻 Autor

**M. Eugenia Alvarez**

## 📄 Licencia

Este proyecto es para fines educativos y de práctica en análisis estadístico y machine learning.

---

*Proyecto desarrollado como parte de la práctica de Estadística e IA4*
