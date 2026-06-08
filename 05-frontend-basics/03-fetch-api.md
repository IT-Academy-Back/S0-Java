# Frontend Basics 3: Fetch i API

En aquesta activitat substituiràs les dades locals per dades que venen d'una API real de proves.

Fins ara el frontend inventava les dades dins d'un array. Ara les demanarà a un servidor, rebrà una response en JSON i la pintarà al DOM.

> **Nota:** `fetch`, JSON, API, request, response... si tot et sona nou, és normal. Aquí només en faràs un tast pràctic. Durant el curs veuràs com es fan peticions HTTP, com es gestionen errors i com s'organitza tot en una aplicació real.

---

## Objectius

En acabar aquesta activitat hauràs practicat:

- Fer una request HTTP amb [`fetch`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).
- Llegir una response JSON.
- Pintar dades rebudes d'una API.
- Mostrar un loading state (estat de càrrega).
- Mostrar un error state (estat d'error).
- Veure la request i la response a DevTools.

---

## Vocabulari mínim

- **API** (Application Programming Interface): contracte que permet que dues parts d'un sistema es comuniquin.
- **Endpoint** (ruta concreta d'una API): URL a la qual fas una request, per exemple `/users`.
- **Request** (petició): missatge que el navegador envia al servidor.
- **Response** (resposta): missatge que el servidor retorna al navegador.
- **JSON** (JavaScript Object Notation): format de text molt habitual per intercanviar dades.
- **Fetch**: funció de JavaScript per fer requests HTTP des del navegador.

---

## API que farem servir

Farem servir [JSONPlaceholder](https://jsonplaceholder.typicode.com/), una API pública de proves pensada per practicar.

En concret, demanarem usuaris a aquest endpoint:

```text
https://jsonplaceholder.typicode.com/users
```

Si obres l'enllaç al navegador, veuràs una llista d'usuaris en JSON.

> **Important:** Aquesta API és externa i de proves. No cal crear cap backend propi per fer aquesta activitat.

---

## Què és fetch

`fetch` és una funció de JavaScript que permet fer requests HTTP des del navegador.

Exemple:

```js
fetch('https://jsonplaceholder.typicode.com/users')
  .then((response) => response.json())
  .then((users) => renderUsers(users))
```

També pots fer-ho amb `async/await`, que acostuma a ser més llegible quan el codi creix:

```js
async function loadUsers() {
  const response = await fetch('https://jsonplaceholder.typicode.com/users')
  const users = await response.json()
  renderUsers(users)
}
```

---

## Exercici

Transforma l'activitat anterior perquè les cards es pintin amb dades rebudes d'una API.

En aquesta tercera activitat pots canviar de **Pet Cards** a **User Cards**. El més important no és el tema visual, sinó entendre el flux:

```text
frontend -> fetch -> API -> JSON -> render al DOM
```

Has de:

- Crear una funció `loadUsers()`.
- Fer `fetch` a `https://jsonplaceholder.typicode.com/users`.
- Transformar la response a JSON.
- Cridar `renderUsers(users)`.
- Mostrar un missatge mentre carreguen les dades.
- Mostrar un missatge si hi ha error.
- Pintar com a mínim el nom, email, ciutat i empresa de cada usuari.

---

## Guia de treball

Pots començar amb aquesta estructura:

```js
const userList = document.querySelector('#user-list')

async function loadUsers() {
  try {
    userList.innerHTML = '<p>Carregant usuaris...</p>'

    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    const users = await response.json()

    renderUsers(users)
  } catch (error) {
    userList.innerHTML = '<p>No s\'han pogut carregar els usuaris.</p>'
  }
}

function renderUsers(users) {
  userList.innerHTML = ''

  users.forEach((user) => {
    userList.innerHTML += `
      <article class="user-card">
        <h2>${user.name}</h2>
        <p>${user.email}</p>
        <p>${user.address.city}</p>
        <p>${user.company.name}</p>
      </article>
    `
  })
}

loadUsers()
```

---

## Requisits mínims

- Les dades ja no poden venir d'un array local.
- Has de fer servir `fetch`.
- Has de pintar les dades rebudes al DOM.
- Has de mostrar un loading state.
- Has de mostrar un error state.
- Has de comprovar la request i la response a DevTools.

---

## Com veure la request a DevTools

1. Obre el navegador.
2. Obre DevTools.
3. Ves a **Network**.
4. Recarrega la pàgina.
5. Busca la request a `jsonplaceholder.typicode.com/users`.
6. Obre **Headers** i comprova el mètode `GET` i el status code.
7. Obre **Preview** per veure el JSON de forma més llegible.
8. Obre **Response** per veure la resposta exacta del servidor.

A Chrome pots consultar la guia [Inspect network activity](https://developer.chrome.com/docs/devtools/network).

---

## Nivell 2

Afegeix una vista de detall:

- Quan cliquis una card, mostra més informació de l'usuari.
- Pots mostrar el telèfon, la web o l'adreça completa.
- No cal fer una segona request encara; pots reutilitzar les dades ja rebudes.

---

## Nivell 3

Millora l'experiència:

- Mostra un missatge si l'array torna buit.
- Desactiva botons mentre carreguen dades.
- Afegeix un petit feedback visual quan les cards s'han carregat correctament.
- Afegeix un cercador per filtrar usuaris pel nom o per ciutat.

---

## Error habitual: fetch no vol dir que tot hagi anat bé

Si el servidor retorna un error HTTP, `fetch` pot no entrar directament al `catch`. Per això, en projectes reals és habitual comprovar `response.ok`.

Exemple:

```js
const response = await fetch('https://jsonplaceholder.typicode.com/users')

if (!response.ok) {
  throw new Error('La request ha fallat')
}

const users = await response.json()
```

No cal que dominis això ara, però és bo que et comenci a sonar.

---

## Recursos recomanats

Per fer aquesta activitat:

- [MDN: Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN: Using fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [MDN: JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON)
- [Chrome DevTools: Network](https://developer.chrome.com/docs/devtools/network)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com/)

Per ampliar quan vulguis entendre millor què passa per sota:

- [MDN: Overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)
- [MDN: Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS)
