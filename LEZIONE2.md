# λ-calcolo

Formalismo introdotto da Church negli anni 30.

Esempio informale:
x-y puo' essere interpretato in tre modi: 

* Quantita' in x,y;
* funzione in x $(f(x) = x - y)$;
* funzione in y $(f(y) = x - y)$;

## Notazione di Church:

$t => λx.t f(x) => λx.x-y$  

$f(y) => λy.x-y$

Supporta bene:
* funzioni in input;
* funzioni in output;

x-y:
* $λx.x-y;$
* $λy.x-y;$
* $h(x,y) = x - y => λx.λy.x-y$

## Definizione: λ-termini

Ogni variabile e' un λ-termine.

$s,t ::= x|(λx.t)|(t.s)$

x =  variabile.

$(λx.t)$ = λ-astrazione (operazione che consente di formare funzioni).

$(t.s)$ = Applicazione (applicare una funzione ad un argomento).

### Esempi:

* $(λx.x)$ e' un λ-termine  (identita').
* $(λx.y)$ e' un λ-termine (costante).
* $λu.v$ non e' un λ-termine perche' mancano le parentesi.

## Convenzione notazionale

* $(λx.t) => λx.t$ (si tolgono le parentesi);
* $t.s1...sn = (((t.s1).s2)...sn)$ (Assumo che le parentesi ci siano e associo a sinistra);
* $λx.t.s = (λx.(t.s))$;
* $λx1...xn.t = λx1.λx2...λxn.t;$

t => funzione/operatore. (t.s) = risultato dell'applicare t ad s visto come argomento.

$(λx.t) =>$ funzione il cui valore in s viene calcolato sostituendo s ad x in t.

La codifica di un numero naturale n e': $n = λfx.f$$(...f(x)).$

## Variabili libere e vincolate

$(λx.xy)x => x$ e' sia vincolata (segnaposto) che non (variabile).

Vanno sostituite le variabili che non sono affiancate ad un λ.

Dato t, si definisce $FV(t) = FV(x) =$ {x}.

$FV(t.s) = FV(t) U FV(s).$

$FV(λx.t)$ = FV(t)\{x}.

#### N.B: In $(λx.xy)x,$ x e' sia libera che vincolata. In questi casi si effettua il renaming delle variabili: $(λz.zy)x.$

Una variabile puo' essere legata da piu' binder.
