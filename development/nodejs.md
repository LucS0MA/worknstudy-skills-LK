# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple)  ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ✔️
- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS* ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

## Ceci est l'index.ts de mon backend, c'est ici qu'est défini le lancement de ma BDD, la défnition de mon schéma Apollo avec GraphQL
ainsi que la définition du port sur lequel se lancera mon API GraphQL ##

import { ApolloServer } from "@apollo/server";
import { startStandaloneServer } from "@apollo/server/standalone";
import { dataSourceGoodCorner } from "./config/db";
import { buildSchema } from "type-graphql";
import AdResolver from "./resolvers/AdResolvers";
import CategoryResolvers from "./resolvers/CategoryResolvers";
import TagResolvers from "./resolvers/TagResolvers";

const start = async () => {
  await dataSourceGoodCorner.initialize();

  const schema = await buildSchema({
    resolvers: [AdResolver, CategoryResolvers, TagResolvers],
  });

  const server = new ApolloServer({
    schema,
  });
  const { url } = await startStandaloneServer(server, {
    listen: { port: 4000 },
  });

  console.log(`🚀 Server listening at: ${url}`);
  console.log('test hot reload')
};
start();


```javascript
// this function takes a path to a .md file of the host system and write the HTML version of this file
// the .html file is given back
const convertMDFileToHTML = (pathToMDfile) => /* ... path to HTML file */
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en production si applicable ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en environement professionnel ❌ 

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
