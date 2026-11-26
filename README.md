# MODELADO COMPUTACIONAL DE LA PROPAGACIÓN ESPACIAL DEL CAPITAL PRODUCTIVO ENTRE REGIONES MEDIANTE LA ECUACIÓN FISHER-KPP

### Ondas viajeras, difusión y crecimiento económico en un modelo de reacción-difusión

**Autores:**
- Valeria Giraldo Echeverri
- Javier Urrego Ojeda

**Universidad:** Pontificia Universidad Javeriana Cali  
**Asignatura:** Computación Científica  
**Docente:** Andrés Julián Castrillón Vásquez  
**Año:** 2026

---

## 1. Descripción del proyecto

Esta investigación estudia la propagación espacial de una variable económica normalizada asociada al capital productivo entre regiones, mediante la ecuación de Kolmogorov-Petrovsky-Piskunov, conocida como ecuación Fisher-KPP.

El trabajo se desarrolla desde un enfoque de modelación matemática y simulación computacional, utilizando escenarios hipotéticos y adimensionales para analizar la influencia del coeficiente de difusión espacial y la tasa de crecimiento local sobre la velocidad de propagación de frentes.

Además, se estudian las ondas viajeras, los puntos de equilibrio y las órbitas heteroclínicas asociadas al modelo.

**Alcance:** la investigación no utiliza datos económicos reales de Colombia ni pretende realizar predicciones sobre el comportamiento real del capital entre regiones. Su propósito es analizar las propiedades matemáticas y computacionales del modelo.

## 2. Pregunta de investigación

¿Cómo influyen el coeficiente de difusión y la tasa de crecimiento local en la velocidad de propagación espacial del capital productivo, según el modelo Fisher-KPP, y qué tan adecuadamente permiten los métodos numéricos aproximar su comportamiento?

## 3. Modelo matemático

Se utiliza la ecuación Fisher-KPP:

$$
\frac{\partial w}{\partial t}
=
D\frac{\partial^2w}{\partial x^2}
+
rw\left(1-\frac{w}{K}\right)
$$

Mediante la normalización:

$$
u=\frac{w}{K}
$$

se obtiene:

$$
\frac{\partial u}{\partial t}
=
D\frac{\partial^2u}{\partial x^2}
+
ru(1-u)
$$

Donde:

- **u(x,t):** variable económica normalizada asociada al capital productivo.
- **D:** coeficiente de difusión espacial.
- **r:** tasa de crecimiento local.
- **K:** capacidad de carga o nivel de saturación de la variable original.
- **x:** coordenada espacial.
- **t:** tiempo.

La velocidad mínima teórica de propagación está dada por:

$$
c_{\min}=2\sqrt{Dr}
$$

## 4. Metodología computacional

La implementación se desarrolló en Python mediante las siguientes herramientas y procedimientos:

- **NumPy:** operaciones numéricas y manejo de arreglos.
- **SciPy:** herramientas de apoyo para los cálculos numéricos.
- **Matplotlib:** generación y visualización de gráficas.
- **Pandas:** organización de resultados.

Métodos numéricos utilizados:

1. Diferencias finitas centrales para la discretización espacial.
2. Runge-Kutta de cuarto orden (RK4).
3. Adams-Bashforth de cuarto orden (AB4).
4. Interpolación lineal para localizar el frente de propagación.
5. Mínimos cuadrados para estimar la velocidad del frente.

La posición del frente se determina mediante el umbral:

$$
u(x_f(t),t)=0.5
$$

Posteriormente, se estima su velocidad mediante un ajuste lineal de la posición respecto al tiempo.

## 5. Experimentos computacionales

Se desarrollaron los siguientes experimentos:

1. Variación del coeficiente de difusión espacial D.
2. Variación de la tasa de crecimiento local r.
3. Comparación de los integradores RK4 y AB4.
4. Análisis de ondas viajeras y espacio fase.
5. Refinamiento de la malla espacial y temporal.
6. Análisis del efecto del horizonte temporal sobre la velocidad estimada.

## 6. Resultados principales

Para el experimento de variación de la difusión, manteniendo r = 1:

| D | Velocidad teórica | Velocidad numérica |
|---|---:|---:|
| 0.5 | 1.4142 | 1.3818 |
| 1.0 | 2.0000 | 1.9461 |
| 2.0 | 2.8284 | 2.7481 |

Para el experimento de variación del crecimiento, manteniendo D = 1:

| r | Velocidad teórica | Velocidad numérica |
|---|---:|---:|
| 0.5 | 1.4142 | 1.3243 |
| 1.0 | 2.0000 | 1.9461 |
| 2.0 | 2.8284 | 2.8479 |

Para el escenario base D = 1 y r = 1, se obtuvieron los siguientes resultados al ampliar el horizonte temporal:

| Ventana temporal | Velocidad estimada | Error frente a 2 |
|---|---:|---:|
| 15–40 | 1.946060 | 2.6970 % |
| 40–80 | 1.978946 | 1.0527 % |
| 80–120 | 1.989083 | 0.5458 % |

Los resultados muestran que el coeficiente de difusión y la tasa de crecimiento influyen en la velocidad de propagación. Asimismo, la velocidad estimada se aproxima progresivamente al valor mínimo teórico al considerar ventanas temporales posteriores.

La validación también mostró coincidencia de las velocidades estimadas a seis decimales en los pasos temporales evaluados, mientras que el refinamiento espacial no presentó una convergencia monótona hacia el valor teórico en la ventana analizada.

## 7. Ondas viajeras y espacio fase

Se utilizó la transformación:

$$
z=x-ct
$$

para expresar el modelo mediante un sistema de ecuaciones diferenciales ordinarias.

El análisis permitió estudiar los puntos de equilibrio normalizados:

$$
E_1=(0,0),\qquad E_2=(1,0)
$$

y la trayectoria heteroclínica que conecta ambos estados.

## 8. Conclusiones

La ecuación Fisher-KPP permite estudiar matemáticamente la interacción entre difusión espacial y crecimiento logístico en una variable normalizada asociada al capital productivo.

Las simulaciones muestran que los parámetros D y r influyen en la velocidad de propagación, de acuerdo con la relación teórica del modelo.

La comparación de integradores, el análisis del espacio fase y las pruebas de refinamiento permitieron examinar el comportamiento numérico de las soluciones y sus limitaciones.

Finalmente, la investigación constituye un estudio teórico-computacional de carácter exploratorio. Una aplicación económica real requeriría datos regionales, definición de indicadores observables y calibración de los parámetros.

## 9. Contenido del repositorio

Este repositorio reúne los materiales desarrollados durante la investigación:

- Informe científico final.
- Notebook de Google Colab con la implementación computacional.
- Gráficas de los experimentos.
- Resultados y material complementario.

## 10. Información académica

**Proyecto final de Computación Científica**

Pontificia Universidad Javeriana Cali  
2026

**Integrantes:** Valeria Giraldo Echeverri y Javier Urrego Ojeda.

**Docente:** Andrés Julián Castrillón Vásquez.
