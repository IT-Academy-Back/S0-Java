# Frontend Basics 1: HTML i CSS

En aquesta primera activitat de frontend construiràs una pantalla estàtica. Encara no farem JavaScript ni crides a cap API.

L'objectiu és entendre que el frontend comença amb estructura i estil: HTML per definir què hi ha a la pàgina i CSS per decidir com es veu.

> **Nota:** Aquí només veuràs la superfície d'HTML i CSS. Durant el curs aprofundiràs en selectors, disseny responsive, animacions i molt més.

---

## Objectius

En acabar aquesta activitat hauràs practicat:

- Crear una pàgina HTML bàsica.
- Fer servir etiquetes com `header`, `main`, `section`, `article`, `h1`, `p`, `img` i `button`.
- Escriure CSS simple.
- Donar estil a cards.
- Fer un layout bàsic amb `flex`.

---

## Què és HTML

HTML defineix l'estructura de la pàgina. És el que diu al navegador quins elements existeixen.

Exemple:

```html
<article class="pet-card">
  <h2>Nala</h2>
  <p>Gos · 3 anys</p>
  <button>Veure més</button>
</article>
```

---

## Què és CSS

CSS defineix l'estil visual de la pàgina: colors, marges, tipografia, mida, distribució i altres detalls.

Exemple:

```css
.pet-card {
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 12px;
}
```

---

## Exercici

Crea una pàgina estàtica de **Pet Cards**.

La pàgina ha de mostrar com a mínim:

- Un títol principal.
- Una descripció curta.
- Tres cards de mascotes.
- Nom de cada mascota.
- Tipus d'animal.
- Edat.
- Una descripció curta.
- Un botó visual de “Veure més”.

No cal que el botó faci res encara.

---

## Estructura mínima recomanada

```text
frontend/
├── index.html
└── styles.css
```

---

## Requisits mínims

- El document ha de tenir estructura HTML correcta.
- El CSS ha d'estar en un fitxer separat.
- Les cards han de tenir una aparença clara i llegible.
- La pàgina s'ha de poder obrir al navegador.

---

## Nivell 2

Millora el disseny:

- Afegeix colors coherents.
- Afegeix espai entre cards.
- Fes que les cards tinguin una ombra suau.
- Fes que el botó tingui estat `hover`.

---

## Nivell 3

Fes que la pàgina sigui responsive:

- En desktop, mostra les cards en fila.
- En mòbil, mostra les cards una sota l'altra.

---

## Recursos recomanats

Per començar:

- [MDN: HTML basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)
- [MDN: CSS basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics)
- [MDN: Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)

Per continuar quan vulguis aprofundir:

- [MDN Learn: Structuring content with HTML](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content)
- [MDN Learn: CSS styling basics](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics)
- [MDN Learn: CSS layout](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout)
