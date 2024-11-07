## Typage avec React

### main.tsx
-> ajouter le code du main.tsx avec le typage HTMLElement

### Interface
Les interfaces permettent d'indiquer les données attendus dans un tableau, objet.

## Typer le code

Dans notre code, on as une petite app permettant d'afficher un élément. Il est constitué d'un composant parent, un composant responsable de l'affichage et un composant permettant d'afficher l'élément en particulier.

Ici, on utilise le `useState` pour passer la valeur de la donnée.

On viens ainsi typer dans les deux composants enfant :

```js
//App.tsx
function App() {
	// state dans App
	// foodlist a besoin du setter (on va lui envoyer via une props)
	// fooddisplay a besoin de la valeur du state pour l'afficher (on va lui filer via une props)
	const [currentFood, setCurrentFood] = useState('muffin');
	return (
		<div>
			<FoodList handleChangeFood={setCurrentFood} />
			<FoodDisplay prefFood={currentFood} />
		</div>
	);
}
```

Dans le composant `FoodList`, on viens typer la référence à la fonction permettant de modifier la valeur du state.

Pour utiliser le bon type, on passeras la souris sur la fonction du `useState`, et on peut voir le type à utiliser.

On viens donc créer une interface permettant de typer la fonction utiliser.

```js
//FoodList.tsx
const pastries = ['muffin', 'chocolat', 'macaron', 'cupcake', 'pop-corn'];

//déclaration de l'interface pour typer la fonction
interface PropsFoodList {
	handleChangeFood: React.Dispatch<React.SetStateAction<string>>;
}

//on viens typer la fonction passer en props
function FoodList({ handleChangeFood }: PropsFoodList) {
	return (
		<ul>
			{pastries.map((food) => (
				<li>
					<button
						type="button"
						onClick={() => {
							handleChangeFood(food);
						}
				}
            >{food}
					</button>
				</li>
			))}
		</ul>
	);
}

export default FoodList;
```

On vient également typer dans le second composant enfant la valeur qui est passer en props

```js
//Foodisplay.tsx

//interface pour type la valeur de la props
interface FoodDisplayProps {
	prefFood: string;
}

//on vient utiliser l'interface pour typer la prop passer au composant
function FoodDisplay({ prefFood }: FoodDisplayProps) {
	return <p>My favorite food is {prefFood}</p>;
}

export default FoodDisplay;
```

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
