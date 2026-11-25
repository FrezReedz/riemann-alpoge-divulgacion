# Cómo un matemático y una IA derribaron el gran muro de los números primos

*Esta es una versión muy simplificada del artículo principal de este repositorio ([README](README.md)); simplificar implica perder precisión, y quien lo publica no es matemático, así que tómalo con pinzas. La escribió Gemini 4 Carbon a partir del artículo principal ya verificado; Claude la revisó y corrigió contra ese artículo y contra los puntos clave del PDF, pero no pasó las tres rondas automáticas de verificación del artículo principal.*

## En 30 segundos

En noviembre de 2026, el matemático Levent Alpöge anunció una demostración de la hipótesis de Riemann, encontrada junto con la inteligencia artificial Claude. Era probablemente el misterio más famoso de las matemáticas, sin resolver durante 167 años. La prueba se escribió en Lean, un lenguaje que el ordenador verifica paso a paso, y quedó certificada al día siguiente. Ahora Jimmie Adriazola la está reconstruyendo al lenguaje matemático habitual para humanos, aunque advierte que esa versión legible sigue incompleta.

## ¿Qué son los números primos y qué afirma la hipótesis de Riemann?

Los números primos solo se dividen de forma exacta entre sí mismos y entre uno, como 2, 3, 5, 7 u 11. De cerca parecen salir al azar, pero vistos de lejos siguen una pauta muy regular.

En 1859, un artículo breve dejó escrita una sospecha decisiva: ¿cuánto pueden apartarse los primos de esa pauta? Detrás de ellos hay un objeto matemático que resuena como el ecualizador de un juego musical, donde cada cero actúa como una nota que mete una pequeña oscilación en su reparto.

Esas notas viven en una franja concreta, y la hipótesis de Riemann dice que todas están clavadas en su línea central; en concreto, el artículo demuestra que ninguna cae a la derecha de ella. Si es así, el desorden de los primos es el mínimo posible, tampoco al separarlos por familias según terminen en 1, 3, 7 o 9.

Si una sola nota se saliera de esa línea, muy lejos estallarían desajustes enormes. La analogía musical falla en algo: nadie mueve esos controles a mano, porque las notas vienen fijadas para siempre por los propios números.

## ¿Por qué no basta con comprobar billones de casos?

Los ordenadores ya han comprobado billones de ceros y todos están en su línea. Pero cuando hay infinitos casos, mirar muchos no demuestra nada.

Imagina explorar un mundo infinito de Minecraft buscando fallos en el reparto de diamantes. Caminar billones de bloques viendo todo en orden tranquiliza mucho, pero no descarta una anomalía colosal mucho más adelante.

La comparación con Minecraft solo cojea en que su terreno nace de un programa con límites técnicos, mientras que la fila de los números primos no la programó nadie y jamás termina.

## ¿Cómo vigilas el infinito usando solo ventanas y un techo?

La primera parte de la prueba, mucho más breve que la segunda, esquiva el choque frontal. Normalmente habría que vigilar subidas y bajadas en cada rincón y a todas las escalas.

Gracias a una propiedad de las cantidades que nunca cambian de signo, basta con poner un techo sin necesitar suelo, ahorrando la mitad del trabajo, y solo en una serie infinita de ventanas espaciadas cada vez más lejanas. Es como vigilar un corredor infinito de Portal instalando láseres únicamente en el techo de cámaras muy separadas: si nada roza esos láseres, es imposible haberse desviado.

Como se tratan juntas varias familias de primos, sus señales podrían anularse entre sí igual que dos ondas opuestas. Para evitarlo, la prueba conecta el exceso con ciertos primos especiales, aplica dos promedios con pesos positivos para que todas las señales se sumen sin cancelarse y usa dos primos auxiliares como filtros del ruido sobrante.

Así todo se reduce a probar que en esas ventanas, tan lejanas como se quiera, el exceso queda por debajo de un techo del orden de la raíz cuadrada de la escala (tras unos ajustes técnicos de normalización). El símil de Portal falla en que un jugador podría agacharse justo en cada cámara, algo que la rigidez matemática impide entre ventanas.

## ¿Qué idea se tomó prestada de un mundo pequeño?

La segunda parte rescata un truco resuelto hace décadas en mundos numéricos finitos, universos pequeños donde los números dan la vuelta al llegar al final como las horas de un reloj.

Imagina entrar a oscuras en una mazmorra de Zelda con una trampa mágica de batería limitada, tu presupuesto de ceros. Si obligas a la trampa a gastar muchas cargas en cada enemigo oculto, es decir, a anularse muchas veces en cada punto especial, caben muy pocos enemigos antes de agotar la batería.

Pero exigir demasiados impactos por enemigo obliga a fabricar una trampa mucho más compleja y dispara el tamaño de su batería total. Son dos costes opuestos que encuentran su equilibrio óptimo cuando los golpes por punto rondan la raíz cuadrada del tamaño del mundo.

La analogía con Zelda falla en un detalle: en el juego la batería se vacía golpe tras golpe, mientras que el objeto auxiliar matemático reparte todo su presupuesto de golpe por pura estructura lógica.

## ¿Por qué se buscan primos que no se rompen en vez de ceros?

Trasladar esa idea a los números ordinarios con muchas repeticiones era el gran paso pendiente. Existía un argumento clásico (de Siegel), aparecido en trabajos de investigadores de OpenAI, que en el fondo era este mismo truco con una sola repetición, el mínimo.

El giro clave consiste en cambiar anularse muchas veces por ser divisible muchas veces por ciertos primos especiales que no se rompen al ampliar los números. Piensa en los bloques de Super Mario: con Mario pequeño, que representa los enteros habituales, cada primo es un bloque indivisible.

Cuando Mario crece con una seta, equivalente a ampliar los enteros añadiendo por ejemplo la raíz cuadrada de un número negativo, algunos bloques saltan en pedazos más pequeños, pero otros aguantan enteros e intactos. En vez de acumular ceros, la prueba acumula divisiones exactas repetidas entre esos bloques irrompibles.

El símil de Super Mario falla en algo básico: apilar bloques suma alturas, mientras que aquí cada nueva capa significa volver a multiplicar por ese mismo primo.

## ¿Cómo funciona la cadena de etapas y cuál es su longitud justa?

Para fabricar tanta divisibilidad, Alpöge y Claude montan una cadena de producción como en Factorio. Cada etapa toma un objeto geométrico lleno de simetrías y lo sube a un espacio más grande, con más dimensiones, conservando parte de su información.

Al pasar por cada máquina junto a esos primos irrompibles, las simetrías internas del proceso obligan al resultado a ganar más divisibilidad por ese primo. Cada etapa pierde un poquito de señal, pero una válvula matemática de seguridad mantiene esas pérdidas pequeñas frente a la ganancia.

¿Cuántas máquinas hay que encadenar? Con pocas etapas falta fuerza para alcanzar el techo fijo, y con demasiadas se acumulan rozamientos por el tamaño creciente de los espacios, la complejidad de cada paso y pequeños desajustes aritméticos.

Por eso la longitud óptima vuelve a ser cercana a la raíz cuadrada de la escala, apoyada en cimientos uniformes y piezas que no vibren. Aquí Factorio se queda corto porque sus máquinas ocupan un mapa plano, mientras que cada etapa matemática salta a un espacio con más dimensiones.

## ¿Por qué todo esto descarta cualquier cero fuera de sitio?

Todo el balance se lleva con siete desigualdades, como siete márgenes de seguridad, y con muchas piezas casi independientes entre sí. Gracias a eso, lo que cuenta es la fuerza media del conjunto y no su eslabón más débil.

Imagina una sala de Dark Souls donde las reglas del motor prohíben superar mil puntos de daño. Si existiera un solo cero fuera de su sitio, meter su exceso en la cadena de etapas multiplicaría el golpe hasta reventar ese techo en alguna ventana; como el techo no se rompe, ese cero rebelde no existe.

La comparación con Dark Souls falla en un matiz clave: un juego recorta el daño excesivo en pantalla aunque el objeto exista, mientras que romper un techo matemático produce una contradicción imposible que prueba que el intruso jamás estuvo ahí. Conviene recordar además que todas estas imágenes muestran la arquitectura del argumento, no su mecánica exacta.

## ¿Qué aportó Alpöge y qué aportó Claude?

El reparto conocido procede únicamente de la nota de cuatro páginas de Alpöge, un resumen breve que no detalla quién hizo cada pieza individual. Recuerda a una campaña cooperativa donde ambos jugadores resuelven salas clave, aunque el símil falla porque aquí no existe un registro público de cada movimiento intermedio.

Esa nota atribuye a Alpöge el plan general y reconocer que aquel argumento de Siegel aparecido en trabajos de OpenAI era el truco de los mundos finitos con una sola repetición. Él describe como punto de inflexión ver aparecer ese efecto por partida doble ("multiplicidad dos") en un objeto concreto, señal de que más etapas podían aumentarlo, aunque no especifica quién formuló el paso a divisibilidad o a ventanas.

A Claude le atribuye proponer la cadena de longitud cercana a la raíz cuadrada de la escala y, en términos generales, los argumentos sobre esos objetos llenos de simetrías en espacios de muchas dimensiones, una parte importante de la maquinaria de la segunda parte. No fue simple cálculo mecánico: una idea central vino de la inteligencia artificial.

## ¿Qué es Lean y por qué la versión humana sigue incompleta?

El 20 de noviembre de 2026, Alpöge publicó su nota junto con la prueba completa en Lean, un lenguaje apoyado en una gran biblioteca verificada que actúa como un compilador implacable: si un solo paso lógico no encaja, se niega a compilar. Al día siguiente quedaron certificados enunciado y demostración, y otro investigador compiló todo de forma independiente: son unos 1,07 millones de declaraciones, con unas 767.000 en la ruta principal.

El símil del compilador falla en que compilar un videojuego normal no impide errores al jugarlo, mientras que en Lean, si la prueba compila, el enunciado queda demostrado sin huecos. Pero tener el sello de la máquina no equivale a comprender la prueba.

Por eso Adriazola reconstruye el argumento para humanos con ayuda de varios modelos de inteligencia artificial, rastreando pasos hacia atrás sin usar Lean como autoridad. Su texto sigue incompleto: faltan por redactar piezas de cuatro bloques internos ya demostrados en Lean y quedan unos pocos teoremas publicados por otros autores por cotejar línea por línea con sus fuentes, además de aportar de paso mejoras colaterales y un atajo aún pendiente de revisión.

## Glosario para curiosos (opcional)

**Función zeta y funciones de Dirichlet.** El instrumento que resuena con todos los primos y sus equivalentes para los primos repartidos en familias.

**Línea crítica.** El eje central de la franja donde deben situarse todos los ceros relevantes.

**Ventanas de Landau.** El principio de rigidez que permite vigilar solo un techo en tramos espaciados cada vez más lejanos.

**Método de Stepanov, Bombieri y argumento de Siegel.** La técnica de mundos finitos con presupuesto limitado de ceros y su versión previa de una sola repetición.

**Cuerpos de números y primos inertes.** Las ampliaciones de los números enteros y los primos que las atraviesan enteros sin partirse.

**Formas automórficas y levantamientos theta.** Los objetos llenos de simetrías geométricas y las etapas que los suben a espacios con más dimensiones.

**No degeneración de Hecke y Teorema del Marco.** La válvula que acota las pérdidas por etapa y el resultado que hace que cuente la fuerza media del conjunto y no la pieza más débil.

**Covolúmenes y grupos de Tate y Shafarevich.** Las medidas que exigen cimientos uniformes y las piezas aritméticas que no deben vibrar al alargar la cadena.

**Mathlib.** La gran biblioteca de matemáticas ya verificadas en Lean sobre la que se apoya la certificación.
