---
title: T.3 - Sistemes seqüencials
---

> [!warning] Atenció
> 
> Aquesta pàgina NO està acabada!

Els circuits seqüencials són circuits amb la capacitat de seguir un procés amb un ordre, per tant, estàn afectats per el moment en el que entren les senyals d'entrada, no només elles afecten el resultat.
Aquests sistemes per a tenir un control del temps fan servir un circuit anomenat **flip-flop**, aquest, és capaç d'emmagatzemar un bit.

# Mantenir el control
## Flip-Flops
Per treballar amb els flip-flops designarem una nomenclatura comú:
- $Q$ o $Q⁺$ S'utilitzarà per a definir l'estat actual
- $Q⁻$ S'utilitzarà per a definir l'estat anterior
- Una *Taula de transicions* serà la taula que marcarà com han de ser les entrades per a guardar un bit en concret depenent del que hi hagés guardat en el moment.
- La *Taula de veritat* serà igual que amb els altres circuits, relacionarà totes les entrades amb les sortides.

Hi ha diferents tipus de flip-flops, tot i que tots parteixen del mateix, el de **tipus RS**:
### Tipus RS
Aquests, tenen 2 entrades, l'entrada $S$ o *set*, que servirà per a guardar un 1 a la memòria i l'entrada $R$ o *reset*, que servirà per deixar la memòria a 0.
Amb portes lògiques, aquests flip-flops es construeixen així:
![Construcció flip-flop SR](/elecdig/b1/t2/sr.png)

Per tant, si $S=1, R=0$ la sortida $Q$ sempre serà 1, per altra banda, si $S=0, R=1$ la sortida $Q$ sempre serà 0.
Això com es pot imaginar, porta un greu problema, no està permès definir $S = 1, R= 1$, ja que **la sortida està indeterminada**.
D'aquesta manera, la taula de transicions i la taula de veritat queden de la següent manera:

Taula de transicions:

| $Q⁻$ | $Q⁺$ | $S$ | $R$ |
| ---- | ---- | --- | --- |
| 0    | 0    | 0   | X   |
| 0    | 1    | 1   | 0   |
| 1    | 0    | 0   | 1   |
| 1    | 1    | X   | 0   |

Taula de veritat:

| $S$ | $R$ | $Q⁺$             |
| --- | --- | ---------------- |
| 0   | 0   | $Q⁻$             |
| 0   | 1   | 0                |
| 1   | 0   | 1                |
| 1   | 1   | X (Indeterminat) |
### Tipus D
El tipus D és molt similar al RS, de fet, és el mateix amb les dues entrades connectades entre si de la següent manera:
![Construcció flip-flop D](/elecdig/b1/t2/d.png)

D'aquesta manera es soluciona el problema de l'entrada indeterminada, ja que mai es podrà definir $S$ i $R$ a 1 a la vegada.
Les seves taules són les següents:

Taula de transicions:

| $Q⁻$ | $Q⁺$ | $D$ |
| ---- | ---- | --- |
| 0    | 0    | 0   |
| 0    | 1    | 1   |
| 1    | 0    | 0   |
| 1    | 1    | 1   |

Taula de veritat:

| $D$ | $Q⁺$ |
| --- | ---- |
| 0   | 0    |
| 1   | 1    |
### Tipus JK
Aquest flip-flop també és similar a un RS, amb les entrades connectades de la següent manera:
![Construcció flip-flop JK](/elecdig/b1/t2/jk.png)

Per tant, quan $J=1, K=1 \Rightarrow Q⁺ = \overline{Q⁻}$ 
Les seves taules, per tant són:

Taula de transicions:

| $Q⁻$ | $Q⁺$ | $J$ | $K$ |
| ---- | ---- | --- | --- |
| 0    | 0    | 0   | X   |
| 0    | 1    | 1   | X   |
| 1    | 0    | X   | 1   |
| 1    | 1    | X   | 0   |

Taula de veritat:

| $J$ | $K$ | $Q⁺$            |
| --- | --- | --------------- |
| 0   | 0   | $Q⁻$            |
| 0   | 1   | 0               |
| 1   | 0   | 1               |
| 1   | 1   | $\overline{Q⁻}$ |
## Activació dels flip-flops
Normalment, els circuits funcionen amb un [[Estructura i algebra de boole#Senyal de rellotge|senyal de rellotge]] per a poder sincronitzar tots els components, per tant, ens interessa que poguem controlar els flip-flops amb una senyal de rellotge, per això, els flip-flops tenen una altra senyal d'entrada, la senyal de *clock*.

Aquesta senyal es pot fer servir de quatre maneres diferents en els circuits:
- Per flanc de pujada
- Per flanc de baixada
- Per nivell alt
- Per nivell baix

El conveni per a saber de quina manera funciona el flip-flop és el següent:
![Conveni rellotge flip-flop](/elecdig/b1/t2/conveni.png)

### Definir de manera asíncrona
Els flip-flops es poden definir de manera asíncrona si porten incorporades les entrades $CLR$ (clear) i $PR$ (preset).

Aquestes entrades ignoren el senyal de rellotge i actuen en qualsevol moment, el seu funcionament és el següent:
- $CLR$ defineix $Q^+ = 0$
- $PR$ defineix $Q^+=1$

## Registres (o també shift registers)
Els registres són uns circuits construïts a base de flip-flops que actuen com una espècie de memòria, a diferència dels flip-flops, aquests poden emmagatzemar vàries quantitats de bits, depenent de la seva construcció.

Hi ha diferents tipus de registres, tot i que tots funcionen a partir del mateix principi, només canvien la forma en la que es llegeixen o entren les dades emmagatzemades.
Per a simplificar el tema, ja que es pot deduir com funcionen els altres, només ensenyaré el **registre universal** o *universal shift register*.

Aquest està construït de la següent manera:
![Construcció registre universal](/elecdig/b1/t2/unireg.png)

Es veu que té diferents entrades i sortides, les entrades són les següents:
- $\overline{LD}/SH$ Selecciona entre el mode en sèrie o el mode en paral·lel
- $SI$ És l'entrada en sèrie, només utilitzada si el mode en sèrie està activat
- $CLK$ Senyal de rellotge
- $CLR$ Si en té, deixa el registre a 0 en totes les posicions
- $D_n$ Entrades en paral·lel, només actives si el mode paral·lel està activat

Les sortides que té son:
- $Q_n$ La sortida en paral·lel, o, si només es llegeix la última, la sortida en sèrie.

## Comptadors
Els comptadors són uns sistemes molt útils que permeten comptar el nombre de cops que ha ocorregut un esdeveniment en particular, tot i contar de 0 a *n*, també poden comptar amb qualsevol seqüència "aleatòria" definida en la seva construcció.
Es diu que un comptador es **asíncron** si els senyal de rellotge (o l'esdeveniment) no arriba a tots els flip-flops a la vegada.
Per altra banda, s'anomena **síncron** si el senyal arriba a tots els flip-flops a la vegada.

Si un comptador es connecta a un rellotge, es pot fer servir com a **divisor de freqüència**, escollint com es vol que es divideixi triant un bit de un pes diferent.

### Comptadors asíncrons
Un comptador asíncron bàsic es construeix de la següent manera:
![Construcció comptador asíncron incremental](/elecdig/b1/t2/comptasinc.png)

Es pot veure que només té una entrada, tot i que té *n* sortides, depenent del número al que es vulgui contar.

Si es vol fer que el comptador sigui decremental, es pot connectar de la següent manera:
![Construcció comptador asíncron decrementall](/elecdig/b1/t2/comptasdec.png)

I, finalment, si es vol seleccionar entre un comptador incremental o decremental senzillament s'ha de col·locar un multiplexor 2x1 entre cada flip-flop que seleccioni entre la sortida negada o no-negada.

### Comptadors síncrons
Els comptadors síncrons es caracteritzen per que el senyal de rellotge arriba a la vegada a tots els flip-flops, aquests es poden construïr per a que segueixin una seqüència en concret.
Per a dissenyar-los es fa de la següent manera:
#### Disseny d'un comptador síncron
1. **Determinar la seqüència**
	1. Per a aquest exemple, farem un comptador asíncron up/down, per tant si $UP/DW = 0$ la seqüència és: $0, 1, 2, 3, 4, 5, 6, 7$ i per a $UP/DW = 1$ la seqüència serà: $7, 6, 5, 4, 3, 2, 1, 0$
2. **Decidir el tipus de flip-flop**
	1. Per a construir l'exemple es faràn servir flip-flops de tipus JK.
3. **Fer la taula de veritat i simplificar per karnaugh**
	1. La taula de veritat queda de la següent manera:


| $UP/DW$ | $Q_2^-$ | $Q_1^-$ | $Q_0^-$ | $Q_2^+$ | $Q_1^+$ | $Q_0^+$ | $J_2$ | $K_2$ | $J_1$ | $K_1$ | $J_0$ | $K_0$ |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0       | 0       | 0       | 0       | 0       | 0       | 1       | 0     | X     | 0     | X     | 1     | X     |
| 0       | 0       | 0       | 1       | 0       | 1       | 0       | 0     | X     | 1     | X     | X     | 1     |
| 0       | 0       | 1       | 0       | 0       | 1       | 1       | 0     | X     | X     | 0     | 1     | X     |
| 0       | 0       | 1       | 1       | 1       | 0       | 0       | 1     | X     | X     | 1     | X     | 1     |
| 0       | 1       | 0       | 0       | 1       | 0       | 1       | X     | 0     | 0     | X     | 1     | X     |
| 0       | 1       | 0       | 1       | 1       | 1       | 0       | X     | 0     | 1     | X     | X     | 1     |
| 0       | 1       | 1       | 0       | 1       | 1       | 1       | X     | 0     | X     | 0     | 1     | X     |
| 0       | 1       | 1       | 1       | 0       | 0       | 0       | X     | 1     | X     | 1     | X     | 1     |
| 1       | 0       | 0       | 0       | 1       | 1       | 1       | 1     | X     | 1     | X     | 1     | X     |
| 1       | 0       | 0       | 1       | 0       | 0       | 0       | 0     | X     | 0     | X     | X     | 1     |
| 1       | 0       | 1       | 0       | 0       | 0       | 1       | 0     | X     | X     | 1     | 1     | X     |
| 1       | 0       | 1       | 1       | 0       | 1       | 0       | 0     | X     | X     | 0     | X     | 1     |
| 1       | 1       | 0       | 0       | 0       | 1       | 1       | X     | 1     | 1     | X     | 1     | X     |
| 1       | 1       | 0       | 1       | 1       | 0       | 0       | X     | 0     | 0     | X     | X     | 1     |
| 1       | 1       | 1       | 0       | 1       | 0       | 1       | X     | 0     | X     | 1     | 1     | X     |
| 1       | 1       | 1       | 1       | 1       | 1       | 0       | X     | 0     | X     | 0     | X     | 1     |

Després de la simplificació per karnaugh, les funcions queden:
$$
K_2=E\cdot \overline{Q_1 \cdot Q_0} + \overline{E} \cdot Q_1 \cdot Q_0$$
$$J_2=E\cdot \overline{Q_1 \cdot Q_0} + \overline{E} \cdot Q_1 \cdot Q_0$$

$$K_1=\overline{E} \cdot Q_0 + E \cdot \overline{Q_0}$$
$$J_1=\overline{E} \cdot Q_0 + E \cdot \overline{Q_0}$$

$$
K_0=1$$
$$J_0=1
$$
4. **Implementar el circuit**
	1. El comptador queda implementat de la següent manera:
	![Construcció comptador síncron](/elecdig/b1/t2/comptsinc.png)