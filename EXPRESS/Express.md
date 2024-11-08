```table-of-contents
```
---
## SetUp 

[Lien du guide](https://dev.to/wizdomtek/typescript-express-building-robust-apis-with-nodejs-1fln)
Pour une installation avec TS, Express

Créer un nouveau folder et se mettre dans celui ci

```bash
npm init -y
```

-y pour skip les questions

```bash
npm install express typescript ts-node @types/node @types/express --save-dev
```

Installer les dépendances

`--save-dev` pour indique que les dépendances sont utilisé uniquement pendant le dev

Création du fichier de config ts : `tsconfig.json`
```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

Créer un folder `/src` et dedans créer un fichier `index.ts`.git

Dans le fichier `index.ts` :
```js
import express from "express";
import type { Request, Response } from "express";

const app = express();
const PORT = process.env.PORT || 3000;

app.get("/", (req: Request, res: Response) => {
	res.send("Hello, typeScript Express");
});

app.listen(PORT, () => {
	console.log(`Server is running at http://localhost:${PORT}`);
});
```

Ajouter les scripts dans `package.json`
```json
"scripts": {
  "start": "ts-node src/index.ts",
  "build": "tsc",
  "serve": "node dist/index.js"
}
```

Pour lancer le serveur, lancer la commande :
```bash 
npm run dev
```
