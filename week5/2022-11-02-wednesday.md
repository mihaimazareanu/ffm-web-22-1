---
date: 02.11.2022, Wednesday
author: Georgios
next-author: Justus
---

## Themen

- React Arrays
- React Event Listeners 
- React State

---

## Notes

None. 

### React Arrays


<div className="App__card-grid">
{USERS.map((currywurst) => {
    return <Card user={currywurst} />;
})}

- Erzeugt Karte für jedes ITEM AUS DEM ARRAY -> Card wird über Callback aufgerufen

- Item, das dynamisch erzeugt wird (im Bsp. Card) erfordert zusätzlick key-Prop, zum Bsp. die ID, also: <Card key={user.id} user={currywurst} />;


export default function Tag ({userRoles}){
    return (
        <>
          {userRoles.map((userRole) => {
            return <li className={"Tag"}>{userRole}</li>
          })}
        </>
    )
}

// Destructured:

export default runction App() {
    return (
        <main className="App__container">
        <Header />
        <div className="App__card-grid">
        {USERS.map(({name, about, roles, id}) => {
            return <Card key={id} name={name} about={about} roles={roles} />
        })}
        </div>
        </main>
    )
}



- Ginge auch mit implizitem Return statt mit explizitem 

- Bei Object destructuring ist die Reihenfolge der Keys nicht relevant, es muss nur mit den gegebenen Keys übereinstimmen. Bei Arrays ist die Reihenfolge allerdings relevant.

- Nur die Keys weiterzugeben, statt des ganzen Objects sieht in der Ausführung dann etwas sauberer aus, da man eben nur noch die Keys aufrufen muss. 

---

### React Event Listeners 

- Event Listeners werden in React direkt in die HTML-Element mit Attributen eingefügt, in camelCase-Schreibweise (z.Bsp. onClick):
<button onClick={add}>+1</button>

- States(Hooks) sind vorgefertigte, von React zur Verfügung gestellte Funktionen, die bestimmte Voraussetzungen erfordern. useState verlangt Variable, die Werte enthält (z.Bsp. const count) und einen “Setter”, der die Funktion enthält.

---

### React State

- EventListener können als Attribute / Event Handler in unsere HTML Elemente eingefügt werden

- Functions lassen sich innerhalb der Components schreiben und dann im Event Handler einfach nur noch aufrufen.

- Wenn man die Funktion als Aufruf in den Event Handler übergibt, wird sie auch direkt ausgeführt, deshalb: Nicht machen.

- Render-life-cycle: Jedes Mal, wenn sich etwas an der Component ändert, wird die Seite neu gerendert.

- useState Hook aus react importieren, dann die Variable, die man durch das render life cycle hindurch aufrecht erhalten will mit useState initialisieren

- const [count, setCount] = useState(0);
count = die Variable, können wir benennen wie wir möchten
setCount = setter Funktion, kann theoretisch mit irgendeinem Wort benannt werden, soll aber set und der Name der Variable enthalten, um einfacher zu verstehen
useState = der Hook
0 = initialer Wert

import {useSteate} from "react";

export default function App() {
    const [count, setCount] = useState(0);


    function add() {
        setCount(count + 1)
    }

    const subtract = () => {
        setCount(count - 1)
    };

    return (
        <div className="App">
            <h1>Event Listeners and State</h1>
            <button onClick={add}>+1</button>
            <button onClick={subtract}>-1</button>
            <p>{count}</p>
        </div>
    );
}


- const [count, setCount] = useState(0); ->
-> aus dem useState Hook bekommen wir einen Array zurück mit zwei Werten. Einmal der Wert und einen “Setter”.
Der Setter ist eine Funktion, die uns der useState zurückgibt
Der Setter ist einer Variable zugewiesen.
Der Setter sollte die Variable selbst im Namen tragen. Best Praxis ist, ihn mir ‘set’’Variablennamen’ zu setzen.
Der Setter muss jedes Mal ausgeführt werden, um die Variable zu verändern.

- Setter können auf die useStates anderer Werte hören, da sie ja schlicht und einfach Functions sind.

- Hook : ist ein Funktionalitätsprinzip in React. Hilft uns dabei, Werte zu speichern in einer Komponente. Werden nicht in Loops, Bedingungen oder verschachtelten Funktionen verwendet.


- Beispiel zum togglen eines Bookmarks für die Quizapp:

const [toggle, setToggle] = useState(false);
const toggleBookmark = () => {
setToggle(!toggle);
}

---

## Material & Links

### React Arrays 
- [React Lists and Keys](https://reactjs.org/docs/lists-and-keys.html)
- [MDN React Getting Started](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started)
- [W3 Array Methods](https://www.w3schools.com/react/react_es6_array_methods.asp)
- [CodeSandbox Stefan](https://codesandbox.io/s/ffm-web-22-1-react-arrays-77mic1?file=%2Fsrc%2FApp.js)

### React State
- [W3 React Events](https://www.w3schools.com/react/react_events.asp)
- [MDN Onclick Event](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/onclick)
- [ReactJS Hooks](https://reactjs.org/docs/hooks-intro.html)
- [CodeSandbox Thomas](https://codesandbox.io/s/hungry-shadow-js9v8f?file=/src/App.js)

---

## Aufgaben

[React Arrays Challenge](../sessions/react-arrays/challenges-react-arrays.md)

[React State Challenge](https://github.com/neuefische/ffm-web-22-1/blob/main/sessions/react-state/challenges-react-state.md)

---

## Fragen und Antworten

None.

---

## Anwesenheit

![2022/11/02](../images/2022-10-20.png)
