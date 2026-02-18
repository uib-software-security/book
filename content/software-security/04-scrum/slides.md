# Metodologia Scrum

---

## Desenvolupament de software

- **El desenvolupament de software** és la **programació**, la **documentació**, les **proves** (_tests_) i la **correcció d'errors** informàtiques necessàries per crear i mantenir aplicacions.
  - Això dona com a resultat un producte de software.
- Es refereix al procés **estructurat** i **planificat** d'escriure i mantenir el codi font, però en un sentit més ampli del terme.
- Les **metodologies de desenvolupament** més importants són:
  - Metodologia **"Waterfall"**
  - Metodologia **"Agile"**, per exemple, **Scrum**.

---

## Fases del procés de desenvolupament de software

- La majoria de metodologies comparteixen alguna combinació de les fases següents del desenvolupament de software:
  - **Anàlisi de requisits**: documentació de les necessitats del client
  - **Disseny**: elecció de la tecnologia, disseny de l'arquitectura del projecte i dels seus components
  - **Implementació/codificació**: programació del codi del projecte
  - **Proves**: tests, intentar detectar imperfeccions per tal de corregir-les
  - **Desplegament**: instal·lació, o totes les activitats que fan que un sistema de software estigui disponible per al seu ús
  - **Manteniment**: ajuda, servei tècnic, millora del software

---

## Model _Waterfall_ (cascada)

![Waterfall model](img/waterfall-model.png)

Problema principal:

Els canvis són difícils i costosos.

---

# Què són les metodologies àgils?

Les metodologies àgils són enfocaments flexibles que permeten adaptar-se als canvis.

Principis clau:

- Entregues freqüents
- Adaptació al canvi
- Col·laboració amb el client
- Equip autoorganitzat

---

# Manifest Àgil (2001)


Valors principals:

-
 Individus i interaccions > processos i eines
-
 Programari funcional > documentació extensiva
-
 Col·laboració amb el client > contracte
-
 Respondre al canvi > seguir un pla

---

## Exemple de metodologia àgil: SCRUM

**Scrum** és un marc de treball àgil per desenvolupar, lliurar i mantenir productes complexos.
  - Es basa en la premissa que, durant el desenvolupament del producte, els clients canviaran d'opinió sobre allò que volen i necessiten.
  - Accepta que el problema no està completament comprès ni definit.
  - Se centra a maximitzar la capacitat de l'equip per lliurar ràpidament en el temps previst i respondre a necessitats d'última hora.

---

Es basa en:

-
 Iteracions curtes
-
 Feedback constant
-
 Millora contínua

Cada iteració s’anomena Sprint.

---

## Introducció a Scrum

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/9TycLR0TqFA?si=23BW6jMyI44x22eq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## SCRUM, una metodologia àgil

Fases, documents i rols de la metodologia Scrum

![Metodologia SCRUM](./img/scrum-methodolody.png)

---

## Scrum: sprint

- Un **Sprint** (o **iteració**) és la **unitat bàsica de desenvolupament** en Scrum
  - La durada és d'entre una setmana i un mes
  - **Comença** amb un esdeveniment de **planificació de l'sprint** (**_sprint planning_**) que estableix un objectiu d'sprint
  - **Acaba** amb una **revisió de l'sprint** (**_sprint review_**) i una **retrospectiva de l'sprint** (**_sprint retrospective_**), on es revisa el progrés per mostrar-lo als interessats i s'identifiquen lliçons i millores.

---

## Scrum: rols

- **Product Owner**
  - Representa les parts interessades (_stakeholders_) i la veu del client
  - És responsable de maximitzar el valor del producte resultant del treball de l'Equip de Desenvolupament
- **Scrum Team** (equip de desenvolupament)
  - Responsable de lliurar les diferents parts del producte dins els períodes establerts (Sprint)
- **Scrum Master**
  - Elimina els obstacles que impedeixen que l'equip assoleixi l'objectiu de cada sprint
  - No és el líder de l'equip (ja que aquest és autoorganitzat), però actua com a protecció entre l'equip i qualsevol influència que el distregui

---

## Rols d'Scrum

![Rols d'Scrum](./img/scrum-roles.png)

---

## Scrum: reunions

- **Daily Scrum**
  - **Cada dia de l'Sprint** es fa una reunió sobre l'estat del projecte, normalment a primera hora del dia.
  - Esdeveniment limitat a 15 minuts
  - Es responen tres preguntes: "Què vaig fer ahir?", "Què faré avui?", "Hi ha algun impediment que m'impedeixi assolir l'objectiu de l'Sprint?"
- **Reunió de Planificació de l'Sprint** (**Sprint Planning**)
  - A l'**inici de l'Sprint**, aquesta reunió planifica la feina que s'ha de dur a terme
- **Reunió de Revisió de l'Sprint** (**Sprint Review**)
  - Al **final de l'Sprint**, per revisar la feina que s'ha completat i la que no
- **Retrospectiva de l'Sprint** (**Sprint Retrospective**)
  - Al **final de l'Sprint**, per identificar els aspectes positius i aquells que cal millorar per optimitzar el rendiment de l'equip

---

## Estimació i planificació àgil

<!-- markdownlint-disable MD033 -->
<iframe width="560" height="315" src="https://www.youtube.com/embed/gE7srp2BzoM?si=QWUp0FxcKBICWav8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<!-- markdownlint-enable MD033 -->

---

## Scrum: documents

- **Product backlog**
  - Conté descripcions genèriques dels requisits, de les funcionalitats desitjables, dels errors existents a resoldre, etc.
  - Es prioritza segons els criteris del Product Owner
- **Sprint backlog**
  - Defineix les tasques necessàries per dur a terme els requisits assignats a l'Sprint actual
  - Les tasques han de ser prou detallades perquè la seva durada sigui curta (p. ex., menys de 2 dies)
- **Sprint burn-down chart**
  - Mesura el nombre de requisits del Product Backlog assignats a l'Sprint actual que encara estan pendents de finalitzar

---v

![Scrum documents](./img/burndown-chart.png)

---

## El Backlog i les User Stories

- El **Product Backlog** és una **llista ordenada** de **tot el que pot ser necessari** per al producte. És l'única font de requisits per a qualsevol canvi que es vulgui fer al producte.
  - El manté i li assigna prioritats el **Product Owner**
  - Pot contenir funcionalitats, millores, errors a corregir, tasques tècniques, etc.
- Els elements del backlog solen escriure's com a **User Stories** (històries d'usuari), una manera concisa de descriure una funcionalitat des del punt de vista de l'usuari.

---v

### Format típic d'una User Story

> "**Com a** [tipus d'usuari], **vull** [una acció], **per tal de** [un benefici]"

📌 Exemple:

> "Com a **usuari registrat**, vull **poder restablir la meva contrasenya**, per tal de **recuperar l'accés si l'oblid**."

---v

### Bones pràctiques per escriure User Stories (INVEST)

- **(I)ndependent**: que no depengui d'altres stories
- **(N)egociable**: pot canviar-se abans de ser desenvolupada
- **(V)aluable**: aporta valor a l'usuari
- **(E)stimable**: es pot estimar l'esforç que comporta
- **(S)mall**: prou petita per ser desenvolupada dins un Sprint
- **(T)estable**: es pot comprovar si s'ha completat correctament

---

## Gestió de projectes Scrum amb GitHub

- **GitHub Projects** permet gestionar visualment el treball del projecte usant vistes com **Kanban**.
- És útil per organitzar i fer seguiment de **User Stories** i sprints.

---v

### Com crear un projecte a GitHub

1. Accedeix a la pestanya **Projects** del repositori.
2. Fes clic a **New project**.
3. A la finestra **Create project**, selecciona **Featured** --> **Kanban**.
4. Assigna un nom al projecte

![Create project](./img/create-project.png)

---v

### Exemple de projecte a GitHub

![Project example](./img/project-example.png)

---v

### Elements típics de GitHub per Scrum (1)

- **Issues**: cada _User Story_ o tasca es crea com un _issue_ (amb títol, descripció, assignació, etiquetes...).
- **Assignees**: permet assignar membres de l'equip a cada issue.
- **Labels**: permeten classificar issues (p. ex. `bug`, `feature`, `enhancement`, etc.).
- **Projects**: ofereix taulers tipus **Kanban**, on els _issues_ passen per columnes (estats) com:
  - **Backlog**: llista de tasques pendents
  - **Ready**: tasques que s'han de fer en el següent _sprint_
  - **In progress**: tasques que s'estan treballant
  - **In review**: tasques que s'han acabat i estan en revisió
  - **Done**: tasques acabades i revisades

---v

### Elements típics de GitHub per Scrum (i 2)

- **Priority**: es poden assignar prioritats a cada _issue_ (p. ex. `P0`, `P1`, `P2`).
- **Size**: es poden assignar mides a cada _issue_ (p. ex. `XS`, `S`, `M`, `L`, `XL`).
- **Estimate**: es poden assignar estimacions a cada _issue_ (p. ex. `1`, `2`, `3`, `5`, `8`).
- **Milestones**: es poden usar per representar sprints o entregues concretes.
  - [Com crear un milestone](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/creating-and-editing-milestones-for-issues-and-pull-requests)

---v

### Exemple de issue (user story)

![Issue d'exemple](./img/issue.png)

---v

### ✅ Bones pràctiques

- Escriure cada issue com una **User Story**:
  - _Com a [usuari], vull [acció], per tal de [benefici]_
- Durant la **planificació de l'sprint**:
  - Assignar cada issue a l'sprint actual (**milestone**)
  - Assignar cada issue a un **membre** de l'equip
  - Assignar una **prioritat**, **mida**, **estimació** i **etiquetes** a cada issue
- Actualitzar l'estat dels issues en cada **Daily Scrum**
- Tancar l'issue quan la funcionalitat s'hagi completat i revisat
- Fer servir **Pull Requests** associades a un issue per controlar el codi relacionat

---

## Avantatges de Scrum

- Flexibilitat per al canvi
- Reducció del temps per poder veure el producte, fins i tot sense estar acabat
- Millor qualitat del software
- Millor productivitat
- Millors estimacions de temps
- Reducció de riscos

---

![Scrum](./img/scrum-diagram.png)

---

# Metodologia Kanban

---

## Què és Kanban?

- **Kanban** és una metodologia àgil de gestió del treball que es centra en el **flux continu** i la **visualització** de les tasques.
- No imposa iteracions ni sprints fixos: el treball flueix a través d’etapes definides segons la capacitat.
- S’adapta bé a equips que necessiten **flexibilitat** i a entorns amb demanda variable (suport, manteniment, desenvolupament continu).
- El nom ve del japonès: **看板** (_kan_ = visual, _ban_ = tauler).

---

## Història de Kanban

- **Origen industrial (Toyota, dècada de 1940)**
  - Taiichi Ohno (Toyota) va introduir Kanban per controlar l’estoc i el flux de peces en la producció.
  - Objectiu: produir “just-in-time”, reduir despesa i evitar acumulació innecessària.
- **Adaptació al software (dècada de 2000)**
  - David J. Anderson va portar els principis de Kanban al desenvolupament de software.
  - L’enfocament es va estendre com a alternativa o complement a Scrum i altres mètodes àgils.
- Avui s’utilitza tant en **manufactura** com en **TI**, **suport**, **disseny** i **gestió de projectes**.

---

## Objectiu de Kanban

- **Maximitzar el valor** lliurat sense sobrecarregar l’equip.
- **Visualitzar el treball** per veure on està cada tasca i on es produeixen colls d’ampolla.
- **Limitar el treball en curs (WIP)** per evitar multitasca excessiva i acabar abans de començar més.
- **Millorar el flux** de manera contínua mitjançant mètriques i retroalimentació.
- **Reduir temps de cicle** des de “començat” fins a “llest”, sense imposar deadlines artificials com els sprints.

---

## Principis de Kanban

1. **Comença amb el que fas ara**: no cal canviar tot el procés; s’aplica sobre el flux actual.
2. **Compromet-te amb canvis incrementals i evolutius**: es millora pas a pas, sense revolucions.
3. **Respecta els rols, responsabilitats i càrrecs actuals**: Kanban no defineix rols nous (a diferència de Scrum).
4. **Encorageja l’acte de lideratge** a tots els nivells: qualsevol pot proposar i impulsar millores.

---

## Pràctica: Visualitzar el flux de treball

- El treball es representa en un **tauler Kanban** (físic o digital).
- **Columnes** = etapes del procés (p. ex. *Backlog*, *Per fer*, *En curs*, *Revisió*, *Fet*).
- **Targetes** = tasques o ítems de treball; es desplacen d’esquerra a dreta segons l’avancament.
- Això permet veure ràpidament l’estat del treball i on es concentren els retards.

---

## Pràctica: Limitar el treball en curs (WIP)

- Es defineix un **límit WIP** per columna (o per etapa).
- Exemple: màxim 3 tasques a “En curs”.
- **Avantatges**:
  - Redueix el canvi constant de context.
  - Força a acabar tasques abans d’encomanar-ne de noves.
  - Fa més visibles els colls d’ampolla i permet actuar-hi.

---

## Pràctica: Gestionar el flux

- **Flux** = com flueixen les tasques des del backlog fins a “Fet”.
- S’analitzen mètriques com:
  - **Temps de cicle** (de “començat” a “llest”).
  - **Throughput** (quantitat d’ítems lliurats en un període).
  - **WIP** per columna.
- L’equip revisa el tauler i les mètriques per detectar problemes i millorar el procés.

---

## Pràctica: Fer explícites les polítiques i millorar col·laborativament

- Les **polítiques** queden clares i visibles (p. ex. “Què significa ‘Fet’?”, “Qui pot moure una tasca a Revisió?”).
- Es fan **reunions de revisió del procés** (similar a una retrospectiva) per ajustar polítiques i límits WIP.
- Kanban no imposa cerimònies concretes; l’equip decideix quines reunions i amb quina freqüència.

---

## Kanban vs Scrum (resum)

| Aspecte | Kanban | Scrum |
|--------|--------|--------|
| **Iteracions** | No; flux continu | Sprints fixos (1–4 setmanes) |
| **Rols** | No en defineix | Product Owner, Scrum Master, Equip |
| **Compromís** | Límits WIP, no “completar sprint” | Objectiu d’sprint, backlog d’sprint |
| **Canvis** | Es poden afegir tasques en qualsevol moment | Backlog d’sprint tancat durant l’sprint |
| **Mètriques** | Flux, temps de cicle, WIP | Velocitat, burn-down |
| **Flexibilitat** | Alta; s’adapta al procés actual | Estructura més definida |

- **Kanban** és molt flexible i adequat per suport, manteniment o equips que no volen sprints.
- **Scrum** ofereix més estructura (rols, esdeveniments, artefactes) i és molt utilitzat en desenvolupament de producte amb entregues iteratives.

---

## Quan triar Kanban?

- Treball **continu** o **imprevisible** (suport, incidents, demandes que arriben sense calendari fix).
- Equips que **no volen** o **no poden** comprometre’s amb sprints.
- Voler **millorar el flux** sense canviar tot el procés ni els rols.
- Combinar amb Scrum: tauler **tipus Kanban** per gestionar el backlog i l’sprint (com amb GitHub Projects).

---

## 🔗 Enllaços

**Scrum**
- [Scrum: The Art of Doing Twice the Work in Half the Time (Jeff Sutherland)](https://amzn.eu/d/fBbLyZd)
- [Mastering Professional Scrum (Ockerman Stephanie, Reindl Simon)](https://amzn.eu/d/781dVum)
- [Essential Scrum: A Practical Guide to the Most Popular Agile Process (Kenneth S. Rubin)](https://amzn.eu/d/aFBOZ14)

**Kanban**
- [Kanban: Successful Evolutionary Change for Your Technology Business (David J. Anderson)](https://www.amazon.com/Kanban-Successful-Evolutionary-Technology-Business/dp/0984521402)
- [Kanban Guide](https://www.scrum.org/resources/kanban-guide-scrum-teams) (Scrum.org)

