# 🔧 Predicción de Carga Última en Materiales

Un modelo de Machine Learning que predice cuánto peso puede soportar un material antes de romperse.

## ¿Qué hace este proyecto?

Predice la **carga última** (máximo peso que soporta) de materiales de acero como A36, S275 y S355. Solo necesitas las medidas de la pieza y algunas propiedades del material.

## 📊 Resultados

- **Precisión del modelo:** 90.29% (R² = 0.9029)
- **Datos analizados:** 124,639 ensayos de tracción
- **Materiales soportados:** A36, S275, S355

## 🎯 ¿Para qué sirve?

- Calcular resistencia de materiales sin hacer ensayos físicos
- Ahorrar tiempo y dinero en diseño estructural
- Optimizar diseños de estructuras de acero
- Ayudar a ingenieros en toma de decisiones

## 🛠️ Tecnologías usadas

- **Python** - Lenguaje principal
- **scikit-learn** - Machine Learning
- **pandas** - Manejo de datos
- **matplotlib/seaborn** - Gráficos
- **Random Forest** - Algoritmo de predicción

## 📁 Estructura del proyecto

```
├── tensile_test_data.csv          # Datos de ensayos
├── ProyectoFinalIA_FelixRuiz.ipynb # Notebook principal
├── modelo_tensile_test.joblib      # Modelo entrenado
└── README.md                       # Este archivo
```

## 🚀 Cómo usar

### 1. Instalar dependencias
```bash
pip install pandas scikit-learn matplotlib seaborn joblib
```

### 2. Ejecutar predicción
```python
import joblib
import pandas as pd

# Cargar modelo
modelo = joblib.load("modelo_tensile_test.joblib")

# Tus datos
datos = {
    'material_type': 'S275',
    'thickness_mm': 15.0,
    'width_mm': 30.0,
    'test_speed_mm_min': 2.0,
    'yield_strength_MPa': 275.0,
    'ultimate_tensile_strength_MPa': 430.0,
    'elongation_at_fracture': 0.23,
    'yield_load_N': 120000
}

# Predecir
df_input = pd.DataFrame([datos])
prediccion = modelo.predict(df_input)[0]
print(f"Carga última estimada: {prediccion:,.2f} N")
```

## 📈 Datos de entrada

El modelo necesita estos datos:

| Dato | Descripción | Ejemplo |
|------|-------------|---------|
| `material_type` | Tipo de material | A36, S275, S355 |
| `thickness_mm` | Espesor en mm | 15.0 |
| `width_mm` | Ancho en mm | 30.0 |
| `test_speed_mm_min` | Velocidad de ensayo | 2.0 |
| `yield_strength_MPa` | Resistencia a fluencia | 275.0 |
| `ultimate_tensile_strength_MPa` | Resistencia a tracción | 430.0 |
| `elongation_at_fracture` | Elongación en fractura | 0.23 |
| `yield_load_N` | Carga de fluencia | 120000 |

## 🔍 Cómo funciona

1. **Carga datos** de 124,639 ensayos reales de materiales
2. **Limpia y prepara** los datos para el modelo
3. **Entrena** un algoritmo Random Forest
4. **Predice** la carga última basada en las propiedades del material

## 📊 Visualizaciones incluidas

- Distribución de tipos de materiales
- Relación entre espesor y carga última
- Matriz de correlación de variables
- Histogramas de propiedades clave

## ⚡ Ejemplo de uso real

**Entrada:**
- Material: S275
- Dimensiones: 15mm x 30mm
- Carga de fluencia: 120,000 N

**Salida:**
- Carga última estimada: 183,593 N
- Factor de seguridad: 1.53

## 🎓 Aprendizajes

- **Random Forest** funciona bien para datos de ingeniería
- **R² de 0.90** indica excelente precisión
- El **espesor y ancho** son los factores más importantes
- Los **diferentes tipos de acero** tienen comportamientos distintos

## 📝 Notas importantes

- El modelo funciona solo con los 3 tipos de acero entrenados
- Los datos vienen de ensayos reales en máquina universal
- La precisión puede variar con materiales muy diferentes a los entrenados

## 👤 Autor

**Felix Ruiz Muñoz**  
Proyecto Final - Inteligencia Artificial
