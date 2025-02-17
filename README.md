# T48A-P04
"""1777771 Cuadros y gráficos estadísticos   Error cuadrático medio .ipynb

# Generar Datos de Temperatura y Crear Histograma

Temperatura en la ciudad de San Luis Potosí en los últimos 5 años

# **Histograma**

**Simulación de Datos**

Para este ejercicio, hemos simulado datos de temperatura utilizando una distribución normal con una media de 20°C y una desviación estándar de 5°C. Esto nos proporciona un conjunto de datos que representa las temperaturas diarias durante los últimos 5 años.

**Histograma**

El histograma es una representación gráfica que muestra la distribución de los datos de temperatura. En el histograma, el eje horizontal representa los rangos de temperatura, mientras que el eje vertical muestra la frecuencia de ocurrencia de cada rango de temperatura.

**Propósito**: El histograma nos ayuda a visualizar cómo se distribuyen las temperaturas a lo largo del tiempo, identificar patrones y detectar posibles valores atípicos.
"""

import numpy as np
import matplotlib.pyplot as plt

# Simular datos de temperatura para los últimos 5 años (365 días por año)
np.random.seed(0)
temperaturas = np.random.normal(loc=20, scale=5, size=5*365)  # Media de 20°C y desviación estándar de 5°C

# Crear el histograma
plt.hist(temperaturas, bins=30, edgecolor='black')
plt.title('Histograma de Temperaturas en San Luis Potosí (Últimos 5 Años)')
plt.xlabel('Temperatura (°C)')
plt.ylabel('Frecuencia')
plt.show()

"""# **Polígono de Frecuencias**

Un polígono de frecuencias es una representación gráfica que muestra la distribución de un conjunto de datos. Se construye trazando puntos en el gráfico que representan la frecuencia de cada intervalo (o "bin") y luego conectando estos puntos con líneas rectas. Los puntos se colocan en los centros de los intervalos.

**Propósito**: El polígono de frecuencias es útil para visualizar la forma de la distribución de los datos y para comparar diferentes distribuciones. Es una alternativa al histograma y puede ser más fácil de interpretar en algunos casos.


"""

# Crear el histograma
hist, bins = np.histogram(temperaturas, bins=30)

# Calcular los puntos medios de los bins
bin_centers = (bins[:-1] + bins[1:]) / 2

# Crear el polígono de frecuencias
plt.plot(bin_centers, hist, marker='o')
plt.title('Polígono de Frecuencias de Temperaturas en San Luis Potosí (Últimos 5 Años)')
plt.xlabel('Temperatura (°C)')
plt.ylabel('Frecuencia')
plt.grid(True)
plt.show()

"""# **Ojiva Menor que**
Una ojiva menor que es un gráfico de frecuencia acumulada que muestra el número acumulado de observaciones por debajo de cada límite de clase. Se construye trazando puntos que representan la frecuencia acumulada en los puntos medios de los intervalos y luego conectando estos puntos con líneas rectas.

**Propósito**: La ojiva menor que es útil para visualizar la distribución acumulativa de los datos y para identificar percentiles y cuartiles.
"""

# Crear el histograma
hist, bins = np.histogram(temperaturas, bins=30)

# Calcular la frecuencia acumulada
frecuencia_acumulada = np.cumsum(hist)

# Calcular los puntos medios de los bins
bin_centers = (bins[:-1] + bins[1:]) / 2

# Crear la ojiva menor que
plt.plot(bin_centers, frecuencia_acumulada, marker='o')
plt.title('Ojiva Menor que de Temperaturas en San Luis Potosí (Últimos 5 Años)')
plt.xlabel('Temperatura (°C)')
plt.ylabel('Frecuencia Acumulada')
plt.grid(True)
plt.show()

"""# **Error Cuadrático Medio (MSE)**
El error cuadrático medio (MSE) es una medida de la calidad de un modelo de predicción. Se calcula como el promedio de los cuadrados de las diferencias entre los valores reales y las predicciones. En este caso, las predicciones son las temperaturas simuladas y los valores reales son las temperaturas con un poco de ruido adicional.

**Propósito**: El MSE nos proporciona una medida cuantitativa de la precisión de las predicciones. Un MSE más bajo indica un mejor ajuste del modelo a los datos reales.


"""

import numpy as np

# Simular datos de temperatura para los últimos 5 años (365 días por año)
np.random.seed(0)
temperaturas_simuladas = np.random.normal(loc=20, scale=5, size=5*365)  # Media de 20°C y desviación estándar de 5°C

# Generar datos reales de temperatura (simulados para este ejemplo)
temperaturas_reales = temperaturas_simuladas + np.random.normal(loc=0, scale=2, size=5*365)  # Añadir ruido con desviación estándar de 2°C

# Calcular el error cuadrático medio (MSE)
mse = np.mean((temperaturas_reales - temperaturas_simuladas) ** 2)
print(f"Error Cuadrático Medio (MSE): {mse}")

"""### American Football Conference (AFC) en 1992

#### AFC East
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| Miami Dolphins        | 11 | 5  | 0  | 0.688| 340 | 281 |
| Buffalo Bills         | 11 | 5  | 0  | 0.688| 381 | 283 |
| Indianapolis Colts    | 9  | 7  | 0  | 0.563| 216 | 302 |
| New York Jets         | 4  | 12 | 0  | 0.250| 220 | 315 |
| New England Patriots  | 2  | 14 | 0  | 0.125| 205 | 363 |

#### AFC Central
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| Pittsburgh Steelers   | 11 | 5  | 0  | 0.688| 299 | 225 |
| Houston Oilers        | 10 | 6  | 0  | 0.625| 352 | 258 |
| Cleveland Browns      | 7  | 9  | 0  | 0.438| 272 | 275 |
| Cincinnati Bengals    | 5  | 11 | 0  | 0.313| 274 | 364 |

#### AFC West
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| San Diego Chargers    | 11 | 5  | 0  | 0.688| 335 | 241 |
| Kansas City Chiefs    | 10 | 6  | 0  | 0.625| 348 | 282 |
| Denver Broncos        | 8  | 8  | 0  | 0.500| 262 | 329 |
| Los Angeles Raiders   | 7  | 9  | 0  | 0.438| 249 | 281 |
| Seattle Seahawks      | 2  | 14 | 0  | 0.125| 140 | 312 |

### National Football Conference (NFC)

#### NFC East
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| Dallas Cowboys        | 13 | 3  | 0  | 0.813| 409 | 243 |
| Philadelphia Eagles   | 11 | 5  | 0  | 0.688| 369 | 244 |
| Washington Redskins   | 9  | 7  | 0  | 0.563| 298 | 263 |
| New York Giants       | 6  | 10 | 0  | 0.375| 259 | 307 |
| Phoenix Cardinals     | 4  | 12 | 0  | 0.250| 196 | 326 |

#### NFC Central
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| Minnesota Vikings     | 11 | 5  | 0  | 0.688| 374 | 249 |
| Green Bay Packers     | 9  | 7  | 0  | 0.563| 276 | 296 |
| Chicago Bears         | 5  | 11 | 0  | 0.313| 295 | 361 |
| Detroit Lions         | 5  | 11 | 0  | 0.313| 273 | 332 |
| Tampa Bay Buccaneers  | 5  | 11 | 0  | 0.313| 267 | 365 |

#### NFC West
| Equipo                | G  | P  | E  | Pct  | PF  | PC  |
|-----------------------|----|----|----|------|-----|-----|
| San Francisco 49ers   | 14 | 2  | 0  | 0.875| 431 | 236 |
| New Orleans Saints    | 12 | 4  | 0  | 0.750| 330 | 202 |
| Atlanta Falcons       | 6  | 10 | 0  | 0.375| 327 | 414 |
| Los Angeles Rams      | 6  | 10 | 0  | 0.375| 313 | 383 |

Ejercicio 1

a) Combine la estadística de los "porcentajes de juegos ganados" para las seis divisiones y clasifique los daos en cinco clases de igual tamaño, mutuamente excluyentes
b) Determine las frecuencias absoluta y relativa de cada clase.
c) Construya un polígono de frecuencias para la distribución del inciso b).
d) Construya una distribución de ojiva de frecuencias acumuladas con el término "mayor que" para la distribución de frecuencias del inciso b)
"""

import numpy as np

np.random.randint(0, 100, 10)

import numpy as np
import matplotlib.pyplot as plt

porcentajes = [
    # AFC East
    0.688, 0.688, 0.563, 0.250, 0.125,
    # AFC Central
    0.688, 0.625, 0.438, 0.313,
    # AFC West
    0.688, 0.625, 0.500, 0.438, 0.125,
    # NFC East
    0.813, 0.688, 0.563, 0.375, 0.250,
    # NFC Central
    0.688, 0.563, 0.313, 0.313, 0.313,
    # NFC West
    0.875, 0.750, 0.375, 0.375]

# Clases
clases = 5
pct_min = min(porcentajes)
pct_max = max(porcentajes)
amplitud = (pct_max - pct_min) / clases

# Limites de clases
lim_class = [pct_min + i * amplitud for i in range(clases + 1)]
class_range = list(zip(lim_class[:-1], lim_class[1:]))

# Frecuencias absolutas y relativas
frec_abs = []
for inf, sup in class_range:
    conteo = sum(1 for x in porcentajes if inf <= x < sup or
                (sup == pct_max and x == sup))
    frec_abs.append(conteo)

frec_rel = [f/len(porcentajes) for f in frec_abs]

# Poligono de frecuencias
centros_clase = [(inf + sup)/2 for inf, sup in class_range]

plt.figure(figsize=(10, 6))
plt.plot(centros_clase, frec_abs, 'bo-')
plt.title('Polígono de Frecuencias PCT NFL')
plt.xlabel('PCT')
plt.ylabel('Frecuencia')
plt.grid(True)
plt.show()

print("\n")

# Ojiva mayor que
frec_acum = []
total = len(porcentajes)
suma_acumulada = total
for freq in frec_abs:
    frec_acum.append(suma_acumulada)
    suma_acumulada -= freq

plt.figure(figsize=(10, 6))
plt.plot([pct_min] + [sup for inf, sup in class_range],
         [total] + frec_acum, 'ro-')
plt.title('Ojiva de Frecuencias Acumuladas Mayor que')
plt.xlabel('PCT')
plt.ylabel('Frecuencia Acumulada')
plt.grid(True)
plt.show()

# Resultados
print("\nIntervalos de Clase y Frecuencias:")
print("Clase\t\tAbs\tRel")
for i, ((inf, sup), abs_f, rel_f) in enumerate(zip(class_range, frec_abs, frec_rel)):
    print(f"{inf:.3f}-{sup:.3f}\t{abs_f}\t\t{rel_f:.3f}")
