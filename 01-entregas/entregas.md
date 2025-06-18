# Manual de Bones Pràctiques per a Lliuraments de Projectes  
*(Per a estudiants de desenvolupament Back-end i Front-end)*

---

## 📌 Introducció

Aquest manual unifica els criteris essencials per fer lliuraments professionals de projectes, combinant:

✅ Bones pràctiques tècniques (codi net, estructura)  
✅ Gestió professional (Git, documentació)
✅ Estàndards de qualitat (principis SOLID/KISS/DRY)

---

## 🔧 1. Configuració del Repositori

### 1.1 Estructura Bàsica


```plaintext
projecte/
├── src/                  # Codi font
├── tests/                # Proves automàtiques  
├── .gitignore            # Fitxers exclosos  
└── README.md             # Documentació principal
```

    🧠 Mantingues una organització clara en carpetes i fitxers
    
    🧠 Fes servir noms en minúscules i sense espais
---
### 1.2 Normes GitHub

- **Noms dels repositoris**: Descriptius i en anglès (ex. `task-manager`, no `projecte1`).
- **Commits**: Atòmics i amb missatges clars, seguint la convenció *Conventional Commits*:

```bash
git commit -m "feat: add user authentication"
git commit -m "fix: resolve login timeout error"
```
      🧠 Branques: Fer servir Gitflow (main, develop, feature/xxx).

## 💻 2. Qualitat del Codi

### 2.1 Principis Fonamentals

| Principi | Descripció                                  |
|----------|---------------------------------------------|
| KISS     | Mantingues el codi senzill i llegible       |
| DRY      | No repeteixis codi. Fes servir mòduls       |
| SOLID    | (Back-end) Disseny OOP amb bones pràctiques |

     🧠 Utilitza patrons com _early return_ o _fail fast_ quan sigui necessari

---

### 2.2 Estil i Convencions

**General**  

✅ Tenir el codi ben formatat, respectant correctament els espais, els salts de línia i la indentació per garantir-ne la llegibilitat.  
✅ Escriure comentaris breus i clars només quan siguin necessaris. 

     🧠 El codi ha de ser **comprensible a primera vista**
     🧠 Programa en anglès.
---

💬 **Nomenclatura**  

✅ Seguir les convencions de nomenclatura.  
✅ Fer servir noms descriptius per a classes, mètodes i variables.  
✅ Els noms dels mètodes sempre s'escriuen amb verbs infinitius.  
✅ Evitar abreviatures poc clares o noms genèrics. 

     🧠 El nom del mètode o funció ha de deixar clar quin és el seu propòsit
---

🩹 **Mètodes Curts amb Única Responsabilitat**

✅ Verificar que els mètodes i classes siguin concisos i no facin massa coses.  
✅ Aplicar el principi de responsabilitat única per millorar llegibilitat i manteniment.  
✅ Considerar dividir mètodes complexos en altres més específics quan calgui.  


     🧠 Evita el codi espagueti.  
---

### 2.3 Criteris Tècnics

📜 **Compliment de requirements** 

✅ Verificar que la solució compleix tots els requisits especificats.  
✅ Cal assegurar que les funcionalitats obligatòries estan implementades correctament.


     🧠 Prova el teu codi sense seguir el camí feliç (*happy path*)
---

🖇️ **Control de la Complexitat**  

✅ Reduir condicionals i bucles imbricats innecessaris.  
✅ Evitar l'ús de variables temporals o `flags` que compliquin el flux.  
✅ Comprovar que totes les opcions dins de les condicions són realistes.  
✅ No utilitzar valors màgics

---

🦾 **Robustesa i Gestió d'Errors**  

✅ Gestiona de forma explícita les excepcions previsibles.  
✅ Evita capturar errors de manera genèrica.


     🧠 Registra els errors de manera que ajudin al diagnòstic però sense exposar informació sensible
     🧠 Mostra missatges d’error clars i útils per a l’usuari, sense detalls interns del sistema
---
🔒 **Codi segur**  

✅ No confiïs mai en l’input de l’usuari: valida les dades.  
✅ Evita biblioteques no mantingudes o amb pocs usuaris.  
✅ No mostris missatges d’error detallats a l’usuari final.  
✅ El codi només han de tenir accés als recursos estrictament necessaris.  


     🧠  Els errors interns han d’anar a logs segurs.  
___

## 📄 3. Documentació

### 3.1 README.md (Obligatori)
Ha d'incloure:
```html
# Nom del Projecte  
**Descripció**: Breu explicació de l'objectiu.  

## 📌 Enunciat del exercici

## 🛠 Tecnologies  
- Frontend: React, Tailwind  
- Backend: Java, MySQL, MongoDB  

## 🚀 Instal·lació  
1. Clonar el repositori: `git clone ...`  
2. Instal·lar dependències: `npm install`  
3. Variables d'entorn: Crear `.env` amb...  

## 📸 Demo  
[Enllaç a Vercel/Netlify] o captures de pantalla. (si és aplicable)

```
