# Introducció a Git i GitHub

Git i GitHub formen part del dia a dia en desenvolupament. Serveixen per guardar l'evolució del codi, recuperar versions anteriors, treballar amb altres persones i entregar projectes de manera ordenada.

No cal que dominis Git complet en aquest sprint. Ara l'objectiu és entendre el cicle bàsic: crear un repositori, veure què ha canviat, guardar canvis amb commits i pujar el projecte a GitHub.

Més endavant treballaràs amb branques, pull requests, conflictes i fluxos de treball més professionals. En aquest bloc només volem que alguns conceptes et comencin a sonar.

Si vols una explicació oficial del paper de Git i GitHub en el desenvolupament, pots consultar [GitHub Docs: About Git](https://docs.github.com/en/get-started/using-git/about-git). No cal llegir-ho tot ara, però és un bon recurs per tornar-hi quan hagis practicat una mica.

---

## Objectius

En acabar aquest bloc hauries de poder:

- Explicar la diferència entre Git i GitHub.
- Crear un repositori Git local.
- Consultar l'estat dels fitxers amb `git status`.
- Preparar canvis amb `git add`.
- Guardar canvis amb `git commit`.
- Consultar l'historial amb `git log`.
- Connectar un repositori local amb GitHub.
- Pujar canvis amb `git push`.

---

## Abans de començar

Per seguir l'exercici necessites un terminal compatible amb Bash.

- A macOS i Linux pots fer servir el terminal del sistema.
- A Windows pots fer servir [Git Bash](https://git-scm.com/downloads), que s'instal·la juntament amb Git.
- Si ja tens WSL configurat, també pots treballar des d'una distribució Linux.

Evita fer aquest exercici amb Command Prompt o PowerShell si encara no tens experiència, perquè algunes comandes poden comportar-se de manera diferent.

Comprova si tens Git instal·lat:

```bash
git --version
```

Si no el tens instal·lat, pots seguir la documentació oficial de [Git downloads](https://git-scm.com/downloads).

Configura el teu nom i correu perquè Git pugui identificar l'autoria dels commits:

```bash
git config --global user.name "El teu nom"
git config --global user.email "el.teu@email.com"
```

---

## Git vs GitHub

**Git** és l'eina que funciona al teu ordinador i guarda l'historial de canvis d'un projecte.

**GitHub** és una plataforma online on pots pujar repositoris, compartir-los i col·laborar amb altres persones.

Una manera simple de veure-ho:

```text
Git    -> controla versions al teu ordinador
GitHub -> allotja repositoris a internet
```

Git pot funcionar sense GitHub. GitHub, en canvi, utilitza Git per gestionar els repositoris.

Una analogia útil:

- Git és com la llibreta de canvis del projecte.
- GitHub és el lloc on comparteixes aquesta llibreta amb altres persones.

Quan treballes localment, Git sap què has canviat al teu ordinador. Quan fas `push`, envies aquests commits al repositori remot perquè també existeixin a GitHub.

---

## Model mental: on són els teus canvis

Git és més fàcil d'entendre si imagines quatre zones:

```text
working directory -> staging area -> local repository -> remote repository
```

| Zona | Què vol dir |
|------|-------------|
| `working directory` | La carpeta on edites fitxers. |
| `staging area` | La zona on prepares què entrarà al proper commit. |
| `local repository` | L'historial de commits guardat al teu ordinador. |
| `remote repository` | La còpia del projecte a GitHub o una altra plataforma. |

Les comandes bàsiques encaixen així:

```text
git status -> mira què ha canviat
git add    -> passa canvis a staging
git commit -> guarda una foto local
git push   -> puja commits al remot
git pull   -> baixa canvis del remot
```

Aquesta és la idea més important del bloc. Si entens aquest flux, després serà molt més fàcil entendre branques, conflictes i pull requests.

---

## Vocabulari que et començarà a sonar

No cal dominar aquests conceptes ara, però és útil que et sonin perquè els veuràs sovint durant el curs:

| Concepte | Idea principal |
|----------|----------------|
| `repository` | Carpeta d'un projecte controlada per Git. |
| `commit` | Punt de control que guarda un canvi concret. |
| `branch` | Línia de treball separada de la principal. |
| `merge` | Acció d'unir canvis d'una branca amb una altra. |
| `merge conflict` | Situació en què Git no pot decidir automàticament quin canvi conservar. |
| `remote` | Repositori allotjat fora del teu ordinador, normalment a GitHub. |
| `origin` | Nom habitual del repositori remot principal. |
| `push` | Enviar commits locals cap a GitHub. |
| `pull` | Baixar canvis de GitHub cap al teu ordinador. |
| `pull request` | Proposta per revisar i integrar canvis en un repositori. |
| `workflow` | Forma acordada de treballar amb Git en un projecte o equip. |

En aquest sprint practicaràs sobretot repositoris, commits, `push` i una mica de repositori remot. Les branques, conflictes, pull requests i fluxos de treball els treballaràs més endavant amb eines i dinàmiques més avançades.

---

## Exercici guiat: crea el teu primer repositori

Crearàs un projecte petit només per practicar Git i GitHub.

### 1. Crea una carpeta de projecte

```bash
mkdir readme-project
cd readme-project
```

### 2. Inicialitza Git

```bash
git init
```

Aquesta comanda converteix la carpeta actual en un repositori Git. A partir d'aquest moment, Git pot seguir els canvis que hi facis.

Git crearà una carpeta oculta anomenada `.git`. No l'has de tocar manualment: és on Git guarda la informació interna del repositori. Si elimines aquesta carpeta, el projecte deixarà de tenir historial Git.

### 3. Crea un README

```bash
touch README.md
```

Obre `README.md` amb el teu editor i afegeix:

```markdown
# Readme Project

Aquest projecte serveix per practicar Git i GitHub.
```

Si no coneixes Markdown, pots consultar la guia [Markdown basic syntax](https://www.markdownguide.org/basic-syntax/).

---

## El cicle bàsic de Git

Quan treballes amb Git, repetiràs moltes vegades aquest cicle:

```text
modificar -> revisar -> afegir -> confirmar
```

Aquest ordre és important. No facis commits a cegues. Primer mira què ha canviat, després decideix què vols incloure i finalment guarda el canvi amb un missatge clar.

### 1. Revisa l'estat del projecte

```bash
git status
```

Git t'indicarà que `README.md` encara no està seguit.

`git status` és una de les comandes que més faràs servir. Abans de qualsevol `add`, `commit`, `push` o entrega, mira l'estat del repositori. T'ajuda a evitar dues errades habituals: oblidar fitxers importants o pujar fitxers que no tocaven.

### 2. Afegeix el fitxer a l'àrea de preparació

```bash
git add README.md
```

Amb `git add` li dius a Git quins canvis vols incloure en el proper commit.

Pensa en `git add` com preparar una motxilla: no tot el que tens sobre la taula ha d'entrar-hi. Pots afegir un fitxer concret, com en l'exemple, o afegir diversos fitxers si tenen sentit dins del mateix commit.

### 3. Fes el primer commit

```bash
git commit -m "docs: create initial README"
```

Un commit és un punt de control del teu projecte. El missatge hauria d'explicar què has canviat.

Un bon commit hauria de representar una idea petita i coherent. Per exemple: crear el README, afegir una funció, corregir una validació o actualitzar instruccions. Si un commit barreja moltes coses diferents, després costa entendre l'historial.

### 4. Consulta l'historial

```bash
git log
```

Veuràs l'historial de commits. Si el terminal entra en una vista de lectura, pots sortir-ne amb `q` o `:q`.

---

## Practica amb més canvis

Afegeix una nova secció al `README.md`:

```markdown
## Objectiu

Aprendre el cicle bàsic de Git: status, add, commit i log.
```

Abans de guardar-ho en un commit, mira què ha canviat:

```bash
git diff
```

`git diff` et mostra les diferències exactes entre el que tenies i el que has modificat. És una manera ràpida de revisar-te abans de guardar el canvi.

Si veus una línia que no volies canviar, encara ets a temps de corregir-la abans del commit.

Ara afegeix i confirma el canvi:

```bash
git add README.md
git commit -m "docs: add project goal"
```

Torna a mirar l'historial:

```bash
git log
```

---

## Missatges de commit

Un bon missatge de commit és curt, concret i ajuda a entendre l'evolució del projecte.

Un missatge dolent diu poc:

```bash
git commit -m "final"
git commit -m "changes"
git commit -m "update"
```

El problema no és l'anglès, sinó la manca d'informació. D'aquí a dues setmanes no sabràs què volia dir `update`.

Exemples:

```bash
git commit -m "docs: add installation steps"
git commit -m "feat: add game board"
git commit -m "fix: validate invalid moves"
```

En aquest sprint no cal que memoritzis totes les convencions. Però sí és bona idea començar a escriure missatges que expliquin el canvi.

Si vols saber més sobre aquest estil, pots consultar [Conventional Commits](https://www.conventionalcommits.org/).

---

## Connecta el projecte amb GitHub

Ara pujaràs el repositori local a GitHub.

### 1. Crea un repositori a GitHub

Ves a [https://github.com](https://github.com) i crea un repositori nou anomenat `readme-project`.

No afegeixis README, `.gitignore` ni cap altre fitxer des de GitHub, perquè ja tens el projecte creat al teu ordinador.

El motiu és evitar començar amb dos historials diferents: un al teu ordinador i un altre a GitHub. En aquest primer exercici volem una situació simple: primer crees el projecte local, després el connectes amb un repositori remot buit.

### 2. Afegeix el repositori remot

GitHub et mostrarà unes comandes semblants a aquestes:

```bash
git remote add origin git@github.com:el_teu_usuari/readme-project.git
git branch -M main
git push -u origin main
```

Què fa cada comanda:

- `git remote add origin ...` connecta el teu repositori local amb el repositori de GitHub.
- `git branch -M main` assegura que la branca principal es diu `main`.
- `git push -u origin main` puja els commits locals a GitHub i recorda aquesta connexió per a futurs `push`.

Executa aquestes comandes des de l'arrel del projecte.

### 3. Comprova el resultat

Entra al repositori de GitHub amb el navegador i comprova que hi apareix el teu `README.md`.

---

## Si GitHub et demana configurar SSH

És possible que GitHub et demani configurar una clau SSH si fas servir una URL que comença per `git@github.com:`.

No cal que entenguis SSH a fons ara. Només has de saber que és una manera segura d'identificar el teu ordinador davant de GitHub.

Pots seguir la documentació oficial:

- [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

També pots fer servir HTTPS si encara no vols configurar SSH:

```bash
git remote add origin https://github.com/el_teu_usuari/readme-project.git
```

---

## Sincronitzar canvis: push i pull

Quan el repositori local ja està connectat amb GitHub, faràs servir aquestes comandes sovint:

```bash
git push
```

Envia els teus commits locals cap a GitHub.

```bash
git pull
```

Baixa canvis de GitHub cap al teu ordinador.

En Sprint 0, el més important és que entenguis aquesta idea:

```text
el teu ordinador <-> GitHub
```

Si treballes sol i sempre fas `pull` abans de començar i `push` quan acabes, normalment evitaràs molts problemes.

---

## Branques, conflictes i fluxos de treball

En projectes reals, normalment no es treballa sempre directament sobre `main`. Es creen branques per separar canvis, es revisen pull requests i es resolen conflictes quan dues persones han modificat la mateixa part del codi.

Ara només cal que et sonin aquestes idees:

- Una `branch` permet treballar en una funcionalitat sense tocar directament la branca principal.
- Un `merge` integra els canvis d'una branca dins d'una altra.
- Un `merge conflict` apareix quan Git no pot unir canvis automàticament.
- Un `pull request` serveix perquè una altra persona revisi els teus canvis abans d'integrar-los.
- Un `workflow` defineix com treballa l'equip: quines branques fa servir, quan obre pull requests i com revisa el codi.

No et preocupis si encara no ho veus clar. Més endavant faràs servir eines i pràctiques més avançades per treballar amb branques, revisions, conflictes i col·laboració real.

---

## Errors habituals quan comences amb Git

Si alguna cosa no funciona, revisa aquests punts abans de bloquejar-te:

- Estàs executant la comanda dins de la carpeta correcta? Comprova-ho amb `pwd`.
- Has inicialitzat Git amb `git init`?
- Has fet `git add` abans de `git commit`?
- El commit ha fallat perquè Git no sap el teu `user.name` o `user.email`?
- Has creat el repositori remot buit o GitHub ja tenia un README propi?
- Estàs fent `push` a la branca correcta?
- Has copiat bé la URL del repositori remot?

Quan dubtis, la primera comanda hauria de ser gairebé sempre:

```bash
git status
```

Git acostuma a donar pistes útils. No cal entendre cada paraula del missatge d'error al principi, però sí aprendre a llegir-lo amb calma i buscar la part que diu què espera Git que facis.

---

## Què has de saber al final d'aquest bloc

Abans de continuar, comprova que pots fer això sense seguir tots els passos literalment:

- Crear una carpeta de projecte.
- Inicialitzar Git amb `git init`.
- Veure l'estat amb `git status`.
- Afegir canvis amb `git add`.
- Crear un commit amb `git commit`.
- Consultar l'historial amb `git log`.
- Explicar la diferència entre Git i GitHub.
- Pujar el projecte a GitHub amb `git push`.

Si això ho tens clar, ja tens la base que necessites per començar a entregar projectes amb més ordre.

---

## Recursos recomanats

Per consultar mentre fas l'exercici:

- [GitHub Docs: About Git](https://docs.github.com/en/get-started/using-git/about-git)
- [Git documentation](https://git-scm.com/doc)
- [GitHub Docs: Get started](https://docs.github.com/en/get-started)
- [Markdown basic syntax](https://www.markdownguide.org/basic-syntax/)
- [Conventional Commits](https://www.conventionalcommits.org/)

Per ampliar quan vulguis entendre Git amb més profunditat:

- [Pro Git](https://git-scm.com/book/en/v2), llibre de referència gratuït
- [The Missing Semester: Version Control and Git](https://missing.csail.mit.edu/2026/version-control/), classe amb materials i vídeo
