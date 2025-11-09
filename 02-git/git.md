# 📘 Introducció a Git i GitHub

---

> **⚠️ Fes servir un terminal compatible amb Bash**
>  
>  Per seguir les instruccions correctament, cal que utilitzis un **terminal compatible amb Bash**, on totes les comandes d’aquest exercici funcionaran tal com estan escrites.
>  
>  **Segons el teu sistema operatiu:**
>  
>  ✅ **macOS** i **Linux**: pots utilitzar el terminal que ja ve instal·lat.
>  
>  ✅ **Windows**: Pots fer servir **[Git Bash](https://git-scm.com/downloads)** (s’instal·la juntament amb Git).
>  O bé, si ja tens configurat el **WSL (Windows Subsystem for Linux)**, pots obrir la distribució de Linux i treballar-hi.
>  
>⚠️ **No facis servir Command Prompt o PowerShell**, ja que algunes comandes (com `touch`, `ssh-keygen`, etc.) podrien no funcionar o comportar-se de manera diferent.



---

## 🧭 Introducció

En aquest exercici t'endinsaràs en l’ús de **[Git](https://git-scm.com/) i [GitHub](https://github.com/)**, dues eines essencials per a qualsevol desenvolupador/a. Aprendràs a portar el control dels canvis del teu projecte, a col·laborar de forma ordenada i a documentar-lo seguint bones pràctiques.

L’objectiu és que siguis capaç de:

- Fer un seguiment clar i fiable dels canvis (traçabilitat).
- Treballar de manera professional amb versions i branques.
- Entendre com es connecta un projecte local amb un repositori remot.
- Crear un `README.md` complet i ben estructurat.

Tot plegat t’ajudarà a establir els fonaments per col·laborar en projectes reals i a presentar millor el teu treball com a desenvolupador/a.

---

## 🗂 Estructura de l’exercici

Per cada bloc, trobaràs:

- 🧠 **Què has d’entendre**
- 🛠️ **Què has de fer**

---

### 1. Instal·lació i configuració de Git

🧠 Git necessita saber qui ets per enregistrar els canvis correctament. El primer que hem de fer és instalarlo i configurarlo.

🛠️ Mira si ja tens git instalat:

```bash
git --version
```

Per instal·lar-lo:

- **Windows**: https://git-scm.com/download/win
- **macOS**: `brew install git`
- **Linux**: `sudo apt install git`

Configura’l:

```bash
git config --global user.name "El teu nom"
git config --global user.email "el.teu@email.com"
```

---

### 2. Git vs GitHub

🧠 Entén la diferència entre:

- **Git** = eina local per controlar versions.
- **GitHub** = plataforma online per compartir i col·laborar.

🛠️ Escriu una definició pròpia de cadascun. Guardala per després afegirla al teu `README.md`. 

---

### 3. Crear el projecte i inicialitzar Git

🧠 Abans de començar a treballar amb Git, cal **crear una carpeta nova** per al teu projecte i **inicialitzar-hi un repositori Git**. Això vol dir que Git començarà a controlar els fitxers i els canvis que hi facis dins d’aquesta carpeta. També aprendràs a crear el teu primer fitxer: el `README.md`, que és el punt de partida de la documentació de qualsevol projecte.

🛠️ Passos:

1. Crea una carpeta nova per al projecte:
   ```bash
   mkdir readme-project
   ```
   Això crea una carpeta anomenada `readme-project`.

2. Entra dins la carpeta:
   ```bash
   cd readme-project
   ```

3. Inicialitza un repositori Git dins d’aquesta carpeta:
   ```bash
   git init
   ```
   Aquesta comanda configura Git perquè comenci a fer el seguiment dels fitxers que afegiràs. Es crearà una carpeta oculta .git pots comprobar que existeix dent ls -a per exemple

4. Crea un fitxer anomenat `README.md`:
   ```bash
   touch README.md
   ```

5. Obre el fitxer `README.md` en el teu editor de text o codi i escriu-hi un títol utilitzant la sintaxi de [Markdown](https://www.markdownguide.org/basic-syntax/). Per exemple:
   ```markdown
   # Projecte fictici de documentació amb Git i GitHub
   ```

ℹ️ Pots consultar la sintaxi bàsica de Markdown aquí: [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)

---

### 4. Estats dels fitxers i primer commit

🧠 Quan treballes amb Git, cada fitxer pot estar en un d’aquests **tres estats**:

1. **Modificat (modified)**: Has fet canvis al fitxer, però Git encara no els té en compte.
2. **Afegit (staged)**: Li has dit a Git que vols incloure aquests canvis en el proper "snapshot".
3. **Confirmat (committed)**: Els canvis ja formen part de l’historial del projecte.

Aquesta separació permet tenir control total sobre **què s’enregistra** i **quan**.

🛠️ Fem el primer commit del teu `README.md`:

1. Comprova l'estat del projecte:
   ```bash
   git status
   ```
   Això et mostrarà els fitxers que han canviat i en quin estat estan. Just després de crear `README.md`, apareixerà com a "Untracked" (no seguit).

2. Afegeix el fitxer `README.md` a la zona d'stage:
   ```bash
   git add README.md
   ```
   Ara el fitxer està **preparat** per ser confirmat.

3. Fes el primer **commit** amb un missatge clar:
   ```bash
   git commit -m "docs: create initial README"
   ```
   Ara Git ha registrat aquest canvi com un punt de control dins de l’historial del projecte.

💡 El prefix `docs:` segueix l’estil **[Conventional Commits](https://www.conventionalcommits.org/)** i indica que estàs treballant en documentació.

A partir d’aquí, qualsevol canvi que facis al projecte seguirà aquest cicle: **modificar → afegir → confirmar**.


---

### 5. Comandes d’inspecció

🧠 Un dels punts forts de Git és que et permet **consultar els canvis** que has fet i **navegar per l’historial** del projecte. Això és clau per entendre l’evolució del teu treball i identificar possibles errors.

Amb Git pots:

- Veure què ha canviat abans de confirmar (`git diff`)
- Consultar quins fitxers estan preparats (`git status`)
- Revisar l’historial de commits (`git log`)

🛠️ Posa-ho en pràctica:

1. Fes un canvi al `README.md`. Per exemple, afegeix una línia com:
   ```markdown
   Aquest projecte serveix per aprendre Git pas a pas.
   ```

2. Abans d’afegir el fitxer, consulta què ha canviat amb:
   ```bash
   git diff
   ```
   Veuràs en vermell el contingut eliminat (si n’hi ha) i en verd el que s’ha afegit. Encara no has fet cap commit nou: estàs **inspeccionant els canvis locals**.

3. Afegeix el fitxer i confirma el canvi:
   ```bash
   git add README.md
   git commit -m "docs: add project description"
   ```

4. Ara consulta l’historial de commits:
   ```bash
   git log
   ```
   Veuràs una llista cronològica amb els missatges dels commits, l’autor i l'identificador únic (hash). Pots recórrer l’historial amb les fletxes i sortir amb la tecla `q`.

5. Afegeix una nova secció al final del teu `README.md` com a pràctica:
   ```markdown
   ## Objectiu del projecte

   Practicar Git i GitHub creant un README ben estructurat i aplicant bones pràctiques de versionat.
   ```

6. I finalment, fes un commit per registrar aquest canvi:
   ```bash
   git add README.md
   git commit -m "docs: add project goal section"
   ```

🎯 Ara ja tens una visió clara de com veure **què has fet**, **quan** i **per què**. Aquestes comandes seran les teves aliades a llarg termini.


---

### 6. Bones pràctiques de commits

🧠 Un bon commit és clar, específic i estructurat.

🛠️ Fes dos commits amb l’estil *conventional commits*:

```bash
git commit -m "docs: add technologies section"
git commit -m "docs: fix typo in description"
```

---

### 7. Connexió a GitHub

🧠 Per poder pujar el teu projecte des del teu ordinador a GitHub, cal establir una connexió entre el teu repositori local i el repositori remot que ara crearem a [https://github.com](https://github.com). Aquesta connexió permet fer comandes com `git push` (pujar canvis) i `git pull` (baixar-los).

---

#### 🔗 Documentació recomanada

- [GitHub: Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [GitHub: Adding a new SSH key to your account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [GitHub: Pushing your first commit](https://docs.github.com/en/get-started/quickstart/create-a-repo#push-an-existing-repository-from-the-command-line)

---

#### 🛠️ Passos per connectar el teu projecte amb GitHub

 **1️⃣ Crea un repositori remot a GitHub**

- Ves a [https://github.com](https://github.com)
- Crea un repositori nou anomenat `readme-project`
- ⚠️ **No afegeixis cap fitxer extra** (ni README, `.gitignore`, etc.)

---

**2️⃣ Afegeix el repositori remot**

GitHub et mostrarà un bloc que diu:

> …or push an existing repository from the command line

I et dona aquestes comandes:

```bash
git remote add origin git@github.com:el_teu_usuari/readme-project.git
git branch -M main
git push -u origin main
```

📝 **Què fa cada comanda?**

- `git remote add origin ...` → Enllaça el repositori local amb el remot de GitHub.
- `git branch -M main` → Assegura que la branca principal es diu `main`. (Només cal si no existia o té un altre nom).
- `git push -u origin main` → Puja el contingut al repositori remot i recorda quina és la branca remota per defecte.

Executa les comandes desde l'arrel del teu projecte.

---

**3️⃣ Comprova que funciona**

Després d'executar aquestes comandes, entra a GitHub i comprova que el fitxer `README.md` ja apareix al repositori remot.

---

#### 🧩 Si GitHub et demana configurar una clau SSH

És possible que GitHub et demani **autenticació SSH** (especialment si treballes amb l’enllaç que comença amb `git@github.com:`).

📣 **Pots demanar ajuda a una IA generativa**, com ara:

> 🔍 *"Com genero i afegeixo una clau SSH per GitHub a Windows/macOS/Linux?"*

També pots seguir aquestes passes mínimes:

```bash
ssh-keygen -t ed25519 -C "el.teu@email.com"
cat ~/.ssh/id_ed25519.pub
```

Després, ves a [https://github.com/settings/keys](https://github.com/settings/keys), clica "New SSH key", i enganxa-hi la clau pública.

---

### 8. Sincronització: `push` i `pull`

🧠 Quan treballes amb Git i GitHub, sovint necessitaràs **sincronitzar** els canvis entre el teu ordinador i el repositori remot (a GitHub):

- 🔼 `git push` = envia els canvis del teu ordinador cap a GitHub.
- 🔽 `git pull` = descarrega els canvis des de GitHub cap al teu ordinador.

Això et permet treballar des de diferents ordinadors, col·laborar amb altres persones o recuperar canvis que hagis fet directament des de la web de GitHub.

---

🛠️ Posa-ho en pràctica:

1. Fes un petit canvi local al fitxer `README.md`. Per exemple, afegeix una línia nova com:

   ```markdown
   Aquesta línia s’ha afegit des del meu ordinador.
   ```

2. Desa els canvis, afegeix-los i confirma’ls:

   ```bash
   git add README.md
   git commit -m "docs: update README with local note"
   ```

3. Envia els canvis a GitHub amb:

   ```bash
   git push
   ```

4. Ara ves al teu repositori **a través del navegador** i edita el `README.md` directament des de la interfície web de GitHub. Per exemple, afegeix una línia com:

   ```markdown
   Aquesta línia s’ha afegit des de GitHub.
   ```

5. Torna al terminal i descarrega els canvis amb:

   ```bash
   git pull
   ```

   Així tindràs **tots els canvis sincronitzats** tant localment com remotament.

---

💡 **Important:** Si edites el mateix lloc del fitxer localment i a GitHub abans de fer `pull`, podries provocar un **conflicte**, que hauràs de resoldre manualment. En aquest exercici no busquem provocar-ne, però és bo saber que pot passar.

---

### 9. Branques i fusió (`merge`)

🧠 Git permet crear **branques** per treballar en funcionalitats o canvis de manera aïllada, sense afectar la branca principal (`main`). Un cop acabat el treball, es poden **fusionar** (merge) els canvis.

---

🛠️ Posa-ho en pràctica:

1. Crea una nova branca per afegir una secció d’instal·lació:

   ```bash
   git checkout -b feature/install-section
   ```

2. Afegeix al fitxer `README.md` la secció:

   ```markdown
   ## Instal·lació
   ```

3. Desa, afegeix i confirma els canvis:

   ```bash
   git add .
   git commit -m "docs: add install section"
   ```

4. Torna a la branca principal i integra els canvis:

   ```bash
   git checkout main
   git merge feature/install-section
   ```

5. Puja-ho a GitHub:

   ```bash
   git push
   ```

---

💡 **Recomanació:** Posa noms descriptius a les branques (`feature/`, `fix/`, `docs/`, etc.) per mantenir l’ordre i facilitar la col·laboració.

---

### 10. Conflictes de fusió

🧠 Un **conflicte de fusió** passa quan dues branques han modificat la mateixa línia d’un fitxer. Git no pot decidir quina versió mantenir i et demana que ho resolguis manualment.

---

🛠️ Simula un conflicte:

1. Crea dues branques des de `main`:

   ```bash
   git checkout -b feature/afegir-frase-1
   ```

   Afegeix al `README.md`:

   ```markdown
   Aquesta frase és de la branca 1.
   ```

   Fes commit i torna a `main`.

   ```bash
   git add .
   git commit -m "docs: afegeix frase 1"
   git checkout main
   ```

2. Crea l’altra branca:

   ```bash
   git checkout -b feature/afegir-frase-2
   ```

   Afegeix **una altra frase a la mateixa línia** del `README.md`:

   ```markdown
   Aquesta frase és de la branca 2.
   ```

   Fes commit, torna a `main` i intenta fer `merge` de les dues:

   ```bash
   git checkout main
   git merge feature/afegir-frase-2
   ```

3. Git mostrarà un **conflicte**. Obre el fitxer i resol manualment el que vols conservar. Exemple de frase resolta:

   ```markdown
   > 🔧 Conflicte resolt manualment entre dues branques.
   ```

4. Un cop resolt, marca el fitxer com a resolt i fes commit:

   ```bash
   git add README.md
   git commit -m "fix: resol conflicte entre frases"
   ```

---

💡 Els conflictes són normals en projectes col·laboratius. És important **entendre què ha passat** i **resoldre’ls amb calma**.

---

### 11. Clonar un repositori

🧠 *Clonar* un repositori vol dir descarregar-ne una còpia completa al teu ordinador per començar a treballar localment amb tot l’historial de Git.

---

🛠️ Afegeix aquesta secció al teu `README.md`:

```markdown
## Clonació del projecte

Per clonar aquest repositori al teu ordinador:
````
```bash
git clone git@github.com:el_teu_usuari/readme-project.git
```

> Substitueix `el_teu_usuari` pel teu nom d’usuari real de GitHub.

💡 També pots fer servir HTTPS si no tens SSH configurat:

```bash
git clone https://github.com/el_teu_usuari/readme-project.git
```

---

### 12. Fork i pull request

🧠 Un *fork* crea una còpia d’un repositori al teu GitHub personal. Serveix per treballar de manera independent en projectes on no tens accés directe.  
Un *pull request* (PR) és una sol·licitud per integrar els teus canvis al repositori original.

---

🛠️ Afegeix aquesta secció al teu `README.md` per explicar com contribuir:

````markdown
## Contribució al projecte

T’animes a col·laborar? Segueix aquests passos:

1. Fes un *fork* d’aquest repositori (botó a dalt a la dreta a GitHub).
2. Clona el teu fork:
```
```bash
git clone git@github.com:el_teu_usuari/readme-project.git
```

3. Crea una nova branca:

```bash
git checkout -b feature/nova-seccio
```

4. Fes els teus canvis, confirma'ls i puja la branca:

```bash
git add .
git commit -m "feat: afegeix nova secció"
git push -u origin feature/nova-seccio
```

5. A GitHub, obre un *pull request* des de la teva branca cap a la branca `main` del repositori original.
````

---

💡 **Recorda:** El control de versions i la col·laboració són habilitats fonamentals per treballar en equip. Aprendre Git i GitHub et prepara per contribuir a projectes professionals o de codi obert amb confiança.

