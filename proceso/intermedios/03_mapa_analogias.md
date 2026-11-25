# Mapa de analogías: la demostración de Alpöge y Claude

Síntesis fiel a *The Alpöge Proof of the Riemann Hypothesis* (Jimmie Adriazola, noviembre de 2026), reconstrucción convencional en dieciocho secciones de la prueba formal de Levent Alpöge y Claude para la hipótesis de Riemann y su generalización a caracteres de Dirichlet primitivos (Teorema 1.1), dividida en reducción al Teorema A (Parte I) y demostración automórfica (Parte II).

## 1. Escenario: el acueducto, las esclusas y el puente de contrapesos

Imagina un acueducto subterráneo interminable sin fisuras permitidas más allá de su eje central de seguridad: cualquier grieta así agitaría el caudal acumulado. Como es inviable abrir toda la galería para medir subidas y bajadas en cada metro, se instalan solo topes de techo en pocas cámaras aisladas aguas abajo tras decantar corrientes cruzadas hacia empujes positivos. Allí el exceso alimenta esclusas en serie cada vez más anchas que empujan desde abajo contra un puente de contrapesos con tirantes redundantes: ciertos sedimentos densos accionan turbinas internas en cada esclusa y multiplican la presión sin fugas; con tantas esclusas como la raíz cuadrada del tramo, cualquier fisura prohibida levantaría el puente.

## 2. Los cinco pilares de la demostración

### (1) Ceros de la función zeta y la línea crítica un medio

- **En el artículo:** Descartar ceros de la función zeta y de las funciones L de caracteres de Dirichlet primitivos con parte real mayor que un medio suele exigir cotas bilaterales sobre sumas suavizadas de primos en toda escala y un puente hacia retículos y levantamientos.
- **En la metáfora:** Un medio es el eje de seguridad del acueducto; un cero más allá sería una fisura profunda que altera el caudal acumulado y obligaría a vigilar crecidas y bajadas continuamente.
- **Límite de la metáfora:** Una grieta física mueve agua continua en un tubo; los ceros habitan el plano complejo, rigen sumas discretas de primos y abarcan infinitas funciones L.

### (2) Reducción por ventanas de Landau

- **En el artículo:** El teorema cuantitativo de Landau (transformadas de Mellin de funciones de un solo signo) exige solo una cota superior unilateral de orden raíz cuadrada en ventanas dispersas: la identidad del exceso la liga a primos inertes, dos promedios fijan pesos positivos en un punto y dos primos auxiliares en media cuadrática dominan los caracteres restantes.
- **En la metáfora:** Basta poner topes de techo en pocas cámaras distantes aguas abajo tras decantadores y dos compuertas auxiliares que dejan solo empujes positivos.
- **Límite de la metáfora:** Un remolino hidráulico podría disiparse entre cámaras; la rigidez analítica de funciones de un solo signo impide que un cero escape siempre a las ventanas.

### (3) Método de Stepanov (equilibrar dos errores opuestos)

- **En el artículo:** Sin Riemann-Roch geométrico sobre cuerpos de números, traduce el pulso de ceros frente a polos de Stepanov-Bombieri a siete desigualdades entre pendientes de retículos hermíticos y alturas de períodos: opone el exceso en primos inertes al techo global y pasa de pendiente maximal a media mediante el Teorema del Marco y series de Poincaré de Bessel casi ortogonales.
- **En la metáfora:** Enfrenta la prensa del exceso a un puente de contrapesos con siete márgenes y tirantes redundantes casi perpendiculares para que mande la resistencia media y no la viga más débil.
- **Límite de la metáfora:** Un puente suma cargas mecánicas; aquí se comparan pendientes aritméticas mediante filtraciones de Harder-Narasimhan y períodos complejos.

### (4) Cadena de levantamientos theta y primos inertes como amplificadores

- **En el artículo:** Encadena levantamientos entre formas automórficas de grupos unitarios de rango creciente con núcleos theta sobre una curva elíptica con multiplicación compleja: en primos inertes, el grupo formal de altura dos y Frobenius factorizan el núcleo e imponen divisibilidad por potencias del primo; componer la cadena suma pendiente y la no degeneración de Hecke en edificios frena pérdidas de colongitud.
- **En la metáfora:** En esclusas sucesivas más anchas, solo ciertos sedimentos (primos inertes) accionan turbinas de doble cámara y suman presión por etapa, mientras válvulas estancas (Hecke) evitan fugas.
- **Límite de la metáfora:** Las esclusas elevan el mismo fluido en metros físicos; cada levantamiento pasa a un grupo unitario mayor y acumula divisibilidad aritmética.

### (5) Equilibrio final en raíz-de-x pasos

- **En el artículo:** La cadena toma longitud cercana a la raíz cuadrada de la escala: más corta no diluye el techo fijo; más larga dispara pérdidas de rango, nivel y congruencias. Se contienen con covolúmenes uniformes en recubrimientos profundos de Shimura (Hilbert-Samuel en torre y primos buenos), cancelación de primos auxiliares escindidos y cotas de Tate-Shafarevich en ventanas de Selmer, cerrando el Teorema A.
- **En la metáfora:** Pocas esclusas ocultan fisuras finas; demasiadas acumulan rozamiento y holguras. Cimientos uniformes en profundidad y tramos sin vibración (Selmer) equilibran ambos errores cuando las esclusas igualan la raíz cuadrada del tramo.
- **Límite de la metáfora:** El óptimo mecánico sigue curvas continuas; aquí exige rangos enteros, cancelaciones aritméticas exactas y cohomología de Galois.

## 3. Estado de Verificación

### Qué certificó Lean y qué no (Sección 1.3)

El 20 de noviembre de 2026, Alpöge publicó una nota de cuatro páginas y una prueba formal del Teorema 1.1 en Lean sobre Mathlib; el 21 de noviembre de 2026, las comunidades de Lean y Mathlib, respaldadas por Lean FRO y la Mathlib Initiative, certificaron enunciado y prueba formales (y Rubinstein compiló el desarrollo independientemente).

El desarrollo consta de unas 1,07 millones de declaraciones, unas 767.000 en la ruta del teorema final (`riemannHypothesis`). La certificación garantiza que el término en Lean prueba el enunciado formal, pero no da —ni tampoco Adriazola, que no leyó declaración por declaración— una demostración convencional legible por humanos. Adriazola (con Claude Fable 5.2 y Opus 5.5, GPT incluyendo GPT 5.6 Pro, y Kimi K3.1 Pro) rastreó dependencias hacia atrás, redactó los argumentos a su nivel natural y citó teoremas publicados en resultados estándar, sin invocar Lean como autoridad matemática.

Así, la reconstrucción convencional sigue incompleta en dos frentes: enunciados internos sin prueba convencional redactada (aunque demostrados en Lean) y teoremas publicados pendientes de cotejo línea por línea (hipótesis, normalizaciones y cuantificadores). La Sección 1.3 destaca dos hallazgos:

1. La cota de grupos de Tate-Shafarevich en ventanas (Hipótesis 17.11) implica una cota hacia la conjetura de Vandiver más fuerte que las publicadas de Soulé y de la Torre Durán (Proposición 17.22), y una rama usa automorfía residualmente reducible unitaria en tres variables (G3, Subsección 17.4) fuera de Allen-Newton-Thorne y Thorne.
2. La cota uniforme en el nivel para covolúmenes sobre recubrimientos profundos de variedades de Shimura unitarias sale de Hilbert-Samuel aritmético modelo por modelo en una torre más una identidad exacta en primos buenos, sin Hilbert-Samuel uniforme previo (Subsección 15.14.4).

Además, Adriazola esbozó (Subsección 17.4.3) una prueba alternativa más corta de una cota efectiva uniforme en cohomología de Galois, no verificada aún ni formalizada en Lean.

### Hipótesis y cuestiones abiertas en la reconstrucción convencional (Subsección 18.7)

La implicación convencional hacia el Teorema 1.1 sigue condicional a cinco bloques pendientes:

1. **Cadena y cotas de Hecke:** Pruebas convencionales de retículos impares (N2), núcleo normalizado (N3) y factor de marco (N1); cuotas, niveles y sistemas de prueba en los tres motores de no degeneración de Hecke; cota polinomial de pesos base, colongitud en el primo auxiliar (L7) y vínculo con retículos de Weyl.
2. **Períodos y multiplicidades:** Relaciones de balancín, diccionarios de períodos, leyes de Weil en paso doble y racionalidad para Bessel; etiquetas y pre-traza en multiplicidades; expansión del núcleo, filas principal y de bucles, y términos degenerados en casi ortogonalidad.
3. **Alturas y términos locales:** Norma de núcleos, valores theta-nulos con el entero de Weber, conteo de clases, emparejamiento final y norma de Fock, entradas (I1 a I17) y pendiente media uniforme en covolúmenes, estructura en primos buenos y pérdidas en órbitas inertes.
4. **Lugares torcidos y ensamblaje:** Partes más y menos (incluido el primo dos) de Tate-Shafarevich en ventanas, entradas genéricas (G1 a G4), propagación y rigidez en formas de Hilbert (rangos cuatro y dos), y módulo de congruencia torcido con módulos de Wach y series theta integrales.
5. **Entradas publicadas por cotejar:** Gallagher (Teorema 7) y rango de Linnik; Thorner-Zaman con Stark; teorema de de Rham de Berger; signos de saltos de Hodge y fase arquimediana; norma de Petersson en Rallis; y medidas entre masa de Siegel, Harish-Chandra y dimensión.

## 4. Las 3 ideas verdaderamente revolucionarias

Según el resumen y la Sección 1, la novedad decisiva descansa en tres ideas que llevan el método de Stepanov de cuerpos finitos a cuerpos de números:

1. **Traducir el método de Stepanov a cuerpos de números sustituyendo la multiplicidad de ceros por divisibilidad de levantamientos theta en primos inertes.**
   - *Por qué es revolucionaria:* Interpreta el conteo de ceros frente a polos de Stepanov-Bombieri como una desigualdad de pendiente sobre retículos hermíticos, donde la divisibilidad p-ádica de núcleos theta en primos inertes —gobernada por el grupo formal de altura dos con multiplicación compleja— suple la anulación de orden alto en puntos racionales.
   - *Atribución (Alpöge frente a Claude):* Se atribuye con claridad a **Alpöge** (humano) el plan general, reconocer que un argumento previo con función auxiliar de Siegel —en trabajo de investigadores de OpenAI— era Stepanov con multiplicidad uno, y el giro al observar multiplicidad dos en un determinante automórfico ortogonal indefinido, sugiriendo que más levantamientos theta elevarían la multiplicidad. **No se atribuye con claridad** quién diseñó la formulación p-ádica con grupos formales de altura dos ni la traducción por ventanas de Landau.

2. **Encadenar una torre de levantamientos theta de longitud raíz cuadrada de la escala para equilibrar los errores.**
   - *Por qué es revolucionaria:* Como en Stepanov-Bombieri los errores se equilibran cuando la multiplicidad iguala la raíz cuadrada del cuerpo finito, encadenar levantamientos theta de longitud raíz cuadrada de la escala entre grupos unitarios de rango creciente equilibra los errores y da la cota unilateral de raíz cuadrada exigida por Landau.
   - *Atribución (Alpöge frente a Claude):* La Sección 1 atribuye explícitamente a **Claude** (IA) proponer una cadena de levantamientos theta de longitud raíz cuadrada de la escala como multiplicidad, partiendo de la intuición previa de **Alpöge** (humano) tras hallar multiplicidad dos en el determinante automórfico.

3. **El aparato de formas automórficas en grupos unitarios de rango superior para sostener la desigualdad de pendiente en familia y controlar los errores globales.**
   - *Por qué es revolucionaria:* Impide el colapso por pendiente maximal o errores de rango y nivel mediante una arquitectura inédita en grupos unitarios de rango alto: series de Poincaré de Bessel casi ortogonales con teorema de marcos, no degeneración de Hecke en edificios, covolúmenes uniformes en recubrimientos profundos de Shimura y cotas de Tate-Shafarevich en ventanas.
   - *Atribución (Alpöge frente a Claude):* Se atribuye explícitamente a **Claude** (IA) los argumentos sobre formas automórficas en grupos de rango superior, pero **no se desglosa con claridad** la autoría individual de cada pieza concreta (teorema del marco, no degeneración de Hecke, uniformidad en recubrimientos profundos o automorfía residualmente reducible y Tate-Shafarevich en ventanas).
