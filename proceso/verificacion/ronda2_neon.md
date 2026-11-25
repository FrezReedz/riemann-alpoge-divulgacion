Total: 64 afirmaciones | CONFIRMADO 46 | IMPRECISO 13 | FALSO 0 | NO EN EL PAPER 5

## IMPRECISO (13)

### 1. Presentación conjunta frente a hallazgo conjunto (línea 3)
- **Frase exacta del artículo:** «En noviembre de 2026, el matemático Levent Alpöge y el modelo de inteligencia artificial Claude presentaron una demostración de la hipótesis de Riemann»
- **Cita literal del paper:** «On November 20, 2026, Levent Alpöge announced a proof of the Riemann hypothesis that he and Claude had found together. He released the proof in Lean.» (`paper.txt`, L13-14); «The proof is due to Levent Alpöge and Claude. On November 20, 2026, Alpöge released a four-page note [2] together with a proof of Theorem 1.1 formalized in Lean [23] on top of Mathlib [73]» (`paper.txt`, L289-291).
- **Explicación breve:** El paper atribuye el hallazgo a ambos («found together», «due to Levent Alpöge and Claude»), pero señala que quien la anunció y publicó fue Alpöge, no ambos conjuntamente.
- **Redacción corregida:** «En noviembre de 2026, el matemático Levent Alpöge anunció una demostración de la hipótesis de Riemann que había encontrado junto con el modelo de inteligencia artificial Claude.»

### 2. «Traduce de nuevo» frente a reconstrucción matemática (línea 3)
- **Frase exacta del artículo:** «El artículo de Jimmie Adriazola la traduce de nuevo a matemáticas legibles por personas.»
- **Cita literal del paper:** «This paper reconstructs in conventional mathematics the proof of the following theorem.» (`paper.txt`, L282); «and a readable proof cannot arise by translating them one at a time. We began at the formal theorem riemannHypothesis, traced its dependencies backward, and identified the mathematical statements on which it depends. Whenever a region of the development implemented a recognizable argument, we stated and proved that argument at its natural mathematical level, and whenever the route reached an established theorem of the literature, we cited that theorem and did not use the formal development as its justification.» (`paper.txt`, L409-414).
- **Explicación breve:** Doble distorsión: Adriazola subraya que no traduce el código declaración por declaración, sino que reconstruye el argumento en matemáticas convencionales citando la literatura; además, «de nuevo» sugiere erróneamente que existía una prueba legible previa convertida después a Lean.
- **Redacción corregida:** «El artículo de Jimmie Adriazola la reconstruye en el lenguaje convencional de las matemáticas para que las personas puedan leerla y comprobarla.»

### 3. Omisión de los ceros no triviales y de la banda crítica (líneas 13 y 15)
- **Frase exacta del artículo:** «Si todos esos ceros están colocados exactamente sobre una línea concreta, llamada **línea crítica**, las oscilaciones son las mínimas posibles y los primos se portan tan bien como pueden.» (L13) / «La hipótesis de Riemann afirma que ningún cero se sale de la línea.» (L15)
- **Cita literal del paper:** «A quantitative form of Landau's theorem on Mellin transforms reduces the zero-free half-plane Re s > 1/2 for Dirichlet L-functions» (`paper.txt`, L17-18); «Theorem 1.1. For every primitive Dirichlet character [χ] the function L(s, [χ]) does not vanish in the half-plane Re s > 1/2. In particular the Riemann zeta function does not vanish in Re s > 1/2.» (`paper.txt`, L284-287, donde la extracción de texto omitió el símbolo del carácter y la barra de fracción); «each zero of [ζ] in the critical strip» (`paper.txt`, L321); «A zero of L(s, [χ]) means a zero in the strip 0 < Re s < 1.» (`paper.txt`, L1221-1223).
- **Explicación breve:** Simplificación engañosa: la función zeta tiene ceros triviales fuera de la línea crítica. La hipótesis solo afecta a los ceros no triviales situados en la banda crítica, y el paper formula el Teorema 1.1 directamente como ausencia de ceros a la derecha de esa línea (lo que, por simetría dentro de la banda crítica, los sitúa sobre ella).
- **Redacción corregida:** «Si todos los ceros relevantes —los situados dentro de la llamada banda crítica— están colocados exactamente sobre una línea central, las oscilaciones son las mínimas posibles y los primos se portan tan bien como pueden. La hipótesis de Riemann afirma que ningún cero de esa banda se sale de la línea; en el enunciado que demuestra el artículo, que la función nunca se anula a la derecha de ella.»

### 4. Atribución a Alpöge de la «cadena de montaje» en el título del Acto II (línea 43)
- **Frase exacta del artículo:** «## Acto II: la cadena de montaje de Alpöge y el truco de los primos inertes»
- **Cita literal del paper:** «The note credits Claude with the proposal that a chain of theta lifts of length about x should play the role of multiplicity, and with the arguments on automorphic forms on groups of higher rank.» (`paper.txt`, L302-304; en el PDF original figura la raíz cuadrada de la escala, cuyo símbolo se perdió al extraer el texto).
- **Explicación breve:** En el artículo divulgativo la «cadena de montaje» representa la cadena de levantamientos theta (L63-65), cuya propuesta el paper atribuye expresamente a Claude, no a Alpöge. Atribuírsela solo a Alpöge en el título contradice los créditos de la Sección 1 y la propia sección de autoría del artículo.
- **Redacción corregida:** «## Acto II: la cadena de montaje de Alpöge y Claude y el truco de los primos inertes»

### 5. Carácter condicional de la Parte II y afirmación «donde nunca había funcionado» (línea 45)
- **Frase exacta del artículo:** «La Parte II, la más larga, demuestra el Teorema A trasladando una idea antigua a un mundo donde nunca había funcionado.»
- **Cita literal del paper:** «Part II proves Theorem A from the hypotheses that Subsection 18.7 lists.» (`paper.txt`, L2912); «The final implication to Theorem 1.1 remains conditional on the hypotheses above.» (`paper.txt`, L18192-18193); «the recognition that an auxiliary-function argument of Siegel, which appeared in mathematical work by researchers at OpenAI, is Stepanov's method with multiplicity one.» (`paper.txt`, L299-300).
- **Explicación breve:** Dos imprecisiones: primero, en el artículo de Adriazola la Parte II no demuestra el Teorema A de forma incondicional, sino a partir de las hipótesis pendientes recogidas en la Subsección 18.7; segundo, el paper no afirma que el enfoque de Stepanov «nunca hubiera funcionado» en cuerpos de números (de hecho, señala que un argumento de Siegel ya equivalía a aplicarlo con multiplicidad uno).
- **Redacción corregida:** «La Parte II, la más larga, demuestra el Teorema A a partir de las piezas pendientes que el autor detalla al final, llevando la idea de Stepanov a un terreno donde hasta entonces solo se había visto en su versión más básica.»

### 6. Generalización excesiva a «los argumentos previos» sobre Siegel (línea 53)
- **Frase exacta del artículo:** «Llevar esa idea a la aritmética de los números ordinarios (en concreto, a lo que los matemáticos llaman *cuerpos de números*) con multiplicidad alta había resultado esquivo: los argumentos previos con función auxiliar, como uno de Siegel, equivalían solo a multiplicidad uno.»
- **Cita literal del paper:** «It credits Alpöge with the plan and with the recognition that an auxiliary-function argument of Siegel, which appeared in mathematical work by researchers at OpenAI, is Stepanov's method with multiplicity one.» (`paper.txt`, L294, L299-300).
- **Explicación breve:** El paper solo menciona un argumento concreto de Siegel con función auxiliar aparecido en trabajo de investigadores de OpenAI. No sostiene que todos «los argumentos previos» en plural equivalieran solo a multiplicidad uno ni relata que el traslado con multiplicidad alta «hubiera resultado esquivo».
- **Redacción corregida:** «Llevar esa idea a la aritmética de los números ordinarios (lo que los matemáticos llaman *cuerpos de números*) con multiplicidad alta era el gran paso: un argumento de Siegel con función auxiliar, aparecido en trabajo de investigadores de OpenAI, equivalía solo a multiplicidad uno.»

### 7. Atribución en solitario a Alpöge y omisión de «inerte» en la regla de divisibilidad (línea 71)
- **Frase exacta del artículo:** «En los cuerpos de números, Alpöge cambia "anularse muchas veces" por "**ser divisible muchas veces por un primo**".»
- **Cita literal del paper:** «Alpöge adapts Stepanov's point-counting method over finite fields. The divisibility that successive theta lifts gain at inert primes plays the role of vanishing to high order at rational points.» (`paper.txt`, L19-21); «It credits Alpöge with the plan and with the recognition that an auxiliary-function argument of Siegel... is Stepanov's method with multiplicity one... The note credits Claude with the proposal that a chain of theta lifts of length about x should play the role of multiplicity» (`paper.txt`, L294, L299-304).
- **Explicación breve:** Aunque el resumen del paper usa «Alpöge» como abreviatura general, los créditos detallados de la Sección 1 no atribuyen en exclusiva a Alpöge la formulación mediante divisibilidad (como el propio artículo reconoce luego en la línea 99). Además, la frase omite que se trata de primos inertes (aunque el párrafo siguiente lo aclara).
- **Redacción corregida:** «En los cuerpos de números, la demostración cambia "anularse muchas veces" por "**ser divisible muchas veces por un primo inerte**".»

### 8. Longitud «igual» frente a «cercana» a la raíz cuadrada (línea 101)
- **Frase exacta del artículo:** «**2. Encadenar una torre de levantamientos de longitud igual a la raíz cuadrada de la escala.**»
- **Cita literal del paper:** «For a sum of length X, a chain of about X theta lifts balances the errors in that inequality» (`paper.txt`, L22-23); «The note credits Claude with the proposal that a chain of theta lifts of length about x should play the role of multiplicity» (`paper.txt`, L302-304); «There are even integers m and k» (`paper.txt`, L2422) elegidos en un rango ligeramente inferior a la raíz cuadrada (`paper.txt`, L1129, L2424, L2449-2450).
- **Explicación breve:** El paper siempre habla de una longitud *aproximadamente* igual («about») a la raíz cuadrada de la escala, y en la construcción formal la longitud es un entero par cercano a esa raíz (incluso ligeramente menor para escalas grandes), no estrictamente igual. La propia línea 102 corrige el matiz usando «cercana».
- **Redacción corregida:** «**2. Encadenar una torre de levantamientos de longitud cercana a la raíz cuadrada de la escala.**»

### 9. Atribución al humano de la observación de la multiplicidad dos (línea 102)
- **Frase exacta del artículo:** «La semilla fue la observación humana de la multiplicidad dos; la cadena, una propuesta de la IA.»
- **Cita literal del paper:** «Alpöge describes the turning point as the appearance of multiplicity two in an automorphic determinant on O(2, n), which suggested that further theta lifts could increase the multiplicity. The note credits Claude with the proposal that a chain of theta lifts of length about x should play the role of multiplicity, and with the arguments on automorphic forms on groups of higher rank.» (`paper.txt`, L300-304).
- **Explicación breve:** El paper dice únicamente que Alpöge *describe* como punto de inflexión la aparición de la multiplicidad dos en un determinante automórfico; en ningún lugar afirma que descubrir u observar esa multiplicidad dos fuera una aportación humana (y no conjunta o de la IA).
- **Redacción corregida:** «El punto de inflexión que relata Alpöge fue la aparición de la multiplicidad dos; la cadena de levantamientos, una propuesta atribuida a la IA.»

### 10. Atribución en el resumen de créditos de «la pista de la multiplicidad dos» a Alpöge (línea 107)
- **Frase exacta del artículo:** «En resumen, según la nota: Alpöge aportó el plan, el reconocimiento del patrón de Stepanov y la pista de la multiplicidad dos; Claude, la idea de la cadena de longitud raíz cuadrada y los argumentos automórficos de rango superior.»
- **Cita literal del paper:** «It credits Alpöge with the plan and with the recognition that an auxiliary-function argument of Siegel, which appeared in mathematical work by researchers at OpenAI, is Stepanov's method with multiplicity one. Alpöge describes the turning point as the appearance of multiplicity two in an automorphic determinant on O(2, n), which suggested that further theta lifts could increase the multiplicity. The note credits Claude with the proposal that a chain of theta lifts of length about x should play the role of multiplicity, and with the arguments on automorphic forms on groups of higher rank.» (`paper.txt`, L294, L299-304).
- **Explicación breve:** El paper solo dice que la nota atribuye a Alpöge dos cosas: el plan y el reconocimiento sobre el argumento de Siegel y Stepanov. No afirma que la nota le atribuya haber aportado «la pista de la multiplicidad dos», sino solo que Alpöge describe ese hallazgo como el punto de inflexión. Además, vuelve a omitir que la longitud de la cadena es *cercana* a la raíz cuadrada.
- **Redacción corregida:** «En resumen, según la nota: Alpöge aportó el plan y el reconocimiento del patrón de Stepanov, y señala como punto de inflexión la aparición de la multiplicidad dos; Claude aportó la propuesta de la cadena de longitud cercana a la raíz cuadrada y los argumentos automórficos de rango superior.»

### 11. Alcance del cotejo pendiente en teoremas publicados (línea 131)
- **Frase exacta del artículo:** «5. **Las piezas prestadas.** Hay teoremas ya publicados por otros autores que aún hay que cotejar línea por línea para confirmar que sus hipótesis encajan exactamente con el uso que se les da.»
- **Cita literal del paper:** «A few of the cited published theorems have not yet been compared line by line with their sources, and Subsection 18.7 lists them as well.» (`paper.txt`, L310-311); «and a separate comparison of each cited theorem with its published statement checks hypotheses, normalizations and quantifiers.» (`paper.txt`, L423-424); «The Rallis inner product identity still requires the comparison of the Petersson norm with the operators of Proposition 15.52. The mass and formal-degree formulas must use the measures of the dimension estimate.» (`paper.txt`, L18190-18192).
- **Explicación breve:** El artículo omite que se trata solo de *unos pocos* («A few») de los teoremas citados y reduce el cotejo únicamente a las hipótesis, cuando el paper indica que revisa hipótesis, normalizaciones y cuantificadores —y de hecho los dos cabos explícitamente abiertos en la Subsección 18.7 son comparaciones de normas y medidas—.
- **Redacción corregida:** «5. **Las piezas prestadas.** Quedan unos pocos teoremas ya publicados por otros autores por cotejar línea por línea con sus fuentes originales para confirmar que sus hipótesis, convenciones de escala, medidas y alcance encajan exactamente con el uso que se les da.»

### 12. «Cota sobre la conjetura de Vandiver» frente a cota en dirección a ella (línea 137)
- **Frase exacta del artículo:** «Uno de los ingredientes implica una cota sobre un viejo problema, la conjetura de Vandiver, **más fuerte que las publicadas**.»
- **Cita literal del paper:** «The bound for Tate-Shafarevich groups on windows of scales, Hypothesis 17.11, implies a bound in the direction of Vandiver's conjecture that is stronger than the published bounds of Soulé [68] and of de la Torre Durán [22] (Proposition 17.22).» (`paper.txt`, L426-429); «The Selmer bound on windows implies a bound in the direction of Vandiver's conjecture that is stronger than the published bounds of Soulé and of de la Torre Durán. Alpöge's announcement [2] describes this bound as a weakening of Vandiver's conjecture.» (`paper.txt`, L16558-16561).
- **Explicación breve:** La conjetura de Vandiver es una afirmación exacta de anulación, no una desigualdad numérica; el paper precisa cuidadosamente que el ingrediente implica una cota *en dirección a* (o un debilitamiento de) dicha conjetura, más fuerte que las cotas publicadas. Además, el calificativo «viejo problema» es contexto externo ausente en el paper.
- **Redacción corregida:** «Uno de los ingredientes implica una cota en dirección a la conjetura de Vandiver —una versión debilitada de este problema clásico— **más fuerte que las publicadas hasta ahora**.»

### 13. «Esboza» frente a prueba completa pendiente de verificación humana independiente (línea 137)
- **Frase exacta del artículo:** «Adriazola esboza además una prueba alternativa más corta de una pieza técnica, aún no verificada ni formalizada.»
- **Cita literal del paper:** «In the course of the reconstruction, we found what appears to be a shorter proof of a uniform bound in Galois cohomology (§17.4.3). That shortcut gives us reason to think the proof as a whole may admit a simpler argument.» (`paper.txt`, L27-29); «The following alternative proof awaits independent human verification and has not been formalized in Lean.» (`paper.txt`, L16749-16750).
- **Explicación breve:** En la Subsección 17.4.3 Adriazola no se limita a «esbozar» un argumento, sino que redacta una demostración alternativa completa paso a paso de una cota uniforme en cohomología de Galois, y precisa que espera verificación *humana independiente* además de no estar formalizada en Lean.
- **Redacción corregida:** «Adriazola presenta además una demostración alternativa más corta de una pieza técnica del argumento, que aún espera verificación humana independiente y no ha sido formalizada en Lean.»

## FALSO (0)

Ninguna afirmación contradice de forma directa y frontal el texto de `paper.txt`.

## NO EN EL PAPER (5)

### 1. «El problema abierto más famoso de las matemáticas» (línea 3)
- **Frase exacta del artículo:** «, el problema abierto más famoso de las matemáticas.»
- **Cita literal del paper:** No aparece en `paper.txt`.
- **Explicación breve:** Es una valoración divulgativa habitual y ampliamente compartida, pero no figura en el artículo de Adriazola.
- **Redacción corregida:** «una demostración de la hipótesis de Riemann, ampliamente considerada el gran problema abierto de la teoría de números.»

### 2. Bernhard Riemann en 1859 y los 167 años (líneas 7, 9 y 15)
- **Frase exacta del artículo:** «## El muro de 167 años» (L7) / «En 1859, Bernhard Riemann publicó un artículo breve sobre los números primos (los que solo se dividen por sí mismos y por uno: 2, 3, 5, 7, 11…) y dejó escrita, casi de pasada, una sospecha que nadie ha podido demostrar desde entonces.» (L9) / «Durante 167 años ha sido el gran muro de las matemáticas.» (L15)
- **Cita literal del paper:** No aparece en `paper.txt` (ni el año 1859, ni el lapso de 167 años, ni la memoria original de Riemann figuran en el texto ni en la bibliografía, `paper.txt`, L18195-18454).
- **Explicación breve:** Conocimiento general correcto (Riemann publicó su memoria en 1859 y hasta noviembre de 2026 pasaron 167 años), pero ausente en el paper. Como detalle técnico menor, la definición divulgativa de primo omite «mayores que uno», aunque los ejemplos lo aclaran.
- **Redacción corregida:** «Como contexto histórico general (ajeno al artículo técnico): en 1859, Bernhard Riemann publicó un trabajo breve sobre los números primos —los enteros mayores que uno que solo se dividen por uno y por sí mismos— y dejó escrita, casi de pasada, una conjetura que permaneció abierta durante 167 años.»

### 3. Descubrimiento histórico de Riemann sobre la función zeta (línea 13)
- **Frase exacta del artículo:** «Riemann descubrió que esa pregunta tiene una respuesta exacta escondida en un objeto que hoy llamamos **función zeta**.»
- **Cita literal del paper:** No aparece en `paper.txt` (el paper usa la función zeta y la fórmula explícita citando el tratado de Davenport [21] en L517 y L1248, sin relato histórico sobre Riemann).
- **Explicación breve:** Conocimiento general correcto sobre el origen histórico de la relación entre los primos y la función zeta, pero el paper no lo menciona.
- **Redacción corregida:** «En el trasfondo clásico del problema, la respuesta a cuánto pueden desviarse los primos de su pauta está codificada en un objeto llamado **función zeta**.»

### 4. Comprobación computacional de billones de ceros (línea 15)
- **Frase exacta del artículo:** «Los ordenadores han comprobado billones de ceros y todos están en su sitio, pero eso no demuestra nada cuando hay infinitos.»
- **Cita literal del paper:** No aparece en `paper.txt` (la única comprobación computacional mencionada en el paper se refiere a la conjetura de Vandiver, `paper.txt`, L16370: «the verification of Vandiver's conjecture for l < 231», donde «231» procede de «2^31» en el PDF).
- **Explicación breve:** Conocimiento general correcto (en escala larga española, billones equivale a millones de millones, y los ordenadores han verificado varios billones de ceros no triviales), pero ausente en el paper.
- **Redacción corregida:** «Aunque el artículo no entra en cálculos numéricos, es bien sabido que los ordenadores han comprobado ya varios billones de ceros no triviales sobre la línea, lo cual no basta como demostración cuando existen infinitos.»

### 5. Elegancia y simplificación de Bombieri al método de Stepanov (línea 49)
- **Frase exacta del artículo:** «Una de las demostraciones más elegantes, debida a Stepanov y simplificada después por Bombieri, se basa en un **pulso entre dos errores opuestos**.»
- **Cita literal del paper:** No aparecen los calificativos «más elegantes» ni «simplificada» en `paper.txt`; el texto solo menciona «Bombieri's form of Stepanov's argument [10]» (`paper.txt`, L355) y «Stepanov's proof of the Riemann hypothesis for curves over finite fields [70], in the form of Bombieri [10]» (`paper.txt`, L823-825).
- **Explicación breve:** Que Bombieri simplificó y generalizó la prueba de Stepanov es conocimiento histórico general correcto (y «más elegantes» es una valoración divulgativa), pero el paper solo se refiere a la versión o forma de Bombieri sin calificarla así.
- **Redacción corregida:** «Una de esas demostraciones, debida a Stepanov y formulada después en la versión de Bombieri, se basa en un **pulso entre dos errores opuestos**.»
