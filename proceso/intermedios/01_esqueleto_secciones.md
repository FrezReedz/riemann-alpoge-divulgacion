# Esqueleto estructural de *The Alpöge Proof of the Riemann Hypothesis*

- **Autor:** Jimmie Adriazola (Arizona State University)
- **Fuente:** `main.pdf` (287 páginas; texto principal: pp. 4–282; Referencias: pp. 282–287; Índice: pp. 1–3)
- **Clasificación MSC 2020:** 11M26, 11M06, 11G05, 11F27, 11F70, 11F80, 14G40
- **Resumen del documento (*Abstract*, p. 1):** El 20 de noviembre de 2026, Levent Alpöge anunció una demostración de la hipótesis de Riemann (*Riemann hypothesis*) hallada junto con Claude y publicada en Lean, posteriormente certificada por las comunidades Lean y Mathlib. Una forma cuantitativa del teorema de Landau sobre transformadas de Mellin (*Mellin transforms*) reduce el semiplano libre de ceros $\operatorname{Re} s > 1/2$ para funciones $L$ de Dirichlet (*Dirichlet $L$-functions*) a una cota unilateral de raíz cuadrada (*one-sided square-root bound*) para sumas de primos suavizadas (*smoothed prime sums*) en intervalos adecuados. Alpöge adapta el método de conteo de puntos de Stepanov (*Stepanov's point-counting method*) sobre cuerpos finitos: la divisibilidad que ganan sucesivos levantamientos theta (*theta lifts*) en primos inertes (*inert primes*) desempeña el papel de la anulación de orden alto en puntos racionales. Cada factor de un primo inerte $p$ aporta $\log p$ al término de divisibilidad en la desigualdad de pendiente (*slope inequality*); para una suma de longitud $X$, una cadena de alrededor de $\sqrt{X}$ levantamientos theta equilibra los errores y produce la cota unilateral de raíz cuadrada que exige el criterio de Landau. En el curso de la reconstrucción, el autor señala haber hallado lo que parece ser una demostración más corta de una cota uniforme en cohomología de Galois (*Galois cohomology*, §17.4.3).

---

## Sección 1: Introducción (*Introduction*, pp. 4–7)

### Párrafo introductorio y teorema principal (pp. 4–5)

El artículo reconstruye en matemáticas convencionales la demostración del siguiente teorema.

- **Teorema 1.1 (`Theorem 1.1`, p. 4).** Para todo carácter de Dirichlet primitivo (*primitive Dirichlet character*) $\chi$, la función $L(s, \chi)$ no se anula en el semiplano $\operatorname{Re} s > \frac{1}{2}$. En particular, la función zeta de Riemann (*Riemann zeta function*) $\zeta(s)$ no se anula en $\operatorname{Re} s > \frac{1}{2}$.

La demostración se debe a Levent Alpöge y Claude. El 20 de noviembre de 2026, Alpöge publicó una nota de cuatro páginas [2] junto con una demostración de Teorema 1.1 formalizada en Lean [23] sobre Mathlib [73], y el 21 de noviembre de 2026 las comunidades de Lean y Mathlib, con el respaldo de Lean FRO y la Mathlib Initiative, certificaron que el enunciado formal y la demostración formal son correctos [72]. La nota describe el argumento como descendiente del método de Stepanov [70] para curvas sobre cuerpos finitos: atribuye a Alpöge el plan y el reconocimiento de que un argumento de función auxiliar (*auxiliary-function argument*) de Siegel —que apareció en trabajo matemático de investigadores de OpenAI— es el método de Stepanov con multiplicidad uno. Alpöge describe el punto de inflexión como la aparición de multiplicidad dos en un determinante automórfico (*automorphic determinant*) sobre $O(2, n)$, lo que sugirió que levantamientos theta ulteriores podrían incrementar la multiplicidad. La nota atribuye a Claude la propuesta de que una cadena de levantamientos theta de longitud alrededor de $\sqrt{x}$ desempeñe el papel de la multiplicidad, así como los argumentos sobre formas automórficas (*automorphic forms*) en grupos de rango superior. Agradece a David Dohan, Ben Michel, Ralph Furman, Eric Price y Cora Vinther.

La reconstrucción no está completa: el artículo demuestra el Teorema 1.1 a partir de los teoremas publicados que cita y de una lista finita de enunciados internos —cada uno enunciado con precisión donde se utiliza y resumido en la Subsección 18.7— cuyas demostraciones convencionales aún no se proporcionan. El desarrollo formal demuestra cada uno de esos enunciados. Asimismo, algunos teoremas publicados citados no han sido todavía comparados línea por línea con sus fuentes, y la Subsección 18.7 también los enumera.

### 1.1 La arquitectura de la demostración (*The architecture of the proof*, pp. 5–6)

Para $x \ge 1$ se define
$$G(x) = \sum_{n \le x} \Lambda(n)\left(\frac{x}{n} - 1\right) - x\log x + (1+\gamma)x,$$
y $G_\chi$ es la función análoga para un carácter de Dirichlet $\chi$, definida en (2.2). La transformada de Mellin de $G$ tiene un polo simple en cada cero $\rho$ de $\zeta$ en la banda crítica (*critical strip*), con residuo $-1/(\rho(\rho-1))$ multiplicado por la multiplicidad. La demostración consta de dos partes:

- **Parte I (reducción a un enunciado aritmético):**
  - La **Sección 2** demuestra una forma cuantitativa del teorema de Landau sobre integrales de Dirichlet de un solo signo (*Dirichlet integrals of one sign*). Si una combinación positiva $G + \sum_i w_i G_{\chi_i}$ es a lo sumo $C x^\theta$ para todo $x$ en ventanas (*windows*) $Y \le x \le Y^{3/2}$, para $Y$ arbitrariamente grande, entonces $\zeta$ y las $L(s, \chi_i)$ no se anulan para $\operatorname{Re} s > \theta$. Por tanto, basta demostrar tal cota con $\theta = \frac{1}{2} + O(\varepsilon)$, en ventanas, para las potencias de un carácter primitivo fijo $\psi_0$. La cota proviene de un cuerpo CM (*CM field*) abeliano $E$ de grado $4n$ con $n$ del orden de $x^{2+8\varepsilon}$, recortado por $\psi_0$ y dos primos auxiliares (*auxiliary primes*) $q$ y $d$.
  - La **Sección 3** demuestra dos identidades. La primera, **Proposición 3.1**, muestra que siete desigualdades entre pendientes de retículos hermíticos (*slopes of hermitian lattices*), alturas de aplicaciones de períodos (*heights of period maps*) y términos locales (*local terms*) acotan una suma $S$ sobre primos inertes en $\mathbb{Q}(\sqrt{-d})$ mediante un término principal explícito. La segunda, **Proposición 3.3**, identifica $S$ menos ese término principal con una combinación de las funciones $G_\psi$ sobre los caracteres $\psi$ de $\operatorname{Gal}(E/\mathbb{Q})$.
  - La **Sección 4** convierte una cota para esa combinación, sumada sobre muchos pesos (*weights*) y muchos nodos (*nodes*), en una cota para una combinación positiva de las $G_\psi$ en un único punto $x$. Un promedio sobre traslaciones elimina los caracteres fuera de una familia pequeña, y una elección equidistribuida de pesos otorga a cada carácter restante un peso positivo. El paso deja los valores $|G_\psi(x)|$ para $3o$ caracteres auxiliares, donde $o$ es el orden de $\psi_0$.
  - La **Sección 5** elige $q$ y $d$ mediante una media cuadrática (*mean square*) sobre familias de módulos primos de modo que esos valores sean a lo sumo $x^{1/2+\varepsilon}$ en una ventana entera, sin asumir ninguna región libre de ceros (*zero-free region*) más allá de la clásica, y construye el cuerpo $E$ y los datos restantes.
  - La **Sección 6** enuncia el teorema aritmético, **Teorema A**, y deduce de él el **Teorema 1.1**.

- **Parte II (Teorema A):**
  - La forma de Bombieri del argumento de Stepanov [10] acota el número de puntos racionales de una curva comparando una función auxiliar de orden de polo controlado con su orden de anulación $M$ en los puntos racionales, equilibrándose los dos errores en $M = \sqrt{q}$.
  - Sobre un cuerpo de números, el conteo de ceros frente a polos pasa a ser una desigualdad de pendiente del tipo de Bost [15] para una familia de aplicaciones entre retículos hermíticos, y el orden de anulación pasa a ser el número $m$ de pasos en una cadena de levantamientos theta entre grupos unitarios (*unitary groups*) de rango creciente.
  - A cada paso el argumento asocia un retículo hermítico sobre el anillo de enteros de $E$ y una aplicación de períodos hacia el dual de un retículo de formas automórficas.
  - En un primo $p$ inerte en $\mathbb{Q}(\sqrt{-d})$, una curva elíptica con multiplicación compleja (*complex multiplication*) por $\mathbb{Q}(\sqrt{-d})$ tiene un grupo formal de altura dos (*formal group of height two*), y el núcleo theta de un levantamiento es divisible por una potencia de $p$ cuyo exponente en peso $\alpha$ tiene término principal $\sum_{i\text{ impar}} \alpha/p^i = \alpha p/(p^2-1)$, que coincide con la contribución de $p$ a la suma $S$.
  - Los operadores de Hecke (*Hecke operators*) en los primos inertes cuestan una pérdida controlada por un teorema de no degeneración (*nondegeneracy theorem*) para representaciones integrales de $\mathrm{GL}_k$.
  - El tamaño arquimediano de la aplicación de períodos es $m$ veces una cantidad próxima a $\sum_t \log \Gamma(a_t)$, medida frente al período de la curva CM, y la teoría de intersección aritmética (*arithmetic intersection theory*) sobre variedades de Shimura unitarias (*unitary Shimura varieties*) acota la pendiente del retículo de formas automórficas.
  - Series de Poincaré de Bessel (*Bessel Poincaré series*) sobre un grupo unitario realizan las aplicaciones de períodos en un lugar complejo, y su casi ortogonalidad (*near orthogonality*) produce la desigualdad de pendiente para la familia.
  - En los lugares donde el tipo local de las formas está torcido (*twisted*), las longitudes de los grupos de Tate–Shafarevich (*Tate–Shafarevich groups*) del cuerpo CM acotan los defectos de congruencia (*congruence defects*) que entran en las alturas, mediante representaciones de Galois (*Galois representations*) asociadas a representaciones automórficas de grupos unitarios y teoría de Hodge $p$-ádica (*$p$-adic Hodge theory*).
  - Los dos términos de error se equilibran en $m = \sqrt{x}$, igual que en el argumento de Stepanov.

### 1.2 Relatos contemporáneos (*Contemporaneous accounts*, p. 6)

Varios grupos comenzaron a traducir, cartografiar, explicar o destilar el desarrollo formal pocos días después de su publicación:
- **Zhang [82]:** relato matemático preliminar de la demostración y sus ingredientes principales, con énfasis en fuentes e historia.
- **Rubinstein [59, 60]:** guía de la demostración junto con una exposición detallada del argumento especializado a la función zeta de Riemann; su ejecución de verificación compiló independientemente el desarrollo formal.
- **Naskręcki [49]:** mapa de la demostración formal, estructura, dependencias, registro de estado de verificación y atlas de la ruta.
- **Epstein [25]:** plano (*blueprint*) legible por humanos que identifica los enunciados de nivel superior, separa el núcleo matemático principal del material de biblioteca y traza la estructura de dependencias.
- **Brox [17]:** dirige un programa en curso para destilar y simplificar la demostración formal en demostraciones más cortas legibles por humanos de la hipótesis de Riemann y de la hipótesis de Riemann generalizada para caracteres de Dirichlet.
- **Slijepčević [67]:** esquema de la demostración en lenguaje estándar, incluyendo el argumento de positividad, las estimaciones de levantamientos theta y retículos, las pérdidas aritméticas y la entrada de representaciones de Galois.

El presente artículo expone el argumento como una única demostración convencional continua con sus pasos abiertos enunciados explícitamente, de modo que el lector pueda juzgar sus demostraciones y sus entradas externas citadas sin apelar al desarrollo formal como autoridad matemática.

### 1.3 Cómo se obtuvo este relato (*How this account was obtained*, pp. 6–7)

El desarrollo formal contiene aproximadamente 1,07 millones de declaraciones, de las cuales unas 767.000 yacen en la ruta de dependencias del teorema final, por lo que una demostración legible no puede obtenerse traduciéndolas una a una. Se partió del teorema formal `riemannHypothesis`, rastreando sus dependencias hacia atrás e identificando los enunciados matemáticos de los que depende. Donde una región implementaba un argumento reconocible, se enunció y demostró a su nivel matemático natural; donde la ruta alcanzaba un teorema establecido de la literatura, se citó dicho teorema sin usar el desarrollo formal como justificación. Este proceso no repite la verificación formal de [72] ni implicó leer cada declaración. El autor utilizó Claude (Fable 5.2 y Opus 5.5), GPT (incluyendo GPT 5.6 Pro) y Kimi K3.1 Pro en la reconstrucción. La certificación formal muestra que el término en Lean demuestra el enunciado formal; la reconstrucción redacta el contenido de las dependencias internas como matemáticas, y una comparación separada de cada teorema citado con su enunciado publicado verifica hipótesis, normalizaciones y cuantificadores.

Dos hallazgos de la reconstrucción conciernen a la fuerza de los enunciados internos:
1. La cota para grupos de Tate–Shafarevich en ventanas de escalas (**Hipótesis 17.11**) implica una cota en dirección a la conjetura de Vandiver (*Vandiver's conjecture*) más fuerte que las cotas publicadas de Soulé [68] y de la Torre Durán [22] (**Proposición 17.22**). Una rama de la demostración formal emplea un enunciado de automorfía (*automorphy statement*) para representaciones de Galois residualmente reducibles de tipo unitario en tres variables, **(G3)** de la Subsección 17.4, que queda fuera de las hipótesis de los teoremas publicados de levantamiento de automorfía (*automorphy lifting theorems*) para representaciones residualmente reducibles.
2. La cota para los covolúmenes de los retículos de formas automórficas necesita una constante independiente del nivel de un recubrimiento profundo (*deep cover*) de una variedad de Shimura unitaria, y el argumento la obtiene del teorema aritmético de Hilbert–Samuel (*arithmetic Hilbert–Samuel theorem*) sobre cada modelo de una torre de modelos y de una identidad exacta en los primos buenos, sin una versión uniforme del teorema de Hilbert–Samuel (Subsección 15.14.4).

### 1.4 Organización (*Organization*, p. 7)

Las Secciones 2 a 6 forman la Parte I. La Parte II comienza en la **Sección 7** con los núcleos theta entre retículos hermíticos sobre el cuerpo CM y su covarianza (*covariance*). La **Sección 8** estudia la función theta de una curva elíptica CM en un primo inerte y demuestra la forma de los núcleos en los parámetros de un grupo formal de altura dos. La **Sección 9** clasifica los emparejamientos semilineales (*semilinear pairings*) en ese grupo formal y demuestra la estimación de valuación (*valuation estimate*) para los núcleos. La **Sección 10** convierte esa estimación en divisibilidad de la composición de una cadena de levantamientos. La **Sección 11** construye los levantamientos y demuestra que forman un dato de cadena (*chain datum*). La **Sección 12** demuestra la no degeneración de operadores de Hecke que controla la pérdida, así como las hipótesis (3.1) y (3.2). La **Sección 13** demuestra la desigualdad de pendiente (3.3) para la familia de aplicaciones de períodos, y la **Sección 14** demuestra sus entradas automórficas para series de Poincaré de Bessel. La **Sección 15** calcula el período de la curva CM y demuestra (3.4), (3.6) y (3.7). La **Sección 16** demuestra (3.5). La **Sección 17** trata los lugares torcidos, la cota de Tate–Shafarevich y la cota de congruencia (*congruence bound*). La **Sección 18** construye los datos, los pesos y los nodos, y demuestra el Teorema A a partir de los enunciados de las secciones precedentes; la **Subsección 18.7** recoge las hipótesis utilizadas en la deducción final.

---

# Parte I: Reducción a un teorema aritmético (*Part I: Reduction to an arithmetic theorem*, pp. 7–44)

---

## Sección 2: Cotas unilaterales en ventanas (*One-sided bounds on windows*, pp. 7–11)

### Párrafo introductorio (p. 7)

Esta sección demuestra el criterio analítico del artículo. Una cota superior $G_+(x) \le C x^\theta$ para una combinación positiva de sumas de primos suavizadas, conocida para $x$ en una sucesión dispersa de ventanas $Y \le x \le Y^\lambda$, excluye ceros de $\zeta$ y de las funciones $L$ de Dirichlet correspondientes del semiplano $\operatorname{Re} s > \theta$. La demostración es una forma cuantitativa del teorema de Landau sobre integrales de Dirichlet de funciones de un solo signo [38].

### Definiciones y enunciados principales (pp. 8–11)

- **Definiciones de las sumas suavizadas (`§2.1`, ec. (2.1)–(2.2), p. 8).** Sea $\Lambda$ la función de von Mangoldt y $\gamma$ la constante de Euler. Para $x \ge 1$ se definen:
  $$G(x) = \sum_{n \le x} \Lambda(n)\left(\frac{x}{n} - 1\right) - x\log x + (1+\gamma)x, \tag{2.1}$$
  y para un carácter de Dirichlet no trivial $\chi$:
  $$G_\chi(x) = \sum_{n \le x} \Lambda(n)\operatorname{Re}\chi(n)\left(\frac{x}{n} - 1\right) + \operatorname{Re}\frac{L'(1,\chi)}{L(1,\chi)}\,x. \tag{2.2}$$
  Sus transformadas de Mellin para $\operatorname{Re} s > 1$ son $F(s) = -\frac{\zeta'(s)}{\zeta(s)}\frac{1}{s(s-1)} - \frac{1}{(s-1)^2} + \frac{1+\gamma}{s-1}$ y $\frac{1}{2}(F_\chi(s)+F_{\bar\chi}(s))$ con $F_\chi(s) = -\frac{L'(s,\chi)}{L(s,\chi)}\frac{1}{s(s-1)} + \frac{L'(1,\chi)}{L(1,\chi)}\frac{1}{s-1}$ (ec. (2.3)–(2.4)), meromorfas en $\mathbb{C}$, analíticas en $s=1$, y con polos simples en $\operatorname{Re} s > 0$ exactamente en los ceros $\rho$ con residuos $-m_\zeta(\rho)/(\rho(\rho-1))$ y $-m_\chi(\rho)/(\rho(\rho-1))$ (ec. (2.5)).

- **Lemas preparatorios (`§2.2`, p. 9):**
  - **Lema 2.1 (`Lemma 2.1`):** Acotación de las colas $\int_0^U e^{-au}\frac{u^k}{k!}\,du \le e^{(b-a)U} b^{-k-1}$ ($b>a$) y $\int_U^\infty e^{-au}\frac{u^k}{k!}\,du \le e^{-(a-b)U} b^{-k-1}$ ($0<b<a$).
  - **Lema 2.2 (`Lemma 2.2`):** Para $0 < \varphi < \pi/2$ y $\alpha \in \mathbb{R}$, todo conjunto de $\lceil 2\pi/\varphi\rceil$ enteros consecutivos contiene un entero $j$ con $\cos(\alpha+j\varphi) \ge \frac{1}{2}$.
  - **Lema 2.3 (`Lemma 2.3`):** Dado un conjunto cerrado discreto $P \subset \mathbb{C}$ estable por conjugación compleja y $\rho_0 = \beta_0 + i\gamma_0 \in P$ con $\theta < \beta_0 < 1$, poniendo $\theta' = (\theta+\beta_0)/2$, para todo $\sigma_1 > 1 + (|\rho_0|^2 + \gamma_0^2)/(\beta_0-\theta)$ fuera de un conjunto numerable, los puntos de $P$ a distancia mínima $r$ de $\sigma_1$ verifican $r < \sigma_1 - \theta'$, $\operatorname{Re} p > \theta'$, y forman un único punto real o un único par de conjugados complejos.

- **Teorema 2.4 (`Theorem 2.4`, Teorema de la ventana / *The window theorem*, p. 9).** Sea $H : [1,\infty) \to \mathbb{R}$ medible con $|H(x)| \le Bx$ para una constante $B$, y supóngase que $A(s) = \int_1^\infty H(x) x^{-s-1}\,dx$ (definida para $\operatorname{Re} s > 1$) se extiende a una función meromorfa en $\mathbb{C}$. Sea $0 \le \theta < 1$. Supóngase que todo polo $p$ de $A$ con $\operatorname{Re} p > \theta$ es simple y satisface $\operatorname{Re} p < 1$, y que el residuo de $A$ en todo polo real $p > \theta$ es positivo. Supóngase que existen constantes $\lambda > 1$ y $C$ tales que, para $Y$ arbitrariamente grande, la desigualdad $H(x) \le C x^\theta$ vale para todo $x$ con $Y \le x \le Y^\lambda$. Entonces $A$ no tiene ningún polo en el semiplano $\operatorname{Re} s > \theta$.

- **Corolario 2.5 (`Corollary 2.5`, p. 11).** Sean $\chi_1, \dots, \chi_N$ caracteres de Dirichlet no triviales, sean $w_1, \dots, w_N > 0$, y póngase $G_+ = G + \sum_{i=1}^N w_i G_{\chi_i}$ con $G$ y $G_\chi$ como en (2.1) y (2.2). Sea $0 \le \theta < 1$, y supóngase que existen constantes $\lambda > 1$ y $C$ tales que, para $Y$ arbitrariamente grande, $G_+(x) \le C x^\theta$ para todo $x$ con $Y \le x \le Y^\lambda$. Entonces $\zeta(s) \ne 0$ y $L(s,\chi_i) \ne 0$ para todo $i$ y todo $s$ con $\operatorname{Re} s > \theta$.

---

## Sección 3: La contabilidad y la identidad del exceso (*The accounting and the excess identity*, pp. 11–15)

### Párrafo introductorio (p. 11)

La Parte II asocia a una cadena de $m$ levantamientos theta una familia de retículos hermíticos y demuestra siete desigualdades entre sus pendientes, las alturas de ciertas aplicaciones de períodos y algunos términos locales. Esta sección demuestra que esas siete desigualdades, escritas como desigualdades entre números reales, acotan una suma $S$ sobre primos mediante un término principal explícito. Después demuestra que $S$ menos ese término principal es una combinación de las funciones $G$ y $G_\psi$ de la Sección 2.1. Ambos resultados juntos reducen la aritmética de la Parte II a una cota superior para dicha combinación.

### Enunciados principales (pp. 12–15)

Para $y > 0$ se pone $\operatorname{ph}(y) = y\log y - y$.

- **Proposición 3.1 (`Proposition 3.1`, p. 12).** Sean $m, f, N_T \ge 1$ enteros, $a_1, \dots, a_{N_T}$ y $w_{j\rho}$ ($1 \le j \le m$, $1 \le \rho \le f$) números reales positivos, y $A = \sum_t a_t$. Sean $v > 0$, $\gamma, \lambda_1, g \in \mathbb{R}$, y $\log\Omega = \gamma + \log(\pi/v) - \lambda_1$. Sea $W$ un conjunto finito no vacío, y para $u \in W$ sean $d_u, T_u > 0$ y $\mu_u^N, \mu_u^M, h_u, E_u \in \mathbb{R}$. Sean $\mu^{\mathsf{C}}, \mathcal{L}, \Gamma, S \in \mathbb{R}$ y $e_1, \dots, e_7 \ge 0$. Supóngase que para todo $u \in W$:
  $$S \le \Gamma + e_1, \tag{3.1}$$
  $$\mu_u^M + \Gamma + \mathcal{L} - E_u - e_2 \le \mu_u^N, \tag{3.2}$$
  $$\frac{\sum_{u'} d_{u'}(\mu_{u'}^N - h_{u'})}{\sum_{u'} d_{u'}} - e_3 \le \mu^{\mathsf{C}}, \tag{3.3}$$
  $$\mu^{\mathsf{C}} + h_u - \mathcal{L} \le \sum_{t=1}^{N_T} \bigl(m\operatorname{ph}(a_t) - m a_t \log\Omega - a_t \log T_u\bigr) + e_4, \tag{3.4}$$
  $$E_u \le m A g + e_5, \tag{3.5}$$
  $$\log T_u \ge \sum_{j=1}^m \frac{1}{f}\sum_{\rho=1}^f \log\frac{w_{j\rho} v}{\pi} + mg - e_6, \tag{3.6}$$
  $$\mu_u^M \ge -e_7. \tag{3.7}$$
  Entonces
  $$S \le \sum_{j=1}^m \sum_{t=1}^{N_T} a_t \left(\log a_t - 1 - \gamma + \lambda_1 - \frac{1}{f}\sum_{\rho=1}^f \log w_{j\rho}\right) + e_1 + e_2 + e_3 + e_4 + e_5 + A e_6 + e_7. \tag{3.8}$$

- **Observación 3.2 (`Remark 3.2`, p. 13).** La Proposición 3.1 tiene la estructura de la demostración de Stepanov de la hipótesis de Riemann para curvas sobre cuerpos finitos [70], en la forma de Bombieri [10]. Allí una función auxiliar se anula hasta orden $M$ en cada punto racional, el conteo de ceros frente a polos acota el número $N$ de puntos por $N - 1 \le \ell + nq/M$, y los dos términos de error se equilibran en $M = \sqrt{q}$. Sobre un cuerpo de números, el conteo de ceros frente a polos se convierte en una desigualdad de pendiente del tipo de Bost [15] para una familia de aplicaciones, que es (3.3), y el orden de anulación se convierte en el número $m$ de levantamientos en (3.4). La desigualdad (3.3) acota la pendiente media de un retículo destino mediante las pendientes de las fuentes de una familia redundante de aplicaciones, y el Teorema 13.8 la deduce de la desigualdad de Bost para una aplicación, la filtración de Harder–Narasimhan (*Harder–Narasimhan filtration*) y un conteo de marcos (*frames*) en un lugar complejo. La Sección 4 muestra que los términos de error se equilibran en $m = \sqrt{x}$.

- **Definición del exceso (`§3.2`, ec. (3.9), p. 13).** Sea $H$ un grupo abeliano finito y $\mathcal{G} = (\mathbb{Z}/2)^2 \times H$, con elementos $g = (e_1, e_2, h)$. Se pone $\Phi = \{g \in \mathcal{G} : e_1 = 0\}$, $f = |\Phi| = 2|H|$, y $p_t(e_1, e_2, h) = (e_1+1, e_2+1, h+t)$ ($t \in H$), biyección de $\mathcal{G}\setminus\Phi$ sobre $\Phi$. Para funciones $G_\psi : (0,\infty) \to \mathbb{C}$ indexadas por caracteres $\psi$ de $\mathcal{G}$, $a > 0$, $t \in H$ y $w : \Phi \to (0,\infty)$, el exceso (*excess*) se define por
  $$\operatorname{De}(a, t, w) = \frac{1}{f} \sum_{g \notin \Phi} \sum_\psi \overline{\psi(g)}\, w(p_t g)\, G_\psi\!\left(\frac{a}{w(p_t g)}\right). \tag{3.9}$$

- **Proposición 3.3 (`Proposition 3.3`, Identidad del exceso / *The excess identity*, pp. 13–14).** Sean $H, \mathcal{G}, \Phi, f, p_t$ como arriba. Para cada primo $p$ sean $I_p \le \mathcal{G}$ un subgrupo y $\sigma_p \in \mathcal{G}$. Sean $d$ un primo y $S_0$ un conjunto finito de primos con $d \notin S_0$, suponiendo que $I_p = \{0\}$ para $p \notin S_0 \cup \{d\}$, que $I_p \subset \Phi$ y $\sigma_p \in \Phi$ para $p \in S_0$, y que $I_d = \{0, (1,0,0)\}$. Póngase $\psi(p^i) = |I_p|^{-1}\sum_{h \in I_p}\psi(i\sigma_p + h)$ para $i \ge 1$ y $\psi(n) = 0$ en otro caso. Para todo $\psi$ no trivial sea $\ell_\psi \in \mathbb{C}$ y $G_\psi(y) = \sum_{n \le y}\Lambda(n)\psi(n)(y/n - 1) + \ell_\psi y$, y para $\psi$ trivial sea $G_\psi = G$ de (2.1) extendida a $y > 0$. Sea $\chi_1(e_1, e_2, h) = (-1)^{e_1}$, y para $i \ge 1$ sea $g_i$ el elemento de $i\sigma_d + I_d$ fuera de $\Phi$. Entonces para todo $a > 0$, $t \in H$ y $w : \Phi \to (0,\infty)$:
  $$2\sum_{\substack{p \notin S_0 \cup \{d\} \\ \sigma_p \notin \Phi}} \log p \sum_{i\text{ impar}} \max\!\left(\frac{a}{p^i} - w(p_t(i\sigma_p)),\, 0\right) + \log d \sum_{i \ge 1} \max\!\left(\frac{a}{d^i} - w(p_t g_i),\, 0\right) = a\!\left(\log a - 1 - \gamma + \ell_{\chi_1} - \frac{1}{f}\sum_{\rho \in \Phi}\log w(\rho)\right) + \operatorname{De}(a, t, w). \tag{3.10}$$

- **Corolario 3.4 (`Corollary 3.4`, p. 15).** Con la notación de la Proposición 3.3 y $\ell_{\chi_1} \in \mathbb{R}$, sean $T \subset H$ con $N_T$ elementos, $a_t > 0$ ($t \in T$), $m \ge 1$, y $w_1, \dots, w_m : \Phi \to (0,\infty)$. Sea $S$ la suma sobre $t \in T$ y $1 \le j \le m$ del miembro izquierdo de (3.10) con $a = a_t$ y $w = w_j$. Si $S$ satisface la conclusión (3.8) de la Proposición 3.1 con estos $a_t$, con $w_{j\rho} = w_j(\rho)$ y con $\lambda_1 = \ell_{\chi_1}$, entonces
  $$\sum_{t \in T}\sum_{j=1}^m \operatorname{Re}\operatorname{De}(a_t, t, w_j) \le e_1 + e_2 + e_3 + e_4 + e_5 + A e_6 + e_7.$$

---

## Sección 4: Del exceso a una cota en un punto (*From the excess to a bound at a point*, pp. 15–18)

### Párrafo introductorio (p. 15)

El Corolario 3.4 acota una suma de excesos sobre muchos pesos $a_t$ y muchos nodos $w_j(\rho)$. El Corolario 2.5 necesita una cota superior para una combinación positiva de las funciones $G_\psi$ en un punto $x$. Esta sección demuestra el paso del primero al segundo mediante dos promedios: un promedio sobre traslaciones por un subgrupo $A_0$ de $H$ elimina todo carácter no trivial en $A_0$, y la suma sobre un conjunto $T$ de pesos equidistribuido en un sentido adecuado asigna a cada carácter restante un peso positivo. El coste del paso es el valor $|G_\psi(x)|$ para un número finito de caracteres auxiliares $\psi$, que la Sección 5 acota.

### Enunciados principales (pp. 15–18)

- **Lema 4.1 (`Lemma 4.1`, Regularidad de las sumas suavizadas, p. 15).** Con $G_\psi$ como en la Proposición 3.3 y $\ell_\psi = L'(1,\chi_\psi)/L(1,\chi_\psi)$ ($\ell_1 = 0$), existe una constante absoluta $C_d$ tal que para todo carácter $\psi$ de $\mathcal{G}$: (i) $|w G_\psi(A/w) - w' G_\psi(A/w')| \le 3A|w-w'|/\min(w,w')$ para $0 < w, w' \le A$; (ii) $|G_\psi(y) - G_\psi(x)| \le \log(x+1) + C_d + |\ell_\psi|$ para $x \ge 2$ y $|y-x| \le 1$.

- **Definición de lugares gruesos (`§4.2`, p. 16).** Sea $A_0 \le H$ un subgrupo, $T_2 \subset A_0$ no vacío, y $\delta_2 = |T_2|/|H|$. Para $u_0 \in A_0$, un elemento $\rho = (0, e_2, h) \in \Phi$ se denomina grueso (*thick*) respecto de $u_0$ cuando $e_2 = 1$ y $h \in T_2 + u_0$. Sea $\Psi_0$ el conjunto de caracteres $\psi$ de $\mathcal{G}$ con $\psi(0,0,s) = 1$ para todo $s \in A_0$ ($|\Psi_0| = 4|H/A_0|$).

- **Teorema 4.2 (`Theorem 4.2`, p. 16).** Sea $K \subset \Psi_0$ un conjunto de caracteres que contiene al carácter trivial y satisface $\psi(1,0,0) = 1$ para todo $\psi \in K$. Sea $T \subset H$ con $N_T \ge 1$ elementos, $c, \nu \ge 0$, y supóngase que todo $\psi \in K$ no trivial en $\{0\}\times\{0\}\times H$ verifica
  $$\left|\sum_{t \in T}\psi(0,0,t) - c N_T\right| \le \nu N_T. \tag{4.1}$$
  Póngase $c_\psi = 1$ si $\psi \in K$ es trivial en $\{0\}\times\{0\}\times H$ y $c_\psi = c$ en caso contrario. Sean $x \ge 3$, $b, b', X' > 0$ con $b' X' \le xb$, $\omega, M \ge 0$, $0 \le \eta' \le b$, $m \ge 1$, $a_t > 0$ con $|a_t/b - x| \le 1$, y $w_{u_0,j} : \Phi \to (0,\infty)$ con $b \le w_{u_0,j}(\rho) \le b + \eta'$ cuando $\rho$ es grueso respecto de $u_0$ y $w_{u_0,j}(\rho) \le 2b'$ en otro caso. Suponiendo para todo $\psi$ de $\mathcal{G}$:
  $$|w G_\psi(A/w) - w' G_\psi(A/w')| \le \frac{3A|w-w'|}{\min(w,w')} \quad (0<w,w'\le A), \tag{4.2}$$
  $$|G_\psi(y) - G_\psi(x)| \le M \quad (|y-x|\le 1), \qquad |G_\psi(y)| \le \omega y \quad (y \ge X'/3), \tag{4.3–4.4}$$
  y $\frac{1}{|A_0|}\sum_{u_0 \in A_0}\sum_{t \in T}\sum_{j=1}^m \operatorname{Re}\operatorname{De}(a_t, t, w_{u_0,j}) \le \mathrm{Err}$, entonces
  $$N_T m b\,\frac{\delta_2}{2}\!\left(\sum_{\psi \in K} c_\psi \operatorname{Re} G_\psi(x) - \nu\sum_{\psi \in K}|G_\psi(x)| - \sum_{\psi \in \Psi_0 \setminus K}|G_\psi(x)| - |\Psi_0|M\right) \le \mathrm{Err} + N_T m\bigl(2f\omega(x+1)b + 6f(x+1)\eta'\bigr). \tag{4.5}$$

- **Proposición 4.3 (`Proposition 4.3`, Los tamaños / *The sizes*, pp. 17–18).** Sean $x \ge 3$, $\varepsilon > 0$, $C \ge 0$, enteros $n, N_T, N_2, m \ge 1$ y reales $a, b, k > 0$ tales que
  $$a \le 2xb, \quad N_T \ge \frac{1}{2}x^{-\varepsilon/8} n, \quad x^{-\varepsilon} n \le N_2 \le n, \tag{4.6}$$
  $$x^{1/2-\varepsilon} \le m \le x^{1/2+\varepsilon/2}, \quad xm \le k \le n^2 x^{1/2-\varepsilon}, \quad x^{3\varepsilon/8} \ge 26. \tag{4.7}$$
  Poniendo $\delta_2 = N_2/n$ y
  $$\mathcal{B} = N_T a\!\left(1 + \frac{m^2}{k}\right) + m\!\left(2nmb x^\varepsilon + \frac{N_2 k b x^{2\varepsilon}}{n^2}\right), \tag{4.8}$$
  se cumple $x^{C\varepsilon}\mathcal{B} \le \frac{10}{13} x^{1/2+(C+3)\varepsilon}\cdot N_T m b \frac{\delta_2}{2}$.
  *(Nota estructural del autor: tras dividir por $N_T mb \delta_2/2$, los cuatro términos de $\mathcal{B}$ tienen las formas $x/m$, $xm/k$, $m x^{c\varepsilon}$ y $k x^{c\varepsilon}/(n N_T)$; el primero y el tercero se equilibran en $m = \sqrt{x}$.)*

- **Corolario 4.4 (`Corollary 4.4`, p. 18).** Bajo las hipótesis del Teorema 4.2 y de la Proposición 4.3 con $n = |H|$ y $N_2 = |T_2|$, si además $\mathrm{Err} \le x^{C\varepsilon}\mathcal{B}$, $2f(x+1)\omega \le \frac{1}{x}$, $6f(x+1)\eta' \le \frac{b}{x}$ y $4x^{\varepsilon-1} + \nu\sum_{\psi \in K}|G_\psi(x)| + |\Psi_0|M \le \frac{3}{13}x^{1/2+(C+3)\varepsilon}$, entonces
  $$\sum_{\psi \in K} c_\psi \operatorname{Re} G_\psi(x) \le x^{1/2+(C+3)\varepsilon} + \sum_{\psi \in \Psi_0 \setminus K} |G_\psi(x)|.$$

---

## Sección 5: Los caracteres auxiliares y el cuerpo huésped (*The auxiliary characters and the host field*, pp. 19–41)

### Párrafo introductorio (p. 19)

El Corolario 4.4 deja dos clases de términos: la cota (4.4) en escalas muy grandes y el valor $|G_\psi(x)|$ para los caracteres $\psi \in \Psi_0 \setminus K$. En la aplicación, los caracteres de $\Psi_0 \setminus K$ son productos de caracteres de módulo fijo con los caracteres cuadráticos de dos primos auxiliares $q$ y $d$. Los conductores de estos caracteres exceden toda potencia de $x$, por lo que la cota requerida en un punto $x$ no se sigue de ninguna región libre de ceros para una función $L$ fija. Esta sección elige $q$ y $d$ de modo que la cota valga en toda una ventana de valores de $x$, mediante una media cuadrática sobre una familia de módulos primos. Después construye el cuerpo CM $E$ recortado por $q$, $d$ y el carácter objetivo, junto con el resto de los datos que emplea la parte aritmética del argumento.

### Enunciados clásicos, definiciones y resultados principales (pp. 19–41)

- **Notación y enunciados clásicos (`§5.1`, pp. 19–24):** Se definen $\Theta(u,\chi) = \sum_{n \le u}\Lambda(n)\chi(n)$, $\Theta(u) = \sum_{n \le u}\Lambda(n)$ y $G_\chi^*(y) = \sum_{n \le y}\Lambda(n)\chi(n)(y/n - 1) + \frac{L'(1,\chi)}{L(1,\chi)}y$ (ec. (5.1)), de modo que $G_\chi = \operatorname{Re} G_\chi^*$. Se recogen ocho enunciados clásicos con constantes absolutas: **(C1)** Chebyshev [19]; **(C2)** teorema de los números primos para caracteres [32, 21]; **(C3)** teorema de Page sobre unicidad del cero real excepcional [55, 21]; **(C4)** ceros y fórmula explícita [21]; **(C5)** teorema de densidad de Montgomery [47, Theorem 12.2]; **(C6)** primos $q \equiv 3 \pmod 8$ en $(\sqrt{U}, U]$ [21]; **(C7)** teorema de los números primos en progresiones aritméticas de módulo grande (rango de Linnik, manteniendo el cero excepcional en el término principal), deducido del teorema de Gallagher **(G1)**–**(G2)** [27, Theorem 7] y de **(C8)** distancia de un cero real a $1$, $\beta \le 1 - c_7/(M^{1/2}\log^2 M)$ [21, Ch. 14].

- **Identidades y escalas delgadas (`§5.2`, pp. 25–26):**
  - **Proposición 5.3 (`Proposition 5.3`, p. 25).** Si $\chi$ es un carácter primitivo módulo $N \ge 3$, $\lambda \ge \max(1,\log N)$, $0 < c_* \le \frac{1}{2}$, y $\chi$ no es real o $L(\beta,\chi) \ne 0$ para $\beta \in (1-c_*, 1)$, entonces para todo $y \ge 2$ con $t_0 = \log y$:
    $$\frac{|G_\chi^*(y)|}{y} \le 2 e^{-c_* t_0}\left(1 + \frac{1}{c_*}\right) + C_1 \lambda^4\left(\frac{2\lambda}{c_1} e^{-c_1 t_0/(2\lambda)} + \frac{8}{c_1^2}\sqrt{t_0}\, e^{-c_1\sqrt{t_0}/2}\right).$$

- **Media cuadrática y uniformidad en una ventana (`§5.3`–`§5.4`, pp. 26–28):**
  - **Proposición 5.4 (`Proposition 5.4`, p. 26).** Si $P$ es un conjunto finito de primos $q > Z$, $E_0$ un conjunto finito de enteros libres de cuadrados $s > 1$, y $\left|\sum_{q \in P}\left(\frac{s}{q}\right)\right| \le \eta |P|$ para todo $s$ libre de cuadrados con $1 < s \le Z^2$ y $s \notin E_0$, entonces
    $$\sum_{q \in P}\left|\sum_{n \le Z} c_n \left(\frac{n}{q}\right)\right|^2 \le |P|\left(\sum_{\substack{n,n'\le Z \\ nn' = \square}} |c_n c_{n'}| + \sum_{s \in E_0}\sum_{\substack{n,n'\le Z \\ nn'/s = \square}}|c_n c_{n'}|\right) + \eta |P|\left(\sum_{n \le Z}|c_n|\right)^2.$$
    Se define el conjunto excepcional $S(z, s^*)$ de enteros libres de cuadrados $s > 1$ cuyo mayor divisor sin factores primos $\le z$ es $1$ o $s^*$.
  - **Proposición 5.6 (`Proposition 5.6`, p. 28).** Bajo $0 < \tau \le \frac{1}{2}$, $8 \le Y \le X$, $Z \ge 2X$, $\eta X \log^2 Z \le 1$, $z\log Y \le \sqrt{Y}$ y la cota de cancelación de símbolos de Legendre fuera de $S(z, s^*)$, para $S_q(y) = \sum_{n \le Z}\Lambda(n)\kappa(n)\left(\frac{n}{q}\right)\min(1, y/n)$ con $|\kappa(n)| \le 1$, el número de $q \in P$ con $|S_q(y)| > \frac{1}{2}y^{1/2+\tau}$ para algún $y \in [Y, X]$ es a lo sumo $\frac{16000 c_0^2}{(1-4^{-\tau})^2}|P| Y^{-2\tau}\log(2Y)$.

- **Primer primo auxiliar $q$ (`§5.5`, pp. 29–31):**
  - **Proposiciones 5.7, 5.8 y 5.9 (`Propositions 5.7–5.9`, pp. 29–30):** Cancelación de $\sum_{q \in P}\left(\frac{s}{q}\right)$ fuera de $S(2, s^*)$ para $q \equiv 3 \pmod 8$ en $(e^{z/2}, e^z]$; cota de la cola $T_Z = \sum_{n > Z}\Lambda(n)\chi(n)/n$ y de $|L'(1,\chi)/L(1,\chi)|$ bajo ausencia de ceros en $\operatorname{Re} s > 1 - \frac{1}{400}$, $|\operatorname{Im} s| \le Q$; y acotación de excepciones por densidad de ceros $|B| \le C_3 Q^{3/160}(2\log Q)^{14}$.
  - **Teorema 5.10 (`Theorem 5.10`, p. 30).** Sean $N_0 \ge 1$, $K \ge 1$, $0 < \varepsilon \le \frac{1}{52}$, $0 < \tau \le \frac{1}{2}$. Existe $Y_0$ tal que para todo $Y \ge Y_0$, poniendo $z = Y^{\varepsilon/5}$ y $P = \{q \equiv 3 \pmod 8 \text{ primo} : e^{z/2} < q \le e^z\}$, el conjunto $P$ es no vacío y para todo $q \in P$ fuera de a lo sumo $Y^{-\tau}|P|$ excepciones, todo carácter primitivo $\xi$ de conductor divisor de $N_0$ y $\chi = \xi \cdot \left(\frac{\cdot}{q}\right)$ satisfacen:
    - (i) $L(s,\chi) \ne 0$ para $\operatorname{Re} s > 1 - \frac{1}{400}$ y $|\operatorname{Im} s| \le N_0 e^z$;
    - (ii) $|L'(1,\chi)/L(1,\chi)| \le 401 c_0 K \log Y$;
    - (iii) $|G_\chi^*(y)| \le y^{1/2+\tau}$ para todo $y \in [Y, Y^K]$.

- **Segundo primo auxiliar $d$ (`§5.6`, pp. 31–34):**
  - **Proposición 5.11 (`Proposition 5.11`, p. 32):** Cancelación de $\sum_{d \in P}\left(\frac{s}{d}\right)$ para primos $d \equiv a_0 \pmod{m_0}$ en $(\sqrt{U}, U]$, con $m_0 = 16 q \prod_{2 < p \le z} p$, $a_0 \equiv 7 \pmod{16}$ y $a_0 \equiv -1 \pmod{q\prod_{2<p\le z} p}$, fuera de $S(z, s^*)$.
  - **Teorema 5.12 (`Theorem 5.12`, p. 33).** Sean $N_0 \ge 1$, $K \ge 1$, $0 < \varepsilon \le \frac{1}{52}$, $0 < \tau \le \frac{1}{2}$. Existe $Y_0$ tal que para $Y \ge Y_0$, $z = Y^{\varepsilon/5}$, $q \equiv 3 \pmod 8$ en $(e^{z/2}, e^z]$, $z\log^2 Y \le z' \le K^2 z\log^2 Y$, y $P = \{d \text{ primo} \in (e^{z'/2}, e^{z'}] : d \equiv 7 \pmod{16},\; d \equiv -1 \pmod{q\prod_{2<p\le z} p}\}$, el conjunto $P$ es no vacío y para todo $d \in P$ fuera de a lo sumo $Y^{-\tau}|P|$ excepciones, todo $\xi$ de conductor divisor de $N_0$, $a \in \{0,1\}$ y $\chi = \xi \cdot \left(\frac{\cdot}{q}\right)^a\left(\frac{\cdot}{d}\right)$ satisfacen:
    - (i) $L(s,\chi) \ne 0$ para $\operatorname{Re} s > 1 - \frac{1}{400}$ y $|\operatorname{Im} s| \le N_0 e^{z+z'}$;
    - (ii) $|L'(1,\chi)/L(1,\chi)| \le 401 c_0 K \log Y$;
    - (iii) $|G_\chi^*(y)| \le y^{1/2+\tau}$ para todo $y \in [Y, Y^K]$.
  - **Corolario 5.13 (`Corollary 5.13`, p. 34):** Extiende las regiones libres de ceros de (i) en los Teoremas 5.10 y 5.12 a todo carácter de Dirichlet primitivo real cuyo conductor divide a $2^j M_1 qd$ ($N_0 = 8 M_1$).

- **El cuerpo huésped $E$ (`§5.7`, pp. 34–35):**
  - **Proposición 5.14 (`Proposition 5.14`, pp. 34–35).** Sea $\psi_0$ un carácter de Dirichlet de conductor $M_\psi$ y orden $o$, $e \ge 0$, y $q \ne d$ primos con $q \equiv d \equiv 3 \pmod 4$ que no dividen a $M_\psi$. Póngase $N_1 = \operatorname{lcm}(2^{e+2}, M_\psi)$, $N = N_1 q d$, $U_1 = \{a \in (\mathbb{Z}/N_1)^\times : a \equiv \pm 1 \pmod{2^{e+2}},\; \psi_0(a)=1\}$, $U \le (\mathbb{Z}/N)^\times$ el subgrupo cuya reducción módulo $N_1$ cae en $U_1$ y cuyos elementos son cuadrados módulo $q$ y módulo $d$, $E = \mathbb{Q}(\zeta_N)^U$ y $H = (\mathbb{Z}/N_1)^\times / U_1$. Entonces: (i) $E/\mathbb{Q}$ es de Galois con grupo isomorfo a $(\mathbb{Z}/2)^2 \times H$; (ii) $E$ es un cuerpo CM que contiene a $\sqrt{-q}$ y $\sqrt{-d}$; (iii) la reducción módulo $2^{e+2}$ induce una sobreyección de $H$ sobre el grupo cíclico $(\mathbb{Z}/2^{e+2})^\times/\{\pm 1\}$ de orden $2^e$ cuyo núcleo tiene orden $c \mid o$, de modo que $[E:\mathbb{Q}] = 4n$ con $n = c 2^e$; (iv) la imagen $A_0$ en $H$ de $\ker\psi_0$ es cíclica de índice $o$ y orden $n/o$, la sobreyección de (iii) es inyectiva en $A_0$, y los caracteres de $H$ triviales en $A_0$ son exactamente las potencias de $\psi_0$.
  - Se identifica $\operatorname{Gal}(E/\mathbb{Q}) \cong \mathcal{G} = (\mathbb{Z}/2)^2 \times H$ haciendo corresponder $(-1)^{e_1}$ al signo en $\sqrt{-d}$ y $(-1)^{e_2}$ al signo en $\sqrt{-q}$, de modo que $\Phi$ es el tipo CM (*CM type*) con acción trivial en $\sqrt{-d}$, y $\chi_1$ corresponde a $\chi_{-d} = \left(\frac{-d}{\cdot}\right)$.

- **Los datos restantes (`§5.8`, pp. 35–41):**
  - **Escala (5.17):** $L_\varepsilon = x^\varepsilon$, $b = e^{L_\varepsilon}$, $a = xb$, $X' = \exp(x^{\varepsilon/3})$, $b' = a/X'$, $\delta_1 = x^{-\varepsilon/8}$.
  - **Proposición 5.15 (`Proposition 5.15`, Rangos de la cadena, p. 36):** Para $0 < \varepsilon < \frac{1}{52}$, $x \ge x_0$ y $x^{2+8\varepsilon} \le n \le 2x^{2+8\varepsilon}$, existen enteros pares $m, k$ y un entero impar $t_r$ tales que $\sqrt{x}\delta_1 \le m \le 2\sqrt{x}\delta_1$, $x^{9/2+10\varepsilon} \le k \le 2x^{9/2+10\varepsilon}$, $r + t_r = 8fr + 4 + T_O n_W$ ($r = k+m-1$, $f = 2n$, $T_O = \lceil x^{377}\rceil$), y satisfacen todas las desigualdades de tamaño (4.6)–(4.7) de la Proposición 4.3.
  - **Proposición 5.16 (`Proposition 5.16`, Los nodos, p. 36):** Para nodos $w_j = b_1 + (j+\frac{1}{2})h_0$ ($0 \le j < m$, $h_0 = 2\lceil x^{c_h}\rceil$, $W \le 32 n^2$), acota los casos de lugares gruesos ($\lceil b\rceil \le b_1 < \lceil b\rceil + W$), lugares delgados y lugares en $T$, verificando $6f(x+1)\eta' \le b/x$, $b' X' = xb$ y $2f(x+1)\omega \le 1/x$ con $\omega = \exp(-x^{\varepsilon/8})$.
  - **Proposición 5.17 (`Proposition 5.17`, El conjunto $T_2$ de tipo Behrend, p. 37):** Construye $T_2 \subset \mathbb{Z}_{\ge 0}$ con $4Ls < n_0$, sin soluciones a $j(s_2-s_1) = i(s_3-s_1)$ ($0 < |i|,|j| \le L$, $i \ne j$), y $|T_2| \ge \frac{n_0}{L}\exp(-36\sqrt{\log n_0 \log L})$.
  - **Definición 5.19 (`Definition 5.19`, Órbita buena para $T$, p. 38) y Proposición 5.20 (`Proposition 5.20`, p. 39):** Define cuándo la órbita de $t \in H$ bajo $h \in H$ (de orden $n_h$) es buena (*good*) para $T$ (tres condiciones: (i) cota $K_\varepsilon$ en ventanas de longitud $L_2$; (ii) cota $\nu_1$ en ventanas de longitud $G'$; (iii) patrón periódico en teselas de longitud $(6r_0+1)u$ con celdas impares disjuntas de $P_t$ y celdas pares con exactamente un elemento par). La Proposición 5.20 (combinada con el Lema 5.18) garantiza la existencia de $T \subset H$ con $\frac{1}{2}\delta_1 n \le |T| \le 2\delta_1 n$, equidistribuido en las clases laterales de $A_0$ con $\delta = x^{-1+\varepsilon}$, y con número de órbitas malas $\beta_p(T)$ acotado en promedio por $\sum_{p \in \mathcal{P}} \frac{\log p}{p}\beta_p(T) \le 4 C_b x^{-2}\delta_1 n \sum_{p \in \mathcal{P}}\frac{\log p}{p}$.
  - **Dos familias de primos auxiliares (`§5.8`, pp. 40–41):** Mediante el teorema de Linnik (**Lema 5.21**) se obtienen tres primos distintos $\equiv 1 \pmod M$ acotados por $M^{A(1+A)^2}$; y mediante **(C9)** (teorema de los números primos para una clase de rayo de un cuerpo cuadrático imaginario, deducido de Thorner–Zaman [75, Theorem 1.4] y la cota de Stark [69, Theorem 1']) junto con el **Lema 5.22**, se obtienen dos primos $g_0 \ne g_1 \in [(kb)^8, 2(kb)^8]$ escindidos en $\mathbb{Q}(\sqrt{-d})$ como $g_i = \pi_i\bar\pi_i$ con $\pi_i \equiv 1 \pmod{Q_S q d}$ y conjuntos excepcionales disjuntos $B_r(g_0) \cap B_r(g_1) = \varnothing$.

---

## Sección 6: El teorema aritmético y la demostración de la hipótesis de Riemann (*The arithmetic theorem and the proof of the Riemann hypothesis*, pp. 41–44)

### Párrafo introductorio (p. 41)

Esta sección reúne los datos de la Sección 5 en una sola definición, enuncia el teorema aritmético que demuestra la Parte II, y deduce de él la hipótesis de Riemann y la hipótesis de Riemann generalizada para funciones $L$ de Dirichlet.

### Definición y teoremas principales (pp. 41–44)

Fíjese un carácter de Dirichlet primitivo $\psi_0$ de conductor $M_\psi$ y orden $o$, fíjese $0 < \varepsilon < \frac{1}{52}$ y póngase $N_0 = 8 M_\psi$.

- **Definición 6.1 (`Definition 6.1`, Datos admisibles / *Admissible data*, p. 42).** Sean $x \ge 3$ y $Y \in \mathbb{R}$ con $Y \le x \le Y^{3/2}$. Los datos admisibles a escala $x$ para la ventana $[Y, Y^{3/2}]$ consisten en:
  - **(D1)** Primos $q$ y $d$ que satisfacen los Teoremas 5.10 y 5.12 con $N_0$, $K = \frac{3}{2}$, $\varepsilon$, $\tau = \varepsilon$ y $z' = z\log^2 Y$; un entero $e \ge 0$ con $x^{2+8\varepsilon} \le c 2^e \le 2 x^{2+8\varepsilon}$; y el cuerpo $E$, los grupos $H$ y $A_0$ y el entero $n = |H|$ de la Proposición 5.14 con $\operatorname{Gal}(E/\mathbb{Q}) \cong \mathcal{G} = (\mathbb{Z}/2)^2 \times H$.
  - **(D2)** Enteros $m, k, t_r$ como en la Proposición 5.15(i).
  - **(D3)** Un conjunto $T \subset H$ con las propiedades de la Proposición 5.20 para $\mathcal{P}$ y $h_p$ especificados en la Sección 9.
  - **(D4)** Un conjunto $T_2 = \{s a_0 : s \in T_2'\} \subset A_0$ dado por la Proposición 5.17 con $n_0 = n/o$, $L = L_w$ y $|T_2| \ge x^{-\varepsilon} n$.
  - **(D5)** Dos primos $g_0 \ne g_1$ con $(kb)^8 \le g_i \le 2(kb)^8$, $g_i = \pi_i\bar\pi_i$ con $\pi_i \in \mathbb{Z}[\frac{1+\sqrt{-d}}{2}]$, $\pi_i \equiv 1 \pmod{Q_S q d}$ y $B_r(g_0) \cap B_r(g_1) = \varnothing$; más tres primos distintos congruentes con $1$ módulo $15 Q_S q d$ y acotados por $(15 Q_S q d)^{A_L(1+A_L)^2}$.

- **Proposición 6.2 (`Proposition 6.2`, p. 42).** Existe $Y_0$ tal que para todo $Y \ge Y_0$ y todo $x \in [Y, Y^{3/2}]$, existen datos admisibles a escala $x$ para la ventana $[Y, Y^{3/2}]$.

- **Teorema A (`Theorem A`, El teorema aritmético / *The arithmetic theorem*, pp. 42–43).** Existe una constante absoluta $C \ge 0$ con la siguiente propiedad. Para todo carácter de Dirichlet primitivo $\psi_0$ existe $0 < \varepsilon_1 \le \frac{1}{52}$, y para todo $0 < \varepsilon < \varepsilon_1$ un número $J \ge 2$, tal que para todo $y$ existen números reales $Y_0 \le Y$ con $Y \ge y$ y la propiedad siguiente: para todo $x$ con $Y \le x \le Y^{3/2}$ existen datos admisibles a escala $x$ para la ventana $[Y, Y^{3/2}]$ con base $Y_0$ (Definición 18.1, añadiendo la condición (D6) sobre grupos de Tate–Shafarevich), pesos $a_t$ ($t \in T$) con $a \le a_t \le a + a/(kx^{13})$, y para cada $u_0 \in A_0$ y $1 \le j \le m$ funciones $w_{u_0,j} : \Phi \to (0,\infty)$, tales que:
  - (i) Para todo $u_0 \in A_0$, todo $j$ y todo $\rho \in \Phi$, el nodo $w_{u_0,j}(\rho)$ satisface las cotas de la Proposición 5.16(i) cuando $\rho$ es grueso respecto de $u_0$ para $T_2$, y las de la Proposición 5.16(ii) en caso contrario.
  - (ii) Para todo $u_0 \in A_0$,
    $$\sum_{t \in T}\sum_{j=1}^m \operatorname{Re}\operatorname{De}(a_t, t, w_{u_0,j}) \le x^{C\varepsilon} \mathcal{B}.$$
  Puede tomarse $C = 3$.

- **Teorema 6.3 (`Theorem 6.3`, La hipótesis de Riemann / *The Riemann hypothesis*, p. 43).** Asúmase el Teorema A. Entonces para todo carácter de Dirichlet primitivo $\psi_0$, la función $L(s,\psi_0)$ no se anula en el semiplano $\operatorname{Re} s > \frac{1}{2}$. En particular, $\zeta(s) \ne 0$ para $\operatorname{Re} s > \frac{1}{2}$.

---

# Parte II: Teorema A (*Part II: Theorem A*, pp. 45–282)


---

## Sección 7: Núcleos theta sobre potencias de una curva elíptica CM (*Theta kernels on powers of a CM elliptic curve*, pp. 45–54)

### Párrafo introductorio (p. 45)

Los retículos del Teorema A son espacios de formas automórficas sobre grupos unitarios sobre el cuerpo CM $E$, y las aplicaciones entre niveles consecutivos de la cadena están dadas por núcleos theta (*theta kernels*). Esta sección define los núcleos en el modelo de Fock (*Fock model*), donde son funciones theta sobre una potencia de una curva elíptica CM (*CM elliptic curve*), y demuestra que son covariantes bajo los grupos unitarios racionales de los dos retículos. La covarianza (*covariance*) es la propiedad que hace que un núcleo defina una aplicación entre espacios de formas automórficas. La Sección 9 estudia los mismos núcleos $p$-ádicamente en un primo inerte en $\mathbb{Q}(\sqrt{-d})$.

### Definiciones y enunciados principales (pp. 45–54)

- **Modelo de Fock, retículos admisibles y entrelazadores (`§7.1`–`§7.3`, pp. 45–51):**
  - Para $K = \mathbb{Q}(\sqrt{-d}) \subset E$ y su subcuerpo totalmente real maximal $E^+$, el **Lema 7.1** garantiza que $E/E^+$ es no ramificada en todo lugar finito, los lugares sobre $2$ se escinden en $E$, y la diferente relativa admite una factorización $\mathfrak{d}_{E/K} = \mathfrak{b}\bar{\mathfrak{b}}$ con $\mathfrak{b}+\bar{\mathfrak{b}} = \mathcal{O}_E$.
  - Dado un ideal no nulo $\mathfrak{c} \subset \mathcal{O}_K$, $\delta \in \mathbb{C}^\times$, $\Lambda = \delta\mathfrak{c}$ de área $A = \frac{\sqrt{d}}{2}|\delta|^2 N\mathfrak{c}$, y $\mathfrak{a} = \mathfrak{c}\mathfrak{b}^{-1}$, sobre $V = \prod_{\tau \in \Phi} M_{r'\times r}(\mathbb{C})$ con forma hermítica $H(z,w) = A^{-1}\sum_{\tau \in \Phi}\operatorname{tr}(z_\tau w_\tau^*)$, $E_H = \operatorname{Im} H$, $q(v) = \frac{\sqrt{d}}{2}H(v,v)$, $\alpha(v) = (-1)^{q(v)}$ y $B = \sqrt{d}\operatorname{Re} H - \operatorname{Im} H$, a retículos autoduales $N \subset E^r$, $N' \subset E^{r'}$ se les asocia el retículo admisible (*admissible lattice*) $\Lambda(N, N') = \iota(\mathfrak{a}\operatorname{Hom}(N, N'))$ (**Lema 7.2**).
  - Mediante los operadores de Heisenberg (*Heisenberg group*) $(U_x G)(z) = G(z+x)\exp(-\pi H(z,x) - \frac{\pi}{2}H(x,x))$, se define el espacio de funciones theta $\Theta(\Lambda_1) = \{G \text{ entera en } V : \alpha(x)U_x G = G\;\forall x \in \Lambda_1\}$ (una recta por el hecho clásico de Weil–Mumford **(W1)**) y los operadores entrelazadores (*intertwiners*) $I_{\Lambda_1 \to \Lambda_2}G = n_{12}^{-1/2}\sum_{y \in \Lambda_2/\Lambda_{12}}\alpha(y)U_y G$, cuya composición $I_{\Lambda_2\to\Lambda_3}I_{\Lambda_1\to\Lambda_2} = \mu(\Lambda_1,\Lambda_2,\Lambda_3)I_{\Lambda_1\to\Lambda_3}$ satisface $\mu = 1$ cuando una de las dos familias toma a lo sumo dos valores distintos (**Lemas 7.3–7.5**).
  - **Vector base y núcleos (`§7.3`, ec. (7.1)–(7.4), pp. 50–51):** Se define el vector base (*base vector*) $e(L, L') = \chi(d_L)^{r'/2}\chi(d_{L'})^{-r/2}\theta_{L,L'}$ con $\theta_{L,L'} = I_{(\mathrm{std},\mathrm{std})\to(L,L')}\theta_0$, el núcleo de nivel $c$ en $x \in M_c^A$,
    $$\theta_{N,N'}[c, x] = \alpha(\iota x)U_{-\iota x}G_c(N, N'), \qquad \theta_{N,N'}[\Xi] = \sum_{x \in M_c^A/(M_c^A \cap M_c^B)} \Xi(x)\,\theta_{N,N'}[c, x], \tag{7.2–7.3}$$
    y, pasando a los chorros (*jets*) de Taylor en el origen y al factor de marco (*frame factor*) $\mu(N,\mathrm{fr})$, el núcleo de paso (*step kernel*):
    $$\operatorname{th}(N, \mathrm{fr}, N', \mathrm{fr}', c, x) = \frac{\mu(N,\mathrm{fr})}{\mu(N',\mathrm{fr}')}\, j_{\lambda,\lambda',n}(J_{N,N',c,x}). \tag{7.4}$$

- **Proposición 7.9 (`Proposition 7.9`, Covarianza / *Covariance*, p. 53).** Sean $N \subset E^r$ y $N' \subset E^{r'}$ retículos autoduales de rangos pares, $\gamma \in U_r$, $\gamma' \in U_{r'}$, y $R = R_{\gamma,\gamma'}$ definida por $(Rz)_\tau = \tau(\gamma')z_\tau \tau(\gamma)^{-1}$.
  - (i) $e(\gamma N, \gamma' N') = e(N, N') \circ R^{-1}$.
  - (ii) Para todo $c \ge 1$ y $x \in M_c^A(N, N')$, $\theta_{\gamma N, \gamma' N'}[c, \operatorname{Ad}(\gamma,\gamma')x] = \theta_{N,N'}[c,x] \circ R^{-1}$, y $\theta_{\gamma N, \gamma' N'}[\Xi \circ \operatorname{Ad}(\gamma,\gamma')^{-1}] = \theta_{N,N'}[\Xi] \circ R^{-1}$ para toda $\Xi$ periódica bajo $M_c^A \cap M_c^B$.
  - (iii) Si el carácter de Hecke $\mu$ del factor de marco tiene tipo infinito (*infinity type*) $(e_\tau)$, es trivial en $E^\times$, y satisface $n_\tau + \frac{r'}{2} - e_\tau = k(\lambda_\tau)$ y $e_\tau - \frac{r}{2} = -k(\lambda'_\tau)$ para todo $\tau \in \Phi$, entonces
    $$\operatorname{th}(\gamma N, \gamma\mathrm{fr}, \gamma' N', \gamma'\mathrm{fr}', c, \operatorname{Ad}(\gamma,\gamma')x) = \rho_{\lambda'}(\gamma') \circ \operatorname{th}(N, \mathrm{fr}, N', \mathrm{fr}', c, x) \circ \rho_\lambda(\gamma)^{-1}.$$
  *(Así el núcleo de paso entrelaza las representaciones $\rho_\lambda$ y $\rho_{\lambda'}$ de los grupos unitarios racionales, y sumar sobre clases con pesos $1/\#\mathrm{Stab}$ define el levantamiento $K_j$.)*

---

## Sección 8: La función theta en un primo inerte (*The theta function at an inert prime*, pp. 54–68)

### Párrafo introductorio (p. 54)

La Sección 9 estudia una serie de la forma $\exp(-\sum \beta(x, y)) U$ en los parámetros del grupo formal de altura dos, con $U$ integral y $\beta$ un emparejamiento biaditivo y semilineal respecto de Frobenius módulo series con exponencial integral. Esta sección demuestra que los núcleos theta de la Sección 7 tienen esta forma en un primo inerte en $\mathbb{Q}(\sqrt{-d})$. Comienza con la función theta de una variable, construye $\beta$ como el coborde del logaritmo de la función theta reducida (*reduced theta function*) y demuestra las propiedades de $\beta$ requeridas por el Teorema 9.3. Luego pasa a funciones theta de retículos hermíticos, primero en coordenadas a lo largo de una base ortonormal del retículo en $p$ y después en coordenadas hiperbólicas (*hyperbolic coordinates*), demostrando la forma $c\exp(-\sum \beta(x, y)) U$ en el Teorema 8.21.

### Definiciones y enunciados principales (pp. 54–68)

- **Función theta reducida y modelo integral (`§8.1`–`§8.4`, pp. 54–60):**
  - Para un retículo $\Lambda \subset \mathbb{C}$ de área $A$, mediante el número único $s_2(\Lambda)$ con $\eta(\omega) = s_2\omega + \frac{\pi}{A}\bar\omega$ (**Lema 8.1**), se define la función theta reducida $\theta(z) = \sigma_\Lambda(z) e^{-s_2(\Lambda) z^2/2}$ (función impar entera con ceros simples en $\Lambda$, $\theta'(0)=1$ y factor de automorfía dado por el **Lema 8.2**).
  - **Proposición 8.4 (`Proposition 8.4`, p. 57).** Para $K = \mathbb{Q}(\sqrt{-d})$ ($d \equiv 7 \pmod{16}$), $\Lambda \subset \mathbb{C}$ con $\mathcal{O}_K\Lambda \subset \Lambda$ y $g_2(\Lambda)^3 - 27 g_3(\Lambda)^2 = 1$, $p \ge 5$ inerte en $K$, $W = W(\overline{\mathbb{F}}_p)$, $K_0 = W[1/p]$ y un isomorfismo $\iota : \mathbb{C} \to \mathbb{C}_p$, existen un número algebraico $u$ y elementos $G_2, G_3$ del cuerpo de clases de Hilbert de $K$ con $G_2 = u^4 g_2(\Lambda)$, $G_3 = u^6 g_3(\Lambda)$ tales que $\iota(G_2), \iota(G_3) \in W$, $\iota(G_2^3 - 27 G_3^2) \in W^\times$ y $|\iota(u)| = 1$. Esto define una curva elíptica lisa y propia $\mathcal{E}: y^2 = 4x^3 - G_2 x - G_3$ sobre $W$ con parámetro local $T = -2x/y$ y logaritmo formal $\ell(T)$.
  - Se define $\Upsilon(T) = -\log\frac{\theta(u\ell(T))}{uT}$ (ec. (8.5)), la relación de equivalencia $B \simeq B'$ cuando $\exp(B - B')$ es integral, y el coborde $\delta\Upsilon(S, T) = \Upsilon(S +_{\mathcal{E}} T) - \Upsilon(S) - \Upsilon(T)$.
  - **Proposiciones 8.8, 8.9 y 8.10 (`Propositions 8.8–8.10`, p. 60):** (8.8) Integridad de $H_t(T) = uT k_t(u\ell(T))$ para $t$ de torsión prima a $p$; (8.9) $\Upsilon([a](T)) \simeq a\bar a\,\Upsilon(T)$ para $a \in \mathcal{O}_K$ con $a\bar a$ impar y primo a $p$; (8.10) biaditividad $\delta\Upsilon(T_1 +_{\mathcal{E}} T_2, T_3) \simeq \delta\Upsilon(T_1, T_3) + \delta\Upsilon(T_2, T_3)$ y adjunción $\delta\Upsilon([a](S), T) \simeq \delta\Upsilon(S, [\bar a](T))$.

- **Emparejamiento en coordenadas de Lubin–Tate (`§8.5`–`§8.6`, pp. 61–64):**
  - **Proposición 8.11 (`Proposition 8.11`, p. 61).** Existen $\varepsilon \in W^\times$ y una serie $\kappa \in W[[T]]$ con $\kappa(0)=0$, $\kappa'(0) \in W^\times$, tales que $\operatorname{lg}(\kappa(T)) = \varepsilon \ell(T)$, donde $\operatorname{lg}$ es el logaritmo de la ley de grupo formal $F$ de altura dos sobre $\mathbb{Z}_p$ de la Sección 9.1. Se ponen $\Upsilon_F = \Upsilon \circ \kappa^{-1}$ y $\beta(X, Y) = \Upsilon_F(F(X,Y)) - \Upsilon_F(X) - \Upsilon_F(Y)$ (ec. (8.6)).
  - **Teorema 8.12 (`Theorem 8.12`, p. 62).** La serie $\beta$ satisface: (i) todo monomio contiene ambas variables; (ii) $\beta(F(X_0,X_1), X_2) \simeq \beta(X_0,X_2) + \beta(X_1,X_2)$ y análogamente en la segunda variable; (iii) $\beta([\alpha]_F X, Y) \simeq \beta(X, [\sigma\alpha]_F Y)$ para todo $\alpha \in \mathbb{Z}_{p^2}^\times$; (iv) $\Upsilon_F([\alpha]_F X) \simeq \alpha\sigma(\alpha)\Upsilon_F(X)$. En particular $\beta$ verifica las hipótesis (i)–(iii) del Teorema 9.3 con $K = K_0$.
  - **Proposición 8.15 (`Proposition 8.15`, p. 64):** Invarianza unitaria $\sum_{i=1}^m \Upsilon(T'_i) \simeq \sum_{j=1}^m \Upsilon(T_j)$ bajo cambios unitarios sobre $\mathbb{Z}_{p^2}$.
  - **Proposición 8.16 (`Proposition 8.16`, p. 64):** Para un par hiperbólico $(f, f')$ de tamaño $m$ sobre $\mathbb{Z}_{p^2}$ y $T_i = \sum_e [f_{e,i}](X_e) +_{\mathcal{E}} \sum_e [f'_{e,i}](Y_e)$, se tiene $\sum_{i=1}^{2m} \Upsilon(T_i) \simeq \sum_{e=1}^m \delta\Upsilon(X_e, Y_e)$.

- **Funciones theta de retículos hermíticos y ley del núcleo (`§8.7`–`§8.8`, pp. 65–68):**
  - **Teorema 8.19 (`Theorem 8.19`, p. 66).** Sea $(M, h)$ un $\mathcal{O}_K$-retículo hermítico definido positivo de rango $n$ con base ortonormal $b_1, \dots, b_n$ de $M_p$, $L \subset V_M$ un retículo con $N L_M \subset L \subset N^{-1} L_M$ ($p \nmid N$), $\alpha: L \to \{\pm 1\}$ semicaracter para $\operatorname{Im} H_M$, y $G \in \Theta(L, \alpha)$ con coeficientes de Taylor algebraicos en $0$. Entonces $\Psi_G(T_1, \dots, T_n) = \exp(\sum_{i=1}^n \Upsilon(T_i))\cdot G(\sum_{i=1}^n b_i \otimes u\ell(T_i))$ tiene coeficientes acotados en valor absoluto, es decir $\Psi_G = c U$ con $c \in \mathbb{C}_p^\times$ y $U$ integral.
  - **Teorema 8.21 (`Theorem 8.21`, Ley del núcleo / *The kernel law*, pp. 67–68).** En el contexto del Teorema 8.19, supóngase $M_p = P \oplus P^\perp$ descomposición ortogonal donde $P^\perp$ posee base ortonormal y $P$ posee base hiperbólica $f_1,\dots,f_m, f'_1,\dots,f'_m$. Definiendo $\Theta(x,y) = G(\sum_{e=1}^m (f_e \otimes u\varepsilon^{-1}\operatorname{lg}(x_e) + f'_e \otimes u\varepsilon^{-1}\operatorname{lg}(y_e)))$, existen $c \in \mathbb{C}_p^\times$ y una serie integral $U(x,y)$ tales que
    $$\Theta(x, y) = c \exp\!\left(-\sum_{e=1}^m \beta(x_e, y_e)\right) U(x, y).$$
  - **Corolario 8.22 (`Corollary 8.22`, p. 68).** Con el cambio a coordenadas de órbita $\Theta^\flat(X) = G(\sum_{r,a,b}(f_{r,a,b}\otimes u\varepsilon^{-1}\Lambda_{r,a,b}(X) + f'_{r,a,b}\otimes u\varepsilon^{-1}\Lambda'_{r,a,b}(X)))$, existe una familia $\upsilon$ en $W$ con $|\upsilon_s| \le 1$ tal que $c^{-1}\Theta^\flat(\varpi X) \in \mathcal{C}(h_\upsilon)$, sirviendo de entrada a la Sección 9.

---

## Sección 9: Divisibilidad en primos inertes (*Divisibility at inert primes*, pp. 69–78)

### Párrafo introductorio (p. 69)

Sea $p$ un primo inerte en $\mathbb{Q}(\sqrt{-d})$. Una curva elíptica con multiplicación compleja por los enteros de $\mathbb{Q}(\sqrt{-d})$ y buena reducción en $p$ posee un grupo formal de altura dos, y la conjugación compleja actúa sobre sus endomorfismos como el Frobenius de $\mathbb{Q}_{p^2}$. Esta sección demuestra que el núcleo theta de un levantamiento, escrito en las variables de una órbita de Frobenius (*Frobenius orbit*), es divisible por una potencia de $p$ cuyo término principal en una cima (*top*) de peso $\alpha$ es $\alpha p/(p^2-1) = \sum_{i\text{ impar}}\alpha/p^i$ (coincidiendo con la contribución de un primo inerte a $S$ en §3.2). El argumento consta de tres pasos algebraicos que no hacen referencia a funciones theta: §9.1 clasifica los emparejamientos biaditivos y semilineales para Frobenius módulo factores de exponencial integral; §9.2 define una clase de series de potencias construida a partir de tal emparejamiento; §9.3 acota inferiormente la valuación de todo emparejamiento de una serie de esa clase con un producto de menores.

### Definiciones y teoremas principales (pp. 69–75)

En toda la sección $p \ge 5$, $K$ es un cuerpo completo de característica cero con valor absoluto ultramétrico $|p|=p^{-1}$, $\operatorname{ord} = -\log_p|\cdot|$, $\gamma_p = \frac{p}{p^2-1} = \sum_{e \ge 0} p^{-(2e+1)}$ y $\rho_p = \frac{1}{p^2-1}$.

- **Emparejamientos en el grupo formal de altura dos (`§9.1`, pp. 69–71):** Se definen $\operatorname{lg}(X) = \sum_{j \ge 0} p^{-j} X^{p^{2j}}$, $\operatorname{lg}^*(X) = \frac{1}{p}\operatorname{lg}(X^p)$, $\mathcal{A}(X,Y) = \sum_{0 \le i \le j} p^{-(i+j+1)} X^{p^{2i}} Y^{p^{2j+1}}$ y $Q_{c,c'}(X,Y) = c\mathcal{A}(X,Y) - c'\mathcal{A}(Y,X)$, con ley de grupo formal $F(X,Y)$ de altura dos.
  - **Teorema 9.3 (`Theorem 9.3`, p. 71).** Supóngase que $K$ es completo, $|K^\times| = p^{\mathbb{Z}}$, $K$ contiene una raíz primitiva de la unidad de orden $p^2-1$, y $\sigma$ es un endomorfismo de anillos de $K$ con $|\sigma a - a^p| \le p^{-1}$ para $|a|\le 1$. Sea $\beta$ una serie en dos variables sobre $K$ tal que: (i) todo monomio de $\beta$ contiene ambas variables; (ii) $d_F\beta \simeq 0$ y $d_F\beta^{\mathrm{sw}} \simeq 0$; (iii) $\beta(\zeta X, Y) \simeq \beta(X, \zeta^p Y)$ para todo $\zeta \in K$ con $\zeta^{p^2-1}=1$. Entonces existe $c \in K$ con $|c| \le 1$ y $\sigma^2 c = c$ tal que $\beta \simeq Q_{c,\sigma c}$.

- **La clase $\mathcal{C}(h_\upsilon)$ de un núcleo (`§9.2`, pp. 72–73):** Fijados $\nu \ge 1$ y $r_0, r_1 \ge 0$, con variables $X_{s,a,b}$ ($s \in \mathbb{Z}/2\nu$), se definen $S_{s,a,b} = \sum_{l \ge 0}(-1)^l X_{s-2l,a,b}^{p^{2l}}$, $h_\upsilon = \sum_s \upsilon_s \sum_{a,b} S_{s,a,b}^p S_{s+1,a,b}$ (ec. (9.3)), y la clase $\mathcal{C}(h)$ de series $\Theta = \sum_{i \ge 0} p^{-i} h^i g_i$ con $g_i$ integrales (ec. (9.4)).
  - **Teorema 9.4 (`Theorem 9.4`, pp. 72–73).** Para $W = W(\overline{\mathbb{F}}_p)$, $K \supset W[1/p]$ conteniendo $\varpi$ con $\varpi^{p^2-1}=p$, $\mathcal{O}=W[\varpi]$, bases duales $\omega_r, \omega_r^* \in W$ fijadas por $\sigma^{2\nu}$, $\lambda(T) = \varpi^{-1}\operatorname{lg}(\varpi T)$, $\mu = \lambda^{-1}$, $\Lambda_{r,a,b} = \sum_{s\text{ par}}\sigma^s(\omega_r^*)X_{s,a,b}$ y $\Lambda'_{r,a,b} = \sum_{s\text{ impar}}\sigma^s(\omega_r)X_{s,a,b}$, y $c \in W$ con $\sigma^2 c = c$, existe una serie $V$ sobre $\mathcal{O}$ tal que $\sum_{r,a,b}(c\mu(\Lambda_{r,a,b})\mu(\Lambda'_{r,a,b})^p - \sigma(c)\mu(\Lambda'_{r,a,b})\mu(\Lambda_{r,a,b})^p) = h_\upsilon + pV$ con $\upsilon_s = c$ ($s$ impar) y $\upsilon_s = -\sigma(c)$ ($s$ par).
  - **Proposición 9.5 (`Proposition 9.5`, p. 73).** Si $\beta$ satisface (i)–(iii) del Teorema 9.3, $U$ es integral y $x_{r,a,b} = \operatorname{lg}^{-1}(\Lambda_{r,a,b})$, $y_{r,a,b} = \operatorname{lg}^{-1}(\Lambda'_{r,a,b})$, entonces $\vartheta(X) = \exp(-\sum_{r,a,b}\beta(x_{r,a,b}, y_{r,a,b})) U(x,y)$ satisface $\vartheta(\varpi X) \in \mathcal{C}(h_\upsilon)$ para cierta familia $\upsilon$ en $W$ con $|\upsilon_s| \le 1$.

- **La estimación de valuación (`§9.3`, pp. 74–75):** Para un polinomio $P$ y una serie $\Theta$ se define $\langle P, \Theta\rangle = (P(\partial)\Theta)(0)$. Dada una forma (*shape*) con conjunto de cimas $\mathcal{T}$, columnas de altura $h_{s,c} \le r_0$ y operador $P_I = \prod_s \prod_{c < n_s}\det(\sum_a y_{s,i,a} X_{s,a,I_{s,c}(i')})$, se definen $\alpha_s$ (número de columnas de altura $1$ si $s \in \mathcal{T}$, $0$ si no), $\operatorname{cap}_s = n_s - \alpha_s$, $\lambda_s = \sum_c h_{s,c} - \alpha_s$, $\mathcal{E}(s) = \{s'-s \bmod 2\nu : s' \in \mathcal{T} \text{ de paridad opuesta}\}$, $\Delta = \sum_s (r_1 \operatorname{lg}_p(\alpha_s) + r_0 r_1 \operatorname{lg}_p(\lambda_s)) + \sum_{s \in \mathcal{T}} \operatorname{lg}_p(\alpha_s)^2$ (ec. (9.5)), y las cotas:
  $$g^A = \sum_{s \in \mathcal{T}} \sum_{\substack{e \ge 0 \\ 2e+1 \notin \mathcal{E}(s)}} \max\!\left(\frac{\alpha_s}{p^{2e+1}} - \operatorname{cap}_{s+2e+1},\, 0\right) - \Delta, \tag{9.6}$$
  $$g^B = \gamma_p \sum_{s \in \mathcal{T}_{\mathrm{ev}}} \alpha_s + \sum_{s \in \mathcal{T}_{\mathrm{odd}}} \sum_{e \ge 0} \max\!\left(\frac{\alpha_s}{p^{2e+1}} - \operatorname{cap}_{s+2e+1},\, 0\right) - \Delta. \tag{9.7}$$
  - **Teorema 9.6 (`Theorem 9.6`, p. 75).** Sea $\varpi \in K$ con $\varpi^{p^2-1}=p$, $|\upsilon_s| \le 1$, y $\Theta$ una serie sobre $K$ con $\Theta(\varpi X) \in \mathcal{C}(h_\upsilon)$. Entonces todo coeficiente $c$ de $\langle P_I, \Theta\rangle$ en las variables de marco satisface:
    - (i) $\operatorname{ord}(c) \ge g^A$;
    - (ii) $\operatorname{ord}(c) \ge g^B - \sum_{s \in \mathcal{T}_{\mathrm{ev}}}\alpha_s$;
    - (iii) Para $J \subset \{0, \dots, r_1-1\}$ y $N_J$ el conteo ponderado de columnas respecto de $J$, $\operatorname{ord}(p^{N_J} c) \ge g^B$.

---

## Sección 10: Divisibilidad a lo largo de la cadena (*Divisibility along the chain*, pp. 78–86)

### Párrafo introductorio (p. 78)

El Teorema 9.6 acota los emparejamientos de un núcleo con productos de menores en una órbita de Frobenius. Esta sección convierte tales cotas en divisibilidad de la composición de los levantamientos sobre formas integrales. El argumento es algebraico sobre espacios de funciones en retículos y usa tres propiedades de los levantamientos: cada levantamiento es una suma finita sobre clases de aplicaciones definidas por núcleos con denominadores acotados; una cota sobre los emparejamientos de un núcleo implica que la aplicación del núcleo, normalizada por la potencia de $p$ de un operador de Hecke, envía la estructura integral de la fuente a un múltiplo de la del destino; y un polinomio en los operadores de Hecke de una órbita conmuta con la composición de los levantamientos salvo una potencia explícita de $p$. Estas propiedades se enuncian en una definición y se demuestra la divisibilidad a partir de ellas.

### Definiciones y enunciados principales (pp. 79–86)

Sea $\mathcal{O}$ un anillo de valuación discreta completo de característica cero, característica residual $p$, cuerpo de fracciones $K$, uniformizante $\pi$ y valuación $\operatorname{ord}(p)=1$. Para $g \in \mathbb{R}$ se escribe $p^g H = \pi^{\lceil g e \rceil} H$.

- **Definición 10.1 (`Definition 10.1`, Dato de cadena / *Chain datum*, p. 79).** Un dato de cadena sobre $\mathcal{O}$ consta de $m \ge 1$, un conjunto finito $\mathcal{V}$ de órbitas, un entero $r \ge 1$, y para cada nivel $0 \le j \le m$: (a) un conjunto $\mathcal{L}_j$ de tuplas de retículos, un conjunto finito $C_j$ de componentes, un $K$-espacio vectorial finito-dimensional $X_j$, y grupos $\Gamma_{j,c}$ actuando en $\mathcal{L}_j$ y linealmente en $X_j$; (b) $\mathcal{O}$-retículos equivariantes $H_j(L) \subset X_j$; (c) familias finitas equivariantes de aristas $E^j_{v,i}(L)$ y exponentes $n^j_{v,i}$ ($0 \le i \le r$) que definen los operadores de Hecke $(T^j_{v,i} F)(c, L) = p^{n^j_{v,i}} \sum_{L'' \in E^j_{v,i}(L)} F(c, L'')$ en el espacio de formas $\mathcal{F}_j$ (con formas integrales $\operatorname{Int}_j$); junto con aplicaciones lineales $K_j : \mathcal{F}_j \to \mathcal{F}_{j+1}$ (*levantamientos* / *lifts*) que satisfacen **(D1)**: existen enteros $d_j \ge 0$ y aplicaciones $\kappa_j(c,L; c',L') : X_j \to X_{j+1}$ tales que $(K_j F)(c',L') = \sum_x w_x^{-1}\kappa_j(c_x, L_x; c', L')(F(c_x, L_x))$ con $\operatorname{ord}(w_x) \le d_j$. Se denota $\mathcal{K}_j = K_{j-1} \circ \dots \circ K_0$.

- **Definición 10.2 (`Definition 10.2`, Cota de entrada / *Entry bound*, p. 79) y Proposición 10.3 (`Proposition 10.3`, p. 80).** Un dato de cadena tiene cota de entrada $g$ en $(j, i_0)$ cuando $p^{n^{j+1}(i_0)}\kappa_j(c,L; c', L'')(H_j(L)) \subset p^g H_{j+1}(L')$ para todo $L'' \in E^{j+1}_{i_0}(L')$. La Proposición 10.3 establece que en ese caso $T^{j+1}_{i_0} K_j(\operatorname{Int}_j) \subset p^{g - d_j}\operatorname{Int}_{j+1}$.

- **Definición 10.4 (`Definition 10.4`, Datos de conmutación de Hecke / *Hecke commutation data*, p. 80).** Consisten en: **(D2)** operadores lineales conmutativos $y_v$ en $\mathcal{F}_0$ que preservan $\operatorname{Int}_0$; **(D3)** para cada $v \in \mathcal{V}$ y $1 \le j \le m$, $\rho_{v,j} \in K^\times$, $\epsilon_{v,j} \in \mathcal{O}^\times$, $\alpha(v,j) \ge 0$ y $c_{v,j,l} \in \mathcal{O}$ ($0 \le l \le r$) con $\operatorname{ord}(c_{v,j,r}) \ge \alpha(v,j)$, tales que $Z_{v,j} = \sum_{l=0}^r (-1)^l c_{v,j,l}\epsilon_{v,j}^{-(r-l)} T^j_{v,r-l}$ satisface $Z_{v,j}\mathcal{K}_j(F) = \rho_{v,j}\mathcal{K}_j(y_v F)$. El precio (*price*) es $\operatorname{Pr}(v, j) = \operatorname{ord}(\rho_{v,j})$.

- **Definición 10.5 (`Definition 10.5`, Cotas de órbita / *Orbit bounds*, p. 80).** El dato tiene cotas de órbita $(g^0, g^1, \alpha)$ cuando tiene cota de entrada $\sum_v b_v$ en $(j, i_0)$ siempre que $b_v \le g^1(v, j+1)$ si $i_0(v) \ge 1$ y $b_v \le \max(g^0(v, j+1), g^1(v, j+1) - \alpha(v, j+1))$ si $i_0(v) = 0$.

- **Teorema 10.7 (`Theorem 10.7`, Divisibilidad de la composición, p. 81).** Sea un dato de cadena con datos de conmutación de Hecke y cotas de órbita $(g^0, g^1, \alpha)$. Sean $B \subset \mathcal{V}$, $\operatorname{PR}(v,j) \ge \operatorname{Pr}(v,j)$ y $S(v) \ge \sum_{j=1}^m \max(g^1(v,j) - \operatorname{PR}(v,j) - g^0(v,j),\, 0)$ ($v \in B$, ec. (10.2)). Para $B' \subset B$, $y_{B'} = \prod_{v \in B'} y_v$ y $F = y_{B'}^m F_0$ con $F_0 \in p^{\sum_{v \in B\setminus B'} S(v)}\operatorname{Int}_0$, se cumple $\mathcal{K}_m(F) \in p^T \operatorname{Int}_m$ con
  $$T = \sum_{j=1}^m\left(\sum_{v \in B}\max\bigl(g^1(v,j) - \operatorname{PR}(v,j),\, g^0(v,j)\bigr) + \sum_{v \notin B} g^0(v,j)\right) - \sum_{j=0}^{m-1} d_j.$$
  Lo mismo vale para todo $F$ en el $\mathcal{O}$-espacio generado por tales formas al variar $B'$.

- **Relación de Hecke de un levantamiento a la cadena (`§10.3`–`§10.4`, pp. 82–86):**
  - **Proposición 10.8 (`Proposition 10.8`, p. 82):** Si los operadores normalizados $E_i^{(j)} = q^{-i(N_j-i)} T^j_{v,i}$ satisfacen la relación de un paso $E_i^{(j+1)} K_j(F) = u_{j+1}^i \sum_{l=0}^i e_l(x_{j+1}) K_j(E_{i-l}^{(j)} F)$ (ec. (10.3)), entonces a lo largo de la cadena vale la identidad polinómica con polinomios simétricos completos $h_l(Y_j)$: $\sum_{l=0}^r (-1)^l h_l(Y_j) q^{l(N_j - 2r + l)} T^j_{v, r-l}\mathcal{K}_j(F) = U_j^r q^{r(N_j - N_0)}\mathcal{K}_j(T^0_{v,r} F)$.
  - **Definición 10.12 (`Definition 10.12`, Núcleos escindidos en la órbita $v$ / *Split kernels*, pp. 84–85):** Axiomas **(S1)** (aristas de tipo $i$ en $L_v \subset \mathbb{Q}_v^{N_j}$ con $N_{j+1}=N_j+g$), **(S2)** (expresión de $K_j$ como suma sobre órbitas con pesos $|\Gamma_{j,c,L}|^{-1}$ y covarianza) y **(S3)** (factorización $\kappa_j(c,L; c',L') = p^{\mu(\operatorname{len} L_v - \operatorname{len} L'_v)} a^{\operatorname{len} L_v} a'^{\operatorname{len} L'_v} q^{-(N_j\operatorname{len} L'_v - N_{j+1}\operatorname{len} L_v)}\Xi(\cdot; 1_{L_v, L'_v})$).
  - **Proposición 10.13 (`Proposition 10.13`, p. 85):** Si un dato de cadena tiene núcleos escindidos en $v$, entonces vale la relación de un paso (10.3) para los operadores brutos $T^{\mathrm{raw}, j}_{v,i}$ con $u_{j+1} = (aa')^{-1}$, $m_{j+1} = a p^\mu$ y $t = g - 1$.

---

## Sección 11: Los levantamientos forman un dato de cadena (*The lifts form a chain datum*, pp. 86–106)

### Párrafo introductorio (p. 86)

Esta sección define las tuplas de retículos, las estructuras integrales y los levantamientos de la cadena en un primo inerte, y verifica para ellos los axiomas de un dato de cadena de la Sección 10. La verificación utiliza tres enunciados: **(N1)** sobre la normalización del factor de marco, **(N2)** sobre el paso de entradas a retículos en las posiciones impares, y **(N3)** sobre la normalización de la función theta base. El Teorema 11.45 ensambla la verificación de modo que el Teorema 10.7 se aplica a la composición de los levantamientos.

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 86–106)

- **Modelos polinomiales, retículos mínimos, componentes y operadores de Hecke (`§11.1`–`§11.2`, pp. 86–92):**
  - **Definición 11.1 (`Definition 11.1`, p. 87):** Modelo polinomial (*polynomial model*) $V_\nu \subset K[X]$ de peso dominante $\nu$ para $\mathrm{GL}_n$, bideterminantes canónicos $\Delta_{S_1}\cdots\Delta_{S_{\nu_1}}$ y retículo mínimo (*minimal lattice*) $W_\nu \subset V_\nu$ (módulo de Weyl sobre $\mathcal{O}$). El **Teorema 11.2 (Green; De Concini–Eisenbud–Procesi)** garantiza que $W_\nu$ es libre con base los bideterminantes estándar y estable bajo $\mathrm{GL}_n(\mathcal{O})$.
  - **Definición 11.3 (`Definition 11.3`, p. 88):** Retículo integral $H_s(\Lambda) \subset V_{\nu^\natural}$ en una posición $(v, s)$ de una órbita, y producto tensorial $H_j(L) = \bigotimes_{v,s} H_s(L_v) \subset X_j$.
  - **Definición 11.5 (`Definition 11.5`, La cadena en $p$, pp. 88–89):** Define las tuplas de retículos $\mathcal{L}_j$, componentes $C_j$ con marcos $\varphi_{c,v}$ y retículos globales autoduales $N_j(c,L) \subset E^{N_j}$, grupos unitarios $\Gamma_{j,c}$ y acciones $\rho_{j,c}$, formando $\mathcal{F}_j$ y $\operatorname{Int}_j$.
  - **Definición 11.7 (`Definition 11.7`, Operadores de Hecke, p. 89):** Define los operadores brutos $T^{\mathrm{raw},(j)}_{v,i}$, los exponentes normalizadores $N'_v(j,i)$ (ec. (11.3)), $T^{(j)}_{v,i} = p^{N'_v(j,i)} T^{\mathrm{raw},(j)}_{v,i}$, y $y_v = p^{A_v} T^{\mathrm{raw},(0)}_{v,r}$ (verificando (D2) en el **Lema 11.8**).
  - **Definición 11.9 (`Definition 11.9`, Serie del núcleo y aplicación de paso, pp. 90–91) y Definición 11.10 (`Definition 11.10`, Levantamientos como sumas de clases, p. 91):** Define la serie de potencias del núcleo $\mathcal{K}_j(c,L;c',L')$ con normalización escalar $s_j$, la aplicación de paso $\kappa_j$, y el levantamiento $(K_j F)(c',L') = c_K \sum_{(c,L) \in R_j} |\Gamma_{j,c,L}|^{-1}\kappa_j(c,L;c',L')(F(c,L))$.
  - **Definición 11.12 (`Definition 11.12`), Teorema 11.13 (`Theorem 11.13`, Minkowski) y Proposición 11.14 (`Proposition 11.14`, (D1) para los levantamientos verdaderos, pp. 91–92):** Acota el orden de todo subgrupo finito de $\mathrm{GL}_n(\mathbb{Z})$ por $M(n)$ y establece (D1) con $d_j = \operatorname{ord}_p D_\Gamma = \sum_{k \ge 0}\lfloor 2f N_m / (p^k(p-1))\rfloor$ ($D_\Gamma = M(2f N_m)$).
  - **Observación 11.15 (`Remark 11.15`, p. 92):** Todos los levantamientos son sumas de clases de la misma forma; el tratamiento separado es la contabilidad que identifica las clases del dato con las órbitas de $\Gamma_{j,c}$ en $\mathcal{L}_j$ con estabilizadores iguales.

- **Transformada de Fourier finita y núcleos en una órbita escindida (`§11.3`–`§11.4`, pp. 92–99):**
  - **Definición 11.17 (`Definition 11.17`) y Proposición 11.18 (`Proposition 11.18`, p. 92):** Identifica la transformada de Fourier finita $\xi_L[\Phi]$ con el núcleo $\theta_{N,N'}[\Xi]$ de (7.3).
  - **Proposición 11.20 (`Proposition 11.20`, Modelo de Schrödinger en la órbita, p. 94):** Si $\sum_i c_i 1_{Y_v(N_i, N'_i)} = 0$, entonces $\sum_i c_i \operatorname{vol}(Y_v(N_i, N'_i))^{1/2}\theta_{N_i,N'_i} = 0$ (y análogamente para $\chi_F^{-1}\theta[\Xi]$).
  - **Hipótesis 11.22 (`Hypothesis 11.22`, Normalización **(N1)**, p. 95):** Existencia de unidades $a_v, a'_v \in \mathcal{O}^\times$ tales que $s_j(c,L;c',L')/s_j(c,L_2;c',L'_2) = a_v^{\operatorname{len} L_v - \operatorname{len} L_{2,v}} (a'_v)^{\operatorname{len} L'_v - \operatorname{len} L'_{2,v}}$.
  - **Definición 11.23 (`Definition 11.23`, Caracteres de paso y factor de marco, p. 96) y Proposición 11.27 (`Proposition 11.27`, (N1), p. 97):** Define los caracteres de paso (*step characters*) $\mu_{j+1}: U^1 \to \mathbb{C}^\times$ con tipo infinito $(\varepsilon_\tau)$ y $w_{j+1}(v,s) = \varepsilon_{\tau_{v,s}} - c_j$ (ec. (11.6)), el idele determinante $d_j(c,L)$ y la fórmula explícita de $s_j$; la Proposición 11.27 demuestra **(N1)** bajo estas normalizaciones de la Definición 11.23.
  - **Proposición 11.28 (`Proposition 11.28`, Forma (S3), p. 98):** Asumiendo (N1), los núcleos satisfacen (S3) de la Definición 10.12 con $a = a_v$, $a' = a'_v$ y $\mu = \mu_v(j+1)$.
  - **Observación 11.29 (`Remark 11.29`, p. 98):** Precisa que la segunda parte de (N1) (que $\chi_F$ aporta unidades en un lugar escindido) se demuestra en el Lema 11.30, mientras que la primera parte depende de la definición del factor de marco de (7.4).
  - **Proposición 11.31 (`Proposition 11.31`, (S1) y (S2), p. 99):** Verifica (S1) (con exponentes normalizadores $N'_v(j,i)$) y (S2).

- **Datos de conmutación, paso de entradas a retículos y cotas de órbita (`§11.5`–`§11.8`, pp. 99–106):**
  - **Proposición 11.32 (`Proposition 11.32`, p. 99) y Teorema 11.33 (`Theorem 11.33`, Integridad de coeficientes, p. 100):** Construye el operador $Z_j$ que satisface (D3) con precio $\operatorname{Pr}(v,j) = N'_v(j,r) - A_v + \frac{n'_v}{2}r(N_j - N_0)$, y demuestra $c_{j,l} \in \mathcal{O}$ y $\operatorname{ord}(c_{j,r}) \ge \alpha_{\mathrm{ev}}(v) := \sum_{s \in T_v\text{ par}}\alpha_s$.
  - **Teorema 11.35 (`Theorem 11.35`, Entradas a retículos en posiciones pares, p. 101):** En posiciones pares, la cota de valuación (11.9) sobre los emparejamientos con menores implica $p^{\sum_{a \le i_0}\lambda^{\natural,(j+1)}_{v,s}(a)}\langle T(G), f\rangle \in p^g H_s(L'_v)$ para todo $G \in H_s(L_v)$.
  - **Hipótesis 11.38 (`Hypothesis 11.38`, **(N2)**, p. 103):** Enuncia el análogo del Teorema 11.35 y del cambio de marcos (Lema 11.37) en las posiciones impares (donde el peso del modelo es dual).
  - **Observación 11.39 (`Remark 11.39`, p. 103):** El mecanismo en posiciones impares es la misma transferencia de Cauchy–Binet aplicada al modelo contragrediente mediante el teorema de Jacobi sobre menores de la matriz adjunta; queda por redactar la contabilidad de potencias del determinante (no involucra series theta).
  - **Corolario 11.40 (`Corollary 11.40`, p. 103):** Asumiendo (N2), deduce la cota de entrada de la Definición 10.2 a partir de cotas de valuación de $\langle \prod_v P^{(i_0(v))}_{I_v}, f\rangle$.
  - **Hipótesis 11.42 (`Hypothesis 11.42`, **(N3)**, ley del núcleo normalizado, p. 104):** En marcos adaptados a $L, L'$ y coordenadas hiperbólicas del Corolario 8.22, la serie del núcleo satisface $\mathcal{K}_j(c,L;c',L') = \exp(-\sum_{v,e}\beta(x_{v,e}, y_{v,e}))\cdot U$ con $U$ integral (es decir, $|c| \le 1$ en el Teorema 8.21).
  - **Teorema 11.44 (`Theorem 11.44`, Cotas de órbita, p. 104):** Asumiendo (N1), (N2), (N3), la cadena posee las cotas de órbita $(g^A, g^B, \alpha_{\mathrm{ev}})$ de la Definición 10.5.
  - **Teorema 11.45 (`Theorem 11.45`, El dato de cadena, p. 105):** Asumiendo (N1), (N2), (N3), para un primo $p \ge 5$ inerte en $K$ y no ramificado en $E$, los datos de las Definiciones 11.5, 11.7 y 11.10 forman un dato de cadena con (D1), datos de conmutación de Hecke (D2)–(D3) y cotas de órbita $(g^A, g^B, \alpha_{\mathrm{ev}})$, por lo que el Teorema 10.7 se aplica a la composición $\mathcal{K}_m = K_{m-1}\circ\dots\circ K_0$. *(El texto recalca en pp. 105–106 que (N1), (N2) y (N3) no se demuestran aquí de forma incondicional.)*

---

## Sección 12: La pérdida y las hipótesis (3.1) y (3.2) (*The loss and the hypotheses (3.1) and (3.2)*, pp. 106–146)

### Párrafo introductorio (p. 106)

Esta sección demuestra las hipótesis (3.1) y (3.2) de la Proposición 3.1 para todo $u_0 \in A_0$. La hipótesis (3.1) compara la suma $S$ sobre primos con la ganancia total (*total gain*) $\Gamma$, definida a partir de las estimaciones de valuación de la Sección 10, los exponentes de no degeneración de los operadores de Hecke y una elección de pesos. La hipótesis (3.2) compara la pendiente de un retículo $N_u$ con la pendiente del retículo base (*base lattice*) $M_u$: $N_u$ es el subretículo de $M_u$ generado localmente por imágenes de potencias de operadores de Hecke, reescalado en cada lugar por la ganancia; su pendiente excede la de $M_u$ en la ganancia menos la colongitud (*colength*) del subretículo, controlada por un teorema de no degeneración para operadores de Hecke en formas integrales de representaciones de $\mathrm{GL}_k$ a lo largo de las aristas del edificio (*building*).
- §12.1 fija las clases de primos, órbitas de Frobenius y las cantidades locales $g^0, g^1, \operatorname{Pr}, \tau, \operatorname{io}, \operatorname{gain}$; §12.2 enuncia el teorema de no degeneración y lo reduce a una arista; §12.3 convierte la no degeneración en una cota de colongitud para $NP_w$; §12.4 define $N_u$ y demuestra (3.2); §12.5 compara la ganancia con la suma sobre primos y demuestra (3.1); §12.6 enumera las entradas tomadas de otros pasos; §12.7–§12.10 desarrollan los tres motores (*engines*) de no degeneración de Hecke.

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 106–146)

- **Primos, órbitas y ganancia total (`§12.1`, pp. 106–109):**
  - Se fijan $w'' = b'/(xn)$, $X'' = xnX'$, $\theta = x^{-\varepsilon}$, $p_* = k^2 x^{26}$ (ec. (12.1)), la partición de los primos inertes $\mathcal{P}$ en clase I ($\epsilon_p=1$) y clase II ($\epsilon_p=0$), las cotas de los nodos **(W1)**–**(W3)** con pesos inferiores $b_t$, las cotas de órbita $g^0_j(t_0)$, $g^1_j(t_0)$ y el precio $\operatorname{Pr}_j(t_0)$ (ec. (12.4)–(12.6)), y el conjunto de órbitas servidas $\mathcal{V}_p$.
  - **Definición 12.3 (`Definition 12.3`, p. 109):** Define para $p \in \mathcal{P}$, $p \le X''$: $S_{t_0} = \lceil \sum_{j=1}^m \max(0, g^1_j(t_0) - \operatorname{Pr}_j(t_0) - \max(g^0_j(t_0), 0))\rceil$, $\tau(p) = e_p + \sum_{t_0 \in \mathcal{V}_p} m(\lceil t_{t_0}\rceil + D_p + 1)$ (si $\mathcal{V}_p \ne \varnothing$, $0$ si no), $\operatorname{io}(p) = 2\operatorname{Sig}(p)\max_{t_0 \in \mathcal{V}_p} S_{t_0}$, y $\operatorname{gain}_j(p) = \sum_{t_0 \in \mathcal{V}_p}\max(g^1_j(t_0)-\operatorname{Pr}_j(t_0), \max(g^0_j(t_0), 0)) + \sum_{t_0 \in R_p \setminus \mathcal{V}_p}\max(g^0_j(t_0), 0)$. Eliminando el conjunto $\mathcal{D}$ de primos sin ganancia distintos de todo $T_u$, se define la ganancia total $\Gamma = \sum_{p \in \mathcal{P}} 2\log p\bigl(\sum_{j=1}^m \operatorname{gain}_j^{\mathcal{D}}(p) - \tau(p)\bigr)$ (ec. (12.7)) y la corrección total $\mathrm{IO} = \sum_{p \in \mathcal{P}} \log p\, \operatorname{io}(p)$.
  - **Observación 12.4 (`Remark 12.4`, p. 109):** Reescribe $\Gamma = \sum_w \sigma(w, \sum_j \operatorname{gain}_j^{\mathcal{D}}(p_w) - \tau(p_w))$ con $\sigma(w, y) = 2\ell_w e_w y$ sobre los lugares finitos $w$ del cuerpo de coeficientes $\mathbf{K}$, que es la forma en que $\Gamma$ entra en la pendiente de $N_u$.

- **No degeneración de operadores de Hecke (`§12.2`, pp. 109–114):**
  - **Definición 12.6 (`Definition 12.6`, Enunciado $\mathrm{LP}(r, \lambda; t, D, \kappa, c^*)$, p. 110):** Se cumple cuando $4(D+1) \le c^*$ y para todo retículo $L \subset \mathbb{Q}_q^k$ existen $r$-aristas $e_1, \dots, e_M$ con destino $L$ y vectores $F_1, \dots, F_M \in V$ tales que (i) $F_i \in N_t^{\mathrm{src}}(\mathrm{src}\, e_i)$, (ii) $F_i \in \varpi^{c^*} R(e')$ para toda $r$-arista $e' \ne e_i$ con la misma fuente, y (iii) existen $n \ge (1-\kappa)\dim V$, $u: \mathcal{O}^n \to N_t^{\mathrm{tgt}}(L)$ y $A \in M_{n \times M}(\mathcal{O})$ con $\sum_i A_{ji}\operatorname{be}(F_i, u(z)) = p^D z_j$. Se define la cuota mínima (*least share*) $\kappa^{\min}(r,\lambda; t, D, c^*)$.
  - **Proposición 12.10 (`Proposition 12.10`, Reducción a una arista, p. 112):** Reduce $\mathrm{LP}(r,\lambda; t, D, \kappa, c^*)$ a la existencia, para cada $r$-arista $e$ hacia un retículo fijo $L_0$, de un sistema fuente-prueba (*source-test system*) en $\{e\}$ de tamaño $n_e \ge \rho\dim V / q^{r(k-r)}$ con pruebas en $\varpi^{c^*}R'(e')$ para $e' \ne e$.
  - **Teorema 12.11 (`Theorem 12.11`, p. 112).** Asúmase la Hipótesis 12.12. Existen constantes $K_\bullet$ (dependientes de $\varepsilon$) tales que para $x$ grande, en las ventanas $a \le a_s \le a + a/(kx^{13})$, $b' \le b_s \le b' + 2n\delta_1 x^\varepsilon \operatorname{La} b'/k$ y bajo las condiciones de tamaño (Z) de §12.6:
    - (i) *Primos pequeños* ($13 \le p < p_*$): vale $\mathrm{LP}(r_0, \lambda; \lceil t^{\mathrm{II}}\rceil, D^{\mathrm{II}}, \kappa^{\mathrm{II}}, 8(D^{\mathrm{II}}+1))$.
    - (ii) *Primos medianos* ($p_* \le p < X'$ sin potencia $p^i$ en $|p^i - X'| \le \rho_B X'$): la media de $\kappa^{\mathrm{I}}(a,b) = \kappa^{\min}(1,\lambda; \lceil t^{\mathrm{I}}(a,b)\rceil, D^{\mathrm{I}}, 8(D^{\mathrm{I}}+1))$ sobre los pesos en las ventanas anteriores es a lo sumo $K_m N(t_0)\nu_1 x^{-13}$.
  - **Hipótesis 12.12 (`Hypothesis 12.12`, Motores de no degeneración de Hecke / *Engines of Hecke nondegeneracy*, p. 113):** Reúne tres enunciados (no demostrados completamente en el artículo; §12.8–§12.10 prueban partes de ellos):
    - **(A) Rango de espacios de símbolos (*Rank of symbol spaces*):** Sobre el cuerpo residual $\mathbb{F}$, para un sistema de marco con $r = r_0$ cimas de marco por segmento construido desde las teselas marcadas de la Definición 5.19(iii), el subespacio generado por las reducciones de los generadores de segmento tiene dimensión al menos $q^{-rK}(1 - N(t_0)r^2 k/Y)\prod_s\binom{d_s+k-1}{k-1}$.
    - **(B) Detección para la forma de Fock torcida (*Detection for the twisted Fock form*):** Para todo $F$ de multigrado $(d_s)$ que satisface las condiciones de cadena y marco con norma balanceada $0$, existe un $G$ integral con las mismas condiciones tal que $\operatorname{ord}_p B(F, \operatorname{ph}(G)) \le n_0 + D_m + D_l + 3\kappa_p$.
    - **(C) Media de las cuotas de segmento (*Mean of the segment shares*):** Para un segmento con $s$ cimas e índice de escisión $\sigma$, la media de su cuota mala (*bad share*) sobre los pesos de las cimas en la ventana y sobre el peso de la siguiente cima es a lo sumo $C(s - \sigma + 1)\nu_1/Y$.
  - **Corolario 12.13 (`Corollary 12.13`, p. 114):** La media de $\kappa_{t_0}$ sobre las ventanas es $\le N(t_0)x^{-12}$ (y puntualmente para $p < p_*$).

- **Colongitud, retículo $N_u$ e hipótesis (3.1) y (3.2) (`§12.3`–`§12.6`, pp. 114–127):**
  - Bajo la estructura local **(F1)**–**(F5)** en $w \mid p$, las **Proposiciones 12.15 y 12.16** acotan el cociente de $M^{\mathrm{ram}}$ por $NP_w = P(M) \cap p^{\lceil \tau(p)\rceil} M \cap V^{\mathrm{ram}}$.
  - **Teorema 12.18 (`Theorem 12.18`, p. 117):** Si vale $\mathrm{LP}$ en cada $v \in \mathcal{V}_p$ y $\operatorname{Sig}(p) \le \frac{1}{2}$, entonces (a) $NP_w \subset p^{\lceil \tau(p)\rceil} M^{\mathrm{ram}}$ y (b) $\operatorname{length}_{\mathcal{O}_w}(M^{\mathrm{ram}}/NP_w) \le v_w(p)\operatorname{rk}(M)(\tau(p) + \operatorname{io}(p))$.
  - **Definición 12.20 (`Definition 12.20`, p. 119):** Define $\Lambda_u \subset M_u^{\mathrm{ram}}$ por sus completaciones ($NP_w$ en $w \mid p \in \mathcal{P}$, $p \le X''$, $p \ne T_u$, $\mathcal{V}_p \ne \varnothing$; $N_w^T$ en $w \mid T_u$; y $M_{u,w}^{\mathrm{ram}}$ en el resto) y el retículo reescalado $N_u = \prod_{w \in W_u} \mathfrak{p}_w^{-\lfloor e_w s_u(w)\rfloor}\Lambda_u$ con $s_u(w) = \sum_{j=1}^m (\operatorname{gain}_j^{\mathcal{D}}(p_w) + F_j(w) - E_{u,j}(w))$ y $\mu_u^N = \mu(N_u)$.
  - **Teorema 12.21 (`Theorem 12.21`, Hipótesis (3.2), p. 120):** Bajo las entradas **(L1)**–**(L8)** y condiciones de tamaño **(Z)** de §12.6 y $\operatorname{Sig}(p) \le \frac{1}{2}$ cuando $\mathcal{V}_p \ne \varnothing$: (i) $\mu_u^M + \Gamma + \mathcal{L} - E_u - e_2 \le \mu_u^N$ con $e_2 = 4\,\mathrm{IO} + \mathrm{LT} + \mathrm{RX} + 1$; (ii) $\mu_{\max}(N_u) \le \mu_{\max}(M_u) + \Gamma + \mathcal{L} - E_u$.
  - **Proposiciones 12.24 y 12.26 (`Propositions 12.24, 12.26`, pp. 122–123):** Comparación primo a primo entre $\operatorname{ask}_{j,s}(p)$ y $\operatorname{gain}_j^{\mathcal{D}}(p) - \tau(p)$ para primos servidos y llanos.
  - **Teorema 12.27 (`Theorem 12.27`, Hipótesis (3.1), p. 124) y Proposición 12.29 (`Proposition 12.29`, Elección de pesos, p. 125):** Si $\operatorname{lhsW} \le x^{-9}$ (existencia de $(a,b) \in \mathrm{Box}$ garantizada por la Proposición 12.29), entonces $S \le \Gamma + e_1$ con $e_1 = 2\log 4\, N_T m b + B_{\mathrm{minor}} \le (2\log 4 + 1) N_T m b$ y $\mathrm{IO} \le N_T m b$.
  - **Subsección 12.6 (pp. 125–127):** Enumera las diez entradas **(L1)**–**(L10)** tomadas de las Secciones 11, 16 y 18 (incluyendo (L7), colongitud en el primo auxiliar $T_u$) y las condiciones de tamaño **(Z1)**–**(Z5)**, **(Z9)**.

- **Motores de no degeneración de Hecke (`§12.7`–`§12.10`, pp. 127–146):**
  - **Motor (C) (`§12.8`, pp. 128–134):**
    - **Teorema 12.34 (`Theorem 12.34`, Teorema de la ventana $p$-ádica para exponentes de Smith, p. 129) y Observación 12.35 (`Remark 12.35`, p. 130):** Acota el promedio sobre una progresión aritmética $z_j = t_0 + dj$ ($p \nmid d$, $0 \le j < Y_0$) del número de exponentes de Smith $\ge E$ de una matriz polinomial $A(z) = \sum_{i=0}^\Delta c_{ab,i}\binom{z}{i}$ en términos de $\Delta/Y_0$ y del coeficiente líder de $\det A(z)$.
    - **Proposición 12.37 (`Proposition 12.37`, p. 131):** Expresa el emparejamiento del operador de atadura (*tie operator*) $\Phi_z$ en la base binomial $\binom{z}{i}$ con coeficiente líder igual a la forma de Fock sin torcer $\langle u, v_0\rangle$.
    - **Teorema 12.38 (`Theorem 12.38`, Cota de ventana en un nivel, p. 131):** Combina el Teorema 12.34 y la Proposición 12.37 para acotar $\sum_{i=0}^{W-1}\operatorname{bad}(\Psi_i, L, k)$.
    - **Pasos abiertos (C6), (C8)–(C11) (`§12.8.5`, pp. 132–133)** y **Proposición 12.40 (`Proposition 12.40`, Numérica de (C7), p. 133):** Verifica que el corchete del Teorema 12.38 es $\le 3/Y$.
  - **Motor (B) (`§12.9`, pp. 134–141):**
    - **Proposición 12.41 (`Proposition 12.41`, Escisión factorial en dígitos, p. 134):** $(\rho + P\beta)! = \rho!(P!)^\beta \beta! c_P(\beta) d_P(\beta,\rho)$ con $1$-unidades $c_P, d_P$.
    - **Definición 12.42 (`Definition 12.42`, espacio $\mathcal{D}(\alpha,\gamma)$), Proposición 12.44 (`Proposition 12.44`), Corolario 12.45 (`Corollary 12.45`) y Proposición 12.47 (`Proposition 12.47`, pp. 134–136):** Decaimiento de los coeficientes de Mahler de $c_P^{\pm 1}, d_P^{\pm 1}$ en $\mathcal{D}(\frac{1}{4}, 0)$ y congruencia módulo $p^c$ de derivadas divididas en dígitos altos.
    - **Proposición 12.49 (`Proposition 12.49`, Proyector extremal de Asherova–Smirnov–Tolstoy, p. 137) y Proposición 12.50 (`Proposition 12.50`, Proyector isotípico $\pi_{S,\theta}$, p. 138):** Estabilidad del retículo balanceado $\mathcal{B}$ bajo potencias divididas y control del proyector extremal; los pasos **(B8)** y **(B9)** quedan abiertos (salvo el teorema publicado de Ramanan–Ramanathan citado en (B9)).
    - **Teorema 12.54 (`Theorem 12.54`, Cota de norma (B7) del proyector isotípico, p. 140) y Observación 12.55 (`Remark 12.55`, p. 141):** Demuestra $p^{N_S}\pi_{S,\theta}\mathcal{B}_d \subset \mathcal{B}_d$ con $N_S = \binom{r}{2}\lfloor \log_p(\deg_S + r - 1)\rfloor$, es decir $v_{BB}(\pi_{S,\theta}F) \ge v_{BB}(F) - N_S$.
  - **Motor (A) (`§12.10`, pp. 141–146):**
    - Lemas algebraicos de levantamiento desde el cuerpo residual, identidad de Frobenius, descomposición en dígitos y concentración de pesos de caminos de Pieri (**Lemas 12.56–12.62**); se enuncian como publicados **(A4)** (monomios estándar integrales de Doubilet–Rota–Stein, De Concini–Eisenbud–Procesi, Désarménien–Kung–Rota) y como abiertos **(A2)**, **(A5)**, **(A6)**, **(A7)** y los factores por cima de **(A9)**.
    - **Lema 12.63 (`Lemma 12.63`, Conteo final del motor (A), p. 144):** Combina los factores $(1-5/Y)^N(1-1/Y)^N(1-r/(2Y))^N A^J \ge 1 - Nr^2k/Y$.
    - **Proposición 12.64 (`Proposition 12.64`) y Corolario 12.65 (`Corollary 12.65`, Entrada (L2), p. 145):** Demuestra $p^{w(\lambda)}\nabla_{\mathcal{O}}(\lambda) \subset \Delta_{\mathcal{O}}(\lambda) \subset \nabla_{\mathcal{O}}(\lambda)$ con $w(\lambda) = \binom{k}{2}\lfloor\log_p(\lambda_1-\lambda_k+k-1)\rfloor$, deduciendo $p^e M^{\mathrm{na}} \subset M$ con $e_p = \lceil C_e f k^2 \log_p a\rceil$.
    - **Proposición 12.67 (`Proposition 12.67`, Cota para $\Pi$ en (Z1), p. 146):** Bajo una cota polinomial $c_G \le x^{C_c}$, demuestra $\Pi \le \exp(x^{\varepsilon/4})$ para $x$ grande.

---

## Sección 13: La desigualdad de pendiente para la familia de aplicaciones de períodos (*The slope inequality for the family of period maps*, pp. 146–158)

### Párrafo introductorio (p. 146)

La hipótesis (3.3) de la Proposición 3.1 exige que la media ponderada por rango de $\mu(N_u) - h_u$ sobre los índices $u \in W$ exceda a la pendiente del dual $R^\vee$ del retículo de formas automórficas en a lo sumo $e_3$. Para una sola aplicación inyectiva, la desigualdad de pendiente de Bost acota $\mu(N_u) - h_u$ por la pendiente maximal de $R^\vee$; la familia necesita más porque $\mu_{\max}(R^\vee)$ puede superar con creces la pendiente media $\mu(R^\vee)$ y porque las imágenes de las aplicaciones $B_u$ se solapan. El argumento de esta sección sustituye la pendiente maximal por la pendiente media: corta cada retículo fuente a lo largo de su filtración de Harder–Narasimhan, traslada cada pieza a un escalón de la filtración de $R^\vee$ mediante la desigualdad de pendiente, y acota inferiormente el rango de ese escalón mediante un conteo de dimensiones en un lugar complejo donde las matrices de las aplicaciones forman un marco casi ajustado (*nearly tight frame*). §13.1 recoge la teoría de pendientes, §13.2 demuestra el teorema del marco, §13.3 deriva las condiciones de marco a partir de cotas de Hilbert–Schmidt para operadores de Gram, §13.4 demuestra (3.3) con un $e_3$ explícito y lo acota, y §13.5 enuncia las entradas automórficas para series de Poincaré de Bessel que la construcción debe proporcionar.

### Definiciones, observaciones y enunciados principales (pp. 146–158)

- **Retículos hermíticos, pendientes y desigualdad de pendiente (`§13.1`, pp. 146–148):**
  - Para un retículo hermítico $\bar L$ sobre $\mathcal{O}_K$ ($K$ totalmente complejo de grado $n_K$), se definen la pendiente $\mu(L) = \frac{2\deg_{\mathbb{Z}} L}{n_K \operatorname{rk} L} - \log 2 + \frac{\log|d_K|}{n_K}$ (ec. (13.1), el doble de la pendiente normalizada de Arakelov de Bost [15]) y la altura de una aplicación $K$-lineal $\operatorname{ht}(\varphi) = \frac{2}{n_K}\sum_{v \in \Sigma_K}\log\|\varphi_v\|_{\mathrm{op}}^2$ (ec. (13.2)).
  - **Proposición 13.1 (`Proposition 13.1`, Filtración de Harder–Narasimhan, p. 147):** Enuncia las propiedades clásicas **(HN1)**–**(HN5)** de las pendientes $x_1 \ge \dots \ge x_\ell$ y subretículos saturados $L_{\ge \theta}$, además de $\mu(L^\vee) = -\mu(L)$ y $\mu_{\min}(L^\vee) = -\mu_{\max}(L)$.
  - **Proposición 13.3 (`Proposition 13.3`, Desigualdad de pendiente / *Slope inequality*, p. 148):** Para $\varphi : V \to V'$ $K$-lineal con $\varphi(A) \ne 0$, $\mu_{\min}(\varphi(A)) \ge \mu_{\min}(A) - \operatorname{ht}(\varphi)$.

- **El teorema del marco y familias de Gram (`§13.2`–`§13.3`, pp. 148–154):**
  - Se define $\Lambda(u, H) = u\log(1 + H/u)$ para $u > 0$, $\Lambda(0, H) = 0$.
  - **Teorema 13.8 (`Theorem 13.8`, Teorema del marco / *Frame theorem*, p. 151).** Sean $\bar N_i$ ($i \in I$) retículos hermíticos sobre $\mathcal{O}_K$ de rango $d_i$ ($\Delta = \sum_i d_i > 0$), $\bar C$ de rango $D$, $B_i : V_i \to W$ con $B_i(N_i) \subset C$ y $\operatorname{ht}(B_i) \le h_i$. Fíjese $v \in \Sigma_K$, matrices invertibles $Y_i, Y'$, $D_1 \ge 0$, matrices complejas $(D+D_1)\times d_i$ denotadas $A_i$ cuyas primeras $D$ filas forman $Y'^{-1}[B_i]_v Y_i$, $\gamma_i > 0$ y $Q = \sum_i \gamma_i A_i A_i^*$. Si $u, H \ge 0$, $0 \le e \le \frac{1}{4}$, $\eta \ge 0$, $0 \le \delta < 1$ satisfacen:
    - (i) $s\Delta \le \sum_i d_i(\mu(N_i) - h_i)$;
    - (ii) $\mu_{\max}(N_i) - h_i \le s + u$ para todo $i$;
    - (iii) $s - \mu_{\min}(C) \le H$;
    - (iv) $(1-\delta)(D + D_1) \le D$;
    - (v) $\sum_i \|\gamma_i A_i^* A_i - 1\|_{\mathrm{HS}}^2 \le e\Delta$;
    - (vi) $\operatorname{tr}(Q^2) \le (1+\eta)(\operatorname{tr} Q)^2/(D + D_1)$,
    entonces
    $$\mu(C) \ge s - \frac{4\Lambda(u, H) + (\eta + 4\sqrt{e})H}{1-\delta}.$$
  - **Observación 13.9 (`Remark 13.9`, p. 152):** La demostración acota el corango de cada escalón $C_{\ge s-\tau}$ ($0 \le \tau \le H$), controlando la mitad inferior del polígono de Harder–Narasimhan de $C$; la estructura hermítica en $v$ es arbitraria gracias a $Y_i, Y'$, y la ganancia respecto de la Proposición 13.3 consiste en pasar de $\mu_{\max}(C)$ a $\mu(C)$ para una familia redundante.
  - **Proposición 13.11 (`Proposition 13.11`, De cotas de Gram a condiciones de marco, pp. 152–153):** Para compresiones isométricas $A_i = P_i V_i$ ($V_i^* V_i = 1$) y operadores de Gram $K_{ij} = \sqrt{\gamma_i\gamma_j} P_i^* P_j$ que cumplen **(G1)**–**(G5)** ($\|K_{ij}\|_{\mathrm{HS}}^2 \le (1+\eta_0)d_i^S d_j^S/D^*$ para $i \ne j$, $\|K_{ii}-1\|_{\mathrm{HS}}^2 \le e_0 d_i^S$, $\widetilde D \le (1+\eta_1)D^*$, $D^* \le \sigma \Delta^S$, $\sum_i (d_i^S - d_i) \le \delta'\Delta^S$), deduce $\sum_i \|\gamma_i A_i^* A_i - 1\|_{\mathrm{HS}}^2 \le 2 e_0 \Delta$ y $\operatorname{tr}(Q^2) \le (1 + 5\sigma + 3\sqrt{\delta'})(\operatorname{tr} Q)^2/\widetilde D$.

- **Realización de Bessel e hipótesis (3.3) (`§13.4`–`§13.5`, pp. 154–158):**
  - **Definición 13.13 (`Definition 13.13`, Realización de Bessel / *Bessel realization*, p. 154).** Una realización de Bessel de la familia $(B_u)_{u \in W}$ en $v \in \Sigma_K$ consta de: (1) un espacio de Hilbert complejo $\mathcal{H}$ de dimensión $D_{\mathrm{all}}$ con inmersión isométrica conjugado-lineal $s : Y_v \to \mathcal{H}$; (2) para cada $u \in W$, un espacio de Hilbert $\mathcal{C}_u$ de dimensión $d_u^S$, una aplicación lineal $P_u : \mathcal{C}_u \to \mathcal{H}$, $c_u > 0$, y una inmersión isométrica lineal $\iota_u : V_{u,v} \to \mathcal{C}_u$; (3) operadores unitarios $V$ de $Y_v$, $U_u$ de $V_{u,v}$ y escalares $a_u \ne 0$, tales que
    $$(B_{u,v}\varphi)(F) = a_u \langle s(VF),\, P_u \iota_u U_u \varphi \rangle_{\mathcal{H}} \qquad (\varphi \in V_{u,v},\; F \in Y_v). \tag{13.4}$$
    Los operadores de Gram son $K_{uu'} = (c_u c_{u'})^{-1/2} P_u^* P_{u'}$.
  - **Teorema 13.15 (`Theorem 13.15`, Hipótesis (3.3), pp. 155–156).** Dadas $\bar R$ de rango $D_{\mathrm{rows}} \ge 1$, $\bar N_u$ de rango $d_u \ge 1$, $B_u : V_u \to Y^*$ y $h_u$, con $s = \sum_u d_u(\mu(N_u)-h_u)/\sum_u d_u$ y $u_F = \max_u(\mu_{\max}(N_u)-h_u) - s$, si se verifican: (a) $B_u(N_u) \subset R^\vee$, (b) $\operatorname{ht}(B_u) \le h_u$, (c) $s + \mu_{\max}(R) \le H$, (d) realización de Bessel en $v$ con $(1-\delta)D_{\mathrm{all}} \le D_{\mathrm{rows}}$, (e) cotas de casi ortogonalidad sobre $K_{uu'}$ y $D_{\mathrm{all}} \le (1+\eta_1)D^*$, y (f) $D^* \le \sigma \sum_u d_u^S$ y $\sum_u (d_u^S - d_u) \le \delta' \sum_u d_u^S$, entonces con
    $$e_3 = \frac{4\Lambda(u_F, H) + (5\sigma + 3\sqrt{\delta'} + 4\sqrt{2 e_0})H}{1-\delta} \ge 0 \tag{13.5}$$
    se cumple $\frac{\sum_u d_u(\mu(N_u)-h_u)}{\sum_u d_u} - e_3 \le \mu(R^\vee)$.
  - **Observación 13.16 (`Remark 13.16`, p. 156):** La condición (K3) de la Sección 18 usa la conclusión ligeramente más débil $s - \log|W| - e_3 \le \mu(R^\vee)$, donde $\log|W| \ge 0$ es holgura irrelevante.
  - **Corolario 13.18 (`Corollary 13.18`, Tamaño de $e_3$, p. 157):** Acota $e_3 \le 8 U \log(1 + x^{C_H}) + 12 b$ (con el Lema 13.17 acotando $u_F$, el Lema 13.19 verificando las condiciones de tamaño y el Lema 13.20 deduciendo la integridad (a) de la divisibilidad local).
  - **Subsección 13.5 (`§13.5`, Entradas automórficas del Teorema 13.15, p. 158):** Especifica los tres insumos automórficos que la Sección 14 demuestra (Teoremas 14.1, 14.2 y 14.3): realización de Bessel con $\delta \le \exp(-x^{\varepsilon_z/7})$, casi ortogonalidad de las series de Poincaré de Bessel y conteo de dimensiones con $\Gamma_0 = \exp(C_\Gamma m^5 f x^\varepsilon)$.

---

## Sección 14: Series de Poincaré de Bessel (*Bessel Poincaré series*, pp. 158–208)

### Párrafo introductorio (p. 158)

Esta sección demuestra las tres entradas automórficas (d) y (e) del Teorema 13.15 a partir de los enunciados recogidos en ella: la casi ortogonalidad de las series de Poincaré de Bessel (*near orthogonality of Bessel Poincaré series*), la cuota de filas irreducibles (*share of irreducible rows*) y la identidad de Bessel (*Bessel identity*) para las aplicaciones de períodos.

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 158–208)

- **Los tres teoremas principales (`§14.1`, p. 159):** Con $G = U(V)$ sobre $F$ totalmente real de grado $f$, $\mathcal{H}$ el espacio de formas automórficas con serie discreta fija en $\infty$ y fijadas por el idempotente de nivel ($D_{\mathrm{all}} = \dim \mathcal{H}$), $D^*$ el producto del grado formal por $\operatorname{vol}([G])$ y el valor en $1$ del idempotente, $P_u : \mathcal{C}_u \to \mathcal{H}$ la aplicación de Poincaré de Bessel, $K_{uu'} = (c_u c_{u'})^{-1/2} P_u^* P_{u'}$ y $\Gamma_0 = \exp(C_\Gamma m^5 f L)$:
  - **Teorema 14.1 (`Theorem 14.1`, Casi ortogonalidad / *Near orthogonality*, p. 159).** Existen constantes absolutas $C_0 \ge 1$ y $C_\Gamma > 0$ tales que si $C_0^{-1} \le d_u^S \Gamma_0^2 / D^* \le C_0$ para todo $u \in W$ (ec. (14.1)), entonces para $x$ grande en función de $\varepsilon$:
    $$\|K_{uu'}\|_{\mathrm{HS}}^2 \le (1+\eta_0)\frac{d_u^S d_{u'}^S}{D^*} \quad (u \ne u'), \qquad \|K_{uu} - 1\|_{\mathrm{HS}}^2 \le e_0 d_u^S, \qquad D_{\mathrm{all}} \le (1+\eta_1) D^*,$$
    con $e_0 \ge 0$ y $\eta_0, \eta_1, \sqrt{e_0} \le \exp(-x^{\varepsilon/8})$.
  - **Teorema 14.2 (`Theorem 14.2`, Cuota de filas irreducibles / *Share of irreducible rows*, p. 159).** Con $\varepsilon_z = \varepsilon/J$ y $D_{\mathrm{rows}} = \dim E_{\mathrm{row}} = (1-\delta) D_{\mathrm{all}}$, para $x$ grande se cumple $0 \le \delta \le \exp(-x^{\varepsilon_z/7})$.
  - **Teorema 14.3 (`Theorem 14.3`, Identidad de Bessel / *Bessel identity*, p. 159).** En el lugar complejo $v$, existen un operador unitario $V$ de $Y_v$, operadores unitarios $U_u$ de $V_{u,v}$ y escalares $a_u \ne 0$ tales que $(B_{u,v}\varphi)(F) = a_u \langle s(VF), P_u \iota_u U_u\varphi\rangle_{\mathcal{H}}$ (ec. (14.2)) y $B_u$ es $K$-racional.

- **La identidad de Bessel y la cadena de transferencias de balancín (`§14.2`, pp. 159–175):**
  - Bajo los axiomas **(P1)**–**(P5)** del subgrupo de Bessel $S = N \rtimes H$, el período de Bessel $\operatorname{per}(\Psi,\theta) = \int_{H(F)\backslash H(\mathbb{A})}\int_{N(F)\backslash N(\mathbb{A})} \theta(na)\psi(n)\Psi(a)\,dn\,da$ (ec. (14.5)):
    - **Proposición 14.5 (`Proposition 14.5`, Desdoblamiento / *Unfolding*, p. 161):** La serie $P_T(g) = \sum_{\gamma \in S(F)\backslash G(F)}\mathrm{Ph}_T(\gamma g)$ converge absolutamente c.t.p. en $L^1([G])$ y existe $c_u > 0$ tal que $\int_{[G]} \theta(g) P_T(g)\,dg = c_u \int_{S_\infty\backslash G_\infty} \operatorname{per}(T(W_u(y)), R_{(y,x_u)}\theta)\,d\nu(y)$ (ec. (14.6)).
    - **Observación 14.6 (`Remark 14.6`, p. 162):** (14.6) no requiere $P_T \in L^2([G])$ ni fijación por el proyector arquimediano, hechos necesarios luego para $P_T \in \mathcal{H}$.
    - **Corolario 14.7 (`Corollary 14.7`, p. 162):** Transfiere relaciones lineales de períodos de Bessel a emparejamientos $\int_{[G]}\theta_i P_{T_i}$.
  - **Hipótesis 14.10 (aplicación de períodos y relación de balancín), Hipótesis 14.11 (diccionarios), Hipótesis 14.12 (racionalidad) y Definición 14.13 (p. 163)** -> **Teorema 14.15 (`Theorem 14.15`, p. 163):** Implican (14.2) (y el Teorema 14.3 si $z$ es común a todo $u \in W$).
  - **Observación 14.16 (`Remark 14.16`, qué deja abierto el Teorema 14.15, p. 164):** Detalla que la relación de balancín transfiere relaciones entre $c(t)\operatorname{perCol}$ a períodos de Bessel locales, mientras que Siegel–Weil y el método de duplicación (*doubling method*) entran en la sobreyectividad de la Hipótesis 14.21.
  - **Hipótesis 14.17 (`Hypothesis 14.17`, Leyes de la torre theta **(T1)**–**(T8)**, pp. 165–166), Proposiciones 14.18 y 14.19 (`Propositions 14.18–14.19`), Teorema 14.20 (`Theorem 14.20`, Transferencia a lo largo de la torre, p. 166), Hipótesis 14.21 (`Hypothesis 14.21`, Diccionarios **(D1)**–**(D6)**, p. 167) y Corolario 14.22 (`Corollary 14.22`, Relación de balancín, pp. 167–168):** Encadenan $n+1$ pasos dobles desde el tope hasta el nivel $0$; la **Observación 14.23 (`Remark 14.23`, p. 168)** pasa del Corolario 14.22 a la Hipótesis 14.10 y el **Lema 14.24 (`Lemma 14.24`, p. 168)** especifica las tres identidades de períodos necesarias para la racionalidad (Hipótesis 14.12).
  - **Identidad de balancín de paso doble (`§14.2.5`, pp. 169–175):** Bajo la **Hipótesis 14.27 (leyes generales de la representación de Weil **(W1)**–**(W7)**)** y la **Hipótesis 14.28 (leyes locales de la tupla **(L1)**–**(L6)**)**, el **Teorema 14.29 (`Theorem 14.29`, p. 173)** demuestra la identidad de paso doble **(T2)** con un único núcleo bivacío real $C = \mathrm{op}_j\operatorname{ctr}(\Psi_1,\Psi_2)$ independiente de la tupla y constante $c_V(j) = \kappa_j sc_j sc_{j+1} c_Q(j) c_G(j) c_T(j)$; la **Proposición 14.30** caracteriza $c_V(j) \ne 0$, y las **Observaciones 14.31 y 14.32 (`Remarks 14.31–14.32`, pp. 174–175)** precisan la normalización y los residuos locales que permanecen abiertos.

- **La cuota de filas irreducibles (`§14.3`, pp. 175–188):**
  - Para etiquetas $c \in \mathbb{F}_g[X]$ (polinomios mónicos de grado $N$ con $c(0)\ne 0$) en $\mathrm{GL}_N(\mathbb{F}_g)$ e idempotentes centrales de Deligne–Lusztig $E_c$: **Proposición 14.34 (`Proposition 14.34`, Pesos de Gelfand–Graev, p. 175):** $\operatorname{wt}(e_U, c) = \operatorname{sq}(c) = \prod_{P \mid c}(g^{\deg P}-1)^{-1}$ para $c$ libre de cuadrados.
  - Se definen tuplas buenas de etiquetas por **(G1)**–**(G5)** (`§14.3.2`, p. 176). **Teorema 14.41 (`Theorem 14.41`, Peso malo en un primo, p. 177):** Acota explícitamente la masa $P^{\otimes \Pi}$ de tuplas no buenas por $W(g)$.
  - **Hipótesis 14.42 (pesos locales), Hipótesis 14.43 (fórmula de multiplicidad) e Hipótesis 14.44 (las filas son las formas buenas, p. 179)** -> **Teorema 14.46 (`Theorem 14.46`, p. 179):** Bajo las condiciones de tamaño (14.17), demuestra $0 \le \delta \le \exp(-x^{\varepsilon'/7})$, dando el Teorema 14.2. **Observación 14.47 (`Remark 14.47`, p. 180):** Los certificados de irreducibilidad (G2)–(G5) se usan luego donde entra el teorema de Jordan; el Teorema 14.2 es un conteo puro.
  - **Idempotentes de nivel en primos auxiliares (`§14.3.6`, pp. 180–186):** **Teorema 14.51 (`Theorem 14.51`, Intercambio de raíces, p. 182):** $\operatorname{tr}(e_J, \chi) = \operatorname{tr}(e', \chi)$ para toda función de clase $\chi$ en $\mathrm{GL}_N(\mathbb{F}_g)$. **Proposición 14.55** y **Teorema 14.56 (`Theorem 14.56`, Expansión en columnas, p. 185):** $\operatorname{Tr}\pi(e') = \sum_{i=0}^{k-1}(g^{k-i}-g^{k-i-1})W_i(\pi) + W_k(\pi)$. **Corolario 14.57 (`Corollary 14.57`, p. 185):** Demuestra la Hipótesis 14.42: $(1-1/g)\operatorname{wt}(e_U, c) \le \operatorname{wt}(e_J, c)$.
  - **Fórmula de multiplicidad (`§14.3.7`–`§14.3.8`, pp. 186–188):** Bajo la **Hipótesis 14.59 (diccionario de etiquetas)** y la **Hipótesis 14.61 (entradas de pre-traza, no demostradas aquí)**, el **Teorema 14.62 (`Theorem 14.62`, p. 187)** demuestra $|D(e') - D^*(e')| \le \exp(-c nf\log n) D^*(e')$, y el **Corolario 14.63** deduce las Hipótesis 14.43 y 14.76.

- **Casi ortogonalidad de series de Poincaré de Bessel y estimaciones orbitales (`§14.4`, pp. 188–208):**
  - **Proposición 14.65 (`Proposition 14.65`, Ensamblaje, p. 188):** Reduce el Teorema 14.1 a cinco estimaciones sobre $K_{uu'} = K^0_{uu'} + K^{\mathrm{deg}}_{uu'}$.
  - **Definición 14.66 (`Definition 14.66`, Familias de términos / *Term families*, p. 189), Teorema 14.67 (`Theorem 14.67`, Cota de pares / *Pair bound*, p. 189) y Corolario 14.70 (`Corollary 14.70`, p. 190):** Derivan las cláusulas fuera de la diagonal y diagonal a partir de cotas sobre filas escalares genéricas, bucles y términos no genéricos.
  - **Hipótesis 14.71 (S-KE, expansión del núcleo), 14.72 (S-MR, fila principal), 14.73 (S-LR, bucles), 14.74 (S-NG, términos no genéricos), 14.75 (S-DG, términos degenerados), 14.76 (S-DIM, fórmula de multiplicidad) y 14.77 (S-SZ, tamaños) (p. 190)**, junto con el **Lema 14.78 (`Lemma 14.78`, p. 190)** (desigualdades de tamaño exponenciales con $r_S = m/2 - 1$) -> **Teorema 14.79 (`Theorem 14.79`, p. 191):** Implican el Teorema 14.1.
  - **Observación 14.80 (`Remark 14.80`, la ventana, p. 191):** Señala que la construcción de las palabras debe establecer (14.1). **Observación 14.81 (`Remark 14.81`, ausencia de circularidad, p. 191):** El Lema 14.14 usa la cláusula diagonal del Teorema 14.1 para demostrar la no anulación en el Teorema 14.3, pero el Teorema 14.1 no depende de las aplicaciones de períodos, evitando ciclos.
  - **Identidades de fibras de Gram, medida de banderas y órbitas cercanas/lejanas (`§14.4.4`–`§14.4.12`, pp. 191–208):**
    - **Proposición 14.82 (`Proposition 14.82`, Identidad de fibra de Gram con soporte compacto, p. 192):** Expresa el promedio orbital sobre $U_J(F)\backslash U_J(\mathbb{A})$ como producto de Euler de densidades locales $D^{\mathrm{sd}}_v(\Phi_v, T)$ usando la fórmula de Siegel–Weil en el rango convergente [79, 40].
    - **Teorema 14.83 (`Theorem 14.83`, Medida de una clase de banderas adaptadas, p. 196):** Acota el covolumen de recubrimiento $\mathrm{CV}_\Gamma(A_B)$ mediante $\int_B D(\tau)\,d\tau$.
    - **Teorema 14.89 (`Theorem 14.89`, Planos hermíticos unimodulares definidos, p. 201):** $\operatorname{defClassNum}(E, 2) \le 4^f \rho^{5f}(1+f\log\rho)^{5f}$, conduciendo a la cota absoluta de volumen $V_{p,q} \le X^{n^2 f}$.
    - **Proposición 14.90 (`Proposition 14.90`, Casi unipotencia, p. 203), Proposición 14.92 (`Proposition 14.92`, Conteo cercano consciente de la filtración, p. 205), Proposición 14.93 (`Proposition 14.93`, Términos cercanos en la región moderada, p. 207) y Proposición 14.94 (`Proposition 14.94`, Banderas raras, p. 208):** Acotan las órbitas cercanas no triviales y las banderas raras, produciendo el error total $|D - M| \le e^{-nf\log n / 16} M$.

---

## Sección 15: Alturas, el período CM y las pendientes de los retículos destino y base (*Heights, the CM period, and the slopes of the target and base lattices*, pp. 208–240)

### Párrafo introductorio (pp. 208–209)

Esta sección demuestra las hipótesis (3.4), (3.6) y (3.7) de la Proposición 3.1. §15.1 fija la normalización de pendientes y alturas; §15.2 demuestra que la constante $\log\Omega$ de la Proposición 3.1 es el grado aritmético normalizado de la recta de períodos de una curva elíptica CM (fórmula de Chowla–Selberg en la forma aquí requerida); §15.3 acota la altura de $B_u$ por el producto de las normas de los $m$ levantamientos y el emparejamiento final; §15.4 enuncia la cota para la pendiente del retículo destino $R^\vee$; §15.5 combina ambas en (3.4); §15.6 demuestra (3.6) mediante la fórmula de dimensión de Weyl y la fórmula de masa de Siegel; §15.7 demuestra (3.7) mediante la teoría integral de módulos de Weyl; §15.8 compara los tres errores con $\mathcal{B}$ de (4.8); §15.9 recoge las entradas de la sección; y §15.10–§15.14 reducen las Hipótesis 15.10, 15.11, 15.12 y 15.16 a enunciados estructurales más finos.

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 209–240)

Se ponen $v = \frac{1}{2}\operatorname{rd}_E$, $\Lambda_a = \log(a\operatorname{rd}_E)$, $g = \log(g_0 g_1)$ (ec. (15.1)) y $\lambda_1 = L'(1,\chi_d)/L(1,\chi_d)$.

- **Pendientes, alturas y el período CM (`§15.1`–`§15.2`, pp. 209–212):**
  - **Observación 15.1 (`Remark 15.1`, p. 210):** Las pendientes $\mu(\Lambda) = \widehat{\deg}(\Lambda)/(n_F \operatorname{rk}\Lambda)$ y alturas $\operatorname{ht}(\phi) = n_F^{-1}\sum_v \log\|\phi\|_v^2$ (ec. (15.2)) son el doble de las de Bost [15] y coinciden exactamente con (13.1)–(13.2).
  - **Proposición 15.3 (`Proposition 15.3`, Chowla–Selberg, p. 210):** Para $d > 3$ primo con $d \equiv 3 \pmod 4$, $\frac{1}{h}\sum_C \log(\mathcal{A}(\Lambda_C)/\pi) = \gamma + \log\frac{2\pi}{\sqrt{d}} - \lambda_1$.
  - **Definición 15.5 (`Definition 15.5`, p. 211) y Proposición 15.6 (`Proposition 15.6`, p. 212):** Define $\log\Omega_\tau = \frac{1}{[M:\mathbb{Q}]}(2\log[\ell_\tau : s\mathcal{O}_M] - \sum_{\rho:M\to\mathbb{C}}\log\|s\|_\rho^2)$ para la recta hermítica $\ell_\tau$, y demuestra que es independiente de $M, \tau, \mathfrak{c}$ e igual a
    $$\log\Omega_\tau = \gamma + \log\frac{\pi}{v} - \lambda_1, \qquad v = \frac{1}{2}\operatorname{rd}_E.$$

- **Alturas de $B_u$, pendiente del retículo destino e Hipótesis (A4) / (3.4) (`§15.3`–`§15.5`, pp. 213–217):**
  - Para la descomposición en cadena $B_u = P_u \circ K_m \circ \dots \circ K_1$ (ec. (15.5)):
    - **Proposición 15.9 (`Proposition 15.9`, p. 213):** Acota $\operatorname{ht}(B_u) \le h_P + \sum_{j=1}^m n_F^{-1}\sum_v h_{K,j}(v) - \ell_\lambda - \langle\log\kappa\rangle$.
    - **Hipótesis 15.10 (normas de los núcleos), Hipótesis 15.11 (emparejamiento final) e Hipótesis 15.12 (constantes de marco) (p. 214):** Dan las cotas $s_j = \sum_{\rho \in \Phi}(\sum_{i=1}^N \operatorname{ph}(\nu_{j\rho i}) - (\sum_{i=1}^N \nu_{j\rho i})\log\Omega) + C_0(f N^2\Lambda_a + f m^3 N^2 L_\varepsilon)$, $h_P \le -\sum_{t \in T} a_t\log T_u + e_P$ y $\ell_\lambda \ge \sum_{j,\rho} h_{j\rho} - e_\lambda$.
    - **Observación 15.13 (`Remark 15.13`, p. 214):** Explica cómo la Hipótesis 15.10 produce el factor $m$ delante de $\operatorname{ph}(a_t)$ en (3.4) y cómo la Hipótesis 15.11 introduce $-a_t\log T_u$ por ramificación en el nivel $T_u$.
    - **Definición 15.14 (`Definition 15.14`, p. 214) y Corolario 15.15 (`Corollary 15.15`, p. 214):** Definen $h_u = h_u^0 - \langle\log\kappa\rangle$ y establecen $\operatorname{ht}(B_u) \le h_u$.
  - **Hipótesis 15.16 (`Hypothesis 15.16`, Pendiente destino, p. 215) y Observación 15.17 (`Remark 15.17`, p. 215):** Acota $\mu^{\mathsf{C}} - \langle\log\kappa\rangle \le \mu_0 + P_{\mathrm{pass}}$ con $\mu_0 \le \sum_{j=1}^m \sum_{\rho \in \Phi}(p_j - q_j)w_{j\rho}\log\Omega + \mathcal{L} + E_b$, $E_b \le C_0 m x^\varepsilon(B_0 + N_c)$; la Observación 15.17 la descompone en pasaje, cota del lado base y cota de covolumen sobre variedades de Shimura unitarias.
  - **Hipótesis 15.18 (`Hypothesis 15.18`, Pesos de los núcleos, p. 215)** -> **Teorema 15.19 (`Theorem 15.19`, p. 216) y Corolario 15.20 (`Corollary 15.20`, p. 217):** Demuestran la desigualdad (3.4) con $e_4 = (50 C_0 + 10)(N_T a \Lambda_a + m x^\varepsilon(B_0 + N_c))$.

- **Hipótesis (A6) / (3.6) e Hipótesis (A7) / (3.7) (`§15.6`–`§15.9`, pp. 217–223):**
  - **Definición 15.22 (`Definition 15.22`, p. 218):** Define $d_u^* = \operatorname{mass}(k) I_\Pi \prod_{\rho \in \Phi}\dim(\lambda_{u,\rho}^{\mathrm{col}})$ y $\log X_u = \frac{1}{fk}\log(D^*/d_u^*)$.
  - **Hipótesis 15.23 (`Hypothesis 15.23`, Presupuesto de dimensión, p. 218):** $D^* \ge (\frac{2}{3})^f \operatorname{mass}(r) I_\Sigma \prod_{\rho \in \Phi}\dim(\lambda_\rho^{\mathrm{row}})$.
  - **Proposición 15.25 (`Proposition 15.25`, p. 219) y Teorema 15.26 (`Theorem 15.26`, Hipótesis (3.6), p. 220):** Bajo la recurrencia de masa de Siegel y $T_u \ge X_u \Gamma^{-2/(fk)}$, demuestran (3.6) con $g = \log(g_0 g_1)$, $v = \frac{1}{2}\operatorname{rd}_E$ y $e_6 = C_6(L_\varepsilon + m^2 L_\varepsilon/k) + 2$.
  - **Observación 15.27 (`Remark 15.27`, p. 220):** Condiciones adicionales sobre el primo auxiliar $T_u$ (cota superior $(1+\frac{1}{fk})X_u\Gamma^{-2/(fk)}$, escisión en $K$ con $\pi \equiv 1 \pmod{Q_S q d (g_0 g_1)^2}$ y $\log T_u \le C m L_\varepsilon$).
  - **Definición 15.28 (`Definition 15.28`, $\mu_{\mathrm{std}}(\nu)$), Proposición 15.30 (`Proposition 15.30`), Proposición 15.32 (`Proposition 15.32`) y Teorema 15.33 (`Theorem 15.33`, Hipótesis (3.7), pp. 220–222):** Demuestran (3.7) con $e_7 = C_7 N_T a \Lambda_a (1 + m/k)$.
  - **Observación 15.34 (`Remark 15.34`, p. 223):** La misma descripción de $M_u$ da $\mu_{\max}(M_u) \le C N_T a \Lambda_a$.
  - **Proposición 15.35 (`Proposition 15.35`, Tamaños de errores, p. 223):** $e_4 + A e_6 + e_7 \le C_8 x^\varepsilon \mathcal{B}$.
  - **Subsección 15.9 (`§15.9`, p. 223):** Lista las hipótesis no demostradas (15.10, 15.11, 15.12, 15.16, 15.18, 15.23) y los teoremas publicados utilizados (primera fórmula límite de Kronecker, producto de Jacobi para $\Delta$, fórmula del número de clases de Dirichlet, teorema principal de multiplicación compleja, fórmula del discriminante en torres, fórmula de masa de Siegel, fórmula de Harish-Chandra de grados formales, fórmula de dimensión de Weyl, identidad de Capelli y dualidad de módulos de Weyl).

- **Reducción de las hipótesis arquimedianas y uniformidad en el nivel (`§15.10`–`§15.14`, pp. 223–240):**
  - **Norma arquimediana de cada levantamiento (`§15.11`, pp. 224–228):** **Proposición 15.39** (cota de bloque en espacio de Fock), **Hipótesis 15.42** (núcleo normalizado), **Hipótesis 15.43** (media de valores theta-nulos; incluye argumento de media logarítmica mediante el entero algebraico de Weber $X$ con $|\rho X| = (\Theta_\rho/E_\rho)^{12}$), **Hipótesis 15.44** (conteo de clases e índices), **Proposición 15.45**, **Teorema 15.46** (deduce Hipótesis 15.10) y **Observación 15.47 (`Remark 15.47`, p. 228)**.
  - **Emparejamiento final (`§15.12`, pp. 228–230):** **Proposición 15.48** (coisometría escalada para la aplicación de ramificación $\operatorname{br}_t$), **Hipótesis 15.50** (norma de Fock de $\xi_{\mathrm{Br}}$) y **Teorema 15.51** (deduce Hipótesis 15.11 asumiendo factorización de $P_u$ a través de $\operatorname{br}_t$).
  - **Constantes de marco (`§15.13`, p. 230):** **Proposición 15.52** (deduce Hipótesis 15.12 a partir de la fórmula del producto interno de Rallis en el rango convergente y la fórmula de Harish-Chandra de grados formales).
  - **Pendiente del retículo destino y covolúmenes en recubrimientos profundos (`§15.14`, pp. 230–240):**
    - **Proposición 15.53 (`Proposition 15.53`, Lado base, p. 231):** Acota $\operatorname{lcv}(R) \le D\langle\log\kappa\rangle + \sum_j \operatorname{lcv}(M_j) + \sum_y \ell_y(\dots)$.
    - **Hipótesis 15.56** (multiplicidades casi constantes) y **Proposición 15.57 (`Proposition 15.57`, Pasaje, p. 232):** Compara $\mu^{(1)}(R^\vee)$ con $\mu^{(0)}(R^\vee)$.
    - **Hipótesis 15.58** y **Hipótesis 15.59** (cota de covolúmenes $\operatorname{lcv}(M_j)/D \le \operatorname{main}_j + C U$); cuatro lemas de retículos (**Lemas 15.60–15.63**, truncamiento, descenso, alturas de componentes a pendiente, torsión plana —con **Observación 15.64 (`Remark 15.64`, el factor 2, p. 236)**— y **Lema 15.65**); entradas **(I1)**–**(I17)** (pp. 236–237, no demostradas aquí).
    - **Teorema 15.66 (`Theorem 15.66`, p. 237):** Asumiendo la Hipótesis 15.69 y **(I1)**–**(I17)**, demuestra la Hipótesis 15.59 con constante $C_0$ independiente de $x$, del punto, de $j$ y del nivel del recubrimiento. **Observación 15.67 (`Remark 15.67`, el signo del término principal, p. 238):** Conecta el signo del peso ancla con la condición (N1).
    - **Proposición 15.68 (`Proposition 15.68`, Relaciones locales de retículos en primos buenos, pp. 238–239):** Deriva de **(G1)**–**(G4)** las dos identidades exactas de caracteres de Chern de los ideales de caracteres de la aplicación de Hodge–Tate en primos buenos.
    - **Hipótesis 15.69 (`Hypothesis 15.69`, Pendiente media uniforme en recubrimientos profundos / *Uniform mean slope on deep covers*, pp. 239–240):** Enuncia la cota inferior uniforme $\frac{1}{\#\mathrm{Comp}}\sum_Z \operatorname{sl}_Z \ge -C(\Lambda_{B(u,g)}\|u\|_1 + q\operatorname{spread}(u))$ con $\operatorname{sl}_Z \le \operatorname{sl}_Z^{B(u,g)}(u)$, explicando la estrategia de torre de modelos integrales toroidales $Y_B$ al tomar $B \to \infty$ (usando Hilbert–Samuel aritmético por modelo fijo, mínimos sucesivos de Zhang, proporcionalidad de Hirzebruch–Mumford y la identidad exacta en primos buenos).
    - **Teorema 15.70 (`Theorem 15.70`, Ensamblaje de la Hipótesis 15.16, p. 240):** Ensambla Proposiciones 15.57 y 15.53, Hipótesis 15.58 y Teoremas 16.6 y 17.37 para concluir la Hipótesis 15.16.

---

## Sección 16: Los términos locales y la hipótesis (3.5) (*The local terms and hypothesis (3.5)* [en marcadores: *(A5)*], pp. 240–247)

### Párrafo introductorio (pp. 240–241)

Esta sección define los números $E_u$ de la Proposición 3.1 y demuestra la hipótesis (3.5) con $g = \log(g_0 g_1)$, $B_0 = f m b L_\varepsilon = 2nmb x^\varepsilon$ y $e_5 = C_E m B_0$, donde $g_0, g_1$ son los dos primos de (D5) y $C_E$ depende únicamente de $\varepsilon$. El número $E_u$ es una suma sobre los lugares finitos del cuerpo de los retículos, con un término por levantamiento que mide el fallo de integridad de un levantamiento en un lugar: cada levantamiento pierde $A\log g_i$ sobre el primo de nivel $g_i$, dando el término principal $m A \log(g_0 g_1)$ que la Proposición 3.1 cancela contra $mg$ en (3.6), mientras las demás contribuciones quedan acotadas por un múltiplo de $m B_0$. Se precisa además que los defectos de congruencia $\eta_j(w)$ de la Sección 17 entran en (3.4) y (3.3), pero no en (3.5).

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 241–247)

Para cada lugar finito $w$ de $L$ se definen $\ell_w = \frac{f_w\log p_w}{[L:\mathbb{Q}]}$ y $\sigma(w, y) = 2\ell_w e_w y$. A partir de los datos de exponentes locales **(L1)**–**(L5)** (`§16.2`, p. 242):

- **Definición 16.5 (`Definition 16.5`, p. 242).** Para $u \in W$, $1 \le j \le m$ y un lugar finito $w$ de característica residual $p = p_w$, define $E_{u,j}(w)$ por casos ($p = T_u$, $p = g_i$, $p = d$, $p \in P^{\mathrm{in}}$, resto):
  - $\varepsilon_u^T$ si $p = T_u$ y $w \in S_u$ ($0$ si $w \notin S_u$);
  - $v_p(D_\Gamma) - \frac{\Delta_j}{2} + \kappa_j + \frac{1}{e_w}\sum_{\rho \in \Phi} n_{u,j}(\rho) v_w(\tau_\rho(\bar\pi_i))$ si $p = g_i$ ($i \in \{0,1\}$);
  - $v_p(D_\Gamma) + \varepsilon_j^d$ si $p = d$; $v_p(D_\Gamma) + \varepsilon_{j,p}^{\mathrm{in}}$ si $p \in P^{\mathrm{in}}$; y $v_p(D_\Gamma)$ en otro caso.
  Se ponen $E_{u,j} = \sum_w \sigma(w, E_{u,j}(w))$ y $E_u = \sum_{j=1}^m E_{u,j}$.
  Se formulan las seis desigualdades **(E1)**–**(E6)** (p. 243): (E1) identidad de grado $|n_{u,j} - \Delta_j - A| \le \delta_j$, y (E2)–(E6) cotas por múltiplos de $B_0$.

- **Teorema 16.6 (`Theorem 16.6`, p. 243) y Corolario 16.7 (`Corollary 16.7`, p. 244).** Si $g_0 \ne g_1$ y valen **(E1)**–**(E6)** para $u$ y $j$, entonces $|E_{u,j} - A\log(g_0 g_1)| \le C_E B_0$ con $C_E = C_g + C_T + C_\Gamma + C_d + C_{\mathrm{in}}$. Sumando sobre $j = 1,\dots,m$ con $g = \log(g_0 g_1)$ y $e_5 = C_E m B_0$, se obtiene $mAg - e_5 \le E_u \le mAg + e_5$ (hipótesis (3.5)) y $e_5 \le C_E \mathcal{B}$.

- **Observaciones 16.8 y 16.9 (`Remarks 16.8–16.9`, p. 244).** La Observación 16.8 fija la consistencia de $g = \log(g_0 g_1)$ entre (3.5) y (3.6); la Observación 16.9 explica que la dependencia de $C_E$ respecto de $\varepsilon$ (vía $C_{\mathrm{in}}$) se absorbe en $x^\varepsilon$ para $x$ grande, aportando $1$ a la constante absoluta $C$ del Teorema A.

- **Hipótesis 16.13 (pérdidas en órbitas inertes) e Hipótesis 16.14 (exponentes y tamaños de los levantamientos) (`§16.4`, p. 246).** Mientras los Lemas 16.10–16.12 derivan (E2)–(E5) y la parte cerrada $P^C$ de (E6), quedan como hipótesis no demostradas aquí la cota $\sum_{p \in P^I} 2\log p\,|\varepsilon_{j,p}^{\mathrm{in}}| \le C'_{\mathrm{in}} B_0$ (Hipótesis 16.13) y las relaciones (E1), (16.1)–(16.3) y $0 \le w_j(\rho) \le 3b$ (Hipótesis 16.14). La Subsección 16.5 especifica cómo $E_{u,j}(w)$ entra con signo negativo en $s_u(w)$ para (3.2) y en la integridad local de los períodos para (3.3).

---

## Sección 17: Los lugares torcidos (*The twisted places*, pp. 247–269)

### Párrafo introductorio (p. 247)

En los lugares donde el tipo local de los levantamientos está torcido (*twisted*), el retículo de formas levantadas integrales difiere del retículo que ve el emparejamiento de períodos, y un módulo de congruencia (*congruence module*) mide la diferencia. Esta sección define los defectos de congruencia $\eta_j(w)$, enuncia las dos cotas que los controlan y demuestra las partes que se reducen a álgebra conmutativa y cohomología de Galois. El Teorema 17.37 combina ambas cotas y su conclusión entra en las alturas de las aplicaciones de períodos en (3.4) y en los parámetros de marco en (3.3) (no en (3.5)). La primera cota, Hipótesis 17.11, acota las longitudes de grupos de Tate–Shafarevich del cuerpo huésped en ventanas de escalas; la Subsección 17.4 muestra que implica una cota en dirección a la conjetura de Vandiver más fuerte que las cotas publicadas de Soulé [68] y de la Torre Durán [22], y rastrea el argumento hasta un enunciado de automorfía para representaciones de Galois residualmente reducibles que no es un teorema publicado.

### Definiciones, hipótesis, observaciones y enunciados principales (pp. 247–269)

- **Defectos de congruencia y grupos de Tate–Shafarevich (`§17.1`–`§17.2`, pp. 247–250):**
  - **Definición 17.1 (`Definition 17.1`, Defecto de congruencia / *Congruence defect*, p. 247).** Para un lugar torcido $w$ ($l = p_w$), $1 \le j \le m$, retículo $\Lambda$ sobre $\mathcal{O}$ de formas integrales de tipo torcido $\mu_w^{\mathrm{tw}}$ y álgebra de Hecke $\mathbb{T}$, descomponiendo $\Lambda_{\mathfrak{m}}\otimes\mathbb{Q} = V_{\mathrm{good}} \oplus V_{\mathrm{bad}}$ en cada ideal maximal $\mathfrak{m}$ de $\mathbb{T}$, se define
    $$\eta_j(w) = \sum_{\mathfrak{m}} \frac{\operatorname{length}_{\mathcal{O}}\!\left(\frac{V_{\mathrm{good}} \cap (\Lambda_{\mathfrak{m}} + V_{\mathrm{bad}})}{\Lambda_{\mathfrak{m}} \cap V_{\mathrm{good}}}\right)}{\operatorname{length}_{\mathcal{O}}(\mathcal{O}/l)},$$
    y $\eta_j(w) = 0$ si $w$ no es torcido.
  - **Definición 17.2 (`Definition 17.2`, Grupos de Tate–Shafarevich $\mathrm{Ш}_l(F, e)$, p. 248).** Con $M_e = \mathbb{Q}_l/\mathbb{Z}_l$ dotado de la acción de $\chi^{-e}$ ($\chi$ carácter ciclotómico $l$-ádico), $\mathrm{Ш}_l(F, e) \subset H^1(G_F, M_e)$ es el subgrupo de clases con $c|_{D_v} = 0$ para $v \mid l$ y $c|_{I_v} = 0$ para todo $v$ finito (y análogamente $\mathrm{Ш}_l(F, e; \mathcal{O})$); para un $l$-grupo abeliano finito $X$, $\lambda(X) = \log|X| = \operatorname{len}_{\mathbb{Z}_l}(X)\log l$.
  - **Proposición 17.7 (`Proposition 17.7`, Restricción a cuerpos abelianos, p. 249):** Para $E \subset \mathbb{Q}(\mu_N)$ y $l \nmid N$ impar con $(l-1)\nmid e$, $\mathrm{Ш}_l(\mathbb{Q}, e) \hookrightarrow \mathrm{Ш}_l(E, e)$ (en la parte $c = (-1)^e$ si $E$ es CM y $e$ es par).
  - **Proposición 17.8 (`Proposition 17.8`, Grupos de clases, p. 249):** Para $l$ impar, $(l-1)\nmid e$, $F_l = \mathbb{Q}(\mu_l)$ y $A = \mathrm{Cl}(F_l)\otimes\mathbb{Z}_l$, se tiene $\dim_{\mathbb{F}_l}\mathrm{Ш}_l(\mathbb{Q}, e)[l] = \dim_{\mathbb{F}_l}(A/lA)^{(\omega^{-e})}$; así la conjetura de Vandiver equivale a $\mathrm{Ш}_l(\mathbb{Q}, e) = 0$ para todo $e$ par con $2 \le e \le l-3$. (Se recuerda la identificación publicada con $K_{2e}(\mathbb{Z})\otimes\mathbb{Z}_l$ por Poitou–Tate y Rost–Voevodsky.)

- **Cota de Selmer en ventanas (`§17.3`, pp. 250–253):**
  - **Definición 17.9 (`Definition 17.9`, Pares de ventana / *Window pairs*, p. 250)** y **Definición 17.10 (`Definition 17.10`, $\chi$-cuerpos $E(\psi_0, e, q, d)$, p. 250).**
  - **Hipótesis 17.11 (`Hypothesis 17.11`, Cota de Selmer en ventanas / *Selmer bound on windows*, p. 250).** Para todo $\psi_0$, $0 < \varepsilon < \frac{1}{52}$ y $e : [1,\infty)\to\mathbb{N}$ con $x^{2+8\varepsilon} \le 2^{e(x)} \le 2x^{2+8\varepsilon}$, existen $J \ge 1$ y $X_0$ tales que para todo $X \ge X_0$ y todo par de ventana $(q, d)$ a escala $X^{1/J}$, existe $Y \in [X^{1/J}, X^{1/2}]$ tal que para todo $x \in [Y, Y^2]$, con $t = \lfloor x^{401}\rfloor$ y $E = E(\psi_0, e(x), q, d)$, todo $\mathrm{Ш}_l(E, e')$ ($0 < e' < t$) es finito y
    $$\sum_l \sum_{1 \le e' < t} \lambda(\mathrm{Ш}_l(E, e')) \le \exp\!\left(\tfrac{1}{2}x^\varepsilon\right).$$
  - **Teorema 17.12 (`Theorem 17.12`, Descomposición, p. 251):** Deduce la Hipótesis 17.11 de dos enunciados no demostrados aquí: **(I)** parte más y $l = 2$ en ventanas (que se escinde en cinco casos, incluyendo el genérico vía `(CorGK)`, casos (II)–(III) vía $\mathrm{GSp}_4$ y caso (V)), y **(II)** parte menos (de tipo Conjetura Principal de Iwasawa / Stickelberger–Kolyvagin).
  - **Proposición 17.13 (`Proposition 17.13`, Partes más vía caracteres, p. 252):** Cuando $l \nmid [(\mathbb{Z}/N)^\times : H]$, $\operatorname{len}_{\mathbb{Z}_l}\mathrm{Ш}_l(E, e)^{c=(-1)^e} = \sum_{\psi \in X_e} \operatorname{len}_{\mathcal{O}}\mathrm{Ш}_l(\mathbb{Q}, e; \psi)/e(\mathcal{O})$.
  - **Proposición 17.14 (`Proposition 17.14`, Parte más genérica desde `(CorGK)`, p. 253).**

- **Consecuencia en dirección a la conjetura de Vandiver y análisis de representaciones de Galois (`§17.4`, pp. 253–262):**
  - Enunciado **(V)**: $\sum_{l \in L}\lambda(\mathrm{Ш}_l(\mathbb{Q}, e)) \le C(e+1)^A$ para todo $e \ge 2$ par y todo conjunto finito $L$ de primos $l \ge 5$ con $(l-1)\nmid 2e$.
  - **Corolario 17.15 (`Corollary 17.15`, Anulación de espacios propios, p. 253):** Bajo (V), $A^{(\omega^{-e})} = 0$ para $\log l > C(e+1)^A$ (un exponencial más pequeño que los umbrales de Soulé [68] y de la Torre Durán [22]).
  - **Observación 17.16 (`Remark 17.16`, Torsiones impares, p. 254):** Para $e$ impar la suma análoga es clásicamente polinomial por los números de Bernoulli y Mazur–Wiles.
  - **Definición 17.17 (`Definition 17.17`, Posición genérica, p. 254)** y cadena de implicaciones **Proposición 17.19 (`(V)` desde `(CorGK)`)**, **Proposición 17.20 (`(CorGK)` desde `(PropGK)`)** y **Proposición 17.21 (`(PropGK)` desde `(Count)` y `(OneChar)`)** (pp. 255–256).
  - **Proposición 17.22 (`Proposition 17.22`, Consecuencia de la cota de Selmer, p. 256):** Bajo la Hipótesis 17.11, el producto $P(T) = \prod_{e < T}\prod_l |\mathrm{Ш}_l(\mathbb{Q}, e)|$ (fuera de dos primos dependientes de $T$) satisface $\log\log P(T) \le \frac{1}{2} T^{\varepsilon/401}$ para $T$ arbitrariamente grandes, estrictamente más fuerte que las cotas publicadas $\log\log P(T) \ll T^2\log T$.
  - **Enunciado `(OneChar)` (p. 257):** Reducido a cuatro entradas no demostradas aquí: **(G1)** inyección tangente (Ribet), **(G2)** desigualdad de intersección en álgebra de Rees trigraduada, **(G3)** finitud y automorfía para representaciones de tipo unitario en tres variables con representación residual $\Psi \oplus 1 \oplus \Psi^{-1}$ (señalando que queda fuera de Allen–Newton–Thorne [1] y Thorne [74]), y **(G4)** rigidez (anulación de grupos de Selmer de Bloch–Kato adjuntos y reducibles).
  - **Observación 17.23 (`Remark 17.23`, Normalizaciones en `(Count)` y `(OneChar)`, p. 258):** Precisa la convención de Frobenius geométrico $\sigma = \sigma_w^{-1}$ y las dos clases de representaciones admisibles $\rho : G_K \to \mathrm{GL}_3(\overline{\mathbb{Q}}_l)$.
  - **Subsecciones 17.4.1–17.4.3 (pp. 258–262):** Tratan los conteos de rango cuatro (propagación de automorfía y criterio de traza para enormidad de Newton–Thorne [51]), los puntos automórficos y cambio de base (Labesse, Mœglin–Waldspurger, Skinner [66] en rango dos de Hilbert), y **§17.4.3 (La cota efectiva de cohomología)**, donde el autor presenta una demostración alternativa (aún pendiente de verificación humana y no formalizada en Lean) de $\log\# H^2(G_{L,S}, \mathbb{Z}_p(e+1)) \le \exp((2ed)^{C_K}\log(2D))$ con $C_K = 150$.

- **La cota de congruencia y el ensamblaje final (`§17.5`–`§17.6`, pp. 262–269):**
  - **Hipótesis 17.24 (`Hypothesis 17.24`, Cota de congruencia, p. 262):** Para $x \ge x_0$ y $1 \le j \le m$,
    $$\sum_{w\text{ torcido}} \ell_w e_w \eta_j(w) \le d_j^0\!\left(C(f m b L_\varepsilon^2 + (\log x)^2 N_c) + \sum_l \log l \sum_{1 \le e < t_r}\operatorname{len}\mathrm{Ш}_l(E, e)\right).$$
  - **Proposición 17.25 (`Proposition 17.25`, p. 262):** Acota el módulo de congruencia por números de congruencia $\delta_x$.
  - **Proposición 17.27 (`Proposition 17.27`, Desigualdad de Fitting, p. 263):** Bajo **(F1)**–**(F4)**, acota $\delta_{x_0} \le \sum_{k=1}^g \operatorname{len}_{\mathcal{O}}\operatorname{Hom}_{R'}(\operatorname{coker} P, (K/\mathcal{O})^{n_k})$. (Después se enumeran los cinco componentes abiertos del paso tres —cotas por bloque, levantamiento cristalino con módulos de Wach, torsión auxiliar, series theta torcidas y sumaciones— y sus entradas publicadas, incluyendo representaciones de Galois [4], Langlands local, Poitou–Tate, Bloch–Kato, módulos de Wach, complejo de Herr y teorema de Berger [7].)
  - **Proposiciones 17.30, 17.31, 17.32, 17.34 y 17.35 (`Propositions 17.30–17.35`, pp. 265–268):** Identifican $\eta_j(w)$ en términos locales, acotan y recortan sistemas propios (con descenso de álgebras de Hecke en el Lema 17.33), reducen la Hipótesis 17.24 a la **Hipótesis 17.36 (`Hypothesis 17.36`, Cota de congruencia por componente, p. 268)**, y muestran (Proposición 17.35) que $\dim M_j = D_0$ implica $d_j^0 \le D_0$.
  - **Teorema 17.37 (`Theorem 17.37`, Cota para los defectos de congruencia, p. 269).** Asumiendo la condición (D6) de la Definición 18.1, la Hipótesis 17.24, $(\log x)^2 \le x^\varepsilon$ y $d_j^0 \le D_0$, para todo $1 \le j \le m$:
    $$\sum_{w\text{ torcido}} \ell_w e_w \eta_j(w) \le (C_N + 1) D_0 x^\varepsilon (B_0 + N_c).$$

---

## Sección 18: La demostración del Teorema A (*The proof of Theorem A*, pp. 269–282)

### Párrafo introductorio (p. 269)

Esta sección ensambla la demostración del Teorema A. Fija la forma de los datos admisibles que utiliza la parte aritmética del argumento, construye los pesos $a_t$ y los nodos $w_{u_0,j}$, enuncia las desigualdades que satisface la cadena de levantamientos theta, y deduce de ellas las siete hipótesis (3.1) a (3.7) de la Proposición 3.1 junto con la cota para los errores. Las desigualdades entre pendientes, alturas y términos locales se demuestran en las secciones sobre la ganancia y la pérdida, la desigualdad de pendiente, el lado arquimediano y los lugares torcidos, y la Hipótesis 18.10 las reúne en un único enunciado.

### Definiciones, hipótesis y enunciados principales (pp. 269–281)

- **Datos admisibles en ventanas de Selmer (`§18.1`, pp. 269–272):**
  - Se define $V(F, t_0) = \sum_l \log l \sum_{i=1}^{t_0-1}\operatorname{length}_{\mathbb{Z}_l}\mathrm{Ш}_l(F, i)$.
  - **Definición 18.1 (`Definition 18.1`, Datos admisibles con base $Y_0$, p. 270).** Para $J \ge 2$, $3 \le Y_0 \le Y \le x \le Y^{3/2}$ con $Y^2 \le Y_0^J$, los datos admisibles a escala $x$ para la ventana $[Y, Y^{3/2}]$ con base $Y_0$ consisten en: **(D1')** primos $q, d$ que satisfacen los Teoremas 5.10 y 5.12 con $K = J$ e $Y_0$ en lugar de $Y$, $e \ge 0$ con $x^{2+8\varepsilon} \le c 2^e \le 2 x^{2+8\varepsilon}$, y el cuerpo $E$ y grupos $H, A_0$; **(D2)–(D5)** de la Definición 6.1; y **(D6)** con $t_0 = \lfloor x^{400}\rfloor$, todo $\mathrm{Ш}_l(E, i)$ ($1 \le i < t_0$) tiene longitud finita y $V(E, t_0) \le \exp(\frac{1}{2}x^\varepsilon)$.
  - **Proposición 18.3 (`Proposition 18.3`, La ventana de Selmer, p. 271) y Proposición 18.4 (`Proposition 18.4`, p. 271):** Asumiendo la Hipótesis 17.11, demuestran la existencia de $J \ge 2$ y de ventanas arbitrariamente altas $[Y, Y^{3/2}]$ con base $Y_0$ en las que existen datos admisibles que cumplen (D1') y (D6) en cada escala $x \in [Y, Y^{3/2}]$.

- **Los pesos y los nodos (`§18.2`, pp. 272–274):**
  - **Definición 18.5 (`Definition 18.5`, Pesos, p. 272):** Enteros $a_t, b_t$ ($t \in T$) con $a \le a_t \le a + \frac{a}{kx^{13}}$ y $b' \le b_t \le (1 + x^{-2})b'$.
  - **Proposición 18.7 (`Proposition 18.7`, p. 273) y Corolario 18.8 (`Corollary 18.8`, p. 273):** Con $h_0 = 2\lceil x^{402}\rceil$, construye enteros $b_1(\rho)$ para elementos cima, gruesos y delgados de $\Phi$ y define los nodos $w_{u_0,j}(\rho) = b_1(\rho) + (j - \frac{1}{2})h_0$ ($1 \le j \le m$), verificando la condición de tipo infinito en raíces de la unidad $\prod_{\rho \in \Phi}\iota(\rho(\zeta))^{w_{u_0,j}(\rho)} = 1$ y las cotas de la Proposición 5.16.

- **Registros de cadena, hipótesis de contabilidad y demostración del Teorema A (`§18.3`–`§18.6`, pp. 274–281):**
  - **Definición 18.9 (`Definition 18.9`, Registro de cadena / *Chain record*, pp. 274–275).** Para constantes $C_* \ge 1, C_H \ge 0$ y exponentes $e_D, e_L \ge 0$, consiste en un conjunto finito no vacío $\mathcal{W}$ ($|\mathcal{W}| \le 2^{k-3}$), para cada $u \in \mathcal{W}$ un primo $T_u$, retículos hermíticos $N_u, M_u$ sobre $\mathcal{O}_E$ y $h_u \in \mathbb{R}$, un retículo hermítico $R$ con dual $R^\vee$, y números $E_{u,j}, \mathcal{L}, \Gamma, \mathcal{I}, \delta, \eta, \epsilon$ que satisfacen las ocho condiciones **(K1)**–**(K8)**:
    - **(K1)** $S - \Gamma \le C_* N_T m b x^{e_L \varepsilon}$ y $0 \le \mathcal{I} \le C_* N_T m b x^{e_L \varepsilon}$.
    - **(K2)** $\mu_{\max}(N_u) \le \mu_{\max}(M_u) + \Gamma + \mathcal{L} - E_u + C_* m B_0$ y $\mu(M_u) + \Gamma + \mathcal{L} - E_u - \operatorname{Lo}_u \le \mu(N_u)$, con $\operatorname{Lo}_u = C_*\mathcal{I} + C_* N_T m(\frac{a}{k} + b')\log T_u + C_* X'' + 1$.
    - **(K3)** $0 \le \delta \le \frac{1}{2}$, $\eta \ge 0$, $0 \le \epsilon \le \frac{1}{4}$, $(\eta + 4\sqrt{\epsilon})x^{C_H} \le 6$, y para todo $H \ge s - \mu_{\min}(R^\vee)$, $s - \log|\mathcal{W}| - \frac{1}{1-\delta}(4 u_F\log(1 + H/u_F) + (\eta + 4\sqrt{\epsilon})H) \le \mu(R^\vee)$.
    - **(K4)** $\mu_{\min}(R^\vee) = -\mu_{\max}(R)$, $s + \mu_{\max}(R) \le x^{C_H} b$, y $\mu(R^\vee) + h_u - \mathcal{L} \le \sum_{t \in T}(m\operatorname{ph}(a_t) - m a_t\log\Omega - a_t\log T_u) + C_* N_T a \Lambda_a + C_* m(B_0 + N_c)x^{e_D\varepsilon}$.
    - **(K5)** $|E_{u,j} - Ag| \le C_* B_0$.
    - **(K6)** $|(h_u + A\log T_u) - (h_{u'} + A\log T_{u'})| \le C_*(N_T a \Lambda_a + m B_0)$.
    - **(K7)** $\log T_u \ge \sum_{j=1}^m \frac{1}{f}\sum_{\rho \in \Phi}\log\frac{w_{u_0,j}(\rho)v}{\pi} + mg - C_*(\Lambda_a + \frac{m^2\Lambda_a}{k})$, $\log T_u \le C_* m L_\varepsilon$ y $|\log T_u - \log T_{u'}| \le C_* \log k$.
    - **(K8)** $-C_* N_T a\Lambda_a(1+\frac{m}{k}) \le \mu(M_u)$, $\mu_{\max}(M_u) \le C_* N_T a\Lambda_a$ y $\mu(N_u) \le \mu_{\max}(N_u)$.
  - **Hipótesis 18.10 (`Hypothesis 18.10`, Registros de cadena, p. 276):** Afirma la existencia de datos admisibles, pesos y un registro de cadena para todo $u_0 \in A_0$ con exponentes absolutos $e_D, e_L$ (pudiendo tomarse $e_D = 2$, $e_L = 0$). La **Proposición 18.11 (`Proposition 18.11`, p. 276)** verifica que los resultados de las Secciones 12–16 producen un registro de cadena con $e_D = 1, e_L = 0$ (y por ende $e_D = 2, e_L = 0$).
  - **Proposición 18.14 (`Proposition 18.14`, p. 279):** Un registro de cadena satisface las siete hipótesis (3.1)–(3.7) de la Proposición 3.1 con errores explícitos $e_1,\dots,e_7$.
  - **Proposición 18.16 (`Proposition 18.16`, p. 280):** Con $\kappa = \max(2, e_D, e_L + 1)$, demuestra $e_1 + e_2 + e_3 + e_4 + e_5 + A e_6 + e_7 \le x^{(\kappa+1)\varepsilon}\mathcal{B}$ (dando $x^{3\varepsilon}\mathcal{B}$, es decir $C = 3$).
  - **Subsección 18.6 (`§18.6`, Demostración del Teorema A, p. 281):** Deduce el Teorema A (con $C = 3$) a partir de las Hipótesis 17.11 y 18.10, dando $\zeta(s) \ne 0$ y $L(s, \chi^{(i)}) \ne 0$ para $\operatorname{Re} s > \frac{1}{2} + 7\varepsilon$ y por tanto para $\operatorname{Re} s > \frac{1}{2}$.

---

### Subsección 18.7: Hipótesis en la deducción final (*Hypotheses in the final deduction*, pp. 281–282) — Extracción íntegra

La Subsección 18.7 recoge la lista completa de hipótesis abiertas internas y entradas/teoremas publicados que intervienen en la deducción final del Teorema 1.1, organizada en cinco bloques:

#### 1. La cadena y las cotas de Hecke (*The chain and the Hecke bounds*, p. 281)
- La **Proposición 11.27** proporciona la valuación del factor de marco (*frame valuation*) bajo las normalizaciones de caracteres de paso y determinantes de la **Definición 11.23** (hipótesis **(N1)** / Hipótesis 11.22).
- Las **Hipótesis 11.38 ((N2))** y **11.42 ((N3))** conciernen, respectivamente, a los retículos en las posiciones impares y a la ley del núcleo normalizado ($|c| \le 1$).
- En la cota de Hecke, el **Teorema 12.54** controla el proyector isotípico, la **Proposición 12.40** acota la pérdida de ventana, y el **Lema 12.63** combina las estimaciones finales de cuotas.
- La **Hipótesis 12.12** (motores (A), (B), (C) de no degeneración de Hecke) aún requiere las estimaciones individuales de cuotas, las comparaciones entre niveles y la construcción de los sistemas de prueba (*test systems*).
- El **Corolario 12.65** utiliza el modelo de retículos de Weyl (*Weyl lattice model*).
- La **Proposición 12.67** requiere una cota polinomial para la constante $c_G$ de los pesos base.
- La colongitud en el primo auxiliar $T_u$ en **(L7)** (§12.6) constituye una entrada adicional.

#### 2. Períodos y multiplicidades (*Periods and multiplicities*, p. 282)
- El **Teorema 14.15** utiliza la relación de balancín (*seesaw relation*), su emparejamiento no nulo y las identificaciones de períodos (**Hipótesis 14.10, 14.11, 14.12**).
- El **Teorema 14.29** demuestra la identidad de paso doble a partir de las leyes generales y locales de la representación de Weil (**Hipótesis 14.27 y 14.28**).
- El **Lema 14.24** especifica las tres identidades de períodos necesarias para la racionalidad.
- El cálculo de multiplicidades requiere las identificaciones de etiquetas (**Hipótesis 14.59**) y las hipótesis de pre-traza (**Hipótesis 14.61**) de las Subsecciones 14.3.7 y 14.3.8.
- Las estimaciones sobre filas individuales en el **Teorema 14.79** también requieren la expansión del núcleo (**Hipótesis 14.71**, S-KE), la fila principal (**Hipótesis 14.72**, S-MR), las filas de bucles (**Hipótesis 14.73**, S-LR) y los términos degenerados y no genéricos (**Hipótesis 14.74–14.75**, S-NG, S-DG).
- El **Lema 14.78** demuestra las dos desigualdades exponenciales de tamaño con $r_S = m/2 - 1$.

#### 3. Alturas y términos locales (*Heights and local terms*, p. 282)
- La norma del núcleo (**Hipótesis 15.10 / Teorema 15.46**) utiliza el valor integral común de Weber (**Hipótesis 15.43**) y las identidades de períodos y normalización de la Sección 15 (**Hipótesis 15.42 y 15.44**).
- El emparejamiento final (**Hipótesis 15.11 / Teorema 15.51**) requiere su factorización a través de la aplicación de ramificación (*branching map*, junto con la **Hipótesis 15.50**).
- Para la cota de covolúmenes, el **Teorema 15.66** especifica el descenso, la torsión plana (*flat twist*) y las comparaciones de retículos bajo sus hipótesis **(I1)–(I17)**.
- La **Hipótesis 15.69** proporciona una cota inferior para el promedio de las pendientes de componentes con el término $q\operatorname{spread}(u)$ en el error.
- La torsión plana aporta el término principal en la desigualdad de covolumen.
- El cambio exacto de estructura integral en los primos buenos (**Proposición 15.68 / (G1)–(G4)**) todavía entra en la uniformidad en el nivel.
- En los lugares auxiliares e inertes, las cotas de grado y de órbitas (**Hipótesis 16.13 y 16.14**) entran en el **Corolario 16.7**.

#### 4. Lugares torcidos y ensamblaje (*Twisted places and assembly*, p. 282)
- El **Teorema 17.12** separa las partes más y menos, incluyendo el primo $2$ (reduciendo la **Hipótesis 17.11** a **(I)** y **(II)**).
- La **Proposición 17.13** separa los sumandos de caracteres cuando el orden del grupo es una unidad.
- La estimación genérica utiliza **`(OneChar)`** (entradas **(G1)–(G4)**) y **`(Count)`**.
- Los dos casos de rango cuatro también requieren propagación de automorfía y rigidez como en la **Subsección 17.4.1**.
- La comparación local de rango dos en la **Subsección 17.4.2** se aplica a formas modulares de Hilbert en la normalización enunciada.
- Para el retículo torcido, las **Proposiciones 17.30 y 17.34** identifican el módulo de congruencia y reducen su estimación a cotas por componente (**Hipótesis 17.36**).
- La estimación de levantamiento de Wach (*Wach lifting estimate*), las cotas para las otras filas locales y las comparaciones de series theta integrales todavía entran en ese argumento.
- La **Proposición 17.35** muestra por qué $\dim M_j = D_0$ basta en el último paso; el **Teorema 17.37** utiliza únicamente $d_j^0 \le D_0$.

#### 5. Entradas publicadas (*Published inputs*, p. 282)
- La **Sección 5.7** *(nota textual en 18.7; corresponde a los enunciados de §5.1 y §5.8)* utiliza el **Teorema 7 de Gallagher** [27] y la cota de cero excepcional **(C8)** para **(C7)**, y el caso de clase de rayo de **Thorner–Zaman** [75] junto con la cota de **Stark** [69] para **(C9)**.
- Para los argumentos locales, el teorema de de Rham de **Berger** es *Théorème 0.6*, equivalentemente *Théorème 5.19*, de [7].
- Para caracteres de Hecke algebraicos, los saltos de Hodge (*Hodge jumps*) en $\tau$ tienen signo $-n_\tau$ en la convención local de Artin.
- En la ecuación funcional CM, la fase arquimediana en tipo infinito $2m$ es $i^{\sum_i |2m_i|}$: sustituir $2m$ en la fase local da esta igualdad al ser par el exponente.
- La **identidad del producto interno de Rallis** todavía requiere la comparación de la norma de Petersson con los operadores de la **Proposición 15.52**.
- Las **fórmulas de masa y de grado formal** (Siegel y Harish-Chandra) deben usar las medidas de la estimación de dimensión (**Hipótesis 15.23 / Proposición 15.25**).
- **Cierre condicional expreso del autor (p. 282):** *La implicación final hacia el Teorema 1.1 permanece condicional a las hipótesis anteriores.*

---

**Confirmación:** Se han procesado las **18 secciones completas** de `main.pdf` (Sección 1 [1.1–1.4], Parte I [Secciones 2–6] y Parte II [Secciones 7–18, incluida la Subsección 18.7 íntegra], abarcando las pp. 4–282 de las 287 páginas del documento).
