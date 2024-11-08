## Menu Mobile

Ici on fais la gestion d'un menu mobile.
```js
export default function Header() {

//useState pour gérer si on doit afficher ou non le menu
//initialiser à false car on souhaite le cacher
const [showMenuMobile, setShowMenuMobile] = useState(false);

return (
	<header className="shadow-md py-3 px-3 flex justify-end static">
		//affichage en desktop
		<div className="hidden md:block">
			//le composant permet d'afficher le menu
			<MenuNav />
		</div>
		//ce partie est cacher en vue desktop et s'affiche que sur mobile
		<div className="md:hidden">
			//on ecoute le clic et cela modifie la valeur de state
			//logo de react feather
			<Menu onClick={() => {
				setShowMenuMobile(!showMenuMobile);
			}}
			/>
			//on évalue la valeur, et si true on affiche le composant 
			{showMenuMobile ? <MenuMobile /> : ""}
		</div>
	</header>
	);

}
```
