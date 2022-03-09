# Workshop Webpack (avec Tailwind et React)

L'objectif de ce workshop est d'observer le fonctionnement d'un boilerplate pour
un début de single-page application avec Webpack, Tailwind et React.

## Installer node

Si node n'est pas installé sur votre système, ou que la version fournie par vos dépots
est trop vieille, installé une version récente de node avec [nvm](https://github.com/nvm-sh/nvm).

## L'objectif de Webpack

Dans le fichier `src/index.js`, on pourrait s'étonner de voir un JavaScript inhabituel:

```js
import "./styles.css"

import React from 'react'
import ReactDOM from 'react-dom'

import MainContainer from "./components/main_container"

ReactDOM.render(<MainContainer/>, document.getElementById('root'));
```

Déjà, à la première ligne, on importe un fichier CSS. Pourtant, la syntaxe du CSS
n'est pas conforme à celle de JavaScript.

Ensuite, de la même manière, on importe des packages installés avec Yarn. Pourtant,
le code final est censé être éxecuté dans un navigateur web, qui ne gère ni les
packages Node ni le mot-clé *import*.

À la dernière ligne, on remarque qu'une balise HTML s'est glissée en plein milieu d'un
appel de fonction. Là encore, cette syntaxe n'est pas supportée par le navigateur.

C'est ici que [Webpack](https://webpack.js.org/) rentre en jeu.

Webpack va tout simplement permettre d'organiser, grâce à un fichier de configuration,
une série d'outils pour construire une application à partir des fichiers sources.

Webpack va ensuite construire des *bundles*, des fichiers `.js` qui contiendront l'entiereté
du code ainsi généré. Ces bundles seront ensuite chargés intelligement dans le navigateur,
de façon à éviter le traffic inutile.

Dans ce projet, on aura besoin de plusieurs outils:

- [Babel](https://babeljs.io/), un compilateur qui comprend le Javascript "moderne".
- [Tailwindcss](https://tailwindcss.com/), un framework qui enrichie la syntaxe du CSS
et permet une façon de styliser des composants très pertinente lorsqu'il est couplé à
React.
- [React](https://reactjs.org/), un framework qui utilise entre autre la syntaxe JSX ainsi
que les classes pour coder des composants directement en Javascript.
- [PostCSS](https://postcss.org/), pour organiser le *build process* des fichiers CSS,
notemment avec Tailwind.

## Votre objectif

Voici quelques exemples de choses à faire pour ce workshop, choisissez l'option qui vous
paraît la plus pertinente à vos yeux.

- Intégrer un de vos projet existant à Webpack.
- Ajouter du contenu à la page web en comptant sur Webpack pour importer toute librairie externe.
    - ex: Ajouter des animations avec le package `animate.css`.
- Importer des images avec `import` et les afficher dans un composant React. Cela nécessitera
l'ajout d'un nouveau *loader* Webpack.

## Tester le projet d'exemple

```
yarn
yarn run webpack-dev-server
```