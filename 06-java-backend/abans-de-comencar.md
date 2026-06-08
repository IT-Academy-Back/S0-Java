# Abans de començar el backend challenge

En aquest document mantindrem alguns termes tècnics en anglès perquè són els que trobaràs en documentació, eines i equips de desenvolupament.

> **Nota:** Si és la primera vegada que obres un projecte Java amb Spring Boot, no et preocupis. No cal que entenguis cada detall de la configuració ni de l'estructura. Durant el curs veuràs Spring Boot a fons. Aquí l'objectiu és tocar el codi i veure com respon.

Abans d'implementar la lògica del 3 en ratlla, comprova que tens clar el flux bàsic d'una aplicació web:

```text
frontend -> request -> controller -> service -> response -> frontend
```

Si encara tens dubtes sobre frontend, backend, API, request, response o JSON, revisa primer els [fonaments pràctics de la web](../04-web-app-intro/web-app-intro.md).

---

## Què et dona el projecte base

El projecte base ja inclou:

- Un frontend preparat per provar el joc visualment.
- Un backend Spring Boot.
- Els endpoints `/game/start` i `/game/play`.
- La classe `MoveRequest` amb `row` i `col`.
- La classe `GameResponse` amb `board`, `status` i `message`.
- Tests d'integració que comproven el comportament de l'API.

La teva feina principal serà implementar i millorar la lògica del joc al backend.

---

## Com arrencar el projecte

Arrenca primer el backend des d'IntelliJ executant `TictactoeBackendApplication`.

El backend hauria de quedar disponible a:

```text
http://localhost:8080
```

Després aixeca el frontend des de l'arrel del repositori:

```bash
docker compose up frontend
```

El frontend quedarà disponible a:

```text
http://localhost:5173
```

---

## Com provar que tot funciona

1. Obre `http://localhost:5173` al navegador.
2. Obre DevTools i ves a **Network**.
3. Clica **New sketch**.
4. Comprova que es crida `/game/start`.
5. Clica una casella.
6. Comprova que es crida `/game/play`.
7. Mira la consola d'IntelliJ i relaciona els logs amb l'acció feta al frontend.

---

## Com executar els tests

Des de la carpeta `backend`:

```bash
./mvnw test
```

Els tests són d'integració: comproven l'API des de fora, com si fossin un client real.
