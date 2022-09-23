# Paradigmi di (linguaggi) programmazione
### Ruolo dei tipi:
Un linguaggio fortemente tipato introduce regole per la scrittura dei programmi.

Per imparare ad usare un linguaggio bisogna capire:
* quali regole sui tipi chiede di rispettare;
* quali controlli vengono effettuati sui programmi.

#### Approcci:
* Static analysis;
* Control flow analysis;
* model checking.

## Crisi dei fondamenti:
- 1600, sviluppo dei calcoli infinitesimali. 
    * Metodi poco chiari, contraddizioni, paradossi dell'infinito.
    * Infinitesimi.
- 1800, geometrie non euclidee

Necessita' di definire i principi della matematica.

### Cantor Dedekind
La consistenza dell'analisi si riduce alla teoria dei sistemi numerici (teoria dei numeri) che a sua volta si riduce all'aritmetica.
La consistenza della geometria si riduce a quella dell'analisi. Se si vuole dare un fondamento alla matematica, bisogna darlo all'analisi.

### Frege
Fine '800, inizio '900. Padre del logismo(fondare la matematica sulla logica).
* Ideografia(∀x A(x), ∃ x . B(x,y))
* Con la logica del primo ordine si puo' scrivere tutto di matematica.
* $[(\vdash A \implies B) \vdash A] \implies \vdash B$ 
* $A \implies \{x : \vdash A(x)\}$

### Hilbert
#### Metodo assiomatico:
F.O.L (first order logic) + Assiomi

#### Aritmetica di Peano
* $∀x ¬(O = S(x))$
* $∀x,y  x + y = y + x$

Contiene 7 Assiomi

#### Consistenza
Non si dimostra il falso.

#### Completezza
Dimostra tutto cio' che e' dimostrabile

#### Decidibilita'.

### Procedura di calcolo
$f: D => D$ Prende qualcosa in input e restituisce qualcosa in output

1. * Funzioni elementari (calcolabili)
   * f,g calcolabili $\implies$ g∘f calcolabile

Calcolabile = Ricorsivo

2. Church ($λ-calcolo$);
3. Turing: 
   * Algoritmo = elenco di regole che una persona puo' eseguire in modo meccanico e preciso.
#### Analisi di Turing:
* Si manipolano simboli scritti su carta, in caselle;
* Si guarda un simbolo;
* Si compie un'azione determinata da: 
  * simbolo osservato;
  * stato mentale;
* L'azione si riduce a riscrivere simboli.

$<2, a, b, x, S>$

2 = Stato;
a = simbolo;
b = scrivo b;
S = {l,r,S}

$f: \N \implies \N \space calcolabile \leftrightarrow ∃ M t.c. ∀ n ∈ \N\space M(n)↓ ∧ M(n) = m \leftrightarrow f(n)↓ ∧ f(n) = m$

Esistono funzioni non calcolabili (Halting problem).

$f(n) = Mn(n)↓ oppure ↑$

$F.O.L \vdash A \implies B \leftrightarrow Mn(n)↓$

Esiste una macchina di Turing U universale $\implies U(n,m)\implies Mn(m).$

Forte distinzione tra la macchina, le istruzioni e gli input/dati.

Dati ≡ Programmi.

### Architettura di Von Neumann:
|Memoria| $\leftarrow Dati \space programmati$

|CPU|

Trasformazione di memoria = Computazione (trasformazione di stati).