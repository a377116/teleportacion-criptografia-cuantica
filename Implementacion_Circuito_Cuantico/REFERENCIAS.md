# Referencias de la implementación

Este documento relaciona las fuentes consultadas con el código, los circuitos y el análisis del proyecto. Los cuadernos implementan los protocolos y las expresiones indicadas a continuación.

## 1. Protocolo de teleportación cuántica

Bennett, C. H., Brassard, G., Crépeau, C., Jozsa, R., Peres, A., y Wootters, W. K. (1993). Teleporting an unknown quantum state via dual classical and Einstein-Podolsky-Rosen channels. Physical Review Letters, 70, 1895–1899.

[Artículo y DOI](https://doi.org/10.1103/PhysRevLett.70.1895)

[PDF](https://journals.aps.org/prl/pdf/10.1103/PhysRevLett.70.1895)

**Aplicación en el proyecto**

Fundamenta la transferencia del estado mediante un par entrelazado, la medición de Alice, la comunicación de dos bits clásicos y las correcciones de Bob.

**Elemento para mostrar**

Página 1896, segunda página del PDF, ecuaciones (5) y (6). Relacionan los resultados de Alice con los estados de Bob y las transformaciones necesarias para recuperar el estado original.

El artículo utiliza un par singlete. Nuestro circuito prepara el estado de Bell |Φ+⟩, por lo que las correcciones se interpretan según esa elección y el orden de las mediciones.

## 2. Construcción y verificación del circuito en Qiskit

IBM Quantum Learning. (s. f.). Qiskit implementation. Curso Basics of quantum information, lección Entanglement in action.

[Documentación y ejemplo](https://quantum.cloud.ibm.com/learning/en/courses/basics-of-quantum-information/entanglement-in-action/qiskit-implementation)

**Aplicación en el proyecto**

Respalda la construcción del circuito con H y CX, las mediciones y las correcciones condicionales X y Z mediante `if_test`.

También explica la verificación mediante la operación inversa de la preparación aplicada al qubit de Bob. En nuestros cuadernos se implementa con `preparacion.inverse()` y una medición final.

**Elemento para mostrar**

Apartado Teleportation, código y diagrama del circuito `protocol`. Después, mostrar el circuito `test`, que incorpora la preparación inversa y la medición de verificación.

En el proyecto se repite esa prueba para los estados |0⟩, |1⟩, |+⟩, |−⟩, |+i⟩ y |−i⟩.

## 3. Adaptación del circuito al procesador IBM

IBM Quantum Documentation. (s. f.). Introduction to transpilation.

[Documentación](https://quantum.cloud.ibm.com/docs/en/guides/transpile)

**Aplicación en el proyecto**

Explica la transformación del circuito lógico para utilizar las compuertas y conexiones disponibles en el procesador. Fundamenta la diferencia visual entre el circuito de Colab y el circuito transpilado de IBM Kingston.

**Elemento para mostrar**

Diagramas “Quantum circuit” y “Quantum circuit after transpilation”, ubicados al inicio de la página.

## 4. Referencia clásica de fidelidad

Massar, S., y Popescu, S. (1995). Optimal extraction of information from finite quantum ensembles. Physical Review Letters, 74, 1259–1263.

[Artículo y DOI](https://doi.org/10.1103/PhysRevLett.74.1259)

**Aplicación en el proyecto**

Fundamenta la referencia clásica de fidelidad promedio de 2/3 para estimar y volver a preparar un estado puro desconocido de un qubit, disponiendo de una sola copia.

**Elemento para mostrar**

Página 1259, primera página del artículo. La expresión `(N + 1)/(N + 2)` aparece dentro del texto. Para N = 1 se obtiene 2/3.

Esta referencia se representa mediante la línea roja de nuestras gráficas. La comparación se realiza con el promedio de los seis estados, preparados con igual frecuencia.

## 5. Protocolo BB84

Bennett, C. H., y Brassard, G. (1984). Quantum cryptography: Public key distribution and coin tossing. Proceedings of the IEEE International Conference on Computers, Systems and Signal Processing, Bangalore, India, 175–179.

[PDF del artículo original](https://arxiv.org/pdf/2003.06557)

**Aplicación en el proyecto**

Fundamenta la selección aleatoria de bits y bases, las mediciones de Bob y el cribado de las posiciones con bases coincidentes.

En el código, las bases se representan mediante 0 para Z y 1 para X.

**Elemento para mostrar**

Página 176, tercera página del PDF porque incluye una portada. Mostrar los vectores de las bases rectilínea y diagonal.

La descripción de los pasos de Alice y Bob continúa en la página 177.

## 6. Interceptación parcial de Eva y QBER

Lee, C., Lee, E., y Lee, W. (2023). Analysis on eavesdropper detection in BB84 quantum key distribution protocol against partial intercept-and-resend attack. International Conference on Optical Network Design and Modeling (ONDM).

[PDF](https://dl.ifip.org/db/conf/ondm/ondm2023/1570879964.pdf)

**Aplicación en el proyecto**

Respalda el modelo de interceptación y reenvío parcial utilizado para Eva y la predicción del QBER.

**Elemento para mostrar**

Tercera página del PDF, ecuación (9) y el párrafo situado debajo de la ecuación (10).

Al fijar el ruido del canal en cero, la expresión se reduce a `QBER = ρ/4`. En nuestros cuadernos, ρ corresponde a `fraccion_eva`.

La línea teórica de nuestras gráficas se calcula con `qber_teoricos = fracciones / 4`.

## 7. Intervalos de confianza de Wilson

NIST/SEMATECH. (s. f.). e-Handbook of Statistical Methods. Sección 7.2.4.1, Confidence intervals.

[Fuente y fórmulas](https://www.itl.nist.gov/div898/handbook/prc/section2/prc241.htm)

**Aplicación en el proyecto**

Respalda los intervalos de confianza de Wilson del 95 % utilizados como barras de incertidumbre del QBER.

**Elemento para mostrar**

Bloque “Formulas for the confidence intervals”, con las expresiones del límite superior y del límite inferior.

En nuestra implementación, la proporción observada es el QBER, el tamaño de muestra es el número de bits conservados después del cribado y se utiliza z = 1.96.

## 8. Estimación de la tasa de clave secreta

Shor, P. W., y Preskill, J. (2000). Simple proof of security of the BB84 quantum key distribution protocol. Physical Review Letters, 85, 441–444.

[Artículo y DOI](https://doi.org/10.1103/PhysRevLett.85.441)

[PDF](https://preskill.caltech.edu/pubs/preskill-2000-proof.pdf)

**Aplicación en el proyecto**

Fundamenta la expresión asintótica `1 − 2h₂(Q)` utilizada para estimar la fracción secreta, bajo el supuesto de errores de bit y fase simétricos y corrección ideal.

El código calcula:

- `fraccion_secreta = max(0, 1 − 2h₂(Q))`.
- `tasa_cribada = bits_conservados / qubits_enviados`.
- `tasa_secreta = tasa_cribada × fraccion_secreta`.

La gráfica representa una estimación asintótica. La implementación calcula esa tasa a partir del QBER simulado.

**Elemento para mostrar**

Página 444, última página del PDF. Localizar la expresión `1 − 2H(δ)` dentro del párrafo que menciona el umbral cercano al 11 %.

## Resultados generados en el proyecto

Las gráficas, los archivos CSV y los archivos JSON contienen los resultados de nuestras simulaciones y de la ejecución en hardware.

La corrida de teleportación en IBM se identifica mediante:

- Procesador `ibm_kingston`.
- Job ID `dboelu44148s739stt70`.
- Seis estados de entrada.
- 1024 ejecuciones por estado.
- Fidelidad promedio observada de 0.9519856771, aproximadamente 95.20 %.

La fidelidad observada se estima mediante la proporción de verificaciones correctas tras aplicar la preparación inversa al qubit de Bob. En hardware, esta medida incluye los efectos de la preparación, las operaciones del circuito y la lectura.
