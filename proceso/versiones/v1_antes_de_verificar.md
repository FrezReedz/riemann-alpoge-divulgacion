# El acueducto sin grietas: cómo un matemático y una IA derribaron el muro de Riemann

**Resumen ejecutivo.** En noviembre de 2026, el matemático Levent Alpöge y el modelo de inteligencia artificial Claude presentaron una demostración de la hipótesis de Riemann, el problema abierto más famoso de las matemáticas. La prueba se escribió en Lean, un lenguaje que un ordenador puede comprobar paso a paso, y quedó certificada en un solo día. El artículo de Jimmie Adriazola la traduce de nuevo a matemáticas legibles por personas. Esa traducción aún no está terminada, y el propio Adriazola señala con precisión qué partes faltan.

---

## El muro de 167 años

En 1859, Bernhard Riemann publicó un artículo breve sobre los números primos (los que solo se dividen por sí mismos y por uno: 2, 3, 5, 7, 11…) y dejó escrita, casi de pasada, una sospecha que nadie ha podido demostrar desde entonces.

Los primos parecen repartirse al azar, pero, vistos de lejos, siguen una pauta bastante regular. La pregunta de fondo es **cuánto pueden apartarse de esa pauta**. ¿Las desviaciones son siempre pequeñas y ordenadas, o puede haber, muy lejos, en números enormes, sorpresas grandes?

Riemann descubrió que esa pregunta tiene una respuesta exacta escondida en un objeto que hoy llamamos **función zeta**. Basta imaginarla como un instrumento que "resuena" con los primos. Ese instrumento tiene unas notas especiales, sus **ceros**, y cada uno de ellos produce una pequeña oscilación en el reparto de los primos. Si todos los ceros están colocados exactamente sobre una franja concreta, llamada **línea crítica**, las oscilaciones son las mínimas posibles y los primos se portan tan bien como pueden. Si un solo cero se saliera de esa línea, en algún lugar muy lejano los primos se desviarían de su pauta mucho más de lo esperado.

La hipótesis de Riemann afirma que ningún cero se sale de la línea. Los ordenadores han comprobado billones de ceros y todos están en su sitio, pero eso no demuestra nada cuando hay infinitos. Durante 167 años ha sido el gran muro de las matemáticas.

La demostración cubre además a las "primas" de la función zeta, las funciones L de Dirichlet, que hacen el mismo papel para los primos repartidos en clases, por ejemplo los que terminan en 1, 3, 7 o 9.

### La metáfora que nos acompañará

Imaginemos un **acueducto subterráneo infinito** con un eje de seguridad central, la línea crítica. La hipótesis dice que todas las grietas, los ceros, están sobre ese eje; una sola desplazada haría que el caudal, el reparto de los primos, se descontrolara en algún tramo lejano. Como la galería no se acaba nunca, hay que demostrar que **no puede haber** grietas fuera del eje sin ir a buscarlas una por una.

---

## Acto I: cambiar una pregunta imposible por "ventanas" de primos

La primera mitad del trabajo, la Parte I del artículo, no ataca el problema de frente. Lo reformula en otro que sí se deja atacar.

**El obstáculo.** Para descartar una grieta fuera del eje, lo habitual sería controlar el caudal en las dos direcciones: demostrar que nunca sube demasiado y que nunca baja demasiado, en todas las escalas a la vez. Es como tener que vigilar crecidas y sequías en cada metro de una galería infinita.

**El truco: las ventanas de Landau.** Edmund Landau demostró hace más de un siglo un principio de rigidez. Cuando una cantidad tiene siempre el mismo signo, por ejemplo cuando solo puede empujar hacia arriba, basta con ponerle **un techo** para controlarla del todo. No hace falta suelo. Alpöge usa una versión cuantitativa de ese principio y gracias a ella se ahorra la mitad del trabajo. En el acueducto, en lugar de medidores de crecida y de sequía por toda la galería, basta con instalar **topes de techo en unas pocas cámaras aisladas**, separadas entre sí, que son las "ventanas". Si el agua nunca golpea esos topes, la rigidez del sistema garantiza que no hay grietas fuera del eje.

Hay un precio que pagar. Para que funcione, el caudal que llega a las cámaras tiene que empujar **solo hacia arriba**, y en la realidad hay corrientes cruzadas. Aquí entra la contabilidad de la Parte I:

- Una **identidad del exceso** relaciona lo que sube por encima de lo esperado con un tipo especial de primos, los **primos inertes**. Conviene explicarlo bien porque serán protagonistas. Cuando los números se amplían a un sistema más rico, como ocurre al pasar a los números complejos, algunos primos se descomponen en factores más pequeños y otros se mantienen enteros, sin partirse. Estos últimos son los "inertes": atraviesan la ampliación intactos.
- Dos promedios bien escogidos concentran todo en **un solo punto** con pesos positivos, que actúan como decantadores que dejan pasar solo los empujes hacia arriba.
- Dos **primos auxiliares**, como dos compuertas adicionales, se encargan del resto de las "primas" de la función zeta en promedio, de modo que no estorben.

**Lo que entrega este acto.** Toda la hipótesis de Riemann queda reducida a un único enunciado, que el artículo llama **Teorema A**. Dice, en esencia, que en esas ventanas el exceso nunca supera un techo del tamaño de la raíz cuadrada de la escala. Si el Teorema A es cierto, la hipótesis de Riemann también lo es.

---

## Acto II: la cadena de montaje de Alpöge y el truco de los primos inertes

La Parte II, la más larga, demuestra el Teorema A trasladando una idea antigua a un mundo donde nunca había funcionado.

### Una idea prestada de un universo más pequeño

Existe una versión "en miniatura" de la hipótesis de Riemann, en mundos numéricos finitos donde la aritmética da la vuelta como en un reloj. Allí el problema se resolvió hace décadas. Una de las demostraciones más elegantes, debida a Stepanov y simplificada después por Bombieri, se basa en un **pulso entre dos errores opuestos**.

El método de Stepanov consiste en fabricar un objeto auxiliar al que se obliga a "anularse muchas veces", es decir, a tener muchos ceros, en ciertos puntos especiales. Por un lado, cuantas más veces se anula, más puntos especiales tiene que haber para justificarlo. Por otro, el objeto no puede crecer sin límite, y eso pone un tope a cuántas veces puede anularse. Si ambas fuerzas se ajustan con cuidado, el número de puntos especiales queda atrapado entre ellas. El ajuste perfecto llega cuando la "multiplicidad", el número de veces que el objeto se anula en cada punto, es del orden de la raíz cuadrada del tamaño del mundo. Ahí los dos errores se equilibran.

Pero el método depende de una herramienta geométrica que solo existe en los mundos finitos, y por eso nadie lo había llevado a los números reales.

### El puente de contrapesos

Alpöge sustituye la herramienta que falta por otra que sí funciona en el caso real: un sistema de **siete desigualdades** que comparan "pendientes" de ciertas redes geométricas con "alturas" de ciertos números asociados.

En la metáfora, el pulso de Stepanov pasa a ser un **puente de contrapesos**. Por debajo, la presión del exceso de los primos inertes empuja hacia arriba. Por arriba, el techo global presiona hacia abajo. El puente tiene **siete márgenes de seguridad** y muchos tirantes casi perpendiculares entre sí, lo que en el artículo corresponde a familias de funciones especiales "casi ortogonales". Gracias a esa redundancia, lo que decide si el puente aguanta es **la resistencia media** de toda la estructura y no la viga más débil. Este paso de lo peor a lo promedio, que el artículo consigue con un resultado llamado Teorema del Marco, es lo que impide que el argumento se derrumbe por un único punto frágil.

### Las esclusas: la cadena de levantamientos theta

Falta lo esencial: ¿de dónde sale tanta presión desde abajo? Para eso Alpöge y Claude montan una **cadena de montaje**.

En matemáticas existen unos objetos llamados **formas automórficas**. Son funciones con simetrías extraordinarias que viven sobre espacios geométricos. Unos operadores llamados **levantamientos theta** permiten tomar una de esas formas y "subirla" a un espacio más grande, con más dimensiones, conservando parte de su información. La demostración **encadena muchos de estos levantamientos**, cada uno hacia un espacio de mayor tamaño.

En el acueducto, cada levantamiento es una **esclusa**. El agua pasa de una a la siguiente, cada vez más ancha, y en cada paso gana presión.

### Los primos inertes como amplificadores

Aquí está el truco más fino. En el método original de Stepanov, la fuerza venía de que el objeto auxiliar se anulaba muchas veces. En el caso real, Alpöge cambia "anularse muchas veces" por "**ser divisible muchas veces por un primo**".

Los primos inertes, los que atraviesan la ampliación sin partirse, tienen una propiedad especial en este contexto. Cuando el levantamiento se mira "a través" de uno de ellos, la estructura interna del proceso, ligada a una curva con simetrías muy particulares, obliga al resultado a ser divisible por potencias de ese primo. Cada esclusa añade más divisibilidad.

En la metáfora, los primos inertes son **sedimentos densos** que, al pasar por cada esclusa, accionan una turbina interna y **multiplican la presión** sin que se escape agua. Al encadenar esclusas, esa presión se acumula.

Para evitar que la presión ganada se pierda por el camino, el artículo usa unas **válvulas estancas**, que en su lenguaje técnico se llaman no degeneración de Hecke y que garantizan que cada paso de la cadena conserve lo que ganó.

### El equilibrio final: tantas esclusas como la raíz cuadrada

Queda decidir cuántas esclusas poner, y aquí reaparece el equilibrio de Stepanov:

- **Con pocas esclusas**, la presión acumulada no basta para vencer al techo fijo y las grietas finas pasan desapercibidas.
- **Con demasiadas**, se acumulan rozamientos y holguras: pérdidas por el tamaño creciente de los espacios, por la complejidad de cada paso y por pequeñas incompatibilidades aritméticas.

El punto óptimo es **una cadena de longitud cercana a la raíz cuadrada de la escala**, el mismo equilibrio que en el universo finito, ahora trasladado al mundo real. Para que la cuenta salga, los "cimientos" deben ser uniformes por muy profunda que sea la estructura (controlar ciertos volúmenes geométricos), y ciertos tramos no deben vibrar (acotar unos objetos aritméticos llamados grupos de Tate-Shafarevich).

Con todo ajustado, si existiera una grieta fuera del eje, la presión acumulada **levantaría el puente**, rompiendo el techo del Teorema A. Como el puente no se levanta, no hay grieta.

Un aviso honesto: la imagen muestra la arquitectura del argumento, no su mecánica, que trabaja con divisibilidades exactas y estructuras aritméticas sin equivalente físico.

---

## Las tres ideas verdaderamente revolucionarias (y quién tuvo cada una)

El artículo permite distinguir qué aportó el humano y qué la máquina, y avisa cuando la atribución no está clara.

**1. Llevar el método de Stepanov a los números reales, cambiando "anularse muchas veces" por "ser divisible muchas veces en los primos inertes".**
Esta es la clave conceptual. La atribución a **Alpöge** es clara. Suyo es el plan general, y fue él quien reconoció que un argumento anterior, procedente del trabajo de investigadores de OpenAI y basado en una función auxiliar de las que se usan en teoría de números desde Siegel, era en el fondo el método de Stepanov con la multiplicidad mínima, una sola vez. El giro decisivo llegó cuando Alpöge observó, en un objeto automórfico concreto, una **multiplicidad dos**, y sospechó que añadir levantamientos theta permitiría aumentarla. El artículo **no deja claro** quién diseñó la formulación precisa en términos de divisibilidad ni la traducción a ventanas de Landau.

**2. Encadenar una torre de levantamientos de longitud igual a la raíz cuadrada de la escala.**
Según el artículo, fue **Claude** quien propuso convertir la intuición de Alpöge en una cadena cuya longitud, la raíz cuadrada de la escala, actúa como multiplicidad y reproduce el equilibrio exacto de Stepanov. La semilla humana fue la observación de la multiplicidad dos. La arquitectura de la cadena fue una propuesta de la IA.

**3. El enorme aparato de formas automórficas en espacios de dimensión alta que hace que la cadena no se desmorone.**
El artículo atribuye explícitamente a **Claude** los argumentos sobre formas automórficas en estos espacios grandes: los tirantes casi perpendiculares, las válvulas estancas, los cimientos uniformes en profundidad y el control de las vibraciones. Adriazola advierte, sin embargo, que **no se desglosa con claridad** quién hizo cada pieza concreta.

En resumen: el humano aporta la visión y el reconocimiento del patrón, y la máquina, la ingeniería que lo hace sostenerse.

---

## Letra pequeña y honestidad científica

### Lo que garantiza el ordenador

El 20 de noviembre de 2026, Alpöge publicó una nota de cuatro páginas junto con una prueba completa escrita en **Lean**. Lean es un lenguaje de programación diseñado para que un ordenador compruebe, sin saltarse un paso, que cada deducción se sigue de las anteriores, apoyándose en Mathlib, una gran biblioteca de matemáticas ya verificadas. Al día siguiente, las comunidades de Lean y Mathlib, respaldadas por Lean FRO y la Mathlib Initiative, **certificaron** que el enunciado formal y la prueba eran correctos. Michael Rubinstein compiló el desarrollo por su cuenta de forma independiente.

La escala es enorme: unos **1,07 millones de declaraciones**, de las que unas **767.000** están en la ruta directa hacia el teorema final.

Eso garantiza que el programa demuestra el enunciado formal, pero no que exista una explicación que una persona pueda leer y enseñar. Certeza no es comprensión.

### Lo que todavía falta para los humanos

El artículo de Adriazola intenta precisamente eso: reconstruir la demostración en el lenguaje convencional de las matemáticas. Para hacerlo se ayudó de varios modelos de IA (Claude Fable 5.2 y Opus 5.5, GPT 5.6 Pro y Kimi K3.1 Pro). Rastreó las dependencias hacia atrás desde el resultado final y citó teoremas ya publicados. Deliberadamente, **no usa Lean como autoridad**, y reconoce que no leyó el código declaración por declaración.

Su reconstrucción está **incompleta**, y el autor lo dice abiertamente. En la Subsección 18.7 explica que la versión humana de la prueba sigue dependiendo de cinco bloques pendientes:

1. **La cadena y sus válvulas.** Faltan pruebas redactadas de varios pasos de la cadena de levantamientos y del control de pérdidas.
2. **Los tirantes del puente.** Faltan detalles sobre las relaciones entre las funciones casi perpendiculares y sus términos secundarios.
3. **Los cimientos.** Faltan cálculos de alturas, volúmenes y contribuciones locales de los primos.
4. **Los tramos sin vibración y el ensamblaje.** Faltan las cotas finales sobre los grupos de Tate-Shafarevich y el montaje del Teorema A.
5. **Las piezas prestadas.** Hay teoremas ya publicados por otros autores que aún hay que cotejar línea por línea para confirmar que sus hipótesis encajan exactamente con el uso que se les da.

Todos estos pasos **están demostrados en Lean**. Lo que falta es su versión legible para personas, o la comprobación manual de que las referencias encajan.

### Hallazgos colaterales

Uno de los ingredientes implica una cota sobre un viejo problema, la conjetura de Vandiver, **más fuerte que las publicadas**. Otro controla de forma uniforme ciertos volúmenes geométricos por una vía nueva. Adriazola esboza además una prueba alternativa más corta de una pieza técnica, aún no verificada ni formalizada.

### En resumen

La máquina dice que el muro ha caído. Los humanos reconstruyen, ladrillo a ladrillo, por qué, y han documentado qué ladrillos faltan. Esa transparencia es quizá la mejor noticia de esta historia.
