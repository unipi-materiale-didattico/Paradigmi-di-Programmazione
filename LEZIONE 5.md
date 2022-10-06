# Lezione 29/09/2022

## Riassunto

* $t,s::= x|\lambda t.x|ts;$
* $t =_\alpha s;$
* $\lambda x.t =_\alpha\lambda y.t[y/x], y \notin FV(t);$
* $t\longrightarrow_\beta s, (\lambda x.t)s\longrightarrow_\beta t[s/x];$
* $t =_\beta s;$ 

Programmi = $\lambda -termini$.

t chiuso se $FV(t) = \empty.$

Esecuzione/Computazione = chiusura transitiva e riflessiva della $\beta$ riduzione. Catena di $\beta$ riduzioni.

Risultato = forma normale.

Alcuni programmi non terminano/non hanno forma normale. In altri programmi c'è almeno una riduzione che porta alla forma normale.

Tutte le forme normali che un termine può raggiungere sono uguali.

___________________________________________________________

## Teorema di Church-Rosser

$t\longrightarrow^*_\beta s_1 \land t\longrightarrow^*_\beta s_2\implies\exists\space u\space t.c.\space s_1\longrightarrow^*_\beta u\space\land s_2\longrightarrow^*_\beta u$

Esiste un ridotto comune che si può raggiungere in un numero finito di passi.

$t\longrightarrow^*_\beta s_1,t\longrightarrow^*_\beta s_2,\space s_1,s_2\in NF\implies s_1 =_\alpha s_2.$

### Corollario 1

Le forme normali sono uniche (mod. $=_\alpha$)

### Corollario 2

$t =_\beta s \leftrightarrow \exists u\space t.c\space t\longrightarrow^*_\beta u\longleftarrow^*_\beta s$.

### Corollario 3

L'ordine delle riduzioni è irrilevante, posso sempre raggiungere un risultato comune. Possiamo fare le riduzioni in parallelo $\implies$ Il $\lambda$ calcolo è parallelizzabile. Non ci sono effetti collaterali imperativi.

Qualsiasi cosa influisca dall'esterno rispetto alla catena di riduzione è un effetto collaterale. (Qualsiasi cosa vada fuori dal processo di riscrittura di un'espressione).

### Trasparenza referenziale

$e\longrightarrow v$ Il significato di e e di ciò che viene calcolato da e è lo stesso.

___________________________________________________________

$F$: Linguaggio funzionale.
E' fatto solo da espressioni.

$e ::= x|n|b|e+e|ite(e,e,e)|x\implies e|ee|ricorsione$

$(x\implies e)a = e[a/x]$.

## Codifica

Codificare = associare un $\lambda$ termine.

### 1. Codifica dei booleani

* $true = \lambda xy.x;$
* $false = \lambda xy.y;
* $ite = \lambda b. \lambda t. \lambda s. bts$

$ite\space true\space ts = (\lambda b.\lambda x.\lambda y.bxy)true\space ts\longrightarrow_\beta(\lambda x.\lambda y.true\space xy)ts\longrightarrow_\beta(\lambda y.true\space ty)s\longrightarrow_\beta(true\space ts) = (\lambda xy.x)ts\longrightarrow_\beta(\lambda y.t)s\longrightarrow_\beta t.$

* $ite(true,e_1,e_2) = e_1;$
* $ite(false,e_1,e_2) = e_2.$

### Esercizio

Sviluppare $ite\space false\space ts.$

### 2. Codifica dei numeri

Astraziione di un'iterazione.

* $o = \lambda f.\lambda x.x;$
* $1 = \lambda f.\lambda x.fx;$
* $2 = \lambda f.\lambda x.f(fx);$
* $n = \lambda f.\lambda x.f^nx;$
* $f^0 x = x;
* $f^{n+1}x = f(f^nx).$

#### SUCC:

$SUCC\space n\longrightarrow^*_\beta n+1$

$\lambda n.\lambda f.\lambda xf(nfx)$

$SUCC\space n = (\lambda n.\lambda f.\lambda xf(nfx))n\longrightarrow_\beta (\lambda f.\lambda xf(nfx))\longrightarrow^*_\beta \lambda f.\lambda x.f(f^nx) = n+1$

$\forall n\space nfx \longrightarrow^*_\beta f^nx$

#### add

$\lambda n.\lambda m.\lambda f.\lambda xnf(mfx)$

$f^n(f^mx)\longrightarrow f^{n+m}$

___________________________________________________________

$F:\N^k\longrightarrow\N$ è implementabile nel $\lambda$ calcolo se $\exists \overline{F}\in\Lambda.\forall n_1...n_k\space F(n_1...n_k) = m.$

$\overline{F}\overline{n_1}...\overline{n_k}\longrightarrow^*_\beta\overline{m}$

La logica non è implementabile nel $\lambda$ calcolo.

Se due formule non sono $\alpha$-equivalenti non possono essere $\beta$-convertibili.

#### Teorema

$\forall t\space t\space ha\space un\space punto\space fisso\space(ta =_\beta a)$

La negazione logica non ha punti fissi$\implies$ non si può implementare la logica nel $\lambda$-calcolo.
