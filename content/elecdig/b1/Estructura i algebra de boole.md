---
title: T.1 - Estructura i àlgebra de boole
---
# Introducció
## Definicions
### Dades analògiques
Les **dades analògiques** són el tipus de dades que varien de forma contínua en el temps, com qualsevol dels senyals de la naturalesa. [[Fulla de referències#Senyal analògic|1]]
Quan es mesuren (mostregen) les dades analògiques, s'ha de tenir en compte la freqüència en la que es mesuren (freqüència de mostreig), ja que aquesta pot determinar la precisió de les dades, inclús falsejar-les completament, com es veu en aquest exemple:

![Untitled](/elecdig/b1/t1/freq_mostreig.png)

Es pot veure clarament que el segon mostreig, serà molt proper a la funció, mentre el primer, ens donarà unes dades completament incorrectes sobre el que s'intenta analitzar.
### Sistemes digitals
Els sistemes digitals són dispositius creats per a:
- generar
- transmetre
- processar
- emmagatzemar

senyals digitals. Per tant, les dades analògiques que es volen tractar s'han hagut de digitalitzar prèviament. [[Fulla de referències#Sistema digital|2]]

### Senyal de rellotge
És un tipus de senyal que alterna entre entre HIGH i LOW de forma homogènia. Ho fa amb un **període** (T), que es defineix com el temps que es tarda entre dues repeticions d'aquest interval. La **freqüència**, mesura el nombre de repeticions per segon, i utilitza el *Hertz*.
$$ f = \frac{1}{T} = T^{-1} \hspace{2cm} T = \frac{1}{f} = f^{-1} $$
## Arquitectura bàsica d'un computador
L'arquitectura bàsica d'un computador és l'arquitectura de Von Neumann, que defineix que un computador ha de tenir un **processador**, **memòria** i una unitat dedicada a **l'entrada i sortida**. A més, aquestes unitats han d'estar connectades entre sí a través d'un **sistema de busos**.

Dins del processador, s'ha de trobar una **unitat de control** i una **unitat aritmètico-lògica** (ALU).

# Àlgebra de Boole
L'àlgebra de Boole és una branca de l'àlgebra que es diferència de l'àlgebra tradicional a través de dos aspectes diferenciadors importants: [[Fulla de referències#Àlgebra de boole|3]]
- Els valors de les variables i funcions només es poden denotar amb *true* o *false*, 1 o 0, Vcc o GND (Són diferentes maneres d'indicar el mateix).
- L'àlgebra de Boole es basa en els seus dos operadors principals, el *or* i l'*and*


## Postulats
Dins de la definició de l'àlgebra de Boole s'inclouen diferents postulats:

| **Postulats**         | OR                   | AND                         |
| --------------------- | -------------------- | --------------------------- |
| Commutativitat        | $a+b = b+a$          | $a \cdot b = b \cdot a$     |
| Element neutre        | $a+0 = a$            | $a \cdot 1 = a$             |
| Distributiva          | $a(b+c) = ab + ac$   | $a+(b\cdot c) = (a+b)(a+c)$ |
| Element complementari | $a+\overline{a} = 1$ | $a\cdot\overline{a} = 0$    |
## Teoremes
Hi ha 13 teoremes a l'àlgebra de Boole, tot i que el més important és el **Teorema de De Morgan**: [[Fulla de referències#Teorema de De Morgan|4]] que especifica aquesta propietat en les funcions booleanes:

$$\overline{A \cdot B} \leftrightarrow \overline{A} + \overline{B}$$
$$\overline{A + B} \leftrightarrow \overline{A} \cdot \overline{B}$$
## Portes lògiques
Hi ha 7 portes lògiques diferents, les quals són:
- **NOT**: $f(x) = \overline{x}$
- **AND** $f(x, y) = x \cdot y$
- **OR** $f(x, y) = x + y$
- **XOR** $f(x, y) = x \oplus y$
- **NAND** $f(x, y) = \overline{x \cdot y}$
- **NOR** $f(x, y) = \overline{x + y}$
- **XNOR** $f(x, y) = \overline{x \oplus y}$
Els símbols de les portes són els següents:
![[elecdig/b1/t1/portes.png]]
## Mínterms i Màxterms
La **Forma canònica** és una manera de representar les funcions Booleanes de forma estandarditzada, que facilita veure els **mínterms** i els **màxterms** de forma senzilla.[[Fulla de referències#Forma canònica|5]]
La funcions es poden expressar en forma canònica a través de:
- **Suma de productes**, $f(a,b) = A  \overline{B} + \overline{A}  B$
- **Producte de sumes** $f(a,b) = (A + B) \cdot (\overline{A + B})$


### Mínterms
Els **Mínterms** són els productes que fan que la funció sigui verdadera on cada variable apareix un cop, aquests, s'expressen com a suma de productes. Si perquè la funció sigui verdadera una o més de les variables han de ser 0, aquestes s'escriuràn negades a la suma de productes.
Per a veure millor els mínterms, aquest és un exemple:

| $n$   | **A** | **B** | **C** | **$f$** | **Mínterm**          |
| ----- | ----- | ----- | ----- | ------: | -------------------- |
| 0     | 0     | 0     | 0     |       0 |                      |
| 1     | 0     | 0     | 1     |       0 |                      |
| 2     | 0     | 1     | 0     |       0 |                      |
| **3** | **0** | **1** | **1** |   **1** | **$\overline{A}BC$** |
| **4** | **1** | **0** | **0** |   **1** | **$A\overline{BC}$** |
| 5     | 1     | 0     | 1     |       0 |                      |
| **6** | **1** | **1** | **0** |   **1** | **$AB\overline{C}$** |
| 7     | 1     | 1     | 1     |       0 |                      |

En l'exemple, es veu com la funció només té mínterms quan dóna 1 i ens podem referir a ells depenent de l'ordre en el que apareixen a la taula, en aquest cas serien els mínterms 3, 4 i 6.

La funció es pot expressar com a la suma dels seus mínterms, per tant, $\overline{A}BC + A\overline{BC} + AB\overline{C}$. A més, si se sap la funció, els mínterms es poden expressar de la següent manera:
$$F(A, B, C) = \sum_{m}{(3, 4, 6)}$$
> [!important]
> Apunt important!
> 
> Recorda que al fer la **taula de veritat**, s'ha de fer de manera **ordenada**, ja que sinó, els nombres dels mínterms quedaràn mal ordenats.
> 
> També, al fer la suma de mínterms, s'ha d'**especificar el seu ordre**.

### Màxterms
També existeixen els màxterms, el concepte és el mateix que els dels mínterms, tot i que s'expressen com a producte de sumes i fan que la funció sigui falsa, amb el mateix exemple d'abans seria:

| $n$ | **A** | **B** | **C** | **$f$** | **Mínterm**      | **Màxterm**                   |
| --- | ----- | ----- | ----- | ------: | ---------------- | ----------------------------- |
| 0   | 0     | 0     | 0     |       0 |                  | $A+B+C$                       |
| 1   | 0     | 0     | 1     |       0 |                  | $A+B+\overline{C}$            |
| 2   | 0     | 1     | 0     |       0 |                  | $A+\overline{B}+C$            |
| 3   | 0     | 1     | 1     |       1 | $\overline{A}BC$ |                               |
| 4   | 1     | 0     | 0     |       1 | $A\overline{BC}$ |                               |
| 5   | 1     | 0     | 1     |       0 |                  | $\overline{A}+B+\overline{C}$ |
| 6   | 1     | 1     | 0     |       1 | $AB\overline{C}$ |                               |
| 7   | 1     | 1     | 1     |       0 |                  | $\overline{A+B+C}$            |

Per tant, els màxterms són 0, 1, 2, 5 i 7. La funció s'expressaria com a $(A+B+C)(A+B+\overline{C})(A+\overline{B}+C)(\overline{A}+B+\overline{C})(\overline{A+B+C})$ o com a :
	$$F(A,B,C) = \prod_{M}{(0, 1, 2, 5, 7)}$$
## Suficiència de la NAND i de la NOR
Tots els circuits es poden expressar com a portes NAND o com a portes NOR, implementar totes les portes amb el mateix tipus de porta ens permet fer servir només un tipus d'integrat, cosa que ens facilita abaratir costos, les equivalències són les següents:
![[elecdig/b1/t1/suficiencia.png]]
