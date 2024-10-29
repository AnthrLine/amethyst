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

Els **Mínterms** són els productes que fan que la funció sigui verdadera, 