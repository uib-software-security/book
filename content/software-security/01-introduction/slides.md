# Introducció a la seguretat del software

---

## Seguretat informàtica o ciberseguretat

- **Definició**: Branca de la informàtica que estudia com assegurar que els recursos dels sistemes informàtics siguin utilitzats de la forma en què es van definir.
- **Objectiu**: Creació de plataformes segures on els agents que hi interaccionen (programes i usuaris) només puguin realitzar accions autoritzades.

---

## Correcció vs. Seguretat

- **Correcció**: Assegura que els sistemes es comportin com s'espera en circumstàncies normals.
  - Exemple: Un sistema de pagament que processa correctament les transaccions.
- **Seguretat**: Es preocupa de prevenir **comportaments no desitjats**.
  - Considera un enemic/oponent/hacker/adversari que intenta de forma **activa** i **maliciosa** eludir qualsevol mesura de protecció

---

## Diferència clau

- **Correcció** -> Què _ha de fer_ un sistema.
- **Seguretat** -> Què _no ha de fer_ un sistema.

---

## Tipus de comportament no desitjat

1. **Confidencialitat**:
   - Assegura que només els usuaris amb drets, privilegis i necessitat d'accedir a la informació poden fer-ho
   - Exemple: Robatori d'informació com secrets corporatius, dades personals,...
2. **Integritat**:
   - Fa que les dades estiguin emmagatzemades com espera l'usuari: que no siguin alterades sense el seu consentiment
   - Exemple: instal·lar software no desitjat (spyware,...), destrucció o modificació de dades (logs, registres de bases de dades...)
3. **Disponibilitat _(Availability)_**:
   - Intenta que els usuaris puguin accedir als serveis amb normalitat en el moment desitjat.
   - Exemple: atac de denegació d'accés (DoS)

---

## Triada CIA

![Triada CIA](./img/cia_triad.png)

---

## Exemples de violacions de seguretat

- **RSA (març 2011)**
  - Es varen robar fitxes que van permetre el compromís posterior dels clients amb dispositius RSA SecureID
  - [Més informació](https://www.bankvault.com/classics-the-2011-rsa-hack/)
- **Adobe (octubre 2013)**: Codi font i registres de clients robats.
  - Es va robar el codi font, i 130 milions de registres de clients (incloses les contrasenyes)
  - [Més informació](https://www.bbc.com/news/technology-24740873)
- **Target (novembre 2013)**: 40 milions de dades de targetes de crèdit i dèbit robades.
  - Es varen robar uns 40 milions de dades de targetes de crèdit i dèbit
  - [Més informació](https://www.nbcnews.com/business/business-news/target-settles-2013-hacked-customer-data-breach-18-5-million-n764031)

---

## Tipus d'atacs informàtics

1. **Interrupció**: Atempta contra la **disponibilitat** d'un recurs informàtic, ja sigui hardware, un servei o informació.
2. **Intercepció**: Vulnera la **confidencialitat** de les comunicacions de dades, ja s'està accedint a informació per a la qual no es té permís.
3. **Fabricació**: Vulnera la característica d'**integritat**, creant recursos nous per a suplantar els autèntics.
4. **Modificació**: Vulnera la **integritat** de les dades, alterant-les d'alguna manera des de la seva font original fins al receptor d'aquestes.

---

## Defectes i vulnerabilitats

- Moltes infraccions comencen explotant una **vulnerabilitat**
- **Vulnerabilitat**: **Defecte del programari** rellevant per a la seguretat que pot ser **explotat** (_exploit_) per produir un comportament no desitjat
- Hi ha un **defecte** del programari quan el programari es comporta incorrectament, és a dir, no compleix el seu requisits
- **Defectes**:
  - **Flaw** (defecte): Defecte en el **disseny**
  - **Bug** (error): Defecte en la **implementació**

---

## Correcció i seguretat

- És massa car corregir tots els _bugs_ abans de desplegar els programes
  - Per tant, les empreses només arreglen els que tenen més probabilitats d'afectar als usuaris normals
- A tenir en compte: els **adversaris/hackers** no són usuaris normals
- L'adversari intentarà activament trobar defectes en interaccions de característiques i casos extrems
  - Per a un usuari típic, trobar un _bugs_ (accidentalment) provocarà un error, que després intentarà evitar.
  - Un adversari treballarà per trobar un _bugs_ i explotar-lo per assolir els seus objectius

---

## Solució

> Per garantir la seguretat, hem d'**eliminar els bugs i defectes de disseny** i/o fer-los més **difícils d'explotar**

---

## Seguretat del software

- La seguretat del software és un tipus de seguretat informàtica que es centra en el **disseny i la implementació segura del software**
  - Evitar vulnerabilitats del codi, flaws i bugs
  - Utilitzant els millors llenguatges, eines i mètodes
- Focus d'estudi: **EL CODI**
- Per contra: molts enfocaments populars de seguretat tracten el programari com una **caixa negra** (ignorant el codi)
  - Seguretat del sistema operatiu, antivirus, tallafocs, etc.

---

## Per què és important la seguretat del software?

- Els **defectes del software** solen ser la causa principal dels problemes de seguretat
  - **La seguretat del software té com a objectiu abordar aquests defectes directament**
- Altres formes de seguretat solen ignorar el programari i construir defenses al seu voltant
  - Però si es mantenen els defectes del programari, els atacants poden trobar una manera de saltar-se aquestes defenses

---

![Seguretat del software](./img/security.png)

---

## Altres formes de seguretat

- Seguretat del **sistema operatiu**
  - Gestionen les accions dels programes (_system calls_)
  - Per exemple, polítiques de lectura i escriptura de fitxers, enviament i recepció de paquets de xarxa, engegar nous programes...
- **Firewalls i IDSs** (_Intrusion Detection System_)
  - Observen, bloquegen i filtren els missatges intercanviats per programes
- **Antivirus**
  - Cerquen signes de comportament maliciós als fitxers locals

---

## Punts de vista sobre seguretat del software

![Punts de vista](./img/blackhat_whitehat.png)

---

## Black Hat vs. White Hat

- **Black Hat**: Perspectiva de l'atacant.
  - Quins defectes constitueixen vulnerabilitats?
  - Com s'exploten?
- **White Hat**: Perspectiva del defensor.
  - Com evitar defectes abans de desplegar-los?
  - Com dificultar l'explotació de vulnerabilitats?
