---
date: 08.11.2022, Tuesday
author: Maximilian Mergenthal
next-author: Melih Firat
---

## Themen

- Recap
- React Global States (Context)

---

## Notes

None.

---

## React Global States

Global States sind von überall aus erreichbar. Man muss sie nicht von Dateien zu Dateien importieren.
(Anwendungsbeispiel: Einkaufswagen wie z.B. bei Amazon || Darkmode)

“Redux”, “zustand.js” sind state-management solutions. In React besitzen wir “Context” dafür.
Für die Context Files sollte ein eigener Context Folder angelegt werden.

Man importiert Context folgendermaßen:

**import { createContext } from “react”;**

Context-Provider:

Mit dem Context-Provider umklammern wir den Bereich, in dem der Context entsprechend agieren soll. Sind die States mehrfach in der gesamten App vorhanden, umklammern wir diese mit den Tags.

In der Context Datei können wir alle unserer global States speichern. Diesen geben wir mit "value" die States, auf die die Children Zugriff haben.

Die Synthax und ein Anwendungsbeispiel sind in Ralf's Demo zu sehen. Siehe weiter unten.

## Material & Links

### React Context

- [Demo Repository von Ralf](https://github.com/actyralf/react-context-demo/tree/solution)

---

## Anwesenheit

![2022/11/08](../images/2022-11-08.png)
