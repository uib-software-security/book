# Revisió del codi: testing i anàlisi

---

## Pràctica actual per desenvolupament segur

- **Testing**
  - Assegureu-vos que el programa s'executa correctament segons un conjunt d'entrades

![Testing](img/testing.png)

- **Beneficis**: una fallada concreta demostra un problema, ajuda a solucionar-ho
- **Inconvenients**: car, difícil, difícil de cobrir tots els camins de codi, sense garanties

---

## Anàlisi estàtica

> Static Analysis

---

## Anàlisi estàtica (1)

- **Anàlisi estàtica de software**: és un tipus d'anàlisi que es realitza sense executar el programa
  - En la majoria dels casos, l'anàlisi es realitza a alguna versió del codi font i en altres casos es realitza al codi objecte
- El terme s'aplica generalment a les anàlisis realitzades per una **eina automàtica**
- L'**anàlisi realitzada per un humà** és anomenat comprensió de programes (o enteniment de programes), o també **revisió de codi**.

---

## Anàlisi estàtica (i 2)

- Analitzar el codi del programa sense executar-lo
  - En cert sentit, estem demanant a un ordinador que faci el que podria fer un humà durant una revisió de codi
- **Beneficis**: una **cobertura (molt) més alta**
  - Raonar sobre moltes possibles execucions del programa
    - A vegades totes, aportant una garantia
  - Raonar sobre programes incomplets (per exemple, biblioteques)
- **Inconvenients**
  - Només pot analitzar propietats limitades
  - Poden faltar alguns errors o tenir falses alarmes
  - Pot ser molt llarg d’executar

---

## Impacte

- Comprova a fons propietats limitades però útils
  - **Elimina categories d'errors**
  - Els **desenvolupadors** poden **concentrar-se** en un **raonament** més profund
- **Fomenta millors pràctiques de desenvolupament**
  - Desenvolupa models de programació que eviten errors típics
  - Encoratja els programadors a reflexionar i posar de manifest els seus supòsits
    - Moltes eines d’anàlisi estàtica permeten l’ús d'anotacions que milloren la precisió de l'eina

---

## L'anàlisi estàtica és impossible?

- L'anàlisi estàtica **perfecta** **no és possible**
- L'anàlisi estàtica **útil** és perfectament **possible**, malgrat
  - **No acabament**: l'analitzador no acaba mai, o
  - **Falses alarmes**: els errors que no són realment errors, o
  - **Errors perduts**: que no es trobin errors NO significa que no hi hagi error

---

## L'art de l'anàlisi estàtica

- Compensacions de disseny d'anàlisi
  - **Precisió**: Modeleu acuradament el comportament del programa, per minimitzar les falses alarmes
  - **Escalabilitat**: Analitzar amb èxit programes grans
  - **Comprensió**: els informes d'error haurien de ser accionables
- Observació: **l'estil del codi és important**
  - Procura ser precís per als programes “bons”.
    - Està bé prohibir el codi “desagradable” en nom de la seguretat
  - Falses alarmes vistes positivament: redueix la complexitat
    - El codi més comprensible per a l'anàlisi és més comprensible per als humans

---

## Static Code Analysis: Scan All Your Code For Bugs

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/Heor8BVa4A0?si=_bV778tveEKrdccu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Exemples d’eines d’anàlisi estàtica**

- Java
  - **Checkstyle**: Es centra en la conformitat amb els estàndards de codificació.
  - **PMD**: Detecta possibles bugs, codi no òptim, complicat o dubtós.
  - **FindBugs**/**SpotBugs**: Identifica patrons de bugs coneguts en el codi Java.
- C/C++
  - **Cppcheck**: Eina d'anàlisi estàtica per a codi C/C++ que detecta diversos tipus d'errors.
  - **Clang Static Analyzer**: Ofereix anàlisi de codi integrat amb el compilador Clang per trobar bugs en codi C/C++. Clang
  - **Coverity**: Proporciona anàlisi avançada per identificar defectes de software en C, C++, i altres.

---v

- **JavaScript**
  - **ESLint**: Eina extensible que detecta problemes trobats en el codi JavaScript, permetent personalitzar regles.
  - **JSHint**: Una eina de validació de codi que ajuda a detectar errors i problemes potencials.
  - **Flow**: Verificador de tipus estàtic per JavaScript que també pot detectar errors en temps de compilació.

---

## Exemples d’eines d’anàlisi estàtica

- **Python**
  - **Pylint**: Analitza codi Python per trobar bugs i senyals de codi de mala qualitat.
  - **PyFlakes**: Detecta errors en codi Python com mòduls o variables no utilitzats.
  - **Mypy**: Verifica tipus de manera estàtica per assegurar que el codi s'adhereix als tipus esperats.
- **Rust**
  - **Clippy**: Una col·lecció de lints per millorar el codi Rust i trobar errors comuns i inusuals.
  - **Rust Analyzer**: Proporciona una sèrie d'analitzadors estàtics per millorar la codificació en Rust.
  - **Cargo Check**: Executa una comprovació ràpida del codi per verificar errors sense compilar el programa completament. **cargo check**

---

## Clippy

- Instal·lació:
  - `rustup component add clippy`
- Executar Clippy:
  - `cargo clippy`
- Configuració al fitxer `clippy.toml` o `.clippy.toml` del projecte
- Llista de regles:
  - [https://rust-lang.github.io/rust-clippy/master/index.html](https://rust-lang.github.io/rust-clippy/master/index.html)

---

## Linting Rust Code With Clippy CLI Rules

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/_YFZZc5jIfY?si=wTml1CftD01OjVH9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Anàlisi de flux

> Flow Analysis

---

<!-- markdownlint-disable MD024 -->
## Anàlisi de flux
<!-- markdownlint-enable MD024 -->

- L'**anàlisi de flux** és un mètode d'**anàlisi estàtica** que estudia el camí que segueixen les dades a través del codi per identificar possibles problemes de lògica o seguretat.
  - L'**objectiu** és detectar condicions errònies, fluxos de dades incorrectes, i altres vulnerabilitats que podrien no ser evidents només amb una revisió de codi estàtica o durant l'execució normal.

---

## Tipus d’anàlisi de flux

- **Anàlisi de Flux de Dades**: Se centra en els camins que les dades prenen a través del programa
  - Aquesta anàlisi ajuda a identificar usos de dades no inicialitzades, fugues de memòria, i accessos a memòria no vàlids.
- **Anàlisi de Flux de Control**: Examina els camins de control dins d'un programa, com les branques en les declaracions condicionals i els bucles
  - Això es fa per assegurar que totes les branques i bucles funcionen com s'espera i per detectar codi inassolible o bucles infinits.

---

## Mètodes i tècniques

- **Graf de Flux de Control (CFG)**: Utilitza representacions gràfiques on els nodes representen unitats bàsiques d'instruccions i les arestes representen el flux de control entre aquestes.
- **Anàlisi tainting**: Segueix la propagació de dades des de fonts no fiables (com entrada d'usuari) per veure si aquestes dades poden afectar àrees crítiques del programa sense ser adequadament validades o sanejades.

![Control Flow Graph](img/control-flow-graph.png)

---

## Anàlisi de flux: Exemple

![Flow Analysis](img/flow-analysis.png)

---

## Execució simbòlica

> Symbolic Execution

---

<!-- markdownlint-disable MD024 -->
## Execució simbòlica
<!-- markdownlint-enable MD024 -->

- És un mètode de test que analitza el codi executant-lo amb **valors simbòlics** en lloc de **valors reals**, permetent explorar molts camins de execució diferents simultàniament
- **Objectiu**: Identificar errors, condicions d'error i vulnerabilitats de seguretat en el codi analitzant com aquest reaccionaria a una àmplia gamma de condicions d'entrada, incloent aquelles poc probables en una execució normal.

---

## Principis bàsics

- **Valors Simbòlics**: En lloc d'utilitzar dades reals, l'execució simbòlica fa servir 'símbols' que representen valors arbitraris d'entrada.
- **Arbre de Decisió**: Genera un arbre on cada node representa un punt de decisió en el codi, i les branques representen els diferents camins d'execució basats en aquestes decisions

---

## Mètodes i tècniques de l'execució simbòlica

- **Restriccions de Camí**: Durante l'execució, es van acumulant condicions o restriccions sobre els valors simbòlics que determinen quins camins són possibles.
- _**Solver**_ **de Restriccions**: Utilitza solucionadors matemàtics per avaluar les restriccions i determinar els valors d'entrada que cobreixen diferents camins de codi.

---

## Exemples de problemàtiques detectades

- **Desbordament de Buffer**: Pot descobrir condicions que portarien a un desbordament de buffer, introduint valors simbòlics que maximitzen la mida dels dades processades.
- **Condició de Carrera**: Podria identificar una condició de carrera potencial analitzant l'ordre simbòlic de les operacions sobre recursos compartits.

---

## Beneficis de l'execució simbòlica

- **Cobertura de Codi**: Millora significativa en la cobertura de codi, assegurant que tots els camins possibles s'explorin.
- **Descobriment de Bugs Profunds**: Pot descobrir errors que són difícils de detectar amb tests basats en entrades concretes.
- **Automatització dels Tests**: Redueix la necessitat d'intervenció humana en la generació de casos de test, millorant l'eficiència dels processos de test.

---

## Anàlisi de flux / Execució simbòlica

- Tot i que ambdues tècniques poden semblar similars en el sentit que **analitzen els camins a través del codi**,
  - l'**execució simbòlica** es centra més en provar tots els **possibles estats** d'un programa a través de l'ús de **valors simbòlics**
  - mentre que l'**anàlisi de flux** es concentra en el seguiment de com les **dades es mouen i modifiquen** dins del programa.
- En la pràctica, l'execució simbòlica i l'anàlisi de flux sovint s'utilitzen **conjuntament** per proporcionar una revisió exhaustiva del codi, on l'anàlisi de flux pot ajudar a definir millor els camins que l'execució simbòlica hauria d'explorar.

---

![Tipus de tests](img/types-of-tests.png)

---

## Tests unitaris

> Unit tests

---

<!-- markdownlint-disable MD024 -->
## Tests unitaris
<!-- markdownlint-enable MD024 -->

- Els **tests unitaris** són procediments que verifiquen el comportament d'una **unitat específica de codi** per assegurar-se que funciona correctament.
- **Unitat**: Una unitat pot ser una **funció**, un **mètode**, o una **classe** dins del software que es pot provar de forma aïllada.

---

## Principis bàsics dels tests unitaris

- **Aïllament**: Cada test unitari ha de ser independent dels altres; això implica que no ha d'interactuar amb bases de dades, fitxers, o components de xarxa, i es deuen utilitzar tècniques com a _**mockups**_ (**maquetes**) o _**stubs**_.
  - _**Stub**_: tros de codi que es fa servir per representar alguna funcionalitat d'un component al procés de desenvolupament de programari
- **Repetibilitat**: Cada test ha de poder ser executat múltiples vegades i en qualsevol entorn, sempre amb el mateix resultat.
- **Automatització**: Els tests unitaris són generalment escrits i executats automàticament per eines de software. Això permet integrar-los en processos d’integració contínua.

---

## Mètodes i tècniques de tests unitaris

- **Frameworks de Testing**: Utilització de frameworks especialitzats, com **JUnit** per **Java**, **PyTest** per **Python**, o **NUnit** per **C#**. Aquests frameworks faciliten la creació, execució, i organització dels tests.
- _**Asserts**_: S'utilitzen afirmacions per comprovar que el codi realitza les operacions correctes. Per exemple, verificar que el resultat d'una funció és el valor esperat.

---

## Exemples de tests unitaris

- **Funció Suma**: Per una funció que suma dos nombres, un test unitari podria comprovar que la suma de 2 i 3 retorni 5.
- **Validació d'Usuari**: Per una funció que valida noms d'usuari, un test unitari podria verificar que el nom "usuari123" sigui acceptat i que "usuari#123" sigui rebutjat.

---

## Beneficis dels tests unitaris

- **Detecció Precoç de Bugs**: Ajuda a detectar errors en les fases inicials del desenvolupament, facilitant la seva solució abans que afectin altres parts del sistema.
- **Documentació de Codis**: Els tests serveixen com a documentació que mostra com es suposa que el codi ha de ser utilitzat.
- **Confiança en Refactoritzacions**: Permet als desenvolupadors modificar el codi existent amb la confiança que no estan introduint errors en funcions ja testejades.

---

## Millors pràctiques

- **Cobertura de Codi**: Intentar cobrir totes les ramificacions i camins possibles dins del codi per assegurar una completa validació.
- **Mantenir els Tests Actualitzats**: Actualitzar els tests unitaris quan el codi canvia per assegurar que continuen sent rellevants i útils.

---

## Write Unit Tests in Rust

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/0G_5uUe_NXk?si=IqnoBNKgtUo-odrx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Tests d’integració

> Integration tests

---

<!-- markdownlint-disable MD024 -->
## Tests d’integració
<!-- markdownlint-enable MD024 -->

- Els **tests d'integració** verifiquen la correcta interacció i funcionament conjunt de múltiples components o mòduls d'un sistema de software.
- **Objectiu**: Detectar problemes associats amb les interfícies entre components, garantint que funcionen junts com s'espera.

---

## Principis bàsics dels tests d'integració

- **Integració Incremental**: Aquesta tècnica comença amb dos components, testeja la seva interacció, i afegeix progressivament més components per testejar. Això pot seguir un enfocament "big bang", "top-down", "bottom-up" o "sandwich".
- Ús de **Stubs** i **Drivers**: En absència d'alguns mòduls, s'utilitzen **stubs** (per mòduls **cridats**) i **drivers** (per mòduls **que criden**) per simular les funcions dels components encara no desenvolupats o integrats.

---

## Mètodes i tècniques de tests d'integració

- **Top-Down**: Comença amb els nivells superiors de control del programa i progressivament integra els nivells inferiors.
- **Bottom-Up**: Contràriament al top-down, aquest enfocament comença amb els mòduls a nivell més baix i avança cap als nivells superiors.
- **Big Bang**: Tots els components o mòduls s'integren en un sol pas i el sistema complet es testeja en conjunt.
- **Sandwich** (**Híbrid):** Combina els enfocaments **top-down** i **bottom-up**.

---

## Exemples de Tests d'Integració

- **Integració de Sistema de Pagament**: Testejant la integració entre un carret de compra en línia i un sistema de processament de pagaments per assegurar que les transaccions es processen correctament.
- **Interacció entre Base de Dades i API**: Verificant que una aplicació web pot recuperar i enviar dades correctament a una base de dades a través d'una API.

---

## Beneficis dels tests d'integració

- **Cobertura de Interaccions**: Assegura que les interaccions entre components són com s'espera, detectant errors que no es poden trobar en tests unitaris.
- **Validació de Disseny**: Confirma que l'arquitectura global del sistema suporta les funcionalitats requerides.
- **Identificació Precoç de Problemes**: Ajuda a descobrir i solucionar problemes d'integració abans que avancin a etapes posteriors de desenvolupament, potencialment estalviant temps i recursos.

---

## Consideracions

- **Planificació**: Requereix una planificació cuidadosa per decidir l'ordre i l'estratègia d'integració.
- **Dependències**: Pot ser desafiador gestionar les dependències entre els components, especialment en sistemes grans i complexes.

---

## Tests de sistema

> System testing or end-to-end (E2E) testing

---

<!-- markdownlint-disable MD024 -->
## Tests de sistema
<!-- markdownlint-enable MD024 -->

- Els t**ests de sistema** són la validació d'un programa de software **complet** i **integrat** per verificar que compleix amb els **requisits** especificats.
- **Objectiu**: Confirmar que totes les parts integrades del software funcionen en harmonia sota condicions que simulen l'ús real, cobrint totes les funcionalitats i fluxos de l'usuari.

---

## Principis bàsics dels tests de sistema

- **Cobertura Completa**: Engloba totes les funcions del sistema en un entorn que imita la producció, incluint la interacció amb bases de dades, xarxes, i altres aplicacions.
- **Tests d'Escenaris d'Usuari**: S'executen escenaris que un usuari real podria realitzar, des de l'inici fins al final, per verificar la resposta del sistema.

---

## Mètodes i tècniques de tests de sistema

- **Automatització de Tests**: Molts tests de sistema són automatitzats per cobrir escenaris complexos i repetitius, utilitzant eines com _Selenium_, _TestComplete_, o _Cypress_.
- **Tests Manual**: Alguns escenaris, especialment els que impliquen percepcions subjectives com la usabilitat, poden requerir intervenció manual.

---

## Exemples de tests de sistema

- **Procés de Compra Online**: Un test E2E podria simular un usuari realitzant una compra completa a una botiga online, des de la selecció de productes fins a la finalització del pagament i recepció de la confirmació.
- **Aplicació Bancària**: Testejar un escenari on un usuari accedeix al seu compte, realitza una transferència, i verifica les transaccions, tot a través de diferents dispositius o plataformes.

---

## Beneficis dels tests de sistema**

- **Assoliment de Conformitat**: Assegura que el sistema compleix amb tots els requisits funcionals i no funcionals.
- **Prevenció de Defectes**: Ajuda a identificar problemes abans que el software arribi als usuaris finals, millorant la satisfacció de l'usuari.
- **Validació d'Experiència d'Usuari**: Confirma que l'experiència de l'usuari és coherent i satisfactòria a través de tot el sistema.

---

## Consideracions dels tests de sistema

- **Complexitat**: Els tests de sistema poden ser complexos i costosos de planificar i executar degut a la seva naturalesa exhaustiva i el necessari entorn de simulació de producció.
- **Manteniment d'Escenaris**: Els tests E2E requereixen manteniment regular per assegurar que segueixen sent rellevants a mesura que el software evoluciona.

---

![Tipus de tests](img/types-of-tests-2.png)

---

## Auditories de codi

> Code audits

---

## Auditoria de codi

- Una **auditoria de codi** és una revisió sistemàtica del codi font per identificar **errors**, **vulnerabilitats** de seguretat, i **ineficiències**.
  - Serveix per assegurar que el software compleix amb els estàndards de codificació i pràctiques recomanades.
- **Objectiu**: millorar la qualitat del software i garantir que està lliure de defectes que podrien afectar la seva funcionalitat o seguretat

![Code Audit](img/code-audit.png)

---

## Components clau de l'auditoria de codi

- **Revisió de Seguretat**: Analitza el codi per identificar vulnerabilitats que podrien ser explotades per atacants, com a injeccions SQL, desbordament de buffers, i fallades de gestió de sessions.
- **Anàlisi de Qualitat de Codi**: Evalua el codi per assegurar que segueix les millors pràctiques de programació, està ben estructurat, i és fàcil de mantenir.
- **Comprovació de Conformitat**: Verifica que el codi compleix amb els estàndards de la indústria i normatives legals, com GDPR per a protecció de dades o HIPAA per a informació sanitària.

---

## Mètodes utilitzats

- **Anàlisi Estàtica**: Utilitza eines que examinen el codi sense executar-lo per detectar errors o patrons de codi problemàtics.
- **Anàlisi Dinàmica**: Implica executar el codi en un entorn controlat per identificar problemes en temps d'execució.
- **Revisions de Codi Manual**: Experts en codi revisen el codi font manualment per detectar problemes que les eines automàtiques poden no detectar.

---

## Beneficis de l’auditoria de codi

- **Millora de la Seguretat**: Redueix el risc de vulnerabilitats de seguretat i exposició a atacs.
- **Augment de la Qualitat del Producte**: Assegura una major estabilitat i rendiment del software.
- **Conformitat amb Normatives**: Garanteix que el software compleix amb les lleis i regulacions aplicables, evitant possibles sancions legals.

---

## Clean code i tests

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/AlK4Vir5fMQ?si=FsBi8WWJyuq86_Wv" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->
