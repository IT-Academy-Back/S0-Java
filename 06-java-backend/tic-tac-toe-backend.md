# Tic-Tac-Toe Backend Challenge

![[Pasted image 20260528133233.png|675]]

> Abans de començar aquesta tasca, assegura't que has fet els [fonaments pràctics de la web](../04-web-app-intro/web-app-intro.md) i el bloc de [Frontend Basics](../05-frontend-basics/01-html-css.md).

En aquesta tasca construiràs amb Java la lògica d'un joc de **3 en ratlla** dins del backend.

L'objectiu és veure com penses, com t'adaptes a Java, com resols la lògica i com millores el teu codi quan ja funciona.

Treballaràs amb dos endpoints ja definits pel projecte base: un per iniciar la partida i un altre per jugar una casella. La request de jugada serà simple: el jugador només indicarà on vol jugar amb una classe ja definida. El backend haurà de guardar l'estat de la partida i retornar el tauler actualitzat.

**Repositori**: https://github.com/IT-Academy-Back/tic-tac-toe-java

---

## Objectius

En acabar aquesta tasca hauràs practicat:

- Implementar lògica de negoci a partir d'un contracte d'API.
- Representar un estat de joc amb un array simple.
- Validar dades d'entrada abans d'aplicar una acció.
- Controlar torns, victòries, empats i jugades invàlides.
- Explicar el teu codi i les teves decisions a un mentor.
- Refactoritzar una primera solució funcional cap a codi més llegible.
- Fer una primera aproximació a l'orientació a objectes, si arribes al nivell avançat.

---

## Descripció

Has de crear un backend que resolgui una partida de **3 en ratlla** entre una persona i la màquina.

El jugador sempre fa una tirada indicant una fila i una columna. Després, si la partida no ha acabat, la màquina fa una tirada aleatòria en una casella lliure.

El backend ha de mantenir l'estat de la partida mentre l'aplicació està en execució. No cal persistència en base de dades.

La partida es representa amb un array de dues dimensions:

```java
int[][] board = new int[3][3];
```

Els valors del tauler són:

| Valor | Significat |
|-------|------------|
| `0`   | Casella buida |
| `1`   | Jugador |
| `2`   | Màquina |

---

## Endpoints del projecte base

El projecte base ja defineix aquests endpoints:

```http
POST /game/start
```

Aquest endpoint inicia o reinicia la partida i retorna un tauler buit.

```http
POST /game/play
```

Aquest endpoint rep la nova jugada del jugador. El backend ha de consultar l'estat actual de la partida, processar la jugada, aplicar la resposta de la màquina si toca i retornar l'estat actualitzat.

Abans de jugaro o usant el botó de restart, el frontend cridarà `/game/start` per crear una partida nova amb el tauler buit.

El projecte base ja inclou `MoveRequest`, que conté les coordenades `row` i `col`. No has de modificar aquest contracte ni fer que el client enviï el tauler.

---

## Request

Una **request** és la petició que envia el client al backend. En aquest cas, conté la fila i la columna on vol jugar el jugador.

Exemple:

```json
{
  "row": 1,
  "col": 1
}
```

### Camps

| Camp | Tipus | Descripció |
|------|-------|------------|
| `row` | `int` | Fila on vol jugar el jugador. Ha d'estar entre `0` i `2`. |
| `col` | `int` | Columna on vol jugar el jugador. Ha d'estar entre `0` i `2`. |

La request ja vindrà representada amb una classe similar a aquesta:

```java
public class MoveRequest {
	// propietats privades no accesibles ni modificalbles desde fora del propi objecte
    private int row;
    private int col;

	// Getters que ens permeten llegir les propietats privades
    public int getRow() {
        return row;
    }

    public int getCol() {
        return col;
    }
}
```

No has de crear ni modificar `MoveRequest`. El teu focus és utilitzar-ne els camps per implementar la lògica del joc.

---

## Response

Una **response** és la resposta que el backend retorna al client. En aquest cas, conté el tauler actualitzat, l'estat de la partida i un missatge curt.

Exemple:

```json
{
  "board": [
    [0, 0, 0],
    [0, 1, 0],
    [0, 2, 0]
  ],
  "status": "IN_PROGRESS",
  "message": "Turn processed"
}
```

### Camps

| Camp | Tipus | Descripció |
|------|-------|------------|
| `board` | `int[][]` | Tauler després de processar la jugada. |
| `status` | `String` | Estat actual de la partida. |
| `message` | `String` | Missatge curt que expliqui què ha passat. |

### Valors possibles de `status`

| Status | Quan s'ha de retornar |
|--------|------------------------|
| `IN_PROGRESS` | La partida continua. |
| `PLAYER_WON` | El jugador ha guanyat. |
| `MACHINE_WON` | La màquina ha guanyat. |
| `DRAW` | No queden caselles lliures i ningú ha guanyat. |
| `INVALID_MOVE` | La jugada no és vàlida. |

---

## Requisits mínims obligatoris

La teva solució ha de complir aquests punts:

- Validar que `row` i `col` estan entre `0` i `2`.
- Utilitzar `MoveRequest`, que ja dona el projecte base.
- No permetre jugar en una casella ocupada.
- Guardar l'estat de la partida en memòria mentre l'aplicació està en execució.
- Aplicar la jugada del jugador amb el valor `1`.
- Fer que la màquina jugui aleatòriament en una casella lliure amb el valor `2`.
- Detectar si el jugador guanya.
- Detectar si la màquina guanya.
- Detectar si hi ha empat.
- Si el jugador guanya amb la seva jugada, la màquina no ha de jugar després.
- Si la jugada és invàlida, el tauler no s'ha de modificar.
- Si la partida ja ha acabat, no s'han d'acceptar més jugades sobre aquell tauler.
- Retornar sempre una resposta JSON coherent.

---

## Nivell 1: Lògica funcional

Primer fes que el joc funcioni.

En aquest nivell pots escriure una solució procedural. No passa res si al principi el codi no està gaire separat en classes o mètodes. El més important és que la lògica sigui correcta.

Has de resoldre com a mínim:

- Validació de la jugada.
- Lectura de la jugada des de `MoveRequest`.
- Control de l'estat intern de la partida.
- Actualització del tauler.
- Tirada random de la màquina.
- Comprovació de files, columnes i diagonals.
- Detecció d'empat.
- Retorn correcte de l'estat de la partida.

> Quan acabis aquest nivell, has d'anar al mentor i explicar-li la teva solució abans de continuar.

### Defensa amb mentor

Prepara una explicació breu de 5-10 minuts sobre:

- Quin recorregut segueix una petició a `/game/play`.
- Com valides una jugada correcta i una d'incorrecta.
- Com decideixes si algú ha guanyat.
- Com decideixes si hi ha empat.
- Quina part del codi et sembla més difícil de mantenir.

---

## Nivell 2: Refactor bàsic a mètodes

Quan el joc ja funcioni, millora el codi sense canviar el comportament.

L'objectiu és que el codi sigui més fàcil de llegir, provar i explicar.

Extreu mètodes amb responsabilitats clares. Per exemple:

- `isValidMove(...)`
- `applyPlayerMove(...)`
- `applyMachineMove(...)`
- `checkWinner(...)`
- `isDraw(...)`
- `buildResponse(...)`

En aquest nivell volem veure que pots passar d'una solució que funciona a una solució una mica més ordenada.

---

## Nivell 3: Primera millora orientada a objectes

Aquest nivell és avançat.

Si ja tens el Nivell 1 i el Nivell 2 ben resolts, intenta reorganitzar el codi amb una primera aproximació a orientació a objectes.

Pots crear classes com:

- `Game`
- `Board`
- `Player`
- `GameStatus`

L'objectiu no és crear moltes classes, sinó separar responsabilitats de forma natural.

Per exemple:

- El tauler sap si una casella està lliure.
- El joc sap quan ha acabat la partida.
- El servei coordina la petició i la resposta.

Mantingues el mateix endpoint i el mateix contracte JSON. El frontend o el client no haurien de notar cap canvi.

---

## Criteris d'avaluació

Es valorarà especialment:

| Criteri | Pes orientatiu |
|---------|----------------|
| Lògica funcional del joc | 50% |
| Gestió de casos límit | 20% |
| Explicació al mentor | 15% |
| Refactor bàsic a mètodes | 15% |

El Nivell 3 pot millorar la valoració qualitativa de la tasca, però no compensa una lògica bàsica incorrecta.

---

## Casos que has de provar

Abans d'entregar, comprova com a mínim aquests casos:

- El jugador juga en una casella buida.
- El jugador intenta jugar fora del tauler.
- El jugador intenta jugar en una casella ocupada.
- El jugador guanya amb una fila.
- El jugador guanya amb una columna.
- El jugador guanya amb una diagonal.
- La màquina pot guanyar després de la seva tirada.
- La partida acaba en empat.
- La màquina no juga si el jugador ja ha guanyat.

---

## Lliurament

Has d'entregar un repositori amb:

- El codi font del backend.
- Un `README.md` amb instruccions clares per executar el projecte.
- Una explicació breu de les decisions principals.
- Una llista dels casos que has provat.

---

## README mínim recomanat

El teu `README.md` hauria d'incloure:

```markdown
# Tic-Tac-Toe Backend

## Descripció
Backend simple per jugar una partida de 3 en ratlla contra la màquina.

## Tecnologies
- Java
- Spring Boot

## Com executar el projecte
Explica aquí les passes necessàries.

## Endpoints
POST /game/start
POST /game/play

### Request
```json
{
  "row": 1,
  "col": 1
}
```

## Decisions preses
Explica breument com has representat el tauler i com controles la partida.

## Proves realitzades
Llista els casos que has comprovat.
```

---

## Recursos recomanats

- [Arrays en Java](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html)
- [Random en Java](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Random.html)
- [Spring: Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)

Per ampliar més endavant, quan ja tinguis més context de Spring:

- [Spring: Building REST services with Spring](https://spring.io/guides/tutorials/rest/)
- [Spring Start Here](https://www.manning.com/books/spring-start-here), de Laurentiu Spilca
