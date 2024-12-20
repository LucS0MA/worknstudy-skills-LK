# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️
- les besoins auxquels répond GraphQL  ✔️
- la définition d'un schéma
- Query  ✔️
- Mutation  ✔️
- Subscription ❌ 

## 💻 J'utilise

### Un exemple personnel commenté ✔️

## Query pour récupérer les Ad de ma BDD selon une recherche par titre partielle ##
  @Query(() => [Ad])
  async getAdsByKeyword(@Arg("adTitle") adTitle: string) {
    const adsByadTitle = await Ad.find({
      where: {
        title: ILike(`%${adTitle}%`),
      },
    });
    return adsByadTitle;
  }



### Utilisation dans un projet ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en production si applicable ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en environement professionnel ❌ / ✔️

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
