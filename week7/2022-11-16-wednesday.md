---
date: 16.11.2022, Wednesday
author: Sascha Rehberg
next-author: Sergey Movsesyan
---

# Vormittag

## Besprechung der Aufgaben von gestern

**Ausgangslage:**
'pages' folder, unterhalb davon 'api' folder.
Alles was in 'api' liegt läuft auf einem Server und wird ausgeführt wenn man eine API Route anfragt.

Postman stellt die gleichen Anfragen wie der Browser, bietet aber auch noch mehr Möglichkeiten. Vieles davon lässt sich mit dem Browser nicht machen, Postman ist also das Tool zum testen der API.

req.method ist in der Regel 'GET', wenn die Anfrage aus dem Browser stammt.

Ohne 'response' werden an den Client keine Daten zurückgesendet, also kommt es zum TimeOut. Daher muss man dem Client in jedem Fall etwas zurückmelden, auch wenn es eine Fehlermeldung ist, damit der User nicht in einer in der Regel viel zu langen Warteschleife hängen bleibt.

Die Routing-Struktur von 'api' ist in Anlehnung an den 'pages' folder aufgebaut. Es gibt noch die zusätzliche Route mit eckigen Klammern `[]` für **Dynamic Routes**

Aufgabe war, aus Client Sicht auf die API zuzugreifen.
Das funktioniert letztlich nicht anders, als auf eine externe API zuzugreifen (siehe Rick and Morty App).

Übliche useEffect Struktur für Fetch, mit leerem dependancy-array. Im fetch muss keine Domain stehen, wenn man auf eine eigene API zugreift, nur der Pfad in unserer eigenen Ordnerstruktur.

Im useState auf einzelne Properties eines Objekts zuzugreifen ist etwas komplizierter als auf ein Array. Deswegen initial Wert des useState auf 'null' (weil gewisse Dinge sonst zu schnell laufen).

Beim Objekt braucht man einen ternery, damit etwas passiert, wenn es das Objekt noch nicht gibt, was ansonsten einen Fehler schmeißen würde.

## Möglicher Fehler in NextJS:

Hydration-error
Beispiel mit Date.now

Teile der Seite werden auf dem Server gerendert und direkt als HTML an den Client zurückgeschickt. (Problem tritt nur mit Next auf, nicht mit React).
Der Client 'rehydriert' den erhaltenen Inhalt, überprüft ihn also daraufhin, ob er mit den eigenen Informationen übereinstimmt, was er dann natürlich nicht mehr tut, nachdem ja Zeit vergangen ist zwischen den beiden Vorgängen.

Passiert gerne bei Date.now, aber auch bei sehr Browser-spezifischen Operationen, die sich z.B. auf das Window beziehen, welches der Server ja gar nicht zur Verfügung hat.

Hydration-process geschieht nur beim echten Reload.

Als Lösung muss man auf Änderungen der State-Variablen reagieren, indem man das dependancy-Array füllt.

## Filtern

Neuer State: Filter-Wert

const [categoryFilter, setCategoryFilter] = useState(null)

Wir haben jetzt einen State, der filtert. Jetzt muss der noch auf die API angewandt werden.
Man muss also neu fetchen, wenn sich der CategoryFilter ändert. Also muss categoryFilter in das dependancy Array.
Ausserdem brauchen wir beim URL Aufruf im fetch eine dynamische URL, die den Filter nutzt. (`/api/products?category=${categoryFilter}`)

# Nachmittag

## Styling in NextJS

Styling funktioniert anders als in React oder JS Vanilla
Benennungskonvention für CSS-Files ist anders

global.css kann nur in der app.js eingebunden werden, die Klassen daraus können dann in der Theorie überall verwendet werden.
_Globale Styles sollte man eigentlich nicht mit Klassen verwenden._

Alle anderen CSS Dateien müssen mit _name_.module.css benannt werden. Modul bedeutet hier Komponente. Dann muss man style von dort importieren.

Die Klassen sind dadurch pro Modul anwendbar, auch mit dem gleichen Namen, weil NextJS den Klassen noch einen generierten Anhang gibt.

**Styled Components**
styled components installieren
in der next.config.js einfügen:

```
compiler: {
 styledComponents: true,
},
```

In der const nextConfig unterhalb von reactStrictMode: true

## Deploy auf Vercel

Account auf Vercel.com anlegen, mit GitHub Konto verknüpfen für Zugriff auf die Repos.

**Vercel deployed nicht, wenn Linterfehler auftreten!**

Vercel wird automatisch von GitHub über Änderungen am Main informiert und deployed diese dann auch. Daher: Immer im Branch arbeiten.

## Wiederholung zu Custom Hooks

Auf der gleichen Ebene wie die app.js einen neuen Ordner 'hooks'
Darin eine neue Datei, zb. useFetch.js
useState und useEffect importieren

```
import { useState, useEffect } from "react";
export default function (urlToFetch, arrayProperty) {
const [state, setState] = useState([]);
useEffect(() => {
async function fetchData() {
const response = await fetch(urlToFetch);
const data = await response.json();
if (arrayProperty) {
setState(data[arrayProperty]);
} else {
setState(data);
}
}
fetchData();
}, [urlToFetch, arrayProperty]};
return [state, setState];
}
```

Den Hook dann importieren und aufrufen, ganz genau so, wie man eigentlich den useState aufruft

Ein Hook wie useFetch im Beispiel oben sollte wiederverwendbar sein.

# Material & Links

Link zu Ralfs Repo vom Vormittag:

- https://github.com/actyralf/next-with-api-demo

- https://vercel.com/

---

## Aufgabe

- Rick and Morty App in NextJS übertragen.

- ***

## Anwesenheit

![2022/11/16](../images/2022-11-16.png)
