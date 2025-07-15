# Laboratorio 1: Multi-Armed Bandits con Algoritmo Epsilon-Greedy

Este laboratorio implementa el algoritmo epsilon-greedy para resolver el problema de multi-armed bandits, con el objetivo de maximizar la recompensa acumulativa a lo largo de múltiples iteraciones.

## 📋 Descripción del Problema

El problema de multi-armed bandits es un paradigma clásico en el aprendizaje por refuerzo donde un agente debe decidir entre múltiples acciones (brazos) sin conocer inicialmente las probabilidades de recompensa de cada uno. El desafío consiste en equilibrar la **exploración** (probar brazos desconocidos) y la **explotación** (usar el conocimiento actual para maximizar recompensas).


## 🚀 Implementación

### Clases Principales

#### 1. Clase `Bandit`
Representa el entorno de 10 brazos:
- **Inicialización**: Genera probabilidades aleatorias para cada brazo (0-1)
- **Método `pull(arm)`**: Devuelve recompensa de 1 con probabilidad específica del brazo, 0 en caso contrario

#### 2. Clase `Agent`
Implementa la estrategia epsilon-greedy:
- **Parámetros**:
  - `k`: Número de brazos (10)
  - `epsilon`: Probabilidad de exploración
  - `counts`: Contador de extracciones por brazo
  - `values`: Valores estimados (Q) para cada brazo

- **Métodos**:
  - `select_arm()`: Selección de brazo con estrategia ε-greedy
  - `update_estimates()`: Actualización de estimaciones usando media incremental

### Algoritmo Epsilon-Greedy

```
Con probabilidad ε: EXPLORAR (brazo aleatorio)
Con probabilidad 1-ε: EXPLOTAR (brazo con mayor Q estimado)
```

### Actualización de Estimaciones

```
Q ← Q + (1/n) × (reward - Q)
```

Donde:
- `Q`: Valor estimado actual
- `n`: Número de veces que se ha seleccionado el brazo
- `reward`: Recompensa obtenida

## 📊 Experimentos y Resultados

### Configuración Base
- **Número de brazos**: 10
- **Iteraciones**: 1,000
- **Epsilon inicial**: 0.1
- **Semilla**: 42 (para reproducibilidad)

### Experimentos con Diferentes Valores de Epsilon

| Epsilon | Comportamiento | Características |
|---------|----------------|-----------------|
| 0.01    | Mayor explotación | Convergencia rápida, menor exploración |
| 0.1     | Balance equilibrado | Buen compromiso exploración-explotación |
| 0.5     | Mayor exploración | Más exploración, convergencia más lenta |

## 📈 Visualizaciones

El notebook incluye las siguientes gráficas:

1. **Recompensa Acumulada vs Iteraciones**: Muestra el progreso del aprendizaje
2. **Valores Estimados vs Probabilidades Reales**: Evalúa la precisión de las estimaciones
3. **Comparación entre diferentes valores de epsilon**: Análisis del impacto del parámetro de exploración

