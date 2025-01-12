---
title: T.3 - Sistemes seqüencials
---
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

