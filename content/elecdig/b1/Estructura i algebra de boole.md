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
És un tipus de senyal que alterna entre entre HIGH i LOW de forma homogènia. Ho fa amb un **període** (T), que es defineix com el temps que es tarda entre dues repeticions d'aquest interval. La **freqüència**, mesura el nombre de repeticions per segon, i uitilitza el *Hertz*.
$$ f = \frac{1}{T} = T^{-1} \hspace{2cm} T = \frac{1}{f} = f^{-1} $$
## Arquitectura bàsica d'un computador
L'arquitectura bàsica d'un computador és l'arquitectura de Von Neumann, que defineix que un computador ha de tenir un **processador**, **memòria** i una unitat dedicada a **l'entrada i sortida**. A més, aquestes unitats han d'estar connectades entre sí a través d'un **sistema de busos**.

Dins del processador, s'ha de trobar una **unitat de control** i una **unitat aritmètico-lògica** (ALU).