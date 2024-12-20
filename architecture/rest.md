# REST API

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP  ✔️
- les statuts HTTP  ✔️
- les endpoints  ✔️
- CORS  ✔️
- la nomenclature recommandée pour les routes  ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

## Ceci est l'index.ts de mon API rest img, cette API rest me permet de gérer les upload des images sur mon application dans laquelle GraphQL ne le permettait pas. ##

import express, { Response } from "express";
import multer from "multer";
import fs from "fs";
import path from "path";

const app = express();
const port = 4000;

const storage = multer.diskStorage({
  destination: function (_req, _file, cb) {
    cb(null, path.join(__dirname, "../uploads/"));
  },
  filename: function (_req, file, cb) {
    cb(null, Date.now() + "-" + file.originalname);
  },
});
const upload = multer({ storage: storage });

app.get("/", (_req, res) => {
  res.send("Healthcheck Okay");
});

app.post("/img", upload.single("file"), (req: any, res: Response) => {
  fs.readFile(req.file.path, (err) => {
    if (err) {
      console.log("error while reading file");
      console.log("Error: ", err);
      res.status(500).json({ error: err });
    } else {
      res
        .status(201)
        .json({ status: "success", filename: "/img/" + req.file.filename });
    }
  });
});

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
