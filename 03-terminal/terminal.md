# 🧪 Introducció al terminal Bash 

En aquest exercici aprendràs les ordres bàsiques de Bash: navegar pel sistema de fitxers, crear i gestionar fitxers i carpetes, consultar contingut, fer cerques i executar scripts simples. **És compatible amb Linux, macOS i també amb Windows utilitzant [Git Bash](https://git-scm.com/downloads).**

⚠️ **No cal instal·lar WSL** per fer aquest exercici. Si estàs en Windows, descarrega i obre **Git Bash**, que ofereix un entorn Bash complet.

---

## 📁 1. Crear l'espai de treball

```bash
# mkdir = "make directory" → crea una carpeta
mkdir terminal-practice

# cd = "change directory" → entra dins la carpeta
cd terminal-practice

# ls = "list" → mostra els fitxers i carpetes del directori actual
ls
```

---

## 📄 2. Crear fitxers i carpetes

```bash
# touch = crea fitxers buits
touch fitxer1.txt fitxer2.txt fitxer3.txt

# mkdir = crea una carpeta
mkdir carpetaA

# ls -l = mostra els fitxers en format llista detallada (long listing)
ls -l
```

---

## 📝 3. Escriure i llegir fitxers

```bash
# echo = escriu text a la sortida
# > = redirecciona la sortida a un fitxer (sobreescriu)
echo "Hola món!" > fitxer1.txt

# >> = afegeix text al final d’un fitxer (sense sobreescriure)
echo "Aquesta és una segona línia." >> fitxer1.txt

# cat = "concatenate" → mostra el contingut del fitxer
cat fitxer1.txt

# grep = "global regular expression print" → cerca línies amb una paraula
grep "Hola" fitxer1.txt

# head = mostra les primeres línies (per defecte 10, amb -n pots definir quantes)
head -n 1 fitxer1.txt

# sort = ordena alfabèticament les línies d’un fitxer
sort fitxer1.txt
```

---

## 🔄 4. Copiar, moure i eliminar fitxers

```bash
# cp = "copy" → copia fitxers
cp fitxer1.txt carpetaA/

# mv = "move" → mou o reanomena fitxers
mv fitxer2.txt carpetaA/renombrat.txt

# rm = "remove" → esborra fitxers
rm fitxer3.txt

# ls -l = comprovar estat actual del directori
ls -l
```

---

## 📋 5. Consulta i verificació

```bash
# ls -l = tornar a llistar els fitxers i carpetes
ls -l

# ls -l carpetaA = veure el contingut i detalls dins la carpetaA
ls -l carpetaA/
```

---

## 🧹 6. Netejar l’exercici

```bash
# cd .. = pujar un nivell al sistema de fitxers (anar a la carpeta anterior)
cd ..

# rm -rf = "remove recursively and force" → elimina tot el directori i el seu contingut
rm -rf terminal-practice
```

---

