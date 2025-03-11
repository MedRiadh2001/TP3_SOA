# TP2 : Implémentation d'une API GraphQL avec Express.js

Ce document présente le compte rendu du **Travail Pratique 2 (TP2)** du cours **SOA et Microservices**. L'objectif de ce TP est de concevoir et implémenter une API GraphQL en utilisant **Express.js** et **Apollo Server**.

---

## Objectifs

- Développer une API GraphQL avec Express.js et Apollo Server.
- Créer un schéma GraphQL et définir les types de données.
- Implémenter des requêtes (Query) et des mutations (Mutation).
- Tester l'API avec GraphQL Playground ou Postman.

---

## Technologies utilisées

- **Node.js** : Environnement d'exécution JavaScript.
- **Express.js** : Framework pour la création d'API.
- **GraphQL** : Langage de requête pour API.
- **Apollo Server** : Serveur GraphQL pour Node.js.

---

## Structure du projet

- **`taskResolver.js`** : Contient la logique de résolution des requêtes et mutations GraphQL.
- **`taskSchema.gql`** : Définit le schéma GraphQL avec les types et les opérations possibles.
- **`taskSchema.js`** : Charge et construit le schéma GraphQL à partir du fichier `.gql`.
- **`index.js`** : Point d'entrée de l'API, intègre Express et Apollo Server.

---

## Détails de l'implémentation

### 1. Schéma GraphQL (`taskSchema.gql`)

Le fichier **`taskSchema.gql`** définit la structure des données et les opérations possibles :

- **Type `Task`** : Représente une tâche avec `id`, `title`, `description`, `completed`, et `duration`.
- **Query** : Permet d'obtenir une tâche par `id` ou la liste des tâches.
- **Mutation** : Permet d'ajouter, modifier ou supprimer une tâche.

### 2. Résolutions (`taskResolver.js`)

Le fichier **`taskResolver.js`** contient les résolveurs qui gèrent les requêtes GraphQL :

- **Query** :
  - `task(id: ID!)` : Renvoie une tâche par son `id`.
  - `tasks` : Renvoie la liste de toutes les tâches.

- **Mutation** :
  - `addTask` : Ajoute une nouvelle tâche.
  - `completeTask` : Marque une tâche comme complète.
  - `changeDescription` : Modifie la description d'une tâche.
  - `deleteTask` : Supprime une tâche.

Les tâches sont stockées sous forme d'un tableau d'objets JavaScript.

### 3. Serveur Express et Apollo (`index.js`)

Le fichier **`index.js`** initialise l'application avec **Express.js** et **Apollo Server** :

1. Charge le schéma GraphQL depuis `taskSchema.js`.
2. Associe les résolveurs au schéma.
3. Démarre le serveur Apollo et le lie à Express.

---

## Instructions d'exécution

1. Clonez ce dépôt sur votre machine locale :

```bash
git clone https://github.com/MedRiadh2001/TP3_SOA.git
```

2. Installez les dépendances :

```bash
npm install
```

3. Démarrez le serveur :

```bash
node index.js
```

4. Accédez à l'API GraphQL via :

```
http://localhost:5000/graphql
```

Vous pouvez tester les requêtes et mutations dans **GraphQL Playground** ou **Postman**.

---

## Exemples de requêtes GraphQL

### 1. Récupérer toutes les tâches

```graphql
query {
  tasks {
    id
    title
    description
    completed
    duration
  }
}
```
!(cap1.png)

### 2. Ajouter une nouvelle tâche

```graphql
mutation {
  addTask(title: "Nouvelle Tâche", description: "Détails", completed: false, duration: 8) {
    id
    title
    description
  }
}
```
!(caps\cap2.png)

### 3. Marquer une tâche comme complète

```graphql
mutation {
  completeTask(id: "1") {
    id
    completed
  }
}
```
!(caps\cap3.png)

### 4. Supprimer une tâche

```graphql
mutation {
  deleteTask(id: "2")
}
```
!(caps\cap4.png)
---

## Auteur

- **Mohamed Riadh Essridi**
- Classe : 4GL1
