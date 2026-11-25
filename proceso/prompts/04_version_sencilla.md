# Versión sencilla (Gemini 4 Carbon High vía `agy`)

Entrada: el artículo principal ya verificado. Después Claude aplicó 12 correcciones (créditos, mención a OpenAI y Siegel, Lean, glosario) y comprobó los puntos nuevos contra el PDF.

```text
Lee COMPLETO el archivo RESUMEN_FINAL_RIEMANN.md (directorio actual). Es un artículo de divulgación ya verificado frase a frase contra el paper "The Alpöge Proof of the Riemann Hypothesis" (Jimmie Adriazola, nov 2026). Es tu ÚNICA fuente de hechos: no añadas ningún dato, cifra, nombre ni afirmación sobre la demostración que no esté en él. Puedes simplificar, nunca cambiar el sentido.

Escribe VERSION_SENCILLA.md, en español: una versión MUCHO más fácil del mismo contenido, para cualquier persona lista pero sin formación matemática (piensa en un gamer de 16 años o en alguien de estudios técnicos).

REGLAS:
1. Cero fórmulas y cero símbolos.
2. En el texto principal, NINGÚN término técnico ni nombre de matemático salvo los imprescindibles: "hipótesis de Riemann", "números primos", "Alpöge", "Claude", "Adriazola" y "Lean". Todo lo demás (Landau, Stepanov, Bombieri, Siegel, levantamientos theta, formas automórficas, primos inertes, Hecke, Tate-Shafarevich, cuerpos de números, línea crítica, función zeta, Teorema A, etc.) se cuenta con palabras normales y ejemplos. Si de verdad hace falta un nombre, ponlo una sola vez entre paréntesis después de la explicación.
3. Usa VARIAS analogías, una por concepto, eligiendo la que mejor explique cada idea, preferiblemente de videojuegos famosos (por ejemplo Minecraft, Super Mario, Zelda, Pokémon, Tetris, Factorio, Dark Souls, Portal, Los Sims). Cada analogía tiene que ser exacta en lo que importa; si en algún punto falla, dilo en una frase. No fuerces un juego donde no encaje. Conceptos que hay que explicar:
   a) Qué son los primos y qué afirma la hipótesis de Riemann (que el "desorden" de los primos tiene un límite máximo; los ceros como "notas" que deben estar todas en una misma línea), y por qué comprobar billones de casos no basta.
   b) El primer gran truco: no hace falta vigilar subidas y bajadas en todas partes, basta con un techo en una serie infinita de "ventanas" cada vez más lejanas; y combinar todas las señales con pesos positivos para que no se cancelen.
   c) La idea prestada de un "mundo pequeño" (mundos numéricos finitos): obligar a un objeto auxiliar con un "presupuesto" limitado de ceros a anularse muchas veces en cada punto especial, lo que limita cuántos puntos caben; dos costes opuestos con un punto óptimo en la raíz cuadrada.
   d) El cambio de "anularse muchas veces" por "ser divisible muchas veces por ciertos primos especiales que no se rompen al ampliar los números".
   e) La cadena de etapas (cada etapa añade divisibilidad), las pérdidas en cada etapa que se mantienen pequeñas, y por qué la longitud óptima de la cadena es cercana a la raíz cuadrada de la escala (pocas etapas no bastan; demasiadas acumulan pérdidas).
   f) La conclusión: si hubiera un cero fuera de su sitio, la presión acumulada rompería el techo; como no lo rompe, no lo hay.
   g) Quién aportó qué, SOLO según lo que dice el artículo (la nota de Alpöge atribuye a Alpöge el plan y el reconocimiento del patrón; él describe como punto de inflexión la "multiplicidad dos"; atribuye a Claude la propuesta de la cadena de longitud cercana a la raíz cuadrada y los argumentos técnicos de la segunda parte). No exageres ni inventes reparto.
   h) Lean (un "compilador" tan estricto que si la prueba compila es correcta), las cifras (1,07 millones de declaraciones, 767.000 en la ruta principal), que se certificó al día siguiente de publicarse, y que la versión legible por humanos de Adriazola está INCOMPLETA (piezas por redactar y unos pocos teoremas publicados por cotejar).
4. Estructura: título atractivo; un párrafo "en 30 segundos"; secciones cortas con subtítulos que sean preguntas ("¿Qué es un número primo?", etc.); frases cortas; nada de párrafos largos. Al final, un "Glosario para curiosos" opcional con los nombres técnicos reales y una línea cada uno.
5. Al principio, una línea en cursiva: que es una versión simplificada de RESUMEN/README del repositorio, que simplificar implica perder precisión, y que quien lo publica no es matemático: tomar con pinzas.
6. Longitud: entre 1.300 y 2.000 palabras.

Escribe solo ese archivo. No ejecutes comandos de terminal.
```
