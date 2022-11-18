# Deployen einer Next.js App mit MongoDB auf Vercel

## Schritt 1 Account und Cluster bei MongoDB Atlas anlegen

- Erstellt einen neuen Account bei [MongoDB Atlas](https://www.mongodb.com/)
- Wählt "Free Tier" aus, um einen kostenlosen Cluster zu erstellen
- Wenn ihr nach Cloud-Provider und Location gefragt werdet, wählt "AWS" und "Frankfurt"
- Im nächsten Schritt sollt ihr einen Datenbank-User anlegen, gebt hier "admin" als Username ein und speichert oder merkt Euch das Passwort - ihr werdet es in späteren Schritten brauchen.
- Bei der Frage, von wo aus Eure Datenbank erreichbar sein soll, bleibt ihr beim Default ("From my local machine" o.Ä.)
- Zusätzlich gebt ihr aber in den Feldern darunter folgende IP-Adresse ein:
  ```
  0.0.0.0/0
  ```
- Diese IP-Adresse wirkt sozusagen als "Wildcard" und sorgt dafür, dass Eure Datenbank von jedem beliebigen Rechner aus erreichbar ist.
- Geht nun im MongoDB-Dashboard auf "Database" (ihr solltet standardmäßig dort landen) und wählt "Connect"
- Dort wählt ihr "Connect using MongoDB Compass" und kopiert den angezeigten Connection-String
- Testet in Compass, ob Eure Connection funktioniert: Wählt "Connect/New Connection", um eine neue Connection zu erstellen
- In das Eingabefeld ("URI") fügt ihr den kopierten Connection String ein.
- **WICHTIG**: Ihr müsst in dem Connection String den Text `<Password>` durch das Passwort ersetzen, das ihr weiter oben dem "admin" User zugewiesen hattet.
- Wenn ihr Euch verbinden könnt, ist der Remote MongoDB Cluster korrekt eingerichtet
- Ihr könnt hier nun wie gewohnt Datenbanken erstellen und Collections anlegen

## Schritt 2 App by Vercel deployen

- Deployed Eure App zunächst einfach durch Hinzufügen eines neuen Projektes auf [vercel.com](https://vercel.com):
  - Wählt "Add New" und "Project"
  - Verbindet Euch mit Eurem Github-Account und wählt das Repository, das ihr deployen wollt
  - Vercel startet automatisch ein Deployment, **ACHTUNG**: dieses wird noch nicht funktionieren!
  - Wenn das Deployment abgeschlossen ist, könnt ihr in Eurem Vercel-Projekt auf "Settings/Environment Variables" gehen.
  - Tragt hier als `key` den gleichen Key ein, den ihr in Eurer `.env.local` Datei hinterlegt habt, z.B. `MONGO_DB_URI`
  - Als `value` tragt ihr den gleichen Connection-String ein, den ihr auch in Compass eingegeben habt.
  - **WICHTIG**: Am Ende des Connection-Strings steht der Datenbank-Name (standardmäßig `/test`), diesen müsst ihr mit dem richtigen Namen Eurer Datenbank ersetzen!
  - Damit die neue Variable berücksichtigt wird, müsst ihr ein erneutes Deployment durchführen, geht hierzu auf "Deployments" und wählt die drei Punkte neben dem letzten Deployment an - hier findet ihr den Befehl "Redeploy"
