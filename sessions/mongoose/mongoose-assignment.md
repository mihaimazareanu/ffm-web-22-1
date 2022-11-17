# Assignment: mongoose CRUD Funktionen

Benutzt bitte dieses [Starter Template](https://github.com/actyralf/mongoose-assignment-starting-point)

- Das Template beinhaltet den letzten Stand unserer "Produkt"-App, an der wir in den letzten Tagen gearbeitet haben
- Wählt auf github "Use this template" und "Create a new repository"
- Dadurch wird eine Kopie des Templates in Eurem eigenen Account hergestellt
- Wechselt in Euren Account und die neu erstellte Kopie
- Wählt dort "Code" und kopiert Euch die github-Adresse Eures Repos
- Geht im Terminal auf Euren Projektordner und ruft `git clone` mit der Adresse Eures Repos auf
- Wechselt in das von `git clone` neu erstellte Verzeichnis
- Ruft `npm install` auf, um die Dependencies zu installieren
- Erstellt eine Datei `.env.local` mit folgendem Inhalt:
  ```
  MONGO_DB_URI=mongodb://localhost:27017/products
  ```

**WICHTIG**: Das Repo verwendet die Datenbank `products` mit einer Collection, die ebenfalls `products` heißt.
Spielt also Eure Testdaten in diese Collection ein.

# Aufgabe 1

Erstellt eine `DELETE`-Route, mit deren Hilfe man Produkte aus der Datenbank wieder löschen kann:

- Der Aufruf der Route erfolgt über `DELETE http://localhost:3000/api/products/[BELIEBIGE PRODUCT ID]`
- Verwendet zum Testen Eurer Delete-Route Postman
- **Hinweis**: Verwendet den bestehenden Route-Handler unter `/pages/api/products/[productId].js`
- **Hinweis**: Ihr könnt die mongoose Methode [Model.findByIdAndDelete()](https://mongoosejs.com/docs/api/model.html#model_Model-findByIdAndDelete) verwenden

# Aufgabe 2

Macht die neue Löschfunktionalität aus Aufgabe 1 in Eurem Client verfügbar:

- Fügt der Liste in `pages/products/index.js` einen Lösch-Button oder ein Lösch-Icon hinzu
- Ruft bei Klick auf diesen Button die neue `DELETE`-Route der Api auf
- **Hinweis**: `fetch()` hat einen zweiten Parameter `options`, mit dem man unter anderem die HTTP-Method für einen Aufruf bestimmen kann
  - [Dokumentation fetch()](https://developer.mozilla.org/en-US/docs/Web/API/fetch)
- **Bonus**: Sorgt dafür, dass nach erfolgreichem Löschen auch Eure Liste neu gerendert wird, so dass das gelöschte Element sofort verschwindet.
  - Hierfür gibt es mehrere mögliche Wege:
    - Reload der kompletten Page
    - Erneuter Aufruf der `fetch()`-Funktion und entsprechendes Setzen des states `products` unmittelbar nach erfolgreichem Löschen
    - Entfernen des ausgewählten Produktes aus dem `products`-Array
    - Führt eine neue State-Variable `shouldReload` ein, die ihr nach dem Löschen auf `true` setzt. Passt das Dependency-Array Eures `useEffect` an, so dass es auf diese neue Variable "lauscht". Prüft dann im `useEffect`, ob die Variable `true` ist und führt nur dann die Funktion `getProducts` aus. **WICHTIG**: Ihr müsst diese Variable mit `true` initialisieren, damit `getProducts` weiterhin bei jedem Laden der Seite aufgerufen wird. **AUCH WICHTIG**: In `getProducts` müsst ihr diese Variable wieder auf `false` zurücksetzen.

# BONUS: Aufgabe 3

Implementiert ein Formular zum Hinzufügen neuer Produkte:

- Unsere API-Route `POST http://localhost:3000/api/products` sollte schon funktionieren, d.h. wir können per API neue Produkte hinzufügen.
- Fügt auf der Produktübersicht ein Formular ein, in dem man neue Produktdaten eingeben kann.
- Schickt die Produktdaten bei `onSubmit` an unsere API.
- **Hinweis**: Schaut auch hier in den `options` von `fetch()` nach, wie man die Daten im `body` versendet.
- **Bonus im Bonus**: Sorgt auch hier wieder dafür, dass das neue Produkt gleich in der Liste erscheint.
