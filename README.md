# Dots and Boxes con Minimax y Poda Alfa-Beta

## 📘 Descripción General
Este proyecto corresponde a un trabajo académico de la asignatura **Fundamentos de Inteligencia Artificial**, cuyo objetivo es poner en práctica los conceptos teóricos de **búsqueda de soluciones en espacios de estados aplicados a juegos con adversario**.

Se desarrolló un sistema capaz de modelar un juego de tablero, representar sus estados y aplicar algoritmos de decisión para que un agente artificial pueda seleccionar la mejor jugada posible frente a un oponente.

---

## 🎯 Objetivos del Proyecto
- Comprender el funcionamiento de los algoritmos de búsqueda adversaria.
- Implementar estructuras de representación de estados de juego.
- Aplicar el algoritmo **Minimax**.
- Optimizar la búsqueda mediante **poda alfa-beta**.
- Visualizar el estado del juego de manera gráfica en consola.

---

## 🧠 Fundamento Teórico

### Juegos con Adversario
En inteligencia artificial, un juego con adversario es un problema donde:
- Hay dos agentes.
- Cada uno busca maximizar su ventaja.
- El resultado depende de las decisiones de ambos.

Estos problemas se modelan como **árboles de juego**, donde:
- Nodos = estados
- Aristas = acciones posibles
- Hojas = estados finales.

---

### Algoritmo Minimax
El algoritmo **Minimax** permite encontrar la mejor decisión suponiendo que el oponente también juega de manera óptima.

Principio:
- Jugador MAX intenta maximizar el valor.
- Jugador MIN intenta minimizarlo.

Se evalúa el árbol alternando turnos hasta cierta profundidad o hasta estados terminales.

---

### Poda Alfa-Beta
Es una optimización de Minimax que:
- Evita explorar ramas innecesarias.
- Reduce el costo computacional.
- Mantiene el mismo resultado final.

Utiliza dos parámetros:
- **α (alpha)** → mejor valor garantizado para MAX.
- **β (beta)** → mejor valor garantizado para MIN.

Cuando **α ≥ β** → se corta la rama.

---

## ⚙️ Implementación Práctica

### Generación de Acciones
Cada estado del juego puede generar el conjunto de jugadas legales disponibles a partir de la configuración actual del tablero.  
Este proceso permite explorar el espacio de estados del juego y construir el árbol de búsqueda necesario para la toma de decisiones.

```python
acciones_disponibles()
```

Esta función retorna todas las acciones válidas que el jugador en turno puede ejecutar desde el estado actual.

---

### Transición de Estados
A partir de una acción válida, se genera un nuevo estado del juego que representa el resultado de aplicar dicha acción al estado actual.

```python
realizar_accion(a)
```

Esta transición es fundamental para simular posibles futuros del juego durante la búsqueda adversaria.

---

### Evaluación Heurística
Debido a que no siempre es posible explorar el árbol de juego hasta estados terminales, se utiliza una función heurística para estimar la calidad de un estado intermedio.

La evaluación se basa en criterios como:
- Diferencia de cajas capturadas entre jugadores.
- Control del tablero.
- Posibilidades futuras de captura.

El valor heurístico guía al algoritmo Minimax en la selección de la mejor jugada.

---

### Motor de Decisión
El núcleo del agente inteligente está implementado mediante el algoritmo Minimax con poda alfa-beta:

```python
minimax_alpha_beta(estado, profundidad, alpha, beta, maximizando)
```

Este algoritmo:
- Alterna turnos entre los jugadores MAX y MIN.
- Busca maximizar la utilidad del jugador MAX y minimizar la del jugador MIN.
- Reduce significativamente el número de estados explorados mediante poda alfa-beta.

---

### Selección de la Mejor Acción
Para determinar la mejor jugada desde el estado actual, se evalúan todas las acciones posibles utilizando el motor de decisión:

```python
mejor_accion(estado, profundidad, maximizando=True)
```

Esta función retorna:
- La acción óptima.
- El valor heurístico asociado.
- El jugador que realiza la jugada.

---

### Visualización del Tablero
Con el fin de facilitar la comprensión del estado del juego, se implementó una función que muestra el tablero en consola utilizando caracteres ASCII.

La visualización representa:
- Vértices del tablero.
- Aristas horizontales y verticales.
- Cajas capturadas.
- Propietario de cada caja.

Esto permite seguir el desarrollo del juego turno a turno de manera clara.

---

## ▶️ Ejecución

Para ejecutar el proyecto y observar el comportamiento del agente inteligente:

```bash
python main.py
```

Durante la ejecución, el tablero se actualizará en la terminal después de cada jugada.

---

## 📊 Aprendizajes Obtenidos
A través de este proyecto se fortalecieron conocimientos en:

- Modelado de juegos como espacios de estados.
- Implementación de búsqueda adversaria.
- Uso de heurísticas para evaluación de estados.
- Optimización mediante poda alfa-beta.
- Representación visual de información en consola.

---

## 🔧 Mejoras Futuras
- Implementar heurísticas más avanzadas para mejorar la toma de decisiones.
- Optimizar el rendimiento del algoritmo para tableros más grandes.
- Añadir interfaz gráfica en lugar de visualización ASCII.
- Incorporar distintos niveles de dificultad para el agente.
- Permitir modo multijugador humano vs humano.

---

## 👨‍💻 Autores
Trabajo realizado por estudiantes de tercer semestre de Ingeniería en Inteligencia Artificial de la Escuela Colombiana de Ingeniería Julio Garavito:

- Andres Steeven Oyuela Mendez  
- Juan David Rojas Heredia
---
## 📌 Conclusión
La implementación realizada evidencia cómo los algoritmos de búsqueda adversaria permiten a un agente tomar decisiones racionales en juegos competitivos. La combinación de teoría y práctica demuestra la aplicabilidad de los fundamentos de la inteligencia artificial en problemas reales de toma de decisiones.
