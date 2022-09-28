# Lezione 4: 27/09/2022

## $Paradigma\space imperativo$

* $Variabili\space mutabili;$
* $Assegnamento;$
* $Computazione = Trasformazione\space di\space stati \rightarrow$ $Conigurazione\space di\space memoria \rightarrow$ $Collezione\space di\space variabili\space con\space i\space valori\space associati.$
* $Si\space procede\space per\space istruzioni.$

## $Paradigma\space funzionale$

* $Programmare\space solo\space con\space espressioni;$
* $Computazione = riscrittura\space di\space espressioni;$
* $Programmazione\space dichiarativa;$
* $Le\space espressioni\space sono\space funzioni\space (ordine\space superiore);$
* $Ricorsione;$

___________________________________________________________

$t,s ::= x|\lambda x .t|ts$

$(\lambda x.t)s\longrightarrow _\beta t[s/x]$

$t =_\alpha s$

$\lambda x.(\lambda y.y)x = \lambda z.z\space perchè: \lambda x.(\lambda y.y)x\longrightarrow _\beta \lambda x.x =_\alpha\lambda z.z$.

$t =_\beta s\space\space if\space t(_\beta\longleftarrow U\longrightarrow_\beta)^*s$

$Catena\space finita\space di\space\beta\space riduzioni\space che\space porta\space da\space t\space ad\space s\space(in\space entrambi\space i\space versi.)$

$Si\space dice\space allora\space che\space sono\space \beta - convertibili.$

### Proposizione

$Se\space\space\space t\longrightarrow ^* _\beta s\space\land\space t =_\alpha t'\implies\exists\space s'|\space t'\longrightarrow_\beta s'\space\land\space s =_\alpha s'$.

* $1.$ $La\space\beta - riduzione\space non\space è\space deterministica.$
  * $((\lambda x.x)I)\Omega$
* $2.$ $La\space \beta - riduzione\space può\space non\space terminare.$
  * $K =\lambda x.\lambda y.x$
  * $KI\Omega = (\lambda xy.x)I.\Omega$
    * $\longrightarrow _\beta I$
    * $\longrightarrow _\beta KI\Omega$

### $1.1$

$t\longrightarrow^*_\beta u_1\space\land\space t\longrightarrow^*_\beta u_2\space\implies u_1 =_\alpha u_2$

$La\space\beta-riduzione\space è\space confluente.$

### $2.2$

$Se\space t\longrightarrow^*_\beta s_1\space\land\space t\longrightarrow^*_\beta s_2\space\implies s_1\longrightarrow^*_\beta w\longleftarrow^*_\beta s_2$

$La\space forma\space normale\space di\space un\space termine,\space se\space c'è,\space è\space unica.$