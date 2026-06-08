# Bones pràctiques per a lliuraments de projectes

Quan entregues un exercici o un projecte, comparteixes una feina que algú haurà d'obrir, entendre, executar i revisar.

Una bona entrega no necessita molta documentació. Necessita que el repositori expliqui les coses importants: què fa el projecte, com s'executa, què has implementat, decisions tècniques i com es pot comprovar que funciona.

Si aquesta informació no hi és, qui revisa haurà de reconstruir el context abans de mirar el codi. El projecte pot estar bé, però costarà més valorar-lo i donar-te feedback útil.

En aquest bloc treballarem tres hàbits bàsics: deixar el repositori net, escriure un [`README.md`](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes) útil i fer commits (canvis guardats amb [Git](https://docs.github.com/en/get-started/using-git/about-git)) amb missatges que s'entenguin.

---

## Objectius

En acabar aquest bloc podràs:

- Preparar un repositori fàcil de revisar.
- Escriure un `README.md` que expliqui què fa el projecte i com s'executa.
- Detectar fitxers que no s'han de pujar al repositori.
- Fer commits amb missatges clars.
- Revisar l'entrega abans d'enviar-la.

---

## Què s'ha d'entendre quan obres el repositori

Quan algú obre el teu repositori, ha de poder trobar ràpidament:

- quin problema resol el projecte,
- quin era l'objectiu de l'exercici,
- quines parts has implementat,
- com s'executa,
- quines tecnologies utilitza,
- on és el codi principal,
- com has comprovat que funciona,
- si hi ha alguna limitació coneguda.

No cal escriure una explicació llarga per a cada punt. Sovint n'hi ha prou amb una frase clara i una comanda ben indicada.

---

## Estructura mínima del repositori

L'estructura pot canviar segons l'exercici. En un projecte petit potser només hi haurà dos o tres fitxers; en un projecte més gran hi haurà carpetes separades. En tots els casos, qui obri el repositori ha de poder trobar ràpidament el codi, la documentació i els fitxers importants.

Exemple simple:

```text
projecte/
|-- src/          # Codi font, si aplica
|-- tests/        # Tests, si aplica
|-- .gitignore    # Fitxers que Git ha d'ignorar
|-- README.md     # Explicació del projecte
```

En els primers exercicis potser encara no hi haurà carpeta `tests`. El que cal evitar és un repositori on costa veure què és cada cosa.

Recomanacions bàsiques:

- Fes servir noms de carpetes i fitxers clars.
- Evita espais i caràcters estranys en noms de fitxers.
- No pugis dependències descarregades, fitxers temporals o configuracions personals.
- Mantingues el codi separat de la documentació quan el projecte creixi.
- Si tens dubtes, mira com està organitzat un projecte base del curs i segueix una estructura semblant.

No cal que el repositori sigui gran ni impressionant. Si és petit però està ben ordenat, qui el revisi entendrà molt més ràpid què has fet.

---

## El paper del README

El `README.md` és el fitxer principal de presentació del projecte. GitHub el mostra automàticament a la pàgina principal del repositori, per això és el primer lloc on es buscarà informació.

Un bon README respon ràpidament aquestes preguntes:

- Què fa aquest projecte?
- Com s'arrenca?
- Què passa quan funciona?
- Què has implementat?
- Com ho has comprovat?

El README s'escriu amb [Markdown](https://www.markdownguide.org/basic-syntax/), un format senzill per crear títols, llistes, links i blocs de codi.

Encara que sigui curt, el README ha d'explicar com a mínim què fa el projecte, com s'executa i què hi has implementat.

---

## README mínim recomanat

Per als primers exercicis, aquest esquema és suficient:

```markdown
# Nom del projecte

## Descripció
Explica breument què fa el projecte i quin era l'objectiu de l'exercici.

## Tecnologies utilitzades
- Java
- Altres tecnologies, si aplica

## Com executar el projecte
Explica els passos necessaris per posar-lo en marxa.

## Què he implementat
Resumeix les funcionalitats principals.

## Proves realitzades
Explica com has comprovat que funciona.
```

Adapta l'esquema al projecte. Si una secció no aporta res, no cal forçar-la. El que sempre ha de quedar clar és què fa el projecte i com s'executa.

Exemple massa vague:

```markdown
Projecte de Java.
```

Exemple més útil:

```markdown
Aplicació simple en Java per practicar la lògica d'un joc de 3 en ratlla. El projecte valida jugades, actualitza el tauler i detecta victòries o empats.
```

Amb una frase així, qui revisa ja sap quin tipus de projecte està mirant i què hauria de fer el projecte.

Més endavant podràs afegir captures, endpoints, variables d'entorn, diagrames, decisions tècniques o instruccions de desplegament. Ara prioritza el que ajuda a executar i revisar el projecte.

---

## `.gitignore`: què ha de quedar fora

No tot el que tens a la carpeta del projecte s'ha de pujar al repositori. Hi ha fitxers generats, configuracions locals i secrets que han de quedar fora.

El fitxer [`.gitignore`](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) indica a Git quins fitxers o carpetes ha d'ignorar.

Exemples habituals:

- carpetes generades com `target/`, `build/`, `dist/` o `node_modules/`,
- fitxers temporals del sistema,
- configuracions personals de l'IDE si no formen part del projecte,
- credencials, tokens, contrasenyes o fitxers `.env` amb secrets.

Pujar `node_modules/` o `target/` fa que el repositori sigui més pesat i menys net. Pujar un `.env` amb credencials pot exposar informació sensible. Encara que sigui un exercici, els secrets no han d'anar al repositori.

Si no tens clar quin `.gitignore` encaixa amb el projecte, pots consultar les plantilles oficials de [github/gitignore](https://github.com/github/gitignore). Un projecte Java, Maven, Node o Spring Boot no ignora exactament els mateixos fitxers.

---

## Git i commits

Els commits ajuden a veure com has construït el projecte. Si l'historial està ben fet, es pot seguir el procés: primer estructura, després funcionalitat, després correccions, després documentació.

Quan tot acaba en un únic commit final, es perd la història del treball. No cal fer molts commits; cal que els commits que hi ha tinguin sentit.

Per a Sprint 0, el més important és:

- Fer commits petits i comprensibles.
- Escriure missatges que expliquin el canvi.
- Evitar un únic commit final amb tota la tasca.
- Revisar `git status` abans d'entregar.

Exemples massa genèrics:

```bash
git commit -m "changes"
git commit -m "final"
git commit -m "stuff"
```

Aquests missatges no expliquen què ha canviat.

Exemples millors:

```bash
git commit -m "docs: add project README"
git commit -m "feat: implement game board"
git commit -m "fix: validate invalid moves"
```

Amb missatges així, l'historial ja explica alguna cosa.

Si vols, pots seguir l'estil de [Conventional Commits](https://www.conventionalcommits.org/), però en aquest sprint el més important és que cada missatge expliqui el canvi.

---

## Qualitat mínima del codi

En una primera entrega no s'espera perfecció, però sí un codi que es pugui llegir amb facilitat. El codi pot funcionar i, alhora, necessitar una mica d'ordre abans de ser revisat.

Punts bàsics a revisar:

- Escriu noms descriptius per a variables, funcions, mètodes i classes.
- Evita noms genèrics com `data`, `thing`, `x` o `test` si pots ser més concret.
- Dona format al codi abans d'entregar.
- Evita repetir blocs de codi sense necessitat.
- Divideix el codi en parts més petites quan una funció o mètode fa massa coses.
- Comprova casos diferents, no només el cas que surt bé a la primera.

Exemple de nom poc útil:

```java
int x = 1;
```

Exemple més clar:

```java
int playerValue = 1;
```

La segona versió ajuda a entendre què representa el valor. Aquesta mena de detall fa que el codi sigui més fàcil de llegir i comentar.

Conceptes com `SOLID`, `DRY`, `KISS`, tests o arquitectura apareixeran durant el curs amb més profunditat. En aquest sprint comencem pel criteri més bàsic: codi que es pugui llegir, executar i explicar.

---

## Errors habituals en els primers lliuraments

Abans d'entregar, revisa aquests punts:

- El repositori no té `README.md`.
- El README només diu “exercici fet” o “projecte Java”.
- No hi ha instruccions per executar el projecte.
- S'han pujat carpetes generades o dependències locals.
- Hi ha un sol commit final amb tots els canvis.
- El projecte no s'ha provat abans d'entregar.
- Hi ha fitxers buits, proves personals o codi comentat sense motiu.
- No queda clar què era obligatori i què has afegit com a millora.

Detectar aquests punts abans d'enviar l'enllaç evita aclariments que no tenen a veure amb la solució tècnica.

---

## Última passada abans d'entregar

Abans d'enviar l'entrega, val la pena fer una última passada ràpida:

- S'entén què fa el projecte?
- Hi ha instruccions per executar-lo?
- El README explica què has fet?
- El repositori està net?
- L'historial de commits té una mica de sentit?
- Has comprovat que el projecte funciona?
- Hi ha alguna limitació coneguda que calgui explicar?

Si en obrir el repositori encara cal explicar massa coses perquè s'entengui, segurament el repositori encara no explica prou bé el projecte.

---

## Bones pràctiques que consolidaràs més endavant

Durant el curs aniràs millorant les entregues amb pràctiques com aquestes:

- Tests automatitzats.
- Gestió d'errors més robusta.
- Separació clara de responsabilitats.
- Estructures de projecte més professionals.
- Treball amb branques, issues (tasques o incidències registrades al repositori) i pull requests (propostes de canvi revisables).
- Documentació d'APIs.
- Decisions tècniques justificades.
- Configuració amb variables d'entorn.
- Contenidors amb [Docker](https://docs.docker.com/get-started/docker-overview/).

Aquest document marca el punt de partida: entregues petites, clares i fàcils de revisar.

---

## Lliurament

Quan entreguis una tasca, comparteix:

- L'enllaç al repositori.
- Una branca o commit concret si el mentor ho demana.
- Un `README.md` amb instruccions clares.
- Qualsevol aclariment necessari per revisar el projecte.

Una bona entrega és codi que funciona i que una altra persona pot entendre, executar i comentar amb tu.
