# Verificación (Gemini 4 Neon XHigh y Gemini 4 Argon High vía `agy`, en paralelo)

Prompt base de la ronda 1 (OUTFILE = verif_neon.md / verif_argon.md):

```text
Eres un verificador de hechos riguroso. En el directorio actual hay:
- paper.txt: texto completo extraído del PDF "The Alpöge Proof of the Riemann Hypothesis" (Jimmie Adriazola, nov 2026). Es la ÚNICA fuente de verdad.
- RESUMEN_FINAL_RIEMANN.md: artículo de divulgación en español basado en ese paper.

Tarea:
1. Lee RESUMEN_FINAL_RIEMANN.md entero y extrae TODAS las afirmaciones fácticas verificables (fechas, cifras, nombres, instituciones, modelos de IA, qué hace cada parte/sección, qué se atribuye a Alpöge, a Claude o a OpenAI, qué certificó Lean, qué queda abierto en la Subsección 18.7, hallazgos colaterales como Vandiver, descripción del método: ventanas de Landau, identidad del exceso, primos inertes, dos primos auxiliares, Teorema A, siete desigualdades, Teorema del Marco, cadena de longitud raíz cuadrada, no degeneración de Hecke, Tate-Shafarevich, etc.).
2. Para cada afirmación, búscala en paper.txt (usa búsquedas y lee las zonas relevantes; presta especial atención a las secciones 1, 1.3 y 18.7 y a todo pasaje sobre quién propuso qué).
3. Clasifícala como:
   - CONFIRMADO (el paper lo dice),
   - IMPRECISO (lo dice pero el artículo lo distorsiona, exagera o simplifica de forma engañosa),
   - FALSO (el paper dice otra cosa),
   - NO EN EL PAPER (no aparece; indica si es conocimiento general correcto, p. ej. Riemann 1859).
   Las metáforas en sí no se verifican; sí lo que afirman sobre la estructura lógica.

Escribe el resultado en el archivo OUTFILE con este formato compacto, en español:
- Línea inicial: "Total: N afirmaciones | CONFIRMADO a | IMPRECISO b | FALSO c | NO EN EL PAPER d".
- Para CONFIRMADO: una sola línea por afirmación: "OK — <afirmación resumida> — paper.txt:<línea>".
- Para IMPRECISO, FALSO y NO EN EL PAPER: un bloque con: la frase exacta del artículo, la cita literal en inglés del paper con número de línea de paper.txt, explicación breve, y redacción corregida propuesta en español llano sin fórmulas.
No modifiques ningún otro archivo. No ejecutes comandos de terminal; usa solo lectura y búsqueda de archivos.
```

Ronda 2: igual, pero sin listar las afirmaciones confirmadas. Ronda 3: además se pidió ser conservador (no marcar simplificaciones divulgativas legítimas) y se prohibió expresamente modificar el artículo; se comprobó por hash que no cambió.
