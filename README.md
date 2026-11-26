Teleportación Cuántica y Criptografía Cuántica

Proyecto final de Mecánica Cuántica
Facultad de Ingeniería — Universidad Autónoma de Chihuahua
Ingeniería Física

Descripción del proyecto

Este proyecto estudia dos aplicaciones fundamentales de la mecánica cuántica en el procesamiento y la transmisión de información: la teleportación cuántica y la criptografía cuántica mediante el protocolo BB84.

Se desarrolla un análisis teórico, matemático y computacional de ambos protocolos, abordando conceptos como superposición, entrelazamiento, medición cuántica, transformaciones unitarias y el teorema de no clonación.

Mediante simulaciones numéricas y circuitos cuánticos se busca comprender el funcionamiento de estos protocolos y analizar sus resultados, relacionando las predicciones teóricas con implementaciones computacionales y experimentales.

Objetivos

- Estudiar los fundamentos físicos y matemáticos de la teleportación cuántica.
- Comprender el papel del entrelazamiento y las mediciones en la transferencia de estados cuánticos.
- Implementar el protocolo BB84 mediante simulaciones numéricas.
- Analizar los efectos de la interceptación de información por parte de un espía.
- Evaluar la tasa de error cuántico de bits (QBER) y la generación de claves.
- Implementar circuitos de teleportación cuántica y estudiar su comportamiento en simulación y hardware cuántico.

Estructura del repositorio

teleportacion-criptografia-cuantica/
│
├── README.md
│
├── Reporte Teleportación cuántica y
│   criptografía cuántica.pdf
│
├── Implementacion_Circuito_Cuantico/
│   │
│   ├── BB84_sin_espia.ipynb
│   ├── BB84_con_espia.ipynb
│   ├── BB84_interceptacion_parcial.ipynb
│   ├── REFERENCIAS.md
│   │
│   ├── BB84_resultados_y_graficas/
│   │   ├── BB84_QBER_y_tasas_de_clave.ipynb
│   │   ├── BB84_QBER_con_incertidumbre.png
│   │   ├── BB84_tasas_de_clave.png
│   │   └── resultados_bb84.csv
│   │
│   ├── Teleportacion_seis_estados_resultados_y_grafica/
│   │   ├── Teleportacion_seis_estados_resultados_y_grafica_ipynb.ipynb
│   │   ├── teleportacion_circuito_logico.png
│   │   ├── teleportacion_conteos_simulados.json
│   │   ├── teleportacion_fidelidades_simuladas.csv
│   │   └── teleportacion_fidelidades_simuladas.png
│   │
│   └── Teleportacion_IBM_Kingston/
│       ├── Teleportacion_hardware_IBM.ipynb
│       ├── teleportacion_circuito_transpilado_IBM_Kingston.png
│       ├── teleportacion_comparacion_hardware.png
│       └── teleportacion_resultados_hardware.json
│
├── notas/
│   ├── Notas_del_codigo.pdf
│   ├── Quantum Computation - Bez.pdf
│   ├── Quantum Computing - Rieffel .pdf
│   ├── Quantum Mechanics - Zubairy.pdf
│   └── contexto_historico.pdf
│
└── referencias/
    ├── Quantum Computation - Bez.pdf
    ├── Quantum Computing - Rieffel.pdf
    └── Quantum Mechanics - Zubairy.pdf

1. Teleportación cuántica

Se estudia el protocolo de teleportación cuántica mediante circuitos de tres qubits.

El procedimiento contempla:

1. Preparación del estado cuántico que se desea teleportar.
2. Generación de un par de qubits entrelazados mediante una compuerta Hadamard y una CNOT.
3. Aplicación de las operaciones de Alice sobre los qubits correspondientes.
4. Mediciones en la base computacional.
5. Aplicación de las correcciones cuánticas de Bob mediante las compuertas X y Z, condicionadas a los resultados de Alice.

Se incluyen simulaciones para estudiar diferentes estados cuánticos, sus resultados y las fidelidades obtenidas.

También se incorpora una implementación en hardware cuántico de IBM, junto con los resultados experimentales y la comparación correspondiente.

2. Criptografía cuántica: protocolo BB84

Se implementa el protocolo BB84, propuesto por Charles Bennett y Gilles Brassard en 1984, para estudiar la distribución cuántica de claves.

Se consideran dos bases de medición:

- Base Z: base computacional.
- Base X: base diagonal.

Las simulaciones contemplan tres escenarios:

BB84 sin espía

Se simula la comunicación entre Alice y Bob sin intervención de terceros. Se generan bits y bases aleatorias, se comparan las bases utilizadas y se obtiene la clave cribada.

BB84 con espía

Se incorpora a Eva como una tercera participante que intercepta y mide los estados cuánticos antes de que lleguen a Bob. Se analiza cómo la elección aleatoria de bases puede introducir errores en la clave compartida.

BB84 con interceptación parcial

Se estudia el efecto de diferentes porcentajes de interceptación sobre la comunicación. Se analiza la relación entre la fracción de qubits interceptados, la QBER y la cantidad de bits que sobreviven al proceso de selección de bases.

3. Análisis de resultados

Se incluyen simulaciones numéricas y herramientas de análisis para estudiar el comportamiento de los protocolos.

Entre los resultados disponibles se encuentran:

- Evolución de la QBER en función del porcentaje de interceptación.
- Comparación entre resultados simulados y predicciones teóricas.
- Análisis de las tasas de generación de claves.
- Gráficas con intervalos de incertidumbre.
- Resultados de fidelidad para diferentes estados teleportados.
- Comparación entre simulaciones y ejecución en hardware cuántico.

Los resultados se encuentran disponibles en archivos CSV, JSON, imágenes y notebooks de Jupyter.

Herramientas y tecnologías

El proyecto utiliza las siguientes herramientas:

- Python: programación y simulación numérica.
- NumPy: generación de datos aleatorios y operaciones numéricas.
- Matplotlib: elaboración de gráficas y visualización de resultados.
- Jupyter Notebook / Google Colab: desarrollo y ejecución de simulaciones.
- Qiskit: construcción y ejecución de circuitos cuánticos.
- IBM Quantum: implementación y evaluación de circuitos en hardware cuántico.

Cómo ejecutar el proyecto

1. Descargar el repositorio

git clone <URL_DEL_REPOSITORIO>

2. Instalar las dependencias

Para las simulaciones BB84:

pip install numpy matplotlib

Para los circuitos de teleportación:

pip install qiskit matplotlib pylatexenc

3. Abrir los notebooks

Se recomienda utilizar Google Colab o Jupyter Notebook.

Abrir los archivos ".ipynb" ubicados en "Implementacion_Circuito_Cuantico/" y ejecutar las celdas en orden.

Para la implementación en hardware IBM se requiere configurar el acceso correspondiente a IBM Quantum y disponer de un backend compatible.

Referencias

Las referencias bibliográficas utilizadas para el desarrollo teórico y computacional se encuentran en:

- "Implementacion_Circuito_Cuantico/REFERENCIAS.md"
- Carpeta "notas/"
- Carpeta "referencias/"

El desarrollo teórico completo se encuentra en el documento:

Reporte Teleportación cuántica y criptografía cuántica.pdf

---

Proyecto desarrollado como parte de la asignatura de Mecánica Cuántica.

Facultad de Ingeniería
Universidad Autónoma de Chihuahua
Ingeniería Física
