---
title: T.2 - Sistemes combinacionals
---
> [!warning] Atenció
> 
> Aquesta pàgina NO està acabada!


>[!info] TL;DR
>
>La sortida d'un **circuit combinacional** només es veu condicionada per l'entrada que té, hi ha diferents tipus, però normalment serveixen per a fer càlculs de l'àlgebra de boole.

## Anàlisi i disseny dels circuits combinacionals
Per a treballar amb circuits combinacionals s'ha de saber com analitzar el que fan, si és que no sabem quin tipus de circuits són, o hem d'aprendre a dissenyar els nostres propis circuits, per poder resoldre els problemes específics que poguem tenir.

L'**anàlisi** d'un circuit combinacional es fa de la següent manera:
### Anàlisi
Una manera senzilla de saber quina funció desenvolupa un circuit és fent la taula de veritat del mateix, per això s'ha de:
-  Trobar les entrades i sortides
- Definir les sortides com a funcions
- Definir les entrades com a variables
- Construïr la taula de veritat
- Obtenir la funció
	- Simplificació gràfica per Karnaugh
	- [[Estructura i algebra de boole#Mínterms i Màxterms|Simplificació per mínterms o màxterms]]
- Esbrinar la funció real del circuit.

### Disseny
Per altra banda, si es vol fer el disseny, s'ha de fer el procés invers que en l'anàlisi, per tant, seria:
- Determinar la funció del circuit, amb entrades i sortides
- Construir la taula de veritat
- Obtenir la funció
	- Simplificació gràfica per Karnaugh
	- [[Estructura i algebra de boole#Mínterms i Màxterms|Simplificació per mínterms o màxterms]]
- Construir el circuit
## Circuits aritmètics
Els diferents circuits aritmètics són els blocs fundacionals de les diferentes operacions aritmètiques que fan els ordinadors, aquests són els següents: [[Fulla de referències#Circuits aritmètics|1]]
### Half adder
El Half adder és el circuit més bàsic que hi ha per afegir números binaris. Concretament, suma dos números de 1 bit cadascú. [[Fulla de referències#Circuits aritmètics|1]], [[Fulla de referències#Half adder|2]]
D'aquesta manera té dues entrades, una per a cada número, i té dues sortides, la suma o $S$ i el *Carry out* o $C_{o}$  tot i que en els half adders es pot dir senzillament *Carry*.

La suma i el $C_{o}$ són sortides de 1 bit cadascuna, siguent el $C_{o}$ la sortida de més pes.

La taula de veritat del half adder queda de la següent manera:

| **A** | **B** | **S** | **$C_{o}$** |
| ----- | ----- | ----- | ----------- |
| 0     | 0     | 0     | 0           |
| 0     | 1     | 1     | 0           |
| 1     | 0     | 1     | 0           |
| 1     | 1     | 0     | 1           |
### Full adder
El Full adder té el mateix concepte que el half adder