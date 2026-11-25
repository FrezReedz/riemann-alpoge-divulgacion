# Paso 0 — Extracción del esqueleto (Gemini 4 Neon, vía `agy`)

Prompt usado para generar `01_esqueleto_secciones.md` a partir de `main.pdf`:

```text
Actúa como un extractor técnico especializado en literatura matemática en LaTeX/PDF. 
Lee el archivo `main.pdf` ("The Alpöge Proof of the Riemann Hypothesis" de Jimmie Adriazola, 287 páginas) y genera en este mismo directorio un archivo llamado `01_esqueleto_secciones.md`.

REGLAS ESTRICTAS DE EXTRACCIÓN:
1. NO resumas, no traduzcas a lenguaje coloquial ni interpretes todavía; extrae la arquitectura fiel del documento en español (manteniendo los nombres técnicos originales en inglés entre paréntesis la primera vez que aparezcan).
2. IGNORA por completo el contenido interno de las demostraciones (`Proof. ... □`). No copies cálculos intermedios, desigualdades de acotación ni manipulaciones algebraicas.
3. Para cada una de las 18 secciones (desde la Sección 1 hasta la 18.7), extrae únicamente:
   - Número, título de la sección y rango de páginas.
   - El párrafo introductorio de la sección (donde el autor explica el propósito de esa sección y cómo conecta con las demás).
   - El enunciado (sin demostración) de los Teoremas principales (`Theorem`), Proposiciones clave (`Proposition`), Definiciones centrales (`Definition`) y Observaciones (`Remark`) que articulan el argumento.
   - Extrae de forma íntegra las ideas de la Sección 1 (1.1 a 1.4) y la lista completa de hipótesis abiertas y teoremas externos de la Subsección 18.7 ("Hypotheses in the final deduction").
4. Estructura `01_esqueleto_secciones.md` con encabezados claros por Parte (Parte I: Reducción a un teorema aritmético; Parte II: Teorema A) y por Sección. Al final del archivo, añade una línea de confirmación indicando cuántas secciones has procesado.
```
