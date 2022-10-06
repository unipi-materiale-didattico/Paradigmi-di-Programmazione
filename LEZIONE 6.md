# Lezione 4/10/2022

$fixs\longrightarrow s(fixs)$

s è del tipo $\lambda f.e.$

$F\longrightarrow^*e[F/f]$

$Y = \lambda f(\lambda x.fxx).(\lambda x.fxx)$

$\Delta_f = \lambda x.fxx$

$Yt\longrightarrow^*_\beta t(Yt)$

$Yt =_\beta t(Yt) perchè\space hanno\space un\space ridotto\space comune.$

$Yt\longrightarrow_\beta (\lambda x.txx)(\lambda x.txx) = \Delta_t\Delta_t\longrightarrow_\beta t(\Delta_t\Delta_t)$

$\Theta = AA$

$A = \lambda y.\lambda x.y(xxy)$

$\Theta t\longrightarrow^*_\beta t(\Theta t)$

$\Theta (\lambda f.e)\longrightarrow^*_\beta e[FACT/f]$

## Esercizi

### MULT

MULT(x,y)

* MULT(0,n) = 0;
* MULT(m+1,n) = ADD(n,MULT(m,n)),

$\lambda f.\lambda m.\lambda n.ite(Eq\space m,0,0,ADDn(f(PREDm)n)$

MULT(m,n) = 

* 0 if m = 0;
* n + (m-1)n altrimenti.

$MULT_\Theta 2\space 2:\Theta(\lambda f.t)2\space 2 \rightarrow t(MULT_\Theta)2\space 2\longrightarrow^*_\beta ite(Eq\space 2,0,0,ADD2(MULT_\Theta(PRED2)2)\longrightarrow^*_\beta ADD2(MULT_\Theta(PRED 2)2)\longrightarrow^*_\beta ADD2(ADD\space 2\space 0)\longrightarrow_\beta 4$

$Y =_\beta \Theta$

___________________________________________________________

## Strategie di valutazione

* Chiamata per nome (Call by name (CBN));
* Chiamata per valore(Call by value(CBV))(Riduco fino ad una forma normale/ad un valore);

### Osservazioni

#### 1

Ci sono termini $t\space che\space terminano\space in\space cbn\space e\space non\space terminano\space in\space cbv$

$t\downarrow_{cbn} \And\space t\uparrow_{cbv}$.

#### 2

##### Teorema

Se un termine t riduce ad una forma normale s, allora  $t\xrightarrow{cbn}^*_\beta s$

Se c'è una forma normale la cbn la raggiunge.

#### 3

cbv è più efficiente 

#### 3.1

Call by need funziona come cbn.

I linguaggi lazy usano call by need

##### Teorema

Call by need è uguale a Call by name a livello del calcolo.

$(\lambda x.t)s$ se in $s$ ho degi effetti collaterali, con cbv so quando verranno effettuate le modifiche, con cbn no.

