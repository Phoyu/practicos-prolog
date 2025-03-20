# Practicos Prolog

Este repositorio contiene un entorno estructurado para resolver y validar ejercicios de Prolog. El proyecto está organizado para ayudar a desarrollar y probar implementaciones de Prolog de manera eficiente.

## Estructura del Proyecto
```
prolog_exercises/ 
├── ejercicio1/ 
│ ├── base.pl # Base de conocimiento con hechos y reglas dados 
│ ├── solucion.pl # Implementación de los predicados requeridos 
│ └── tests.pl # Pruebas automatizadas para validar la solución 
├── ejercicio2/ 
│ ├── ... 
└── ejecutar_tests.pl # Script para ejecutar todas las pruebas a la vez
```

## Cómo Usar Este Proyecto

### 1. Configurar un Ejercicio

Para cada nuevo ejercicio:

1. Crea un directorio con el nombre del ejercicio
2. Crea tres archivos:
   - `base.pl`: Contiene los hechos, reglas y predicados dados
   - `solucion.pl`: Donde se implementa la solución
   - `tests.pl`: Casos de prueba para validar la implementación

### 2. Implementar Soluciones

En `solucion.pl`, primero se carga la base de conocimiento:

```prolog
% Cargar la base de conocimiento
:- [base].

% Implementa los predicados aquí
mi_predicado(X, Y) :-
    % Implementación
```

### 3. Escribir Pruebas
En tests.pl, usa plunit de SWI-Prolog para escribir pruebas:

```prolog
% Cargar tu solución
:- [solucion].

% Cargar el framework de pruebas
:- use_module(library(plunit)).

% Definir casos de prueba
:- begin_tests(mi_predicado).

test(caso_basico) :-
    mi_predicado(a, b).

test(caso_negativo, fail) :-
    mi_predicado(x, y).

:- end_tests(mi_predicado).
```

### 4. Ejecutar Pruebas
Ejecutar todas las pruebas:

```bash
swipl -s ejecutar_tests.pl
```

Ejecutar pruebas para un ejercicio específico:
```bash
swipl -s ejercicio1/tests.pl -g "run_tests,halt"
```

Ejecutar pruebas para un predicado específico:

```bash
swipl -s ejercicio1/tests.pl -g "run_tests(mi_predicado),halt"
```
### 5. Desarrollo Interactivo
Para desarrollo y pruebas interactivas:

Inicia SWI-Prolog en el directorio del ejercicio:

```bash
cd ejercicio1
swipl
```

Carga la solución:

```prolog
?- [solucion].
```
Prueba tus predicados directamente:

```prolog
?- mi_predicado(X, Y).
```
O ejecuta las pruebas:

```prolog
?- [tests].
?- run_tests.
```
Consejos de Depuración
* Usa `trace/1` para depurar predicados específicos:
```prolog
?- trace(mi_predicado).
?- mi_predicado(X, Y).
```
* Usa `gtrace.` para el depurador gráfico
* Después de modificar archivos, usa `make.` para recargarlos

## Requisitos
SWI-Prolog (recomendada versión 8.0 o superior)