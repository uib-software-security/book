# Desenvolupament segur de software

---

## Disseny i construcció de programari segur: Introducció

> Designing and Building Secure Software

---

## Elaboració de programari segur

- **Enfocament defectuós**: dissenyeu i creeu programari, i al principi ignoreu la seguretat
  - Afegiu seguretat un cop es compleixin els requisits funcionals
- **Millor enfocament**: **incorporar seguretat** des del principi
  - Incorporar un pensament de seguretat en totes les fases del procés de desenvolupament

---

## Procés de desenvolupament

- Molts processos de desenvolupament; **quatre fases comunes**:
  - **Requisits**
  - **Disseny**
  - **Implementació**
  - **Proves/assegurament**
  - Les fases de desenvolupament s'apliquen a tot el projecte, als seus components individuals i als seus perfeccionaments/iteracions
- On encaixa l'enginyeria de seguretat?
  - **Totes les fases!**

---

## Waterfall model

![Waterfall model](img/waterfall-model.png)

---

## SCRUM, an agile methodology

Phases, documents and roles of the Scrum methodology

![Metodologia SCRUM](./img/scrum-methodolody.png)

---

## Activitats sobre enginyeria de seguretat a cada fase del desenvolupament del software

![Activitats sobre enginyeria de seguretat](img/security-engineering-activities.png)

---

## Exemple de funcionament: banca en línia

- Volem escriure un programari que permeti als titulars de comptes d'un banc tenir accés en línia als seus comptes
- Requisits:
  - Permetre dipòsits als comptes
  - Garantir que només els titulars autoritzats gestionin els fons
  - Assegurar l'accés del titular per retirar o transferir fons
  - Evitar interferències de tercers
  - Altres requisits de seguretat a determinar

![Banca en línia](img/online-banking.png)

---

## Modelització d'amenaces o anàlisi de riscos arquitectònics

> Threat Modeling, or Architectural Risk Analysis

---

## Modelització d'amenaces

- La **modelització d'amenaces** consisteix a identificar i fer **explícites les capacitats i objectius potencials d'un adversari**.
  - Si aquestes suposicions no reflecteixen la realitat, l'anàlisi de riscos serà **enganyosa** i el sistema pot quedar exposat.
- Aquesta activitat és **fonamental per a la seguretat del software**, ja que permet avaluar si les mesures de protecció seran efectives contra els escenaris d'atac possibles.
- Forma part de l'**anàlisi del risc arquitectònic**, que avalua:
  - La **probabilitat** que es produeixin determinades amenaces,
  - L'**impacte** que tindrien en el sistema,
  - I les **mesures** per minimitzar aquest risc.

> 🔎 Sense una modelització clara de l'adversari, no podem saber si el nostre disseny el podrà resistir.

---

## Exemple: Usuari de xarxa

- Un usuari (anònim) que es pot connectar a un servei a través de la xarxa
- Podrà:
  - **mesurar** la mida i el moment de les peticions i respostes cap al servei i del servei
  - realitzar **sessions paral·leles**
  - proporcionar **entrades amb format incorrecte, missatges amb format incorrecte**
  - **deixar anar o enviar missatges addicionals**

---v

- **Exemples d'atacs**: injecció SQL, cross site-scripting (XSS), cross site request fogerty (CSRF), buffer overrun/ROP payloads,...

![Usuari de xarxa](img/network-user.png)

---

## Exemple: Usuari espia (_snooping user_)

- Usuari d'Internet **a la mateixa xarxa** que altres usuaris d'algun servei
  - Per exemple, algú connectat a una xarxa Wi-Fi no xifrada en una cafeteria
- Per tant, pot:
  - **Llegir/mesurar** els **missatges** dels altres
  - **Interceptar**, **duplicar** i **modificar missatges**

---v

- **Exemples d'atacs**: **segrest de sessions** (i altres robatoris de dades), llegir comunicació no encriptada, aprendre coses de les comunicacions xifrades inferint propietats en funció de la mida o la freqüència dels missatges, **denegació de servei**

![Usuari espia](img/snooping-user.png)

---

## Exemple: Usuari co-ubicat (_co-located user_)

- Usuari d'Internet **a la mateixa màquina** que altres usuaris d'algun servei
  - Per exemple, **programari maliciós** (_**malware**_) instal·lat a l'ordinador portàtil d'un usuari
- Per tant, pot:
  - **Llegir/escriure** fitxers de l'usuari (p. ex., _cookies_) i memòria
  - **Llegir pressions de tecles** i altres esdeveniments
  - Llegir/escriure la **pantalla** de l'usuari (p. ex., per **falsificar**)

---v

- **Exemples d'atacs**: **robatori de contrasenya** (i altres credencials/secrets)

![Usuari co-ubicat](img/co-located-user.png)

---

## Disseny orientat a amenaces

- Cada **model d'amenaça** defineix un perfil diferent d'adversari, i això condiciona directament les decisions de disseny.
- Exemple de casos típics:

---v

### 1. Atacants només de xarxa

- Es pressuposa que l'atacant només pot **interactuar amb el sistema a través de la xarxa**, però **no pot llegir el trànsit**.
- En aquest escenari, **no és necessari xifrar les comunicacions**.
  - Aquesta era la suposició en sistemes antics com **telnet**.

---v

### 2. Atacants espies (_snooping attackers_)

- Es pressuposa que l'atacant pot **escoltar el trànsit de xarxa** (ex: en una Wi-Fi oberta).
- Cal **xifrar les comunicacions** per garantir la confidencialitat:
  - A nivell de **capa d'enllaç** (ex: WPA2),
  - A nivell de **capa de xarxa** (ex: IPsec),
  - O a nivell de **capa d'aplicació** (ex: TLS/SSL).
- El dissenyador ha de decidir **quina capa és la més adequada** segons els requisits del sistema.

---v

### 3. Atacants co-ubicats (_co-located attackers_)

- L'adversari té **accés al mateix dispositiu físic** que l'usuari (ex: malware instal·lat).
- Pot accedir a:
  - **Fitxers locals** (ex: cookies),
  - **Memòria compartida**,
  - O fins i tot capturar **pantalles i pulsacions de teclat**.
- En aquest cas, **no s'han d'emmagatzemar secrets en text pla**.
  - És recomanable l'ús de **dispositius externs i independents** per l'autenticació (ex: 2FA amb hardware token o SMS).

---

## Mal model = Mala seguretat

- Qualsevol **suposició** que feu al vostre model són **forats potencials que l'adversari pot explotar**
- P. ex.: Suposar que no hi ha usuaris espies (_snooping users_) ja no és vàlid
  - Prevalència de xarxes wi-fi en la majoria de desplegaments
- Altres suposicions errònies
  - **Suposició**: el trànsit xifrat no porta informació
    - No és cert! Mitjançant l'anàlisi de la mida i la distribució dels missatges, podeu inferir l'estat de l'aplicació
  - **Suposició**: el temps (_timing_) i característiques d'una comunicació porten poca informació
    - No és cert! Les mesures de temps de les implementacions prèvies de RSA (criptografia asimètrica) es podrien utilitzar eventualment per revelar una clau secreta SSL remota

---

## Trobar un bon model

- **Comparar amb sistemes similars**
  - A quins atacs s'enfronta el vostre disseny?
- **Comprendre atacs passats (estat de l'art) i patrons d'atac**
  - Com s'apliquen al vostre sistema?
- **Desafia els supòsits del teu disseny**
  - Quines capacitats ha de tenir un atacant per derrotar els mecanismes de defensa que esteu pensant utilitzar?
  - Quina és la probabilitat que un atacant tingui aquestes capacitats? Com ho sabràs? I quin seria el cost d'un fracàs?
  - Què et costaria potencialment un incompliment?
  - Què costaria un desenvolupament més segur?

---

## Requisits de seguretat

> Security Requirements

---

## Requisits de seguretat del software

- Els **requisits de software** generalment són sobre **què hauria de fer el software**
- També volem tenir **requisits de seguretat**
  - **Objectius** (o **polítiques**) **relacionats amb la seguretat**
    - Exemple: el saldo del compte bancari d'un usuari no hauria de ser conegut ni modificat per un altre usuari, tret que estigui autoritzat
  - **Mecanismes** necessaris **per fer-los complir**
    - Exemple:
    - Els usuaris s'identifiquen mitjançant contrasenyes,
    - Les contrasenyes han de ser "fortes" i
    - La base de dades de contrasenyes només és accessible al programa d'inici de sessió

---

## Tipus típics de requisits

- Polítiques
  - Confidencialitat (i privadesa i anonimat)
  - Integritat
  - Disponibilitat
- Mecanismes de suport a les polítiques
  - Autenticació
  - Autorització
  - Auditabilitat

---

## Privadesa i confidencialitat

- Definició: **informació sensible no filtrada** a persones no autoritzades
  - Es diu **privadesa** per a les persones, **confidencialitat** per a les dades
- Exemple de política: l'estat del compte bancari (inclòs el saldo) només pot ser conegut pel propietari del compte
- Filtració directes o per canals laterals
  - Exemple: manipular el sistema per mostrar directament el saldo bancari d'en Bob a l'Alice
  - Exemple: determinar que Bob té un compte al Banc A perquè hi ha un temps de retard més curt quan hi ha una fallada d'inici de sessió
- Una **filtració directa** es produeix mitjançant el mecanisme d'interacció previst del sistema de programari, mentre que una **filtració de canal lateral** prové de mesuraments d'altres funcions del sistema, com ara el temps, l'ús d'energia o l'ús de l'espai

---

## Anonimat

- Un **tipus específic de privadesa**
- Exemple: els no titulars de comptes bancaris haurien de poder navegar pel lloc d'informació bancària sense ser rastrejats
  - Aquí l'adversari és el propi banc
  - També ho podrien ser altres anunciants (_third party advertisers_)
  - Els exemples anteriors consideraven com a possibles adversaris altres titulars de comptes

---

## Integritat

- La **integritat** vol dir que la **informació no es pot modificar** sense autorització.
- Exemple: **només el propietari d'un compte** pot fer retirades.
- Tipus de violacions:
  - **Directa**: l'atacant modifica les dades ell mateix.
  - **Indirecta**: l'atacant **enganya el sistema** perquè ho faci per ell (ex: _Cross-Site Request Forgery_)
  - El **Cross-Site Request Forgery (CSRF)** és un atac en què un usuari autenticat és enganyat per enviar una petició no desitjada a una aplicació web en què està connectat, sense adonar-se'n

---

## Disponibilitat

- La **disponibilitat** vol dir que el sistema està **actiu i accessible quan es necessita**.
- Exemple: poder entrar al banc online i consultar el saldo en qualsevol moment.
- Els **atacs de denegació de servei (DoS)** busquen **fer caure el sistema**:
  - Saturant-lo amb peticions falses
  - Tallant l'accés a la xarxa

---

## Mecanismes de suport

- Són eines que ajuden a **fer complir els requisits de seguretat** d'un sistema:
  - **Autenticació**: saber qui ets
  - **Autorització**: saber què pots fer
  - **Auditoria**: deixar constància del que ha passat
- Aquests mecanismes depenen del **tipus d'usuaris** i de les **normes de seguretat** que es volen aplicar.

> 🔐 Sense aquests mecanismes, les polítiques de seguretat no es poden fer efectives.

---

## Autenticació

- L'**autenticació** serveix per saber **qui és realment un usuari** abans de deixar-lo fer res.
- Es pot basar en:
  - **Què sap** (ex: contrasenya)
  - **Què és** (ex: empremta digital)
  - **Què té** (ex: mòbil o targeta)
- Si es combinen diversos d'aquests mètodes, en diem **autenticació multifactor**.
  - Exemple: entrar al banc amb contrasenya i codi SMS.

> 🧾 Sense autenticació, no es pot aplicar cap política de seguretat.

---

## Autorització

- L'**autorització** decideix **què pot fer cada usuari** dins del sistema.
- Exemple: Bob pot accedir al seu compte, però **no al de l'Alice**.
- Les regles d'autorització es poden basar en:
  - **Usuaris concrets**
  - **Rols** (ex: administrador, usuari, convidat)

> ✅ Un cop sabem qui ets (autenticació), cal decidir **què tens permís per fer**.

---

## Auditoria

- L'**auditoria** serveix per **registrar què passa dins del sistema**, per saber si hi ha hagut errors o accions malicioses.
- Aquesta informació s'emmagatzema en **fitxers de registre (logs)** que han d'estar ben protegits.
- Exemple: totes les accions d'un compte bancari es registren i es poden revisar si cal.

> 📋 Sense auditoria, no podem saber **què ha passat** ni demostrar-ho.

---

## Definició dels requisits de seguretat

- Els **requisits de seguretat** indiquen **què cal protegir** i **contra què**.
- Es poden definir a partir de:

### ✅ Normes o polítiques generals

- Lleis o estàndards (ex: **LOPD** de protecció de dades, **HIPAA** per dades mèdiques a USA, **SOX** per dades financeres a USA)
- Valors de l'organització (ex: protegir la privadesa)

### 🔍 Modelització d'amenaces

- Quins **atacs** ens preocupen més?
- Quins **atacs ja han passat**, aquí o en sistemes similars?

> 🎯 Un bon sistema comença per saber **quines amenaces vol evitar**.

---

## Casos d'abús

- Els **casos d'abús** mostren **què no hauria de poder passar** en un sistema.
- Complementen els **casos d'ús**, que descriuen el comportament correcte.
- Exemple
  - ✅ **Cas d'ús**: un gestor pot canviar el tipus d'interès d'un compte.
  - ❌ **Cas d'abús**: un usuari falsifica la identitat d'un gestor i fa el mateix canvi.

> ⚠️ Pensar en casos d'abús ajuda a descobrir vulnerabilitats abans que ho faci un atacant.

---

## Definició de casos d'abús

- Un **cas d'abús** descriu com un **atacant pot aprofitar una debilitat** per trencar la seguretat del sistema.
- Es basa en el **model d'amenaça** i ajuda a identificar què pot passar si una protecció falla o no existeix.
- Exemples
  - 🔓 Un atacant co-ubicat roba el fitxer de contrasenyes si **no està xifrat**.
  - 🔁 Un espia de xarxa fa un **replay attack** si els missatges **no tenen identificador únic (_nonce_)**.

> 🧠 Pensar en casos d'abús t'obliga a imaginar **com es podria atacar el teu sistema** i avançar-te als riscos.

---

## Casos d'ús vs. casos d'abús

![Casos d'ús vs. casos d'abús](img/use-vs-abuse-cases.png)

---

## Evitar defectes de disseny amb principis

> Avoiding Flaws with Principles

---

## Defecte de disseny = _Flaw_

- Els errors de seguretat poden ser:
  - **_Flaws_**: errors en el **disseny** del sistema
  - **_Bugs_**: errors en la **implementació** del codi
- Els **flaws** són especialment perillosos perquè poden afectar tot el sistema des de l'origen.
- Segons Gary McGraw, el **50% dels problemes de seguretat venen del disseny**.

> 🛠️ Millor prevenir els errors durant el **disseny**, abans d'escriure cap línia de codi.

![Software security](img/software-security.png)

---

## Disseny vs. Implementació?

- Hi ha molts **nivells diferents de decisions de disseny de sistemes**
  1. **Alt nivell**: actors principals (**processos**, com servidor web i servidor de bases de dades), **interaccions** i llenguatge(s) de programació a utilitzar
  2. **Mitjà nivell**: **descomposició** d'un actor en **mòduls/components**, identificar les funcionalitats bàsiques i com funcionen juntes.
  3. **Baix nivell**: com **implementar tipus de dades** i funcions, etc.

- Els nivells 2 i 3 poden ser **disseny o implementació**, segons com es plantegin.

> 🧩 El límit entre dissenyar i programar sovint no és clar, però **els dos afecten la seguretat**.

---

## Disseny de programari segur

- El procés de disseny de programari té com a objectiu produir una arquitectura de programari segons **bons principis i regles**
- Aquest és un **procés iteratiu**.
  - Primer feim el nostre **disseny inicial**.
  - I després realitzem una **anàlisi basada en el risc** d'aquest disseny.
  - Com a resultat, podem determinar que cal **millorar el disseny**
  - Per tant, apliquem els nostres **principis i regles** i després millorem fins que estem satisfets.

![Software design](img/software-design.png)

---

## Principis i normes

- Un **principi** és una idea general que ajuda a fer **bons dissenys** (ex: "mantenir-ho simple").
- Una **norma** és una **regla concreta** que posa aquest principi en pràctica (ex: "no utilitzar valors per defecte insegurs").
- La diferència entre principi i norma **pot ser difusa**, i sovint **van de la mà**.
- Durant el disseny del programari ens centrem en **principis**, perquè ajuden a **evitar errors de base (_flaws_)**.

> 📐 Els principis guien el disseny; les normes guien l'aplicació pràctica.

---

## Categories de principis

- **Prevenció**
  - Objectiu: Eliminar completament els defectes del programari
  - Exemple: errors de _buffer overflow_ es poden evitar utilitzant un llenguatge segur de memòria (_memory-safe_), com Java o Rust
- **Mitigació**
  - Objectiu: Reduir el dany de l'explotació de defectes desconeguts
  - Dissenyar el nostre programari de manera sigui més difícil que un adversari exploti aquests defectes d'una manera que li sigui rendible
  - Exemple: executar cada pestanya del navegador en un procés independent, de manera que l'explotació d'una pestanya no permet accedir a les dades en una altre
- **Detecció** (i **recuperació**)
  - Objectiu: identificar i comprendre un atac (i desfer el dany)
  - Exemple: monitorització i _snapshots_ per revertir a un estat anterior

---

## Els Principis

- Afavoreix la simplicitat
  - Utilitzeu valors predeterminats segurs (_fail-safe defaults_)
  - No espereu usuaris experts
- Confiar amb reticències
  - Utilitzar una petita base informàtica de confiança
  - Concedir el mínim privilegi possible
    - Fomentar la privadesa
    - Compartimentar
- Defensar en profunditat
  - No dependre d'un sol tipus de defensa
  - Utilitzeu els recursos de la comunitat (codi endurit i dissenys verificats): no hi ha seguretat per l'obscuritat
- Monitoritzar i rastrejar

---

## Categoria de disseny: afavoreix la simplicitat

> Design Category: Favor Simplicity

---

## Afavorir la simplicitat

- Feu-ho tan senzill que és evident que és correcte
  - S'aplica a la interfície externa, el disseny intern i la implementació
    - Es coneix clàssicament com a **economia de mecanisme**
  - **Categoria: Prevenció**

---v

- _"Hem vist errors de seguretat en gairebé tot: sistemes operatius, programes d'aplicacions, maquinari i programari de xarxa i els mateixos productes de seguretat. Aquest és un resultat directe de la complexitat d'aquests sistemes. Com més complex és un sistema, com més opcions té, més funcionalitat té, més interfícies té, més interaccions té, més difícil és analitzar [la seva seguretat]"_. —Bruce Schneier

[https://www.schneier.com/essays/archives/1999/11/a_plea_for_simplicit.html](https://www.schneier.com/essays/archives/1999/11/a_plea_for_simplicit.html)

---

![Keep it simple](img/keep-it-simple.png)

---

## Utilitzeu valors predeterminats a prova d'errors (_fail-safe_)

- Algunes **opcions de configuració o ús afecten** la **seguretat** d'un sistema
  - La longitud de les claus criptogràfiques
  - L'elecció d'una contrasenya
  - Quines entrades es consideren vàlides
- **L'opció predeterminada hauria de ser segura (_fail-safe_)**
  - **La longitud de la clau predeterminada és segura** (p. ex., claus RSA de 2048 bits)
  - **Sense contrasenya predeterminada**: no es pot executar el sistema sense escollir-ne una
  - **Llista blanca** d'objectes vàlids, en lloc de llista negra d'objectes no vàlids

---

## No espereu usuaris experts

- Els dissenyadors de programari haurien de considerar com la **mentalitat i les habilitats** dels **usuaris** (dels menys sofisticats) d'un sistema **afectaran la seguretat**
- Afavorir les **interfícies d'usuari senzilles**
  - **L'elecció natural o òbvia és l'opció segura**
    - O eviteu les opcions, si és possible, pel que fa a la seguretat
  - **No feu que els usuaris prenguin decisions de seguretat freqüents**
    - Evitar la fatiga de l'usuari

---

## Contrasenyes

- Objectiu: **fàcil de recordar** però **difícil d'endevinar**
  - Resulta **equivocat** en molts casos!
    - Difícil d'endevinar = Difícil de recordar!
  - **Problema agravant**: **ús repetit** de contrasenyes
- Les **eines de trencament de contrasenyes** entrenen les dades publicades per endevinar ràpidament les contrasenyes habituals
  - John the Ripper, [http://www.openwall.com/john/](http://www.openwall.com/john/)
  - Project Rainbow, [http://project-rainbowcrack.com/](http://project-rainbowcrack.com/)
  - molts més ...
  - Les **10 pitjors contrasenyes** de 2022: 123456, 123456789, qwerty, password, 1234567, 12345678, 12345, iloveyou, 111111, 123123 (de [SplashData](https://www.emcrc.co.uk/post/most-common-passwords-of-the-year-revealed-is-yours-on-the-list))

---

## Mesurador de força de contrasenya

- **Ofereix _feedback_ als usuaris** sobre la **força** de la **contrasenya**
  - Destinat a mesurar la **capacitat d'endevinar**
  - La investigació demostra que **poden funcionar**, però el disseny ha de ser **estricte** (per exemple, forçant caràcters inusuals)
- Per exemple: [https://www.passwordmonster.com/](https://www.passwordmonster.com/)

![Password strength meter](img/password-strength-meter.png)

---

## Categoria de disseny: confiança amb reticències

> Design Category: Trust With Reluctance

---

## Confia amb reticència, _Trust with Reluctance_ (TwR)

- La **seguretat de tot el sistema** depèn del **funcionament segur de les seves parts**
  - Aquestes parts són **de confiança**
- Així: **Millorar la seguretat reduint la necessitat de confiança**
  - Mitjançant un millor disseny
  - Mitjançant un millor procés d'implementació
  - En no fer suposicions innecessàries
    - Si utilitzeu codi de tercers, com sabeu què fa?
    - Si no ets un expert en criptografia, per què creus que pots dissenyar/implementar el teu propi algorisme?
- **Categories: Prevenció i mitigació**

---

## Petita base informàtica de confiança (_Trusted Computing Base, TCB_)

- Mantingueu el **TCB petit** (i senzill) per **reduir la susceptibilitat general al compromís**
  - La base informàtica de confiança (TCB) comprèn els components del sistema que han de funcionar correctament per garantir la seguretat
  - **Categoria: Prevenció**
- Exemple: nuclis de sistemes operatius
  - Els nuclis imposen polítiques de seguretat, però sovint són milions de línies de codi
    - El compromís en un controlador de dispositiu compromet la seguretat en general
  - Millor: minimitza la mida del nucli per reduir els components de confiança
    - Els controladors de dispositiu es van moure fora del nucli en dissenys de micro-nucli

---

## Privilegi mínim

- No doneu a una part del sistema més privilegis dels que necessita per fer la seva feina
  - **Categoria: Mitigació**
- Exemple: Atenuar les delegacions
  - El programa de correu delega a l'editor per crear correus
    - `vi`, `emacs`
  - Però molts editors permeten escapar a un intèrpret d'ordres per executar programes arbitraris: massa privilegis!
  - Millor disseny: utilitzeu un editor restringit (`pico`)

---

## Lliçó: La confiança és transitiva

- **Si confies en alguna cosa, confies en allò en què confia**
  - Aquesta confiança es pot equivocar
- Exemple de client de correu electrònic anterior
  - Programa de correu delega a un editor arbitrari
  - L'editor permet executar codi arbitrari
  - Per tant, el correu permet executar codi arbitrari

---

## Regla: validació d'entrada

- La validació d'entrada és **una mena de privilegis mínims**
  - Només **confieu en un subsistema** en **determinades circumstàncies**
  - Validar que aquestes circumstàncies es compleixen
- Diversos **exemples** fins ara:
  - Confiar en una funció determinada si el rang dels seus paràmetres és limitat (p. ex., dins de la longitud d'un buffer)
  - Confiar en un camp de formulari de client si no conté etiquetes `<script>` (i altres cadenes interpretables amb codi)
  - Confieu en una cadena codificada en YAML si no conté cap codi

---

![Humor amb SUDO](img/sudo-humor.png)

---

![Humor amb DROP DATABASE](img/drop-database-humor.png)

---

## Promoure la privadesa

- Un bon objectiu general del sistema és **restringir la circulació de dades sensibles** tant com sigui possible
  - En fer-ho, promou la privadesa **reduint la confiança/privilegi**
  - **Categoria: Mitigació**
- Exemple. Un sistema d'admissions rep **cartes de recomanació** (sensibles) en PDF.
  - ❌ Si es permet descarregar-les, es poden filtrar si l'ordinador es compromet.
  - ✅ Millor: veure els PDFs només al navegador, **sense descarregar-los**.

> 🔒 Com menys dades sensibles circulin, **menys oportunitats tindrà un atacant**.

---

## Compartimentació

- **Aïllar un component del sistema** en un compartiment, o _**sandbox**_, reduint-ne els privilegis fent impossibles determinades interaccions
  - **Categoria: Prevenció i Mitigació**
- Exemple: Una base de dades d'estudiants:
  - ❌ Si està connectada a Internet, és vulnerable.
  - ✅ Millor: només accessible des de terminals autoritzats dins del campus.

> 🧱 Separar components redueix l'impacte d'un atac si una part es veu compromesa.

![Sandboxes](img/sandboxes.png)

---

## Categoria de disseny: Defensa en profunditat, Seguiment/Traçabilitat

> Design Category: Defense in Depth, Monitoring/Traceability

---

## Defensa en profunditat

- **Seguretat per diversitat**
  - Si es trenca una capa, n'hi ha una altra de caràcter materialment diferent que cal evitar
  - **Categories: Prevenció/Mitigació**
- Exemple: Per protegir un sistema, pots fer **diverses coses a la vegada**:
- 🔥 Posar un **tallafoc** per bloquejar ports no desitjats.
- 🔒 **Xifrar les dades** que viatgen per la xarxa.
- 🧪 Usar un **llenguatge segur** (com Rust) per evitar vulnerabilitats com els _buffer overflows_.

> 🛡️ Com més barreres diferents poses, **més difícil serà atacar el sistema**.

---

## Utilitzeu els recursos de la comunitat

- Aprofita **codi segur ja existent** (com biblioteques criptogràfiques), però assegura't que **s'adapta al teu cas**.
- Mantén-te **informat sobre vulnerabilitats i bones pràctiques**.
- Fonts recomanades:
  - 🏛️ **NIST**: entitat oficial dels EUA que publica estàndards de seguretat.
  - 🌐 **OWASP**: comunitat oberta sobre seguretat web (famós pels rànquings de vulnerabilitats).
  - 🛡️ **CERT**: centre que investiga i publica vulnerabilitats i guies de resposta.
  - 🔎 **SANS**: portal de notícies i formació sobre seguretat.
  - 📚 **Conferències i revistes**: per seguir les tendències i tècniques més recents.

> 👥 La seguretat no es fa sol: **reutilitza i aprèn de la comunitat**.

---

## Seguiment i traçabilitat

- Si el sistema pateix un atac, cal saber-ho i **entendre què ha passat**.
- Per això, el programari ha d'**enregistrar informació rellevant** (_logs_).
- **Categoria: Detecció i Recuperació**
- **Què registrar?**
  - Peticions rebudes, errors, accions d'usuari, etc.
- **Per què serveix?**
  - Per **detectar atacs** i **analitzar l'origen dels problemes**.
  - Amb **agregadors de logs** (com _Splunk_) es poden combinar registres de diferents aplicacions per veure **l'impacte global** d'un incident.

> 📊 Sense registres, és com si el sistema fos **una caixa negra** quan falla.

---

## Principals defectes de disseny

> Top Design Flaws

---

## Principals defectes de disseny?

- El nostre enfocament en **principis** i **regles** pretén **evitar defectes de seguretat**
  - Hem vist diversos exemples de defectes fins ara
- Llançament recent: **IEEE Center for Secure Design**
  - Comprèn els millors professionals de la seguretat de la indústria, la investigació i el govern
- Enfoc inicial del centre: **quins són els principals defectes de disseny de seguretat del programari?**

[https://ieeecybersec.wpengine.com/center-for-secure-design/](https://ieeecybersec.wpengine.com/center-for-secure-design/)

![Center for Secure Design](img/center-for-secure-design.png)

---

## Els 10 defectes principals (1)

1. Assumeixen la confiança, en lloc de donar-la o concedir-la explícitament
2. Utilitzen un mecanisme d'autenticació que es pugui evitar o manipular
3. Autoritzen sense tenir en compte el context suficient
4. Confonen les dades i les instruccions de control, i processen les instruccions de control de fonts no fiables
5. No validen les dades de manera explícita i exhaustiva
6. No utilitzen correctament la criptografia
7. No s'han pogut identificar les dades sensibles i com gestionar-les
8. Ignoren els usuaris
9. Integren components externs sense tenir en compte la seva superfície d'atac
10. Limiten de manera rígida els canvis futurs als objectes i als actors

---

## Els 10 defectes principals (i 2)

> Ja n'hem tractat diversos. Anem a veurer-ne d'altres

1. Assumeixen la confiança, en lloc de donar-la o concedir-la explícitament
2. **Utilitzen un mecanisme d'autenticació que es pugui evitar o manipular**
3. Autoritzen sense tenir en compte el context suficient
4. Confonen les dades i les instruccions de control, i processen les instruccions de control de fonts no fiables
5. No validen les dades de manera explícita i exhaustiva
6. **No utilitzen correctament la criptografia**
7. **No s'han pogut identificar les dades sensibles i com gestionar-les**
8. Ignoren els usuaris
9. **Integren components externs sense tenir en compte la seva superfície d'atac**
10. Limiten de manera rígida els canvis futurs als objectes i als actors

---

## Error: Bypass d'autenticació (1)

- Clients obligats a acceptar certificats SSL no vàlids
  - Omet l'autenticació del client del servidor:
    - Realment estic parlant amb el meu banc o amb un lloc que pretén ser el meu banc?
- El navegador web presenta un avís
  - Però quants usuaris faran clic?

![Bypass d'autenticació](img/bypass-authentication.png)

---

## Error: Bypass d'autenticació (2)

- Les aplicacions mòbils utilitzen SSL entre bastidors; què passa quan una aplicació rep un certificat no vàlid?
  - "Tot i que és comprensible que els desenvolupadors desactivin la validació del certificat SSL en la fase de desenvolupament, aquests desenvolupadors bàsicament es van oblidar d'eliminar el codi d'acceptació de tot quan van llançar les seves aplicacions".
    - Fahl et al, "Rethinking SSL Development in an Appified World", CCS'13 (Competició NSA 2014 Best Cybersecurity Paper)
- Recordeu: **la seguretat no és una característica**
  - Necessitat de provar què no hauria de passar

---

## Error: Bypass d'autenticació (i 3)

- **Tokens d'autenticació amb timeouts llargs**
  - Motiva els intents de força bruta de robar _cookies_ de sessió
    - Recordeu l'error d'auth_token de Twitter de la unitat de seguretat web
  - Però no es pot fer massa curt o irritarà els usuaris
- En general: eviteu la derivació de l'autenticació desenvolupant bons casos d'abús, violant la suposició de coneixement o possessió únics.
  - Com podria un adversari aprendre una contrasenya? Falsar una biomètrica? Voleu robar un identificador de sessió?

---

## Error: criptografia dolenta (o incorrecta)

- **(Recordau) No utilitzeu la vostra pròpia criptografia**
  - Exemples d'ús-recursos comunitaris: tant el disseny com la implementació són difícils d'encertar
- No assumir que et dóna una cosa que no:
  - L'algorisme de xifratge pot protegir la **confidencialitat** però no la **integritat**.
  - El hashing protegeix la **integritat** però no la **confidencialitat**.
- **Saber utilitzar-lo correctament**
  - Utilitzeu claus de mida suficient generades correctament
  - Protegiu les claus del compromís
    - No els codifiqueu ni els incrusteu en binaris desplegats

---

## Error: ignorar quines dades són sensibles

- **Penseu bé en les fonts de dades**: quines requereixen protecció?
  - Informació d'identificació personal, lectures de sensors, claus criptogràfiques, fitxes de sessió, dades de geolocalització, ...
    - Falla: dades privades exposades a l'accés general
- Com canvien les dades i la seva exposició a mesura que l'**aplicació evoluciona al llarg del temps**?

---v

![Dades sensibles](img/sensitive-data.png)

---

## Falla: ignora la superfície d'atac dels components externs

- **Superfície d'atac**: Elements d'un sistema que un adversari pot atacar o utilitzar en un atac
- **Els components de tercers només fan el que jo vull?**
- Falla de _**shellshock**_: "Bourne again shell" (bash) —utilitzat pels llocs web (per a CGI) DHCP i altres funcions— és molt més potent del necessari per a aquestes tasques
  - Per tant: la fallada en bash comporta una greu vulnerabilitat a la xarxa

---v

![Shellshock](img/shellshock.png)

---

## Security Design Principles

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/LUW8FCTgS2I?si=CulWeFo4CRw8Wrli" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Microsoft Security Development Lifecycle

> MSDL

---

## Microsoft Security Development Lifecycle (1)

- El cicle de vida de desenvolupament de seguretat de Microsoft (_Security Development Lifecycle, SDL_) és un procés de garantia de seguretat de programari líder en el sector
- Una iniciativa de Microsoft i una política obligatòria des del 2004, l'SDL ha tingut un paper fonamental a l'hora d'incorporar la seguretat i la privadesa al programari i la cultura de Microsoft.
- La incorporació de seguretat a **cada fase SDL** del cicle de vida del desenvolupament ajuda a **detectar els problemes** aviat i ajuda a **reduir els costos** de desenvolupament.
- [https://learn.microsoft.com/en-us/windows/security/security-foundations/msft-security-dev-lifecycle](https://learn.microsoft.com/en-us/windows/security/security-foundations/msft-security-dev-lifecycle)
- [https://www.microsoft.com/en-us/securityengineering/sdl](https://www.microsoft.com/en-us/securityengineering/sdl)

---

## Microsoft Security Development Lifecycle (i 2)

![Microsoft SDL](img/microsoft-sdl.png)

---

## Simplified Implementation of the Microsoft SDL

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/WQTvv0Gek58?si=_vw_lrodKDNJYi-v" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Microsoft SDL Review

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/rPfoD7jEXnU?si=54YVv4dMcCZ5EXOa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->
