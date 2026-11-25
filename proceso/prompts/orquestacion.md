# Prompt de orquestación (dado a Claude Code)

Este es el encargo que recibió Claude Code (Claude Opus 5.5) para coordinar las fases 1 a 3:

```text
MODO AHORRO EXTREMO DE CUOTA:
Tengo menos del 9% de cuota semanal en Claude. Por tanto:
1. PROHIBIDO leer el archivo `01_esqueleto_secciones.md` directamente en tu contexto.
2. PROHIBIDO lanzar subagentes internos de Claude (`Task` con Opus o Sonnet).
3. Delega las Fases 1 y 2 ejecutando `agy` por terminal (`Bash`). Antes de lanzar el primer comando, ejecuta `agy --help` (si no conoces la sintaxis exacta) para verificar los flags de modo no interactivo y selección de modelo.

El objetivo final es transformar el paper "The Alpöge Proof of the Riemann Hypothesis" (Jimmie Adriazola, nov 2026) en un artículo de divulgación brillante en español para alguien ajeno a las matemáticas ("cero fórmulas").

Ejecuta estas 3 fases en orden:

### FASE 1: Destilación Causal vía AGY (`Gemini 4 Neon`)
Usa `Bash` para pedir a `agy` (modelo `Gemini 4 Neon`) que lea `01_esqueleto_secciones.md` y genere `02_cadena_logica.md` con estas instrucciones:
- Agrupa las 18 secciones en 6 grandes bloques narrativos (2 de la Parte I y 4 de la Parte II).
- Para cada bloque, crea una ficha sin símbolos matemáticos con: (1) El obstáculo concreto, (2) El truco o herramienta de Alpöge (ventanas de Landau, método de Stepanov, cadena de $\sqrt{x}$ levantamientos theta, primos inertes), (3) El resultado que entrega al siguiente bloque, y (4) Separación entre "Idea Genial / Motor" y "Fontanería Técnica".
- Añade al final un apartado breve llamado "Estado de Verificación" extrayendo los puntos clave de la Sección 1.3 (certificación en Lean de 1,07 millones de declaraciones) y la Subsección 18.7 (qué hipótesis siguen abiertas en lenguaje convencional).

### FASE 2: Metáfora Maestra vía AGY (`Gemini 4 Carbon`)
Cuando compruebes por Bash que `02_cadena_logica.md` existe y no está vacío, usa `Bash` para pedir a `agy` (modelo `Gemini 4 Carbon`) que lea `02_cadena_logica.md` y genere `03_mapa_analogias.md` con estas instrucciones:
- Diseña una ÚNICA metáfora física o cotidiana coherente que sostenga toda la demostración de principio a fin (ej. acústica/resonancia, cartografía de terreno sumergido o esclusas/contrapesos).
- Mapea sin contradicciones los 5 pilares: (1) Ceros de Zeta y línea crítica 1/2, (2) Reducción por ventanas de Landau, (3) Método de Stepanov (equilibrar dos errores opuestos), (4) Cadena de levantamientos theta y primos inertes como amplificadores, (5) Equilibrio final en $\sqrt{x}$ pasos.
- Copia al final del archivo el apartado "Estado de Verificación" y las "3 ideas verdaderamente revolucionarias" (distinguiendo qué aportó Alpöge y qué propuso Claude).
- Mantén `03_mapa_analogias.md` conciso y limpio (máximo 1.800 palabras).

### FASE 3: Redacción Final (TÚ, con `Claude Sonnet 5.5`)
Cuando exista `03_mapa_analogias.md`, lee ÚNICAMENTE ese archivo y redacta `RESUMEN_FINAL_RIEMANN.md` (entre 2.000 y 2.500 palabras, estilo periodístico de alta divulgación tipo *Quanta Magazine*):
- **Regla de Cero Jerga:** Prohibido usar ecuaciones, LaTeX o símbolos matemáticos ($s$, $\chi$, $\zeta$, $O(\epsilon)$). Si aparece un término inevitable (como "función zeta" o "primos inertes"), defínelo en lenguaje llano en el mismo párrafo.
- **Estructura obligatoria:**
  1. Titular y resumen ejecutivo (4 líneas).
  2. El muro de 167 años (la Hipótesis de Riemann sin matemáticas).
  3. Acto I: Cambiar una pregunta imposible por "ventanas" de primos.
  4. Acto II: La cadena de montaje de Alpöge y el truco de los primos inertes (desarrollando la metáfora maestra).
  5. Las 3 ideas verdaderamente revolucionarias (humano vs. IA).
  6. Letra pequeña y honestidad científica (Lean vs. reconstrucción humana y flecos de la Sección 18.7).

Empieza ahora comprobando la sintaxis de `agy` por terminal y lanzando la Fase 1.
```

Con una indicación añadida: *"damos por bueno ese pdf, así que lo resultante debe ser 100% fiel al pdf, y el objetivo es divulgar esto entre mentes humanas competentes y capaces de entender conceptos, pero debe ser lenguaje humano y comprensible"*.

Desviaciones respecto al plan: la Fase 3 la escribió Claude Opus 5.5 (el modelo de la sesión), no Sonnet 5.5. A la Fase 1 se le pidió además extraer las "3 ideas revolucionarias", porque la Fase 2 debía copiarlas de su salida. Después de la redacción se añadieron las tres rondas de verificación contra el texto íntegro del PDF, descritas en [`METODOLOGIA.md`](../../METODOLOGIA.md).
