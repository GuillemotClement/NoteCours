app.tsx
```js
import HelloMessage from './HelloMessage';

import './style.css';

  

function App() {

// Passer le user en propriété du composant HelloMessage et utiliser les données pour afficher le bon message

// Ne pas oublier de typer les propriétés dans le composant HelloMessage

  

const user = {
firstname: 'Dave',
lastname: 'Lopper',
};

  

return (

<div>

<HelloMessage firstname={user.firstname} lastname={user.lastname} />

</div>

);

}

  

export default App;
````
composant
```js

//on ajoute l'interface pour Ts
interface IPropsMessage {

firstname: string;

lastname: string;

}

  
//on type la props avec l'interface.
//si pas respecter on obtient une erreur
function HelloMessage({ firstname, lastname }: IPropsMessage) {

return (

<p>

Hello {firstname} {lastname} !

</p>

);

}

  

export default HelloMessage;
```

## Afficher un tableau d'élément
```js
import Macaron from "./Macaron";

  

export default function App() {

// simu de recup des data d'un call api

// on recup un tableau json

const data = [

{

id: 1,

couleur: "marrond",

parfum: "choco",

},

{

id: 2,

couleur: "jaune",

parfum: "citron",

},

{

id: 3,

couleur: "rose",

parfum: "fraise",

},

];

  

// on vient fabriquer un tableau d'élément React (jsx) a partir du tableau d'objet

// on peut de cette manière le mettre dans le JSX

// il faut passer une key pour react. Elle doit être unique

// on utilise map pour passer un tableau d'objet en tableau d'un élément

const arrayJsxMacaron = data.map((macaron) => {

return <Macaron {...macaron} key={macaron.id} />;

});

return (

<div className="app">

<header>

<h1>Welcome in the Gizmo Store</h1>

</header>

<main>

<h2>Macarons</h2>

<div className="">

{/* Le tableau de composant Macaron créer avec map */}

<ul>{arrayJsxMacaron}</ul>

</div>

</main>

<footer>

<p>Copyright</p>

</footer>

</div>

);

}
```
