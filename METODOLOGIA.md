# Cómo se hizo este resumen

> **Aviso.** Quien firma este repositorio no es matemático. El resumen se basa **exclusivamente** en el manuscrito de Jimmie Adriazola citado abajo, y se ha dado por bueno su contenido. Aunque se ha verificado frase a frase contra el texto original, puede contener imprecisiones. Tómalo con pinzas y, ante cualquier duda, manda el original.

## Créditos

- **La demostración:** Levent Alpöge y Claude (Anthropic), anunciada el 20 de noviembre de 2026 y formalizada en Lean.
- **El manuscrito en el que se basa todo este trabajo:** Jimmie Adriazola, *The Alpöge Proof of the Riemann Hypothesis* (noviembre de 2026, 287 páginas).
  - Repositorio del autor: <https://github.com/jimjamzola/RH-Alpoge-Reconstruction>
  - PDF: <https://github.com/jimjamzola/RH-Alpoge-Reconstruction/blob/main/manuscript/main.pdf>
  - Perfil: <https://github.com/jimjamzola>
- **La formalización en Lean** (mantenida por la comunidad): <https://github.com/leanprover-community/riemann-hypothesis>

Este repositorio **no** incluye el PDF ni su texto completo. Para leerlos, ve al repositorio del autor.

## El reto

Convertir un manuscrito técnico de casi 300 páginas en un artículo de unas 2.500 palabras que una persona curiosa sin formación matemática pueda leer sin una sola fórmula, **sin traicionar el original**. Además, se hizo con muy poca cuota de uso disponible, así que el diseño reparte el trabajo pesado entre varios modelos y deja que cada uno lea solo lo imprescindible.

## La cadena de producción

| Paso | Modelo | Entrada → salida | Prompt |
|---|---|---|---|
| 0. Extracción | Gemini 4 Neon (vía `agy`) | `main.pdf` → `01_esqueleto_secciones.md` | [`prompts/00_extraccion.md`](proceso/prompts/00_extraccion.md) |
| 1. Destilación causal | Gemini 4 Neon High | `01` → `02_cadena_logica.md` (6 bloques narrativos) | [`prompts/01_fase1_cadena_logica.md`](proceso/prompts/01_fase1_cadena_logica.md) |
| 2. Metáfora maestra | Gemini 4 Carbon High | `02` → `03_mapa_analogias.md` | [`prompts/02_fase2_metafora.md`](proceso/prompts/02_fase2_metafora.md) |
| 3. Redacción | Claude Opus 5.5 (Claude Code) | `03` → `RESUMEN_FINAL_RIEMANN.md` | [`prompts/orquestacion.md`](proceso/prompts/orquestacion.md) |
| 4. Verificación ×3 | Gemini 4 Neon XHigh + Gemini 4 Argon High | artículo + texto íntegro del PDF → informes | [`prompts/03_verificacion.md`](proceso/prompts/03_verificacion.md) |

Claude Code (Claude Opus 5.5) actuó como orquestador: lanzó cada modelo desde la terminal con la herramienta `agy`, comprobó que cada archivo existía antes de pasar al siguiente, escribió el artículo y aplicó las correcciones. El plan original preveía Claude Sonnet 5.5 para la redacción, pero la sesión corría con Opus 5.5 y así consta.

### Por qué tres rondas de verificación

Cada paso de una cadena de resúmenes puede introducir errores, y los resúmenes de resúmenes los acumulan. Por eso la verificación **no** se hizo contra los archivos intermedios, sino contra el **texto íntegro del PDF** extraído con `pdftotext`:

1. **Primera ronda.** Dos verificadores independientes (Neon y Argon) extrajeron cada afirmación del artículo, la buscaron en el paper y la clasificaron como confirmada, imprecisa, falsa o "no está en el paper", citando la línea exacta. Detectaron errores reales: el método de Stepanov explicado al revés, "unas pocas ventanas" donde hacen falta infinitas, "números reales" donde el paper dice cuerpos de números, y atribuciones entre Alpöge y Claude más tajantes de lo que dice el texto. Además, Claude Code comprobó a mano el pasaje de atribución (Sección 1 del paper). Se aplicaron 29 correcciones.
2. **Segunda ronda.** Sobre el texto corregido: **0 afirmaciones falsas** y 13 matices, que también se aplicaron.
3. **Tercera ronda.** Otra vez con los dos verificadores en paralelo y con la instrucción de ser conservadores. Neon: 52 afirmaciones, 48 confirmadas, **0 imprecisas, 0 falsas** y 4 de contexto histórico general. Argon: 55 afirmaciones, 52 confirmadas, **0 imprecisas, 0 falsas** y 3 de contexto histórico general. No hizo falta ningún cambio: la versión publicada es exactamente la que pasó esta ronda.

Reglas de seguridad de cada ronda: los verificadores **solo podían escribir su informe**, nunca tocar el artículo. Se comprobó por hash que el artículo no cambiaba durante la revisión. Solo se aplicaron correcciones respaldadas por una cita literal del paper.

Lo que **no** está en el paper (el año 1859, los 167 años, los billones de ceros comprobados por ordenador) es contexto histórico general, y los verificadores lo marcaron como tal.

Todos los informes están en [`proceso/verificacion/`](proceso/verificacion/) y la versión del artículo anterior a las correcciones en [`proceso/versiones/`](proceso/versiones/).

## Estructura del repositorio

```
README.md                     ← el artículo (lo importante)
METODOLOGIA.md                ← este documento
proceso/
  prompts/                    ← todos los prompts, tal cual se usaron
  intermedios/                ← 01 esqueleto, 02 cadena lógica, 03 mapa de analogías
  verificacion/               ← informes de las tres rondas
  versiones/                  ← el artículo antes de verificar
```

---

## Reflexión final: ¿podría haberlo hecho un humano solo?

*Esto es opinión nuestra, no algo que diga el paper.*

Imaginemos a alguien mucho más brillante que Einstein o que el propio Alpöge. ¿Habría llegado solo a esta demostración, o el trabajo de Claude era imprescindible?

Primero hay que deshacer un malentendido: **esto no es un problema de "cálculos"** en el sentido de hacer muchas cuentas, como quien calcula decimales de pi. La prueba no es una búsqueda por fuerza bruta. Es una cadena enorme de razonamientos: definiciones, lemas y estimaciones encadenados. Lo que pesa es el **volumen de razonamiento correcto**, no la potencia de cálculo.

Lo que sabemos por el propio paper:

- **Las ideas de partida eran humanas y accesibles.** El método de Stepanov para mundos finitos existe desde hace décadas, y los levantamientos theta y las formas automórficas son teoría conocida. La nota de Alpöge le atribuye a él el plan y el reconocimiento clave: un argumento de Siegel era el método de Stepanov con multiplicidad uno. Su punto de inflexión fue ver una multiplicidad dos. Un genio humano podría, en principio, haber tenido esas mismas intuiciones.
- **Pero una de las ideas centrales la propuso la máquina.** La nota atribuye a Claude la propuesta de usar una cadena de levantamientos de longitud cercana a la raíz cuadrada como multiplicidad, y los argumentos sobre formas automórficas en rango superior. Claude no fue solo un "calculista".
- **El volumen es descomunal.** La prueba formal tiene unos 1,07 millones de declaraciones, unas 767.000 en la ruta directa al teorema. La reconstrucción humana ya ocupa 287 páginas, se ha hecho con ayuda de varios modelos de IA y **todavía no está completa**.
- **La amplitud también lo es.** El argumento toca a la vez teoría analítica de números, geometría aritmética, formas automórficas en grupos de rango alto, teoría de Hecke y cohomología de Galois. Rara vez una sola persona domina todo eso al nivel que exige cada pieza.

Nuestra opinión: **no era imposible para una mente humana en principio, pero sí, muy probablemente, en la práctica.** Un superhumano quizá habría tenido las ideas clave. Ejecutar y comprobar un argumento de este tamaño sin errores habría llevado, siendo optimistas, muchos años o décadas, seguramente con un equipo y un proceso de revisión largo. Las grandes demostraciones del siglo XX que se acercan a esta escala fueron obras colectivas de años. Tres cosas parecen haber sido decisivas y difíciles de sustituir:

1. **La velocidad para explorar** variantes de la idea, desde la multiplicidad dos hasta la cadena de raíz cuadrada, y descartar las que no funcionan.
2. **La capacidad de sostener una construcción gigantesca** coherente de principio a fin.
3. **La verificación formal en Lean.** La comunidad certificó la prueba al día siguiente de publicarse, en vez de esperar años de revisión humana.

Dicho de otro modo: el genio humano puso la chispa y la dirección, y la máquina hizo posible recorrer el camino en un tiempo humano. Pero no hay que caer en la caricatura de "el humano piensa y la máquina calcula", porque según la propia nota de Alpöge una de las ideas clave vino de Claude.

Es imposible saber con certeza qué habría pasado en un mundo sin IA, así que esta reflexión es especulación informada y nada más.

---

*Metodología y reflexión escritas con ayuda de Claude (Anthropic), con la misma cautela que el resto del repositorio: no somos matemáticos y puede haber imprecisiones.*
