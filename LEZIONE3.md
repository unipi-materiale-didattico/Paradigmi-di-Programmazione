22/09/2022

$t[s/x]$ termine ottenuto sostituendo tutte le occorrenze libere di x in t con s.
* $x[s/x]$ = s;
* $y[s/x]$ = y;
* $tu[s/x]$ = $t[s/x] u[s/x]$;
* $(λx.t)[s/x]$ = $λx.t$ perche' le occorrenze di x in t sono legate al λ.

#### Problema:
$(λx.y)[x/y]$ = λx.x Risulta la funzione costante = alla funzione identita'.

Bisogna garantire che non avvenga la cattura di variabili con la sostituzione:
* $(λx.t)[s/x] = λx.t$;
* $(λy.t)[s/x] = λy.t[s/x] se y ∉ FV(s);$
* $(λy.y)[s/x] = (λz.t[z/y])[s/x] = λz.t[z/t][s/x] z ∉ FV$(t) e z ∉ FV(s). Renaming che riduce al caso 2.
  
#### Esempio:
$(λy.x)[y/x] = (λz.x)[y/x] = λz.y$ Rimane una funzione costante.

#### Esercizio:
Calcolare:
* $(λy.x(λw.vwx))[uv/x]$;
* $(λy.x(λx.x))[λy.xy/x]$.

### α-Conversione:

$λx.t =_α λy.t[x/y] (y ∉ FV(t)).$

$=_α ⊆ Λ x Λ$ 

E' la piu' piccola equivalenza compatibile con la sintassi del calcolo.

#### Definizione induttiva:
* Assioma di base: $λx.t =_α λy.t[y/x];$
* $t =_α t;$
* $(t =_α s) => (s =_α t);$
* (t =$_α$ s) & (s =$_α$ u) => (t =$_α$ u);
* (t =$_α$ t') & (s =$_α$ s') => ts =$_α$ t's';
* $(t =_α s)$ =>  $λx.t =_α λx.s;$

#### Esempi:
* function succ(x){x+1}  =$_α$ function succ(y){y+1};
* $λxy.x(xy) =α λab.a(ab);$

#### Lemma:
$(t =_α t') \land (s =_α s') \implies t[s/x] =_α t'[s'/x];$

#### N.B
$F: Λ^n => Λ t1 =α s1... tn =α sn => F(t1...tn) =α F(s1...sn)$.

### Calcolo e semantica:

($\lambda$.t)s =>$\beta$ t[s/x].

($\lambda$.t)s = Redex

t[s/x] = Contractum

=>$\beta \subseteq \Lambda \times \Lambda$;

* ($\lambda x$)s $\longrightarrow_\beta$ t[s/x];
* (t $\longrightarrow_\beta$ s)$\implies$ $\lambda x.t \longrightarrow_\beta \lambda x.s$;
* $(t \longrightarrow_\beta s)\implies(tv\longrightarrow_\beta sv)$;
* $(t \longrightarrow_\beta s)\implies(ut\longrightarrow_\beta us)$;

#### Esempi di calcolo:
* $(\lambda x.x(xy))t \longrightarrow_\beta t(ty)$;
* $(\lambda x.(\lambda y.yx)z)v \longrightarrow_\beta (\lambda y.yv)z \lor(\lambda x.zx)v\longrightarrow_\beta zv$;

Un termine puo' avere piu' $\beta$ redex. La $\beta$ riduzione non e' deterministica.

$(\lambda x.xx)t = \Delta \longrightarrow_\beta tt$;

$(\lambda x.xx)(\lambda x.xx) = \Omega\longrightarrow_\beta\Delta\Delta$  La computazione puo' non terminare.

K = $\lambda xy.y$;

K$\Omega = (\lambda xy.y)\Omega$;

$(\lambda xy.y)(\Delta\Delta)$

$K\Omega\longrightarrow_\beta K\Omega$ Puo' andare avanti all'infinito continuando a ridurre $\Omega$.

$K\Omega\longrightarrow_\beta\lambda y.y = I$ Oppure puo' terminare se riduco K.

#### Definizione:
Un termine t e' una/in forma normale se non $\beta$-riduce a niente.

t ha una forma normale se $\exist$ un termine s tale che t $\beta$-riduce ad s in un numero finito di passi.

$\exist s \in NF . t \longrightarrow^*_\beta s$.

$\N\longrightarrow\Lambda$   
Ad ogni n $\in\N$ associo un termine $c_n$ (detti Numerali di Church) = $\lambda f.\lambda x.f^n(x)$
$f^0x = x; f^nx = f(f^{n-1})$ numero di interazioni.

$c_0 = \lambda f.\lambda x.x$

$c_1 = \lambda f.\lambda x.fx$;

$c_2 = \lambda f.\lambda x.f(fx)$;

Generica procedura che itera un numero di volte una funzione.

$F: \N^k\longrightarrow\N$

$t_Fc_{n_1}...c_{n_k}\longrightarrow_\beta c_F(n_1...n_k)$.

#### Esercizi: 
  * SUCC = $\lambda n.\lambda f.\lambda x.f(nfx)$ $\beta$-ridurre:
    * SUCC $c_0$;
    * SUCC $c_1$;
    * SUCC $c_2$;
* ADD = $\lambda n.\lambda m.\lambda f.\lambda x.nf(mfx)$ Calcolare:
  * ADD($c_1$);
  * ADD($c_2$);  
