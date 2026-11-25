> **Divulgación, no matemáticas de primera mano.** Este artículo resume en español, sin fórmulas, el manuscrito [*The Alpöge Proof of the Riemann Hypothesis*](https://github.com/jimjamzola/RH-Alpoge-Reconstruction/blob/main/manuscript/main.pdf) de **Jimmie Adriazola** ([repositorio](https://github.com/jimjamzola/RH-Alpoge-Reconstruction)) y se basa **únicamente** en ese texto. Quien lo publica no es matemático: aunque se ha verificado frase a frase contra el original en tres rondas, **tómalo con pinzas**, porque puede haber imprecisiones. Cómo se hizo, los prompts, los créditos y una reflexión final: [METODOLOGIA.md](METODOLOGIA.md).

# El acueducto sin grietas: cómo un matemático y una IA derribaron el muro de Riemann

**Resumen ejecutivo.** En noviembre de 2026, el matemático Levent Alpöge anunció una demostración, encontrada junto con el modelo de inteligencia artificial Claude, de la hipótesis de Riemann, el problema abierto más famoso de las matemáticas. La prueba se escribió en Lean, un lenguaje que un ordenador puede comprobar paso a paso, y al día siguiente de publicarse quedaron certificados como correctos tanto su enunciado formal como su demostración. El artículo de Jimmie Adriazola la reconstruye en el lenguaje convencional de las matemáticas, para que las personas puedan leerla y comprobarla. Esa traducción aún no está terminada, y el propio Adriazola señala con precisión qué partes faltan.

---

## El muro de 167 años

En 1859, Bernhard Riemann publicó un artículo breve sobre los números primos (los que solo se dividen por sí mismos y por uno: 2, 3, 5, 7, 11…) y dejó escrita, casi de pasada, una sospecha que nadie ha podido demostrar desde entonces.

Los primos parecen repartirse al azar, pero, vistos de lejos, siguen una pauta bastante regular. La pregunta de fondo es **cuánto pueden apartarse de esa pauta**. ¿Las desviaciones son siempre pequeñas y ordenadas, o puede haber, muy lejos, en números enormes, sorpresas grandes?

Riemann descubrió que esa pregunta tiene una respuesta exacta escondida en un objeto que hoy llamamos **función zeta**. Basta imaginarla como un instrumento que "resuena" con los primos. Ese instrumento tiene unas notas especiales, sus **ceros**, y cada uno de ellos produce una pequeña oscilación en el reparto de los primos. Si todos los ceros relevantes (los llamados "no triviales", que viven en una banda concreta) están colocados exactamente sobre la línea central de esa banda, la **línea crítica**, las oscilaciones son las mínimas posibles y los primos se portan tan bien como pueden. Si un solo cero se saliera de esa línea, en algún lugar muy lejano los primos se desviarían de su pauta mucho más de lo esperado.

La hipótesis de Riemann afirma que ninguno de esos ceros se sale de la línea; en la forma que demuestra el artículo, que la función nunca se anula a la derecha de ella. Los ordenadores han comprobado billones de ceros y todos están en su sitio, pero eso no demuestra nada cuando hay infinitos. Durante 167 años ha sido el gran muro de las matemáticas.

La demostración cubre además a las "primas" de la función zeta, las funciones L de Dirichlet, que hacen el mismo papel para los primos repartidos en clases, por ejemplo los que terminan en 1, 3, 7 o 9.

### La metáfora que nos acompañará

Imaginemos un **acueducto subterráneo infinito** con un eje de seguridad central, la línea crítica. La hipótesis dice que todas las grietas, los ceros, están sobre ese eje; una sola desplazada haría que el caudal, el reparto de los primos, se descontrolara en algún tramo lejano. Como la galería no se acaba nunca, hay que demostrar que **no puede haber** grietas fuera del eje sin ir a buscarlas una por una.

---

## Acto I: cambiar una pregunta imposible por "ventanas" de primos

La Parte I del artículo, mucho más breve que la segunda, no ataca el problema de frente. Lo reformula en otro que sí se deja atacar.

**El obstáculo.** Para descartar una grieta fuera del eje, lo habitual sería controlar el caudal en las dos direcciones: demostrar que nunca sube demasiado y que nunca baja demasiado, en todas las escalas a la vez. Es como tener que vigilar crecidas y sequías en cada metro de una galería infinita.

**El truco: las ventanas de Landau.** Edmund Landau demostró hace más de un siglo un principio de rigidez para cantidades de un solo signo. Alpöge usa una versión cuantitativa: basta con ponerle al caudal **un techo**, sin necesidad de suelo, porque lo que queda por debajo del techo nunca cambia de signo. Así se ahorra la mitad del trabajo. Y ni siquiera hace falta poner el techo en todas partes. En el acueducto, en lugar de medidores de crecida y de sequía por toda la galería, basta con instalar **topes de techo en una sucesión de cámaras espaciadas**, las "ventanas", que se extienda tan lejos como se quiera. Si el agua nunca golpea esos topes, la rigidez del sistema garantiza que no hay grietas fuera del eje.

Hay un precio que pagar. El argumento trata a la vez la función zeta y sus "primas", y sus señales podrían cancelarse entre sí como corrientes cruzadas. Aquí entra la contabilidad de la Parte I:

- Una **identidad del exceso** relaciona lo que sube por encima de lo esperado con un tipo especial de primos, los **primos inertes**. Conviene explicarlo bien porque serán protagonistas. Cuando los números enteros se amplían a un sistema aritmético más rico, como los enteros a los que se añade la raíz cuadrada de un número negativo, algunos primos se descomponen en factores más pequeños y otros se mantienen enteros, sin partirse. Estos últimos son los "inertes": atraviesan la ampliación intactos.
- Dos promedios bien escogidos concentran todo en **un solo punto** con pesos positivos, que actúan como decantadores: hacen que las señales de los distintos ceros se sumen en lugar de cancelarse.
- Dos **primos auxiliares**, como dos compuertas adicionales, elegidos mediante un argumento de promedio, mantienen bajo control en toda la ventana el pequeño grupo de funciones auxiliares que sobreviven al paso anterior, de modo que no estorben.

**Lo que entrega este acto.** Toda la hipótesis de Riemann queda reducida a un único enunciado, que el artículo llama **Teorema A**. Dice, en esencia, que en ventanas tan lejanas como se quiera pueden elegirse los datos de modo que el exceso quede bajo un techo técnico que, una vez normalizado, equivale a una cota del orden de la raíz cuadrada de la escala. Si el Teorema A es cierto, la hipótesis de Riemann también lo es.

---

## Acto II: la cadena de montaje de Alpöge y Claude y el truco de los primos inertes

La Parte II, la más larga, demuestra el Teorema A (a partir de las piezas pendientes que el autor enumera al final) llevando una idea antigua a un terreno donde hasta entonces solo se había visto en su versión más básica.

### Una idea prestada de un universo más pequeño

Existe una versión "en miniatura" de la hipótesis de Riemann, en mundos numéricos finitos donde la aritmética da la vuelta como en un reloj. Allí el problema se resolvió hace décadas. Una de esas demostraciones, debida a Stepanov y reformulada después por Bombieri, se basa en un **pulso entre dos errores opuestos**.

El método de Stepanov consiste en fabricar un objeto auxiliar al que se obliga a "anularse muchas veces", es decir, a tener muchos ceros, en ciertos puntos especiales. El objeto tiene un "presupuesto" limitado de ceros. Por eso, cuantas más veces se le obliga a anularse en cada punto especial, menos puntos caben antes de agotar ese presupuesto, y más bajo queda el tope sobre cuántos puntos puede haber. A cambio, exigir demasiadas anulaciones obliga a fabricar un objeto más complicado, y ese coste crece. Hay, pues, dos errores que tiran en sentidos opuestos. El ajuste perfecto llega cuando la "multiplicidad", el número de veces que el objeto se anula en cada punto, es del orden de la raíz cuadrada del tamaño del mundo. Ahí los dos errores se equilibran y la cota sobre el número de puntos es la mejor posible.

Llevar esa idea a la aritmética de los números ordinarios (en concreto, a lo que los matemáticos llaman *cuerpos de números*) con multiplicidad alta era el gran paso pendiente: un argumento de Siegel con función auxiliar, aparecido en trabajo de investigadores de OpenAI, equivalía solo a multiplicidad uno.

### El puente de contrapesos

En los cuerpos de números, el recuento de ceros frente al presupuesto se convierte en una desigualdad entre "pendientes" de ciertas redes geométricas, integrada en un sistema de **siete desigualdades** que enlazan esas pendientes con "alturas" de ciertas aplicaciones y con contribuciones locales de los primos.

En la metáfora, el pulso de Stepanov pasa a ser un **puente de contrapesos**. Por debajo, la presión del exceso de los primos inertes empuja hacia arriba. Por arriba, el techo global presiona hacia abajo. El puente tiene **siete márgenes de seguridad** y muchos tirantes casi perpendiculares entre sí, lo que en el artículo corresponde a familias de funciones especiales "casi ortogonales". Gracias a esa redundancia, lo que decide si el puente aguanta es **la resistencia media** de toda la estructura y no la viga más débil. Este paso de lo peor a lo promedio, que el artículo consigue con un resultado llamado Teorema del Marco, es lo que impide que el argumento se derrumbe por un único punto frágil.

### Las esclusas: la cadena de levantamientos theta

Falta lo esencial: ¿de dónde sale tanta presión desde abajo? Para eso Alpöge y Claude montan una **cadena de montaje**.

En matemáticas existen unos objetos llamados **formas automórficas**. Son funciones con simetrías extraordinarias que viven sobre espacios geométricos. Unos operadores llamados **levantamientos theta** permiten tomar una de esas formas y "subirla" a un espacio más grande, con más dimensiones, conservando parte de su información. La demostración **encadena muchos de estos levantamientos**, cada uno hacia un espacio de mayor tamaño.

En el acueducto, cada levantamiento es una **esclusa**. El agua pasa de una a la siguiente, cada vez más ancha, y en cada paso gana presión.

### Los primos inertes como amplificadores

Aquí está el truco más fino. En el método original de Stepanov, la fuerza venía de que el objeto auxiliar se anulaba muchas veces. En los cuerpos de números, la demostración cambia "anularse muchas veces" por "**ser divisible muchas veces por un primo inerte**".

Los primos inertes, los que atraviesan la ampliación sin partirse, tienen una propiedad especial en este contexto. Cuando el levantamiento se mira "a través" de uno de ellos, la estructura interna del proceso, ligada a una curva con simetrías muy particulares, obliga al resultado a ser divisible por potencias de ese primo. Cada esclusa añade más divisibilidad.

En la metáfora, los primos inertes son **sedimentos densos** que, al pasar por cada esclusa, accionan una turbina interna y **multiplican la presión** sin que se escape agua. Al encadenar esclusas, esa presión se acumula.

Extraer esa divisibilidad tiene un coste: en cada paso se pierde algo. Un resultado técnico llamado no degeneración de Hecke actúa como **válvula de seguridad**: mantiene esa pérdida acotada y pequeña frente a lo que se gana.

### El equilibrio final: tantas esclusas como la raíz cuadrada

Queda decidir cuántas esclusas poner, y aquí reaparece el equilibrio de Stepanov:

- **Con pocas esclusas**, la presión acumulada no basta para vencer al techo fijo y las grietas finas pasan desapercibidas.
- **Con demasiadas**, se acumulan rozamientos y holguras: pérdidas por el tamaño creciente de los espacios, por la complejidad de cada paso y por pequeñas incompatibilidades aritméticas.

El punto óptimo es **una cadena de longitud cercana a la raíz cuadrada de la escala**, el mismo equilibrio que en el universo finito, ahora trasladado a los cuerpos de números. Para que la cuenta salga, los "cimientos" deben ser uniformes por muy profunda que sea la estructura (controlar, sin que la constante empeore, los "covolúmenes" de ciertas redes de formas automórficas), y ciertos tramos no deben vibrar (acotar unos objetos aritméticos llamados grupos de Tate-Shafarevich).

Con todo ajustado, si existiera una grieta fuera del eje, la presión acumulada **levantaría el puente**, rompiendo el techo del Teorema A. Como el puente no se levanta, no hay grieta.

Un aviso honesto: la imagen muestra la arquitectura del argumento, no su mecánica, que trabaja con divisibilidades exactas y estructuras aritméticas sin equivalente físico.

---

## Las tres ideas verdaderamente revolucionarias (y quién tuvo cada una)

El artículo recoge los créditos que da la propia nota de Alpöge. Es un resumen breve que no detalla quién hizo cada pieza individual.

**1. Llevar el método de Stepanov de los mundos finitos a los cuerpos de números, cambiando "anularse muchas veces" por "ser divisible muchas veces en los primos inertes".**
Esta es la clave conceptual. La nota atribuye a **Alpöge** el plan general y el reconocimiento de que un argumento de Siegel con función auxiliar, que había aparecido en trabajo matemático de investigadores de OpenAI, era en el fondo el método de Stepanov con la multiplicidad mínima, una sola vez. Alpöge describe como punto de inflexión la aparición de una **multiplicidad dos** en un objeto automórfico concreto, que sugería que más levantamientos theta podrían aumentarla. El texto no dice quién diseñó la formulación precisa en términos de divisibilidad ni la traducción a ventanas de Landau.

**2. Encadenar una torre de levantamientos de longitud cercana a la raíz cuadrada de la escala.**
La nota atribuye a **Claude** la propuesta de que una cadena de levantamientos theta de longitud cercana a la raíz cuadrada de la escala hiciera el papel de la multiplicidad, reproduciendo el equilibrio de Stepanov. El punto de inflexión que relata Alpöge fue la aparición de la multiplicidad dos; la cadena, una propuesta atribuida a la IA.

**3. El enorme aparato de formas automórficas en espacios de dimensión alta que hace que la cadena no se desmorone.**
La nota atribuye a **Claude**, en términos generales, "los argumentos sobre formas automórficas en grupos de rango superior", que sostienen buena parte de la maquinaria de la Parte II. No desglosa qué piezas concretas incluye esa atribución.

En resumen, según la nota: Alpöge aportó el plan y el reconocimiento del patrón de Stepanov, y señala como punto de inflexión la multiplicidad dos; Claude, la propuesta de la cadena de longitud cercana a la raíz cuadrada y los argumentos automórficos de rango superior. No es un simple reparto entre visión humana e ingeniería mecánica: una de las ideas centrales vino de la IA.

---

## Letra pequeña y honestidad científica

### Lo que garantiza el ordenador

El 20 de noviembre de 2026, Alpöge publicó una nota de cuatro páginas junto con una prueba completa escrita en **Lean**. Lean es un lenguaje de programación diseñado para que un ordenador compruebe, sin saltarse un paso, que cada deducción se sigue de las anteriores, apoyándose en Mathlib, una gran biblioteca de matemáticas ya verificadas. Al día siguiente, las comunidades de Lean y Mathlib, respaldadas por Lean FRO y la Mathlib Initiative, **certificaron** que el enunciado formal y la prueba eran correctos. Michael Rubinstein compiló el desarrollo por su cuenta de forma independiente.

La escala es enorme: unos **1,07 millones de declaraciones**, de las que unas **767.000** están en la ruta directa hacia el teorema final.

Eso garantiza que el programa demuestra el enunciado formal, pero no que exista una explicación que una persona pueda leer y enseñar. Certeza no es comprensión.

### Lo que todavía falta para los humanos

El artículo de Adriazola intenta precisamente eso: reconstruir la demostración en el lenguaje convencional de las matemáticas. Para hacerlo se ayudó de varios modelos de IA (Claude Fable 5.2 y Opus 5.5, modelos GPT, incluido GPT 5.6 Pro, y Kimi K3.1 Pro). Rastreó las dependencias hacia atrás desde el resultado final y citó teoremas ya publicados. Deliberadamente, **no usa Lean como autoridad**, y reconoce que no leyó el código declaración por declaración.

Su reconstrucción está **incompleta**, y el autor lo dice abiertamente. En la Subsección 18.7 explica que la versión humana de la prueba sigue dependiendo de cinco bloques pendientes:

1. **La cadena y sus válvulas.** Faltan pruebas redactadas de varios pasos de la cadena de levantamientos y del control de pérdidas.
2. **Los tirantes del puente.** Faltan pruebas redactadas de varias identidades de "periodos", del cálculo de multiplicidades y de las estimaciones de las familias casi perpendiculares.
3. **Los cimientos.** Faltan cálculos de alturas, covolúmenes y contribuciones locales de los primos.
4. **Los tramos sin vibración y el ensamblaje.** Faltan los ingredientes profundos de las cotas sobre los grupos de Tate-Shafarevich (incluido un resultado de automorfía que va más allá de los teoremas publicados), las estimaciones en los llamados lugares torcidos y piezas del montaje final.
5. **Las piezas prestadas.** Quedan unos pocos teoremas ya publicados por otros autores por cotejar línea por línea con sus fuentes, para confirmar que sus hipótesis, normalizaciones y alcance encajan exactamente con el uso que se les da.

Los enunciados internos de los cuatro primeros bloques **están demostrados en Lean**; lo que falta es su versión legible para personas. En el quinto, Adriazola cita la literatura en lugar de apoyarse en Lean, y lo que falta es el cotejo manual.

### Hallazgos colaterales

Uno de los ingredientes implica una cota en dirección a la conjetura de Vandiver (una versión debilitada de ese problema clásico) **más fuerte que las publicadas**. Otro consigue controlar de forma uniforme ciertos covolúmenes sin necesitar un teorema general (una versión uniforme del teorema aritmético de Hilbert-Samuel) que no existe publicado. Adriazola presenta además una demostración alternativa más corta de una pieza técnica, que aún espera verificación humana independiente y no está formalizada en Lean.

### En resumen

La máquina dice que el muro ha caído. Los humanos reconstruyen, ladrillo a ladrillo, por qué, y han documentado qué ladrillos faltan. Esa transparencia es quizá la mejor noticia de esta historia.
