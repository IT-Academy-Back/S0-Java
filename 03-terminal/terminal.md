# Introducció al terminal, Linux i Bash

El terminal és una eina bàsica de desenvolupament. El faràs servir per moure't per carpetes, executar projectes, treballar amb Git, instal·lar dependències, llegir errors i automatitzar tasques.

No cal que dominis [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) (una shell molt utilitzada en entorns Unix i Linux) a fons en aquest sprint. L'objectiu és que entenguis què estàs fent quan escrius una comanda i que puguis moure't per un projecte sense dependre sempre de la interfície gràfica.

Aquest bloc funciona a Linux, macOS i Windows amb [Git Bash](https://git-scm.com/downloads). Si estàs a Windows, no cal instal·lar WSL per fer aquesta pràctica.

---

## Objectius

En acabar aquest bloc hauries de poder:

- Explicar què són el terminal, la shell i Bash.
- Entendre per què molts entorns de desenvolupament fan servir comandes d'estil Linux.
- Saber en quina carpeta estàs amb `pwd`.
- Veure el contingut d'una carpeta amb `ls`.
- Entrar i sortir de carpetes amb `cd`.
- Distingir entre rutes relatives i rutes absolutes.
- Crear carpetes i fitxers.
- Llegir contingut d'un fitxer.
- Copiar, moure i eliminar fitxers amb cura.
- Entendre per què aquestes comandes et serviran durant el curs.

---

## Terminal, shell i Bash

Quan obres el terminal, veus una finestra on pots escriure comandes. Però hi ha tres idees diferents que convé separar:

| Concepte | Què és |
|----------|--------|
| **Terminal** | La finestra o aplicació on escrius comandes. |
| **Shell** | El programa que interpreta les comandes i les envia al sistema operatiu. |
| **Bash** | Una shell molt utilitzada en entorns Linux i en moltes eines de desenvolupament. |

Una manera simple de veure-ho:

```text
tu escrius una comanda -> la shell la interpreta -> el sistema operatiu l'executa
```

Exemple:

```bash
ls
```

Quan escrius `ls`, Bash interpreta que vols llistar el contingut de la carpeta actual i demana al sistema operatiu que ho faci.

---

## Per què parlem de Linux

[Linux](https://documentation.ubuntu.com/desktop/en/latest/tutorial/the-linux-command-line-for-beginners/) és una família de sistemes operatius molt utilitzada en servidors, contenidors Docker, cloud, eines de desenvolupament i entorns backend.

Encara que treballis amb macOS o Windows, moltes eines que faràs servir durant el curs segueixen convencions de Linux:

- comandes com `pwd`, `ls`, `cd`, `mkdir`, `rm` o `cat`,
- rutes separades amb `/`,
- scripts d'execució,
- contenidors Docker,
- servidors remots,
- pipelines d'automatització.

macOS ja inclou una shell compatible amb aquest estil de treball. Windows pot fer servir Git Bash per practicar les mateixes comandes bàsiques.

No necessites instal·lar Linux ara. Necessites entendre el vocabulari i les comandes mínimes perquè Git, Docker, Maven o qualsevol eina de backend no et semblin una caixa negra.

---

## Com llegir una comanda

Una comanda acostuma a tenir aquesta forma:

```text
comanda opcions arguments
```

Exemple:

```bash
ls -l carpetaA
```

Què vol dir cada part:

| Part | Exemple | Significat |
|------|---------|------------|
| Comanda | `ls` | Acció que vols executar. |
| Opció | `-l` | Modifica com s'executa la comanda. |
| Argument | `carpetaA` | Indica sobre què actua la comanda. |

No totes les comandes tenen opcions o arguments.

```bash
pwd
```

Aquesta comanda només mostra on ets.

---

## El filesystem: carpetes, fitxers i rutes

El terminal sempre treballa des d'una carpeta concreta. Aquesta carpeta és el teu **directori actual**.

Els projectes s'organitzen com un arbre de carpetes i fitxers:

```text
projecte/
|-- README.md
|-- src/
|   |-- Main.java
|-- tests/
```

Una **ruta** indica on és un fitxer o carpeta.

Hi ha dos tipus de rutes que veuràs constantment:

| Tipus | Exemple | Què vol dir |
|-------|---------|-------------|
| Ruta absoluta | `/Users/anna/projectes/app` | Ruta completa des de l'arrel del sistema. |
| Ruta relativa | `src/Main.java` | Ruta calculada des de la carpeta on ets ara. |

Alguns símbols importants:

| Símbol | Significat |
|--------|------------|
| `.` | Carpeta actual. |
| `..` | Carpeta pare, un nivell enrere. |
| `/` | Separador de carpetes en rutes d'estil Linux. |
| `~` | Carpeta personal de l'usuari. |

Exemples:

```bash
cd ..
cd ~/projectes
cd ./src
```

---

## Hàbits bàsics abans de practicar

Abans de començar amb comandes que creen o eliminen fitxers, tingues presents aquests hàbits:

- Escriu les comandes en minúscules. En sistemes d'estil Linux, `pwd` i `PWD` no són el mateix.
- Fes servir la tecla `Tab` per autocompletar noms de carpetes i fitxers.
- Fes servir les fletxes amunt i avall per recuperar comandes anteriors.
- Si una comanda queda oberta o t'has equivocat, prova `Ctrl+C` per cancel·lar-la.
- Evita espais en noms de carpetes i fitxers quan treballis amb terminal. Si n'hi ha, hauràs d'utilitzar cometes, per exemple `cd "la meva carpeta"`.
- No copiïs comandes amb `sudo` si no entens què fan. `sudo` executa una comanda amb permisos d'administrador i pot modificar parts sensibles del sistema.

Aquest sprint no busca que memoritzis moltes comandes. Busca que agafis el costum de mirar on ets, llegir què fa una comanda i no executar-la a cegues.

---

## Abans de començar: situa't

Quan obres el terminal, el primer que has de saber és on ets. Molts errors passen perquè executes una comanda des d'una carpeta equivocada.

Fes servir:

```bash
pwd
```

`pwd` vol dir `print working directory` i mostra la ruta de la carpeta actual.

Després mira què hi ha dins d'aquesta carpeta (list):

```bash
ls
```

La idea bàsica és aquesta:

```text
pwd -> on soc?
ls  -> què hi ha aquí?
cd  -> on vull anar? (change directory)
```

Aquest patró et servirà constantment quan treballis amb projectes reals.

---

## 1. Crear l'espai de treball

Ara crea una carpeta només per practicar:

```bash
mkdir terminal-practice -> (make directory)
cd terminal-practice
pwd
ls
```

Què fa cada comanda:

- `mkdir terminal-practice` crea una carpeta nova.
- `cd terminal-practice` cambia al dierectori dins la carpeta.
- `pwd` comprova on ets.
- `ls` mostra el contingut de la carpeta actual.

Com que acabes de crear la carpeta, és normal que `ls` no mostri res.

---

## 2. Crear fitxers i carpetes

Crea alguns fitxers buits i una carpeta:

```bash
touch fitxer1.txt fitxer2.txt fitxer3.txt
mkdir carpetaA
ls
```

Si vols veure més informació, pots fer servir:

```bash
ls -l
```

`ls -l` mostra el contingut en format llista, amb permisos, propietari, mida i data de modificació.

També pots mostrar fitxers ocults:

```bash
ls -a
```

Els fitxers ocults solen començar amb un punt, com `.gitignore` o `.env`.

---

## 3. Escriure i llegir fitxers

Pots escriure text dins d'un fitxer des del terminal:

```bash
echo "Hola món" > fitxer1.txt
```

El símbol `>` escriu el contingut al fitxer. Si el fitxer ja tenia contingut, el substitueix.

Per afegir una línia sense esborrar el contingut anterior, fes servir `>>`:

```bash
echo "Aquesta és una segona línia." >> fitxer1.txt
```

Ara llegeix el contingut:

```bash
cat fitxer1.txt
```

Altres comandes útils per consultar contingut:

```bash
grep "Hola" fitxer1.txt
head -n 1 fitxer1.txt
sort fitxer1.txt
```

Què fan:

- `grep "Hola" fitxer1.txt` busca línies que contenen la paraula `Hola`.
- `head -n 1 fitxer1.txt` mostra només la primera línia.
- `sort fitxer1.txt` ordena les línies alfabèticament.

No cal memoritzar-les totes ara. L'important és entendre que el terminal també serveix per inspeccionar fitxers.

---

## 4. Copiar, moure i eliminar fitxers

Practica amb aquestes comandes:

```bash
cp fitxer1.txt carpetaA/
mv fitxer2.txt carpetaA/reanomenat.txt
rm fitxer3.txt
ls -l
ls -l carpetaA/
```

Què fan:

- `cp fitxer1.txt carpetaA/` copia `fitxer1.txt` dins de `carpetaA`.
- `mv fitxer2.txt carpetaA/reanomenat.txt` mou i reanomena el fitxer.
- `rm fitxer3.txt` elimina el fitxer.
- `ls -l carpetaA/` mostra el contingut de `carpetaA`.

Ves amb cura amb `rm`: elimina fitxers. Abans d'esborrar, comprova sempre on ets amb `pwd` i què hi ha amb `ls`.

---

## 5. Tornar enrere i netejar l'exercici

Per sortir de la carpeta actual i tornar a la carpeta anterior:

```bash
cd ..
pwd
```

Quan hagis acabat, pots eliminar la carpeta de pràctica:

```bash
rm -rf terminal-practice
```

`rm -rf` elimina una carpeta i tot el seu contingut. Fes-la servir amb molta cura i només quan tinguis clar on ets.

Abans d'executar-la, comprova:

```bash
pwd
ls
```

---

## 6. Patrons que veuràs durant el curs

Moltes eines de desenvolupament es fan servir des del terminal. Ara potser només executes comandes simples, però aviat veuràs comandes com aquestes:

```bash
git status
git commit -m "docs: update README"
./mvnw test
docker compose up
npm install
```

No cal que les entenguis totes ara. El que sí has d'entendre és que cada comanda s'executa des d'una carpeta concreta i pot llegir, crear o modificar fitxers del projecte.

Abans d'executar una comanda nova, acostuma't a preguntar-te:

- En quina carpeta soc?
- Aquesta comanda llegeix informació o modifica fitxers?
- Necessito executar-la des de l'arrel del projecte?
- Si falla, quin missatge d'error m'està donant?

---

## Comandes bàsiques d'aquest bloc

| Comanda | Per a què serveix |
|---------|-------------------|
| `pwd` | Mostra la carpeta actual. |
| `ls` | Mostra el contingut d'una carpeta. |
| `ls -l` | Mostra el contingut amb més detall. |
| `ls -a` | Mostra també fitxers ocults. |
| `cd carpeta` | Entra dins d'una carpeta. |
| `cd ..` | Puja un nivell. |
| `cd ~` | Va a la carpeta personal de l'usuari. |
| `mkdir nom` | Crea una carpeta. |
| `touch fitxer.txt` | Crea un fitxer buit. |
| `echo "text" > fitxer.txt` | Escriu text en un fitxer i substitueix el contingut anterior. |
| `echo "text" >> fitxer.txt` | Afegeix text al final d'un fitxer. |
| `cat fitxer.txt` | Mostra el contingut d'un fitxer. |
| `grep "text" fitxer.txt` | Busca text dins d'un fitxer. |
| `cp origen desti` | Copia fitxers o carpetes. |
| `mv origen desti` | Mou o reanomena fitxers o carpetes. |
| `rm fitxer.txt` | Elimina un fitxer. |

---

## Què has de saber al final d'aquest bloc

Abans de continuar, comprova que pots:

- Obrir el terminal i saber en quina carpeta estàs.
- Explicar amb paraules simples què fa Bash.
- Entrar a una carpeta de projecte.
- Llistar fitxers visibles i ocults.
- Crear un fitxer o carpeta.
- Llegir un fitxer senzill.
- Moure o copiar un fitxer.
- Esborrar fitxers amb prudència.
- Entendre que Git, Docker, Maven i altres eines s'executen des del terminal.

No cal saber Bash avançat ara. Durant el curs faràs servir el terminal moltes vegades i aquestes comandes s'aniran fent familiars amb la pràctica.

---

## Recursos recomanats

Per repassar les comandes bàsiques:

- [Ubuntu: The Linux command line for beginners](https://documentation.ubuntu.com/desktop/en/latest/tutorial/the-linux-command-line-for-beginners/)
- [MDN: Command line crash course](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line)

Per ampliar o consultar exemples ràpids quan ja hagis practicat una mica:

- [The Missing Semester: Introduction to the Shell](https://missing.csail.mit.edu/2020/course-shell/), classe amb materials i vídeo
- [tldr pages](https://tldr.sh/), exemples curts de comandes de terminal
