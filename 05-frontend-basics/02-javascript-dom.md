# Frontend Basics 2: JavaScript i DOM

Ara que ja tens una pàgina estàtica, faràs que la pàgina reaccioni amb JavaScript.

En aquesta activitat encara no consumirem una API. Primer treballarem amb dades locals dins del mateix fitxer JavaScript.

> **Nota:** Si és la primera vegada que veus JavaScript, no passa res. L'objectiu és que comencis a veure com es connecta amb la pàgina. La sintaxi i les eines les treballaràs amb molt més profunditat durant el curs.

---

## Objectius

En acabar aquesta activitat hauràs practicat:

- Entendre què és JavaScript al navegador.
- Seleccionar elements del DOM amb `querySelector`.
- Escoltar clics amb `addEventListener`.
- Crear HTML des de JavaScript.
- Pintar cards a partir d'un array local.
- Mostrar un detall quan l'usuari fa clic.

---

## Què és el DOM

El **DOM** és la representació que fa el navegador de la teva pàgina HTML. Amb JavaScript pots llegir i modificar aquesta estructura.

Exemple:

```js
const title = document.querySelector('h1')
title.textContent = 'Pet Cards'
```

---

## Dades locals

Comença amb un array com aquest:

```js
const pets = [
  { name: 'Nala', type: 'Gos', age: 3, description: 'Li agrada jugar al parc.' },
  { name: 'Misu', type: 'Gat', age: 2, description: 'És tranquil i curiós.' },
  { name: 'Taca', type: 'Conill', age: 1, description: 'Busca una casa amb calma.' }
]
```

---

## Exercici

Transforma la pàgina estàtica anterior perquè les cards es generin amb JavaScript.

Has de crear:

- Un contenidor buit al HTML, per exemple `#pet-list`.
- Una funció `renderPets(pets)`.
- Una funció `renderPetCard(pet)`.
- Un event de clic per mostrar el detall d'una mascota.

---

## Guia de treball

Pots començar amb aquesta estructura:

```js
const petList = document.querySelector('#pet-list')
const petDetail = document.querySelector('#pet-detail')

function renderPets(pets) {
  petList.innerHTML = ''

  pets.forEach((pet) => {
    petList.innerHTML += renderPetCard(pet)
  })
}

function renderPetCard(pet) {
  return `
    <article class="pet-card">
      <h2>${pet.name}</h2>
      <p>${pet.type} · ${pet.age} anys</p>
      <button>Veure més</button>
    </article>
  `
}

renderPets(pets)
```

---

## Requisits mínims

- Les cards s'han de pintar des de JavaScript.
- Les dades han de venir d'un array local.
- Ha d'existir almenys un event de clic.
- En clicar una mascota, s'ha de mostrar més informació.

---

## Nivell 2

Afegeix un cercador:

- Crea un input de text.
- Filtra les mascotes pel nom.
- Si no hi ha resultats, mostra un missatge.

---

## Nivell 3

Millora la interacció:

- Marca visualment la card seleccionada.
- Afegeix un botó per netejar la cerca.
- Mostra el nombre de resultats.

---

## Recursos recomanats

Per començar:

- [MDN: JavaScript basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [MDN: Document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
- [MDN: addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

Per continuar quan vulguis aprofundir:

- [MDN Learn: Dynamic scripting with JavaScript](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting)
