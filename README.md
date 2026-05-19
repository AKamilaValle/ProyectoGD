[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=AKamilaValle/ProyectoGD)

# Proyecto: Metabolismo Celular

## Información de las estudiantes
María Belén Galindo Ramírez \[22211755]; l22211755@tectijuana.edu.mx

Ana Kamila Valle Z. Flores \[22211769]; l22211769@tectijuana.edu.mx

Gemelos Digitales

Ingeniería Biomédica

## Docente
Dr. Paul Antonio Valle Trujillo; paul.valle@tectijuana.edu.mx

Departamento de Ingeniería Eléctrica y Electrónica, Tecnológico Nacional de México/IT Tijuana, Blvd. Alberto Limón Padilla s/n, Tijuana, C.P. 22454, B.C., México.

## Descripción de la asignatura
La asignatura de Gemelos Digitales forma parte del plan de estudios de la carrera en Ingeniería Biomédica con la siguiente competencia general del curso: Formula el gemelo digital a través de datos experimentales para el desarrollo estrategias de control mediante teorías de sistemas dinámicos no lineales y la experimentación in silico. Esta asignatura pretende aportar al perfil del Ingeniero Biomédico la capacidad de realizar investigación científica en el área de Biología de Sistemas con la finalidad de dirigir y participar en equipos de trabajo interdisciplinarios en contextos nacionales e internacionales, así como de proporcionar soluciones informáticas para resolver problemas en el campo de la Ingeniería Biomédica con ética profesional.

En el contexto de sistemas dinámicos que describen sistemas biológicos o fisiológicos, el modelizado in silico es una extensión lógica de la experimentación in vitro controlada, es el resultado natural del gran aumento de la potencia computacional disponible a un costo que disminuye continuamente, combinando las ventajas de la experimentación in vivo e in vitro, sin someterse a las consideraciones éticas y la falta de control asociadas con los experimentos in vivo. A diferencia de los experimentos in vitro, que existen de forma aislada, los modelos in silico permiten incluir un conjunto prácticamente ilimitado de variables y parámetros, lo que hace que los resultados sean más aplicables en problemas del mundo real. La experimentación in silico ha dado lugar al paradigma denominado como "gemelos digitales" (en inglés digital twins); en esencia, los gemelos digitales son una réplica o representación digital de un proceso o sistema del mundo real, donde por replica se refiere a un modelo computacional desarrollado con base en datos experimentales y características especiales que le permiten conectar lo físico con lo virtual con el propósito de mejorar el rendimiento de un sistema, detectar y prevenir fallas, y realizar predicciones sobre su respuesta ante diferentes estímulos o escenarios de operación; una definición más formal establece que: un gemelo digital es un conjunto de modelos adaptativos que emulan el comportamiento de un sistema físico en un sistema virtual obteniendo datos en tiempo real para actualizarse a lo largo de su ciclo de vida; replica al sistema físico para predecir fallas y oportunidades de cambio, prescribir acciones en tiempo real para optimizar y/o mitigar eventos inesperados observando y evaluando el perfil operativo del sistema. En el campo particular de la Biología de Sistemas, un gemelo digital se presenta como un algoritmo o conjunto de algoritmos computacionales desarrollados con base en modelos mecanicistas de un organismo vivo, esto con el objetivo de emular su fisiología para ilustrar su dinámica en el corto y en el largo plazo, así como predecir su respuesta a diferentes estímulos endógenos y exógenos.

## Objetivo
Analizar la dinámica de un modelo matemático basado en ecuaciones diferenciales ordinarias (EDO) no lineales que describe la cinética enzimática del metabolismo celular, con el fin de determinar la viabilidad biológica del sistema, sus estados de reposo y su estabilidad local.

## Descripción del sistema
El metabolismo celular representa la red compleja de reacciones bioquímicas que permiten a la célula transformar nutrientes en energía y componentes estructurales. En este proyecto, el proceso se centra en la cinética enzimática, donde una enzima facilita la conversión de un sustrato en un producto final indispensable para las funciones celulares. El modelo matemático describe la interacción entre tres variables de estado principales:
 
- **x(t):** Concentración del complejo Enzima-Sustrato (mM).
- **y(t):** Concentración del Producto Final (mM).
- **z(t):** Concentración del Sustrato disponible (mM).
El sistema se formula mediante las siguientes tres EDOs no lineales de primer orden:
 
$$
\begin{aligned}
\dot{x} &= axz - bx \\
\dot{y} &= cyz - dy \\
\dot{z} &= -exyz
\end{aligned}
$$

donde los parámetros del sistema definen la cinética de las interacciones metabólicas. En términos biológicos, *a* representa la afinidad y tasa de formación del complejo enzima-sustrato (x), mientras que *b* mide la velocidad de su disociación o pérdida. Por otro lado, *c* indica la eficiencia con la que el sustrato se transforma en el producto final (y), y *d* es la tasa de depuración o consumo de dicho producto. Finalmente, el parámetro *e* cuantifica el agotamiento constante del sustrato (z) derivado de la actividad conjunta del sistema.
<p align="center">
  <img src="https://github.com/user-attachments/assets/640fa24f-ab11-402c-9547-0de24c2fa18d" alt="Metabolismo celular" width="450" />
</p>
A través de la experimentación *in silico*, se busca predecir el comportamiento del biorreactor ante perturbaciones exógenas (inyección de sustrato) y analizar las condiciones que garantizan la estabilidad del metabolismo.
 
Palabras clave: Cinética Enzimática; Sustrato; Condiciones de Estabilidad; Enzima; Puntos de equilibrio.
 
## Actividades a realizar
1. Procesamiento y normalización de datos experimentales asociados al metabolismo celular mediante suavizado gaussiano (`smoothdata`) y cálculo de bioestadísticos: Error estándar, margen de error, intervalos de confianza del 95%, valor P, coeficiente de determinación (R²), suma residual de cuadrados (RSS) y Criterio de Información de Akaike (AIC).
2. Aplicación de regresión simbólica mediante el software Eureqa para la deducción y obtención de las ecuaciones diferenciales del modelo matemático no lineal, y ajuste de parámetros mediante la función `fitnlm` de MATLAB por mínimos cuadrados.
3. Cálculo analítico y numérico de los tres puntos de equilibrio del sistema:
	- eq1: (x\*, y\*, z\*) = (1, 0, b/a) — Inestable
	- eq2: (x\*, y\*, z\*) = (0, 1, d/c) — Caso marginal
	- eq3: (x\*, y\*, z\*) = (0, 0, 0) — Caso marginal
4. Obtención de la Matriz Jacobiana y evaluación de los valores propios (eigenvalores) para determinar las condiciones de estabilidad local de cada punto de equilibrio.
5. Construcción del diagrama de bloques en Simulink para integrar las ecuaciones diferenciales del sistema en lazo cerrado, empleando el solver `ode23t` con paso máximo de 1E-3.
6. Implementación de una señal de control externa (tipo Step / Pulse Generator) para simular la inyección y perturbación del sustrato (U) en el biorreactor.
7. Desarrollo de funciones especializadas en MATLAB para la automatización, simulación y diseño de gráficas comparativas entre el modelo optimizado y los datos experimentales normalizados.
8. Diseñar un diagrama biológico sobre la dinámica del sistema y la interacción entre sus variables con las figuras de https://bioart.niaid.nih.gov/ o https://www.biorender.com/.
## Lista de archivos incluidos en el repositorio
1. Cuaderno computacional de MATLAB [.mlx].
2. Modelo de Simulink [.slx].
3. Imágenes de las simulaciones [.pdf].
4. Análisis matemático [.pdf].
5. Diagrama biológico del sistema [.png].
## Referencias
\[1] P. A. Valle, Syllabus para Gemelos Digitales, Tecnológico Nacional de México / Instituto Tecnológico de Tijuana, Tijuana, B.C., México, 2025. Permalink: https://biomath.xyz/course/
 

 
