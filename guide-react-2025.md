#  Guide React.js en 2025 :

## 1. Introduction Générale – Pourquoi React est toujours pertinent en 2025 ?

**Popularité et communauté inégalées :** Plus d’une décennie après son lancement, React demeure l’une des bibliothèques front-end les plus utilisées et demandées. Elle s’est maintenue **n°1 des frameworks front-end** chaque année depuis 2016 selon les sondages, devançant constamment Vue.js et Angular ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=,JavaScript%20frameworks%20in%202025%2C%20leaving)). En 2022, **81,8 % des développeurs JavaScript utilisaient React** et près de la moitié des autres souhaitaient l’apprendre ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=,JavaScript%20frameworks%20in%202025%2C%20leaving)) ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=%2A%2081.8,claim%20the%20second%20spot%20in)). Cette large adoption s’accompagne d’un **écosystème riche** (des milliers de packages NPM), d’une documentation abondante et d’une communauté active, ce qui fait de React un choix sûr et pérenne.

**Évolution continue :** React a su évoluer pour rester à la pointe. Depuis l’introduction du **Virtual DOM** et du modèle déclaratif qui ont révolutionné le développement web, React a ajouté de nombreuses améliorations : le système de **composants fonctionnels avec Hooks** (qui a supplanté en grande partie les classes), l’optimisation du rendu avec **Fiber** et le **Mode Concurrent** (introduit en version 18), ou encore **Suspense** pour la gestion asynchrone ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=frameworks%20that%20rendered%20content%20dynamically,wide%20array%20of%20learning%20resources)) ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=,one%20of%20the%20world%E2%80%99s%20largest)). Récemment, React explore le rendu côté serveur au niveau des composants avec les **React Server Components (RSC)**, une nouveauté majeure qui réduit drastiquement le JavaScript envoyé au client. Ces évolutions successives, couplées à l’appui de **Meta (Facebook)** et de grandes entreprises, expliquent pourquoi **React reste un choix pertinent en 2025** pour des applications web modulaires, performantes et maintenables.

**Un écosystème complet :** L’un des atouts de React en 2025 est d’offrir un **éventail de solutions** pour tous les besoins de développement web. Que ce soit pour monter une simple SPA (Single-Page App) ou une application complexe, React s’intègre avec de nombreux outils : des bundlers modernes (Vite, webpack), des frameworks complets (Next.js, Remix), des solutions mobiles (React Native) ou desktop (Electron). Il existe des bibliothèques pour presque tout : routage, gestion d’état, utilitaires UI, etc. Cette versatilité, combinée aux bonnes pratiques que nous allons détailler, fait de React un **choix toujours d’actualité en 2025** malgré l’émergence de nouveaux concurrents.

## 2. Installation et Configuration – Démarrer un projet React moderne

Au fil du temps, les outils pour initialiser un projet React ont évolué. En 2025, on privilégie des solutions **légeres et rapides** pour le développement, tout en offrant des options pour le rendu côté serveur et l’intégration de TypeScript.

### 2.1 Setup avec **Vite** : la nouvelle référence pour les SPAs

Pour une application React standard (SPA en client-side rendering), **Vite** s’est imposé comme le successeur moderne de Create React App. Vite est un bundler ultra-rapide qui utilise *esbuild* sous le capot, offrant un rechargement à chaud quasi-instantané et une configuration minimale ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Vite%20is%20often%20considered%20the,has%20a%20smaller%20configuration%20overhead)) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=deviate%20much%20from%20it,has%20a%20smaller%20configuration%20overhead)). Contrairement à Create React App (CRA) qui embarquait webpack et beaucoup de configuration par défaut, Vite est **léger, non-opinionated**, et sert principalement de **serveur de développement ESM** efficace. Il reprend une structure similaire à CRA (il est quasiment un *drop-in replacement*), ce qui facilite la transition ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=React%20with%20Vite)) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=%2A%20almost%20a%20drop,getting%20to%20know%20React%27s%20fundamentals)).

**Création d’un projet avec Vite :** En pratique, démarrer un projet React avec Vite est simple. On utilise le scaffolding officiel :

```bash
# Création d'un projet React+Vite (JavaScript par défaut)
npm create vite@latest my-react-app -- --template react

# Pour TypeScript:
npm create vite@latest my-react-app-ts -- --template react-ts
```

<small>*Si vous avez Yarn : `yarn create vite` ou PNPM : `pnpm create vite` fonctionne de même.*</small>

Une fois lancé (`npm install` puis `npm run dev`), Vite offre un serveur de dev ultrarapide. Par défaut, il produit une application **SPA/CSR** (Client-Side Rendering). Cependant, Vite peut aussi prendre en charge le SSR de manière optionnelle si nécessaire (via un plugin), bien que pour des besoins avancés de SSR on se tourne souvent vers Next.js (voir section suivante) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Vite%20favors%20creating%20single,as%20Vue%2C%20Svelte%2C%20and%20Solid)). L’avantage de Vite est qu’il **n’impose aucune structure** au-delà du minimum : à vous de choisir vos bibliothèques de routage, de state management, etc. ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Vite%20with%20React%20allows%20developers,on%20you)). Cela en fait un excellent choix pour **apprendre React** ou pour des projets où l’on souhaite garder le contrôle total sur l’architecture.

**Pourquoi Vite plutôt que CRA ?** CRA n’est plus recommandée en 2025 car son bundler webpack rendait le rechargement lourd à mesure que le projet grossit. Vite apporte une approche modernisée (bundling différé des modules seulement quand nécessaire) qui accélère grandement l’expérience développeur ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Vite%20is%20often%20considered%20the,has%20a%20smaller%20configuration%20overhead)). De plus, CRA est officieusement *dépréciée* par la communauté en faveur de Vite ou Next.js ([Which is the standard now? create-react-app or vite? - Reddit](https://www.reddit.com/r/react/comments/195xnkd/which_is_the_standard_now_createreactapp_or_vite/#:~:text=Reddit%20www,app%20as%20it%27s%20outdated)). En résumé, **Vite = simplicité de CRA + vélocité inégalée**. 

### 2.2 Setup avec **Next.js** : le choix pour applications SSR et full-stack

Pour les applications plus complexes, nécessitant du **rendu serveur (SSR)**, du **prérendu statique (SSG)**, ou un backend intégré, **Next.js** est devenu le framework React de référence. Next.js fournit une structure « batteries incluses » autour de React, avec un écosystème mature et une excellente intégration des nouveautés React. C’est le choix évident si vous souhaitez utiliser React dans un cadre **opinionated** et full-stack ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=React%20with%20Next)).

**Création d’un projet Next.js :** La commande officielle est tout aussi simple : 

```bash
npx create-next-app@latest my-next-app --typescript
# ce qui configure un projet Next 13+ avec TypeScript, ESLint, etc.
```

Après l’installation, vous avez une application structurée, avec un dossier `pages/` (ou `app/` pour le nouveau mode App Router) pour vos pages, un routage automatique, le support de l’SSR et SSG prêt à l’emploi, la gestion d’images optimisée, etc.

**Rendu universel et RSC :** Next.js prend en charge **toutes les méthodes de rendu** : SSR, SSG, ISR (Incremental Static Regeneration) et CSR ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Next.js%20prioritizes%20server,RSF%29%20as%20architectural%20primitives)) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=use%20SSG%2C%20the%20actual%20application,keep%20up%20with%20the%20pace)). Depuis Next.js 13, le *App Router* utilise par défaut les **React Server Components (RSC)** pour un rendu plus performant (nous détaillerons les RSC plus loin). Next permet ainsi de mélanger dans la même application des pages statiques, des pages rendues à la volée sur le serveur, et des composants purement client, en profitant de chaque approche là où elle est pertinente ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=What%20makes%20this%20even%20more,keep%20up%20with%20the%20pace)). Par exemple, une page marketing peut être générée statiquement (SSG) pour une performance maximale, tandis qu’une page utilisateur personnalisée peut être rendue serveur à chaque requête (SSR) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=What%20makes%20this%20even%20more,keep%20up%20with%20the%20pace)). **Next.js offre cette flexibilité sous une API unifiée**, ce qui en 2025 est un atout précieux pour optimiser à la fois les performances et le SEO.

**Full-stack et API intégrées :** Contrairement à React seul (où il faut un backend séparé), Next.js permet de créer des applications *full-stack*. Il embarque un système d’API routes (fonctions serverless) et gère l’authentification, les accès BDD, etc., au sein même du projet. Avec l’arrivée des **Server Actions/Functions** (expérimental dans React 18+), Next permet même de définir des actions serveur directement aux côtés de vos composants ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=While%20React%20itself%20only%20allows,RSF)) ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=%2A%20full,and%20many%20other%20rendering%20techniques)). En somme, Next vise à faire de **React un framework full-stack**, ce que confirment ses évolutions récentes ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=While%20React%20itself%20only%20allows,RSF)). 

**Pourquoi Next.js ?** En 2025, Next.js est prisé car il « emballe » les bonnes pratiques : le routage basé fichier, la division du code, la configuration webpack/vite gérée, le support TypeScript par défaut, etc. Il a le soutien de Vercel (éditeur de Next), qui collabore étroitement avec l’équipe React pour pousser les limites (Next a souvent été le terrain d’essai des nouveautés React comme les RSC). Le revers de la médaille est que Next.js ajoute une couche de complexité et évolue vite : adopter Next, c’est accepter de suivre de près ses mises à jour (par ex, la transition Next 12 -> 13 avec le nouvel App Router a été significative). Malgré cela, pour une application professionnelle évolutive, Next.js est souvent le **meilleur choix en production** grâce aux fonctionnalités intégrées et à son **écosystème robuste**.

### 2.3 TypeScript avec React : une évidence en 2025

Quel que soit le setup (Vite, Next ou autre), l’usage de **TypeScript** est fortement répandu en 2025 dans l’écosystème React. TypeScript apporte le typage statique à JavaScript, ce qui améliore la fiabilité et la maintenabilité du code à mesure qu’une codebase grossit. 

**Installation :** Avec Vite ou Next, il suffit souvent de choisir le template TypeScript (`--template react-ts` avec Vite, ou `--typescript` avec create-next-app). Si on migre un projet existant, installer les dépendances `typescript` + `@types/react` + `@types/react-dom`, puis renommer les fichiers `.js` en `.tsx` (pour composants) ou `.ts`. 

**Configuration :** Un fichier `tsconfig.json` sera généré par défaut. React fonctionne sans configuration spéciale (juste s’assurer que `"jsx": "react-jsx"` est activé pour la compilation JSX). La plupart des outils (CRA, Vite, Next) configurent cela automatiquement.

**Pourquoi TypeScript ?** En 2025, TypeScript est devenu quasi indispensable sur les projets sérieux. Il attrape à la compilation de nombreuses erreurs (props manquantes, types mal utilisés) et facilite l’auto-complétion IDE. Next.js et Vite intègrent très bien TS (Next supporte les types pour les `getServerSideProps` etc.). La transition vers TS a été massive ces dernières années dans l’écosystème React, et la majorité des librairies fournissent maintenant leurs définitions de types. En résumé, **choisir TypeScript permet d’éviter bien des bugs en amont et de documenter son code par les types**, ce qui est précieux sur les projets complexes de 2025.

**Outils de Lint et formatage :** N’oublions pas en setup d’ajouter ESLint (souvent inclus dans Next, ou via `npm init @eslint/config`) et Prettier pour assurer un code propre et homogène. Le plugin `eslint-plugin-react` et éventuellement `eslint-plugin-react-hooks` vous aideront à respecter les conventions React (par ex, règles des Hooks). Un fichier de configuration standard avec extends `"plugin:react/recommended"` et `"plugin:react-hooks/recommended"` convient dans la plupart des cas.

## 3. Les Bases de React – Composants, JSX et Hooks fondamentaux

Une fois l’environnement prêt, il est crucial de maîtriser les **fondamentaux de React** : la notion de composant et de JSX, puis les Hooks de base pour la gestion d’état et le cycle de vie fonctionnel.

### 3.1 JSX et Composants : la construction de l’UI en React

**JSX – JavaScript XML:** JSX est la syntaxe propre à React qui permet d’écrire du HTML imbriqué directement dans le JavaScript. Concrètement, plutôt que d’utiliser `React.createElement(...)` à la main, on peut écrire : 

```jsx
const element = <h1>Hello, world!</h1>;
```

Dans ce code, `<h1>Hello</h1>` ressemble à du HTML, mais c’est du **JSX**. C’est en fait du sucre syntaxique transformé en appels React (via Babel) au moment du build. **JSX décrit à quoi doit ressembler l’UI** en combinant la puissance de JavaScript et la simplicité du XML. Officiellement, *« JSX est une extension de syntaxe à JavaScript qui permet d’écrire des éléments HTML dans du JS »* ([JSX in React - Detailed Explanation with example](https://webwithnikhil.hashnode.dev/jsx-in-react-detailed-explanation-with-example#:~:text=What%20is%20JSX%3A)). Le navigateur ne peut pas lire JSX tel quel, mais les outils de compilation (Babel) le transforment en code JS standard.

JSX peut inclure **des expressions dynamiques** en JavaScript, en les plaçant entre accolades `{ }`. Exemple : 

```jsx
const name = "Alice";
const element = <p>Bonjour, {name.toUpperCase()} !</p>;
```

Ici, l’expression `{name.toUpperCase()}` sera évaluée et son résultat inséré dans le JSX ([JSX in React - Detailed Explanation with example](https://webwithnikhil.hashnode.dev/jsx-in-react-detailed-explanation-with-example#:~:text=The%20following%20example%20declares%20a,wrapping%20it%20in%20curly%20braces)). On peut mettre toute expression JS valide entre accolades (opérations ternaires, appels de fonction, etc.), ce qui rend JSX extrêmement puissant pour générer du contenu dynamique.

**Composants React :** Les composants sont les briques de base d’une application React. Un **composant** est soit une fonction, soit une classe, qui **retourne du JSX** représentant une partie de l’UI. React va organiser ces composants hiérarchiquement pour former l’interface complète. *« Les composants vous permettent de découper l’UI en pièces indépendantes et réutilisables, et de penser à chaque pièce isolément »* ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=Components%20let%20you%20split%20the,detailed%20component%20API%20reference%20here)). 

En pratique, on écrit aujourd’hui quasi exclusivement des **composants fonctionnels**. Par exemple :

```jsx
function Welcome(props) {
  return <h1>Bonjour, {props.name}</h1>;
}
```

Ce composant `Welcome` prend des **props** (ici `props.name`) et retourne un élément `<h1>` personnalisé ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=The%20simplest%20way%20to%20define,to%20write%20a%20JavaScript%20function)). Pour l’utiliser, on peut l’inclure dans du JSX comme une balise : `<Welcome name="Alice" />`. React va appeler la fonction en lui passant `{ name: "Alice" }` comme `props` ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=However%2C%20elements%20can%20also%20represent,defined%20components)), puis récupérer l’élément retourné (`<h1>Bonjour, Alice</h1>`). 

En JSX, dès qu’on utilise un élément dont le nom commence par une majuscule, React le traite comme un **composant personnalisé** (et non une balise HTML native) ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=1.%20We%20call%20,h1)). 

Exemple d’utilisation dans un rendu :

```jsx
const app = <div>
  <Welcome name="Alice" />
  <Welcome name="Bob" />
</div>;
ReactDOM.createRoot(document.getElementById('root')).render(app);
```

Ce code affichera deux titres de bienvenue pour Alice et Bob. Chaque instance de composant reçoit ses propres props.

**Props et état :** Les *props* (propriétés) sont les données passées d’un parent à un composant enfant, de manière immuable. Un composant peut aussi avoir un **état interne** mutable pour gérer des données qui changent au cours du temps (voir Hook *useState* ci-dessous). On distingue donc « **données de présentation** » (via props) et « **données internes** » (via state). React suit un flux de données **unidirectionnel (top-down)** : les props descendent du parent vers l’enfant, garantissant une certaine prévisibilité ([27 Best JavaScript Frameworks For 2025 | LambdaTest](https://www.lambdatest.com/blog/best-javascript-frameworks/#:~:text=without%20a%20hitch.%20,This%20is)).

Notons qu’il existe aussi les **composants classes** (définis via `class MyComponent extends React.Component` avec une méthode `render()` qui retourne du JSX ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=You%20can%20also%20use%20an,class%20to%20define%20a%20component))). Ils étaient courants avant 2019, car seuls les composants classes géraient l’état et le cycle de vie. Mais depuis l’introduction des Hooks, on peut faire tout cela dans des fonctions, rendant les classes largement obsolètes. On les mentionne pour mémoire, mais en pratique *ce guide se concentre sur les fonctionnels + Hooks*, le standard actuel.

### 3.2 Hooks fondamentaux – useState, useEffect, useRef, useMemo, useCallback

Les **Hooks** (apparus en React 16.8) sont des fonctions spéciales permettant d’« accrocher » des fonctionnalités React à nos composants fonctionnels. Les principaux Hooks à connaître dès le début sont : `useState`, `useEffect`, `useRef`, `useMemo`, `useCallback`. Chacun répond à un besoin spécifique.

- **useState – état local du composant :** `useState` permet d’ajouter un *state* dans une fonction composant. *« useState est un Hook qui vous permet d’ajouter un état React à des composants fonctionnels »* ([Using the State Hook – React](https://legacy.reactjs.org/docs/hooks-state.html#:~:text=What%20is%20a%20Hook%3F%20A,We%E2%80%99ll%20learn%20other%20Hooks%20later)). On l’appelle ainsi : 

  ```jsx
  import { useState } from 'react';
  function Counter() {
    const [count, setCount] = useState(0); // état initial à 0
    // ...
  }
  ```
  
  Ici, on déclare un état `count` avec sa fonction de mise à jour `setCount`. `useState(0)` initialise `count` à `0`. À chaque rendu, React nous redonnera la valeur courante de `count`. Pour la modifier, on appelle `setCount(nouvelleValeur)` et React re-rendra le composant avec cette mise à jour. **Exemple concret :**
  
  ```jsx
  function Counter() {
    const [count, setCount] = useState(0);
    return (
      <div>
        <p>Vous avez cliqué {count} fois</p>
        <button onClick={() => setCount(count + 1)}>Cliquez-moi</button>
      </div>
    );
  }
  ```
  
  À chaque clic, `setCount(count + 1)` indique à React de **re-render** le composant `Counter` avec `count` incrémenté. React s’assure de **préserver la valeur de `count` entre les rendus** (c’est le but du Hook) et de n’afficher que les changements nécessaires dans le DOM.

  > 🔎 *À savoir :* React garantit que l’appel à `useState` renvoie la même paire `[state, setState]` à chaque rendu, en maintenant en interne une mémoire pour chaque Hook appelé dans l’ordre. On ne doit appeler les Hooks qu’au **top-level** du composant (pas dans une boucle ou un `if`), afin de conserver cet ordre d’appel stable d’un rendu à l’autre.

- **useEffect – effets de bord et cycle de vie :** `useEffect` sert à exécuter du code après le rendu, typiquement pour des *effets de bord* : appels API, abonnements, mise à jour manuelle du DOM, logging… *« En utilisant ce Hook, vous dites à React que votre composant doit faire quelque chose **après** le rendu » ([Using the Effect Hook – React](https://legacy.reactjs.org/docs/hooks-effect.html#:~:text=What%20does%20,call%20some%20other%20imperative%20API))】. En classe, on utilisait `componentDidMount/Update`; avec les Hooks, un `useEffect` englobe ces usages. Exemple :

  ```jsx
  import { useEffect } from 'react';
  function App() {
    const [data, setData] = useState(null);
    useEffect(() => {
      // Effet : appel fetch après le rendu initial
      fetch('/api/todos').then(res => res.json()).then(setData);
    }, []); // [] = dépendances, ici vide => effet exécuté une fois en montage
    
    // ...
  }
  ```
  
  Dans cet exemple, le `useEffect` avec dépendances `[]` se déclenche une seule fois au montage du composant (comportement équivalent à `componentDidMount`). On aurait pu ne pas mettre de tableau ou y mettre des variables dépendantes pour exécuter l’effet après chaque mise à jour de ces variables.  
  **Explications :** Quand React render `<App />` la première fois, il exécute le contenu du composant puis, une fois le DOM mis à jour, il appelle la fonction passée à `useEffect`. Ici on en profite pour démarrer un *fetch*. On pourrait aussi utiliser `useEffect` pour :
  
  - Mettre à jour le document.title en fonction d’un state (ex: compteur ([Using the Effect Hook – React](https://legacy.reactjs.org/docs/hooks-effect.html#:~:text=What%20does%20,call%20some%20other%20imperative%20API))】.
  - Souscrire à un flux (un WebSocket, un événement navigateur) lors du mount, et **nettoyer** à l’unmount. Pour cela, le Hook peut retourner une fonction de cleanup qui sera exécutée avant le prochain effet ou lors de la destruction du composant.
  
  Exemple de cleanup :
  ```js
  useEffect(() => {
    const id = setInterval(() => console.log('tick'), 1000);
    return () => clearInterval(id); // nettoyage à la fin
  }, []);
  ```
  
  Ainsi `useEffect` couvre le rôle de `componentWillUnmount` via la fonction de retour.  
  👉 En résumé, `useEffect` est **LE** Hook pour orchestrer du code en réaction au cycle de vie du composant : après chaque rendu initial ou mise à jour (selon dépendances fournies). Par défaut, un useEffect sans dépendances spécifiques s’exécute après **chaque** ren ([Using the Effect Hook – React](https://legacy.reactjs.org/docs/hooks-effect.html#:~:text=specific%20APIs%20where%20JavaScript%20already,provides%20a%20solution))0】.

- **useRef – Référence mutable :** `useRef` fournit un moyen de conserver une valeur mutablie *qui persiste à travers les rendus* sans provoquer de re-render quand elle change. On l’utilise souvent pour **stocker une référence vers un élément DOM** ou une valeur quelconque dont on veut se souvenir sans la mettre dans le state. Par exemple :

  ```jsx
  import { useRef, useEffect } from 'react';
  function FocusInput() {
    const inputRef = useRef(null);
    useEffect(() => {
      inputRef.current.focus(); // met le focus sur l'input après le rendu
    }, []);
    return <input ref={inputRef} type="text" />;
  }
  ```

  Ici `useRef(null)` initialise une ref dont la propriété `.current` pointera vers l’élément `<input>` DOM une fois rendu. On peut ainsi manipuler directement le DOM (focus, scroll, etc.). Contrairement à useState, **modifier `inputRef.current` ne déclenche pas de rendu**. C’est simplement une boîte où stocker une valeur persistante.

  Autre usage : conserver une valeur précédente. Ex :
  ```js
  const prevCount = useRef(count);
  useEffect(() => {
    prevCount.current = count;
  }); 
  ```
  À chaque rendu, `prevCount.current` gardera l’ancienne valeur de `count`, accessible au prochain rendu. Ce type de mécanisme est utile pour comparer l’évolution de props ou états entre deux renders sans engendrer de nouvelle render, ou pour stocker un identifiant unique.

- **useMemo – calcul mémoïsé :** `useMemo` sert à **mémoïser le résultat d’un calcul coûteux** afin de l’éviter aux rendus suivants si les données d’entrée n’ont pas changé. En d’autres termes, on demande à React de *cacher* le résultat d’une fonction entre deux renders. *« `useMemo` est un Hook React qui vous permet de mettre en cache le résultat d’un calcul entre les re-rendus  ([reactjs - Understanding of useMemo (does useMemo actually memoize?) - Stack Overflow](https://stackoverflow.com/questions/77144467/understanding-of-usememo-does-usememo-actually-memoize#:~:text=React%20documentation%20of%20))7】. Syntaxe :

  ```jsx
  const result = useMemo(() => computeExpensiveValue(x, y), [x, y]);
  ```

  Ici, la fonction `computeExpensiveValue(x, y)` ne sera recalculée que si `x` ou `y` changent ; sinon, React renverra la valeur mémoïsée du dernier ren ([useMemo – React](https://react.dev/reference/react/useMemo#:~:text=On%20the%20initial%20render%2C%20,with%20no%20arguments))4】. C’est utile pour optimiser des calculs intensifs (filtrage d’une grande liste, calcul math lourd, etc.) pour ne pas les refaire inutilement à chaque render. **Attention :** on utilise useMemo *uniquement* pour optimiser – il ne doit pas affecter le résultat fonctionnel, seulement les performances. Si le calcul est léger, pas besoin de useMemo (cela ajoute une complexité inutile).

  Exemple concret :
  ```js
  const sortedList = useMemo(() => heavySort(list), [list]);
  ```
  Cela évite de trier `list` à chaque rendu si `list` est inchangée.

- **useCallback – fonction mémoïsée :** `useCallback` est à useMemo ce que les fonctions sont aux valeurs. Il renvoie la **même fonction** entre les rendus tant que ses dépendances ne changent pas. *« `useCallback` est un Hook qui permet de cacher (mémoïser) une définition de fonction entre deux re-rendus  ([useCallback – React](https://react.dev/reference/react/useCallback#:~:text=useCallback))6】. Syntaxe :

  ```jsx
  const handleClick = useCallback(() => {
    doSomething(param);
  }, [param]);
  ```

  Ce Hook est souvent utilisé pour **mémoriser des callbacks passés à des composants enfants** afin d’éviter de retrigger leur re-rendu inutilement. Par exemple, si on passe une prop de type fonction à un composant optimisé (via `React.memo`), il est utile que la référence de cette fonction reste stable tant que possible. `useCallback` renvoie la même fonction `handleClick` tant que `param` reste identiq ([useCallback – React](https://react.dev/reference/react/useCallback#:~:text=useCallback))6】.

  Autre usage : éviter de recréer des gestionnaires d’événements lourds à chaque rendu.

**À retenir :** `useMemo` et `useCallback` sont des outils d’optimisation (voir section Performance), pas à utiliser systématiquement. Ne les employez que si un problème de performance concret se pose, car un usage excessif peut complexifier le code pour un gain négligeable.

### 3.3 Exemple complet – Composant combinant plusieurs Hooks

Pour illustrer l’usage combiné de ces Hooks, voici un exemple de composant commenté :

```jsx
import React, { useState, useEffect, useRef, useMemo, useCallback } from 'react';

function SearchList({ items }) {
  // State pour le terme de recherche
  const [query, setQuery] = useState('');
  // Ref pour stocker le dernier terme de recherche validé (pour illustrer useRef)
  const lastSearch = useRef('');
  
  // Mémoriser la liste filtrée via useMemo pour éviter de recalculer à chaque frappe si inutile
  const filteredItems = useMemo(() => {
    console.log('Filtrage en cours...');
    return items.filter(item => item.includes(query));
  }, [items, query]);
  
  // Callback mémoïsé pour afficher la sélection (pour démonstration useCallback)
  const handleSelect = useCallback((item) => {
    alert(`Vous avez sélectionné "${item}"`);
  }, []);  // pas de dépendance, la fonction ne dépend d'aucune variable externe
  
  // Effet : log du terme de recherche quand il change
  useEffect(() => {
    if (query) {
      console.log(`Nouvelle recherche: ${query}`);
      lastSearch.current = query; // stocke la dernière recherche non-vide
    }
  }, [query]);
  
  return (
    <div>
      <input 
        value={query}
        onChange={e => setQuery(e.target.value)}
        placeholder="Rechercher..."
      />
      <p>Résultats pour "<b>{query}</b>" ({filteredItems.length} éléments)</p>
      <ul>
        {filteredItems.map(item => (
          <li key={item}>
            {item} <button onClick={() => handleSelect(item)}>Sélectionner</button>
          </li>
        ))}
      </ul>
      <p style={{ fontStyle: 'italic', color: '#555' }}>
        Dernière recherche effectuée : "{lastSearch.current}"
      </p>
    </div>
  );
}
```

**Explication :** Ce composant `SearchList` maintient un champ de recherche contrôlé par l’état `query`. À chaque changement, on filtre la liste `items` reçue via une fonction potentiellement lourde (ici un simple `.filter`, mais imaginez un calcul plus complexe). On utilise donc `useMemo` pour ne faire le filtrage que lorsque `query` ou `items` changent, évitant du travail inutile. Un `console.log` dans le filtre permet de voir que le filtrage n’est pas appelé à chaque rendu si `query` reste le même.

Le Hook `useEffect` ici enregistre simplement la dernière recherche non vide dans `lastSearch.current` (via `useRef`) et logge la requête. La ref `lastSearch` persiste entre rendus sans provoquer de re-render lorsqu’on la met à jour. Enfin, `useCallback` fixe la référence de la fonction `handleSelect` pour éviter de la recréer à chaque rendu (bien que dans ce cas précis, l’utilité soit limitée puisque `handleSelect` ne dépend de rien; on le montre surtout par pédagogie).

Ainsi, on voit dans un même composant l’utilisation combinée de plusieurs Hooks de base, chacun ayant un rôle précis : état local, effet sur mise à jour, mémoïsation de valeur calculée, ref persistante, et callback stable.

## 4. State Management Moderne – Context, Redux Toolkit, Zustand, Jotai

Pour des applications de taille intermédiaire à grande, la gestion de l’état global (partagé entre multiples composants) devient un défi. React propose le **Context API** en natif et l’écosystème offre des solutions populaires comme **Redux** (désormais via Redux Toolkit), ou plus récentes comme **Zustand** et **Jotai**. Chacune a ses avantages selon la complexité de l’état à gérer.

### 4.1 Contexte React (Context API)

Le **Context API** est intégré à React depuis la v16.3 et permet de partager des données **globalement** à travers la hiérarchie de composants sans passer explicitement par les props à chaque niveau. *« Le Contexte offre un moyen de passer des données à travers l’arborescence de composants sans avoir à passer explicitement des props à chaque niveau  ([Context - React](https://legacy.reactjs.org/docs/context.html#:~:text=Context%20provides%20a%20way%20to,a%20typical%20React%20application%2C))9】. On crée un contexte via `React.createContext(valeurInitiale)` puis on englobe son arbre dans un `<MonContexte.Provider value={…}>` pour fournir la donnée, et enfin les composants enfants peuvent consommer cette donnée via un `useContext(MonContexte)`.

**Cas d’usage :** thèmes visuels, utilisateur connecté, paramètres d’application, ou tout état “global” qu’on ne veut pas passer de parent en parent. Par exemple, un contexte `ThemeContext` qui fournit le thème (“clair” ou “sombre”) à toute l’appli, évitant de propager ce choix manuellement partout.

**Limites :** Le contexte n’est pas une panacée pour tout état global. Il est parfait pour des données relativement **stables** ou peu fréquemment mises à jour (ex : thème, locale). En revanche, si on y stocke un état qui change souvent, chaque changement re-render *tous* les consommateurs du contexte, ce qui peut dégrader les performances. React 18 a amélioré les performances du contexte, mais cela reste un point d’attention. Pour des états plus conséquents (beaucoup de données, mise à jour fréquente, logique métier poussée), on recourt souvent à des bibliothèques externes offrant plus de fonctionnalités (timelines d’actions, outils de debug, etc.).

### 4.2 Redux Toolkit – État global prévisible et structuré

**Redux** a longtemps été l’outil phare pour la gestion d’état global dans les applications React. Il impose un modèle **unidirectionnel strict** (flux d’actions -> reducers -> store) et une architecture prévisible. Toutefois, Redux pur avait la réputation d’exiger beaucoup de code *boilerplate*. C’est là qu’intervient **Redux Toolkit (RTK)**, la version moderne et simplifiée de Redux. D’ailleurs, *« Redux Toolkit est la méthode recommandée officiellement pour écrire la logique Redux  ([Getting Started with Redux](https://redux.js.org/introduction/getting-started#:~:text=Getting%20Started%20with%20Redux%20Redux,and%20contains%20packages%20and))6】 depuis 2019.

**Ce qu’apporte Redux Toolkit :** 
- Un utilitaire `configureStore` qui crée le store avec les bonnes options par défaut (inclus immer, redux-thunk, etc.).
- La fonction `createSlice` qui permet de définir *state initial + reducers + actions* en une fois, avec une syntaxe concise. On peut ainsi écrire des *reducers mutables* (grâce à Immer qui gère l’immutabilité en coulisse).
- Des bonnes pratiques intégrées (par exemple, il interdit les mutations directes du state dans un reducer hors Immer).
- (Optionnel) **RTK Query** : un outil intégré pour les appels API et le caching de données serveur, évitant d’ajouter des libs type React Query à part.

**Exemple d’utilisation Redux Toolkit :**

```js
// store.js
import { configureStore, createSlice } from '@reduxjs/toolkit'

const todosSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => { state.push(action.payload) },
    removeTodo: (state, action) => { return state.filter(todo => todo.id !== action.payload) }
  }
});

export const { addTodo, removeTodo } = todosSlice.actions;
export const store = configureStore({
  reducer: { todos: todosSlice.reducer }
});
```

Ici on définit un état `todos` (liste), avec deux reducers (ajout, suppression). On exporte les actions créées automatiquement (`addTodo` etc.) et le store configuré. Dans le composant, on utilise `useSelector` pour lire le state et `useDispatch` pour envoyer les actions :

```jsx
import { useSelector, useDispatch } from 'react-redux';
import { addTodo, removeTodo } from './store';

function TodoApp() {
  const todos = useSelector(state => state.todos);
  const dispatch = useDispatch();
  // ...
  dispatch(addTodo({ id: 5, text: 'Acheter du lait' }));
}
```

**Avantages :** Redux (avec RTK) excelle pour des **états globaux complexes** impliquant de nombreuses mutations, une logique de mise à jour élaborée, ou le besoin d’outils de debug (le Redux DevTools est très pratique pour visualiser le flux d’actions). Il est **prédictible** et encourage une architecture claire en séparant données et affichage. Redux Toolkit élimine 80% du code répétitif, rendant Redux à nouveau attractif en 2025 pour des applications de grande envergure.

**Inconvénients :** Même simplifié, Redux ajoute une couche d’abstraction (notion de store, actions, etc.) qui peut sembler lourde pour de petites applis. Pour un état global léger, c’est parfois *trop* d’infrastructure. De plus, gérer tout via Redux peut conduire à un store monolithique si on n’organise pas bien ses slices. Enfin, Redux impose de la **cérémonie** (même si RTK la réduit) et une certaine courbe d’apprentissage. C’est pourquoi sont apparues des alternatives plus simples.

### 4.3 Zustand – État global simple comme un Hook

**Zustand** (mot allemand pour « état ») est une bibliothèque légère de gestion d’état global, construite sur une API de Hooks. Son slogan : *« Un petit state manager *barebones* rapide et évolutif, utilisant des principes flux simplifiés. Il offre une API confortable basée sur les hooks, sans boilerplate et non opinionated  ([GitHub - pmndrs/zustand:  Bear necessities for state management in React](https://github.com/pmndrs/zustand#:~:text=A%20small%2C%20fast%20and%20scalable,hooks%2C%20isn%27t%20boilerplatey%20or%20opinionated))3】. En pratique, Zustand permet de créer un store global très facilement, sans le formalisme de Redux.

**Utilisation basique :** 

```js
import create from 'zustand';

const useStore = create(set => ({
  bears: 0,
  increase: () => set(state => ({ bears: state.bears + 1 })),
  clear: () => set({ bears: 0 })
}));
```

On obtient un Hook `useStore` que l’on peut utiliser dans n’importe quel composant :

```jsx
function BearCounter() {
  const bears = useStore(state => state.bears);
  const increase = useStore(state => state.increase);
  return <div>
    <h1>{bears} ours dans la réserve</h1>
    <button onClick={increase}>+1 ours</button>
  </div>;
}
```

Ici, `useStore(selector)` nous donne accès à la portion de state souhaitée, et le composant se re-render **automatiquement** quand cette partie du state chan ([GitHub - pmndrs/zustand:  Bear necessities for state management in React](https://github.com/pmndrs/zustand#:~:text=Use%20the%20hook%20anywhere%2C%20no,render%20on%20changes))4】. Pas besoin de Provider ou de connecteur : le Hook `useStore` gère tout (il utilise le Context API en interne, mais de façon optimisée).

**Points forts :** Zustsand est extrêmement **léger** à mettre en place (quelques lignes pour définir un store) et n’impose pas de structure. On peut avoir plusieurs stores si on veut séparer des logiques. Il est **rapide** et évite les pièges classiques (il mentionne par ex résoudre le problème du « zombie child » qu’on rencontrait parfois avec Redux ou Conte ([GitHub - pmndrs/zustand:  Bear necessities for state management in React](https://github.com/pmndrs/zustand#:~:text=Don%27t%20disregard%20it%20because%20it%27s,gets%20all%20of%20these%20right))3】). Son API étant proche des Hooks React, il est simple à apprendre : on a l’impression d’utiliser un `useState` global. 

En 2025, de nombreux développeurs adoptent Zustand pour des projets de taille moyenne où Redux semblerait trop lourd. Par exemple, pour une application où l’état global se limite à quelques objets (utilisateur courant, panier e-commerce, etc.) avec des mises à jour simples, Zustand fait le travail avec un code minimal.

**Limites :** Zustand ne fournit pas nativement d’outils comme Redux DevTools (quoique on peut brancher une extension). Il est moins structurant, donc c’est au développeur d’organiser son store proprement. En cas d’app très grande, on risque aussi de recréer un mini-Redux (plusieurs slices, etc.) – à ce stade, peut-être que Redux aurait été aussi bien. Toutefois, Zustand supporte la composition de stores et reste performant (utilise un algorithme intelligent pour ne re-render que les composants dont la sélection de state a changé). 

En somme, **Zustand simplifie la gestion d’état global** en la ramenant à l’essentiel : un store comme simple objet JavaScript, modifié via des fonctions, et accessible via un Hook. Cette approche rencontre un fort succès en 2025 pour sa **simplicité sans compromis majeur sur la performance**.

### 4.4 Jotai – État global atomique et découplé

**Jotai** (mot japonais pour « atome ») propose une approche différente, inspirée de Recoil (librairie développée par Facebook) : l’**atomic state management**. Dans Jotai, on modélise l’état global non pas comme un seul store monolithique, mais comme un ensemble d’**atomes** indépendants. *« Jotai adopte une approche atomique de la gestion d’état globale : on construit l’état en combinant de petits atomes, et les rendus sont automatiquement optimisés en fonction des dépendances à ces atomes  ([Jotai, primitive and flexible state management for React](https://jotai.org/#:~:text=Jotai%20takes%20an%20atomic%20approach,to%20global%20React%20state%20management))0】. Chaque composant peut s’abonner à un ou plusieurs atomes, et ne re-rendra que si les atomes qu’il utilise changent, évitant le problème de re-rendus en cascade du Context classique.

**Principe :** On crée des *atoms* via `atom(initialValue)` :

```js
import { atom, useAtom } from 'jotai';
const countAtom = atom(0);
```

Puis dans un composant :

```jsx
function Counter() {
  const [count, setCount] = useAtom(countAtom);
  return <button onClick={() => setCount(c => c+1)}>Compteur : {count}</button>;
}
```

Ici, `useAtom(countAtom)` joue un rôle similaire à `useState`, sauf que l’état est global et partagé. On peut utiliser `countAtom` dans n’importe quel composant, tous verront la même valeur et seront mis à jour ensemble quand elle change. On peut aussi définir des *derived atoms* qui dépendent d’autres atomes :

```js
const doubleCountAtom = atom((get) => get(countAtom) * 2);
```

Ensuite `useAtom(doubleCountAtom)` renverra toujours le double de count, recalculé à la volée quand `countAtom` change. On peut également écrire des atomes async (pour des données fetchées) ou des atoms write-only pour encapsuler de la logique.

**Avantages :** Jotai offre une **granularité fine** : chaque atome est comme une cellule d’état isolée. Les composants ne lisent que ce dont ils ont besoin. Cela évite l’effet boule de neige où modifier une valeur dans un contexte force le re-render de toute l’arborescence consommatrice de ce contexte. Jotai élimine quasiment le besoin de mémoïser ou d’optimiser les re-rendus liés à l’état global, car le moteur interne s’en charge (un composant ne se rend que si un atome dont il dépend a changé, sinon il reste inta ([Jotai, primitive and flexible state management for React](https://jotai.org/#:~:text=Jotai%20takes%20an%20atomic%20approach,to%20global%20React%20state%20management))0】). C’est donc **performant par conception**.

De plus, Jotai est assez **flexible** pour convenir à des petites ou grosses apps : on peut commencer en l’utilisant comme un simple `useState` global, puis évoluer en structurant différents atomes.

**Limites :** Le concept d’atomes peut demander un petit effort de compréhension initial (différent de Redux ou Zustand). Pour des états très liés, ça marche bien, mais si on doit orchestrer plusieurs atomes ensemble (ex: mises à jour dépendantes), il faut penser aux atoms dérivés ou write functions. Cela reste globalement simple, mais c’est un paradigme différent. 

Jotai étant encore relativement jeune, son écosystème est plus restreint que Redux (mais on trouve des extensions pour la persistance, l’immer, etc.). Néanmoins, il est **production-ready** et utilisé dans des entreprises innovant ([Jotai, primitive and flexible state management for React](https://jotai.org/#:~:text=Jotai%20is%20trusted%20in%20production,at%20innovative%20companies%20like%20these))4】.

**Quand choisir quoi ?** – En 2025, on peut dresser quelques recommandations : 

- Pour **un état global minimal** (quelques variables), utilisez **Context** ou un petit store **Zustand** pour la facilité.
- Pour **une app complexe d’envergure** où la prédictibilité et les outils de debug sont cruciaux, **Redux Toolkit** reste une valeur sûre.
- Pour un besoin d’état global **modulaire et ultra-réactif** (beaucoup d’inter-dépendances fines), **Jotai** offre une solution élégante en évitant les re-rendus inutiles.
- N’hésitez pas à **combiner les approches** : par exemple, Context pour des configs globales statiques + Zustand pour un état global business, ou Redux pour certaines parties et Context pour d’autres. L’important est de garder le code clair.

Enfin, notez qu’il existe d’autres libraries non abordées ici, comme **MobX** (orienté POO réactive) ou **XState** (machines à états), qui peuvent convenir à des cas spécifiques. L’arsenal React est riche – mais pour la plupart des cas, les solutions ci-dessus couvrent bien les besoins en privilégiant soit la simplicité (Zustand, Context) soit la robustesse et structure (Redux) ou la granularité (Jotai).

## 5. React Server Components (RSC) – Rendu côté serveur au niveau du composant, avec Next.js

Les **React Server Components** représentent l’une des avancées les plus marquantes de React récemment. Introduits en alpha fin 2021 et popularisés via Next.js 13+, ils permettent de faire tourner des composants React **entièrement sur le serveur**, sans envoyer leur code JS au client, tout en s’intégrant dans une arborescence de composants client. En 2025, les RSC sont en voie de stabilisation et Next.js les utilise par défaut pour améliorer les performances des applications.

### 5.1 Principe des RSC et avantages

Traditionnellement, deux modes de rendu React existaient :
- **CSR (Client-Side Rendering)** pur : on envoie une page quasi vide et un gros bundle JS au client, qui exécute React pour construire le DOM. Problème : temps au premier rendu plus lent, SEO et performance initiale moins bonn ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=Since%20React%20rose%20to%20the,cause%20of%20concern%20for%20developers)) ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=The%20problem%20with%20this%20approach,best%2C%20causing%20poor%20SEO%20performance))1】.
- **SSR/SSG (Server-Side)** : on génère le HTML sur le serveur (à la volée ou à l’avance) puis on l’envoie, le client voit du HTML déjà formaté (meilleur TTFB), puis un bundle JS hydrate le tout pour le rendre interact ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=These%20solutions%20include%20static%20site,are%20rendered%20at%20request%20time))1】. C’est mieux pour le SEO et la vitesse perçue, mais ça implique quand même d’envoyer la logique de composant au client (pour hydratation), donc des bundles parfois lourds.

**Les RSC introduisent un troisième mode mixte** : *« Les React Server Components permettent d’écrire des UI qui sont rendues (et optionnellement mises en cache) sur le serveur  ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=As%20described%20by%20Vercel%3A))7】. Concrètement, un **Server Component** est exécuté sur le serveur (Node.js par ex) et renvoie une arborescence *sérialisée* qui sera intégrée dans le DOM du client **sans nécessiter d’hydratation**. Seuls les composants marqués explicitement comme *client* (interactifs) enverront du JS au navigateur. 

**Avantages :**
- **Zero bundle cost** pour le code des composants serveur : la logique de ces composants n’est jamais envoyée au client. Par exemple, un composant qui fait une requête DB et affiche du texte – tout cela se fait côté serveur, le client ne reçoit que du HTML pré-mâché. Moins de JS = chargement plus rapide.
- **Accès direct aux données serveur** : Un RSC peut faire des requêtes à la base de données ou au filesystem directement (puisqu’il tourne côté serveur), sans passer par des API intermédiaires ni exposer des clés sensibles au clie ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=In%20Server%20Components%2C%20component%20logic,your%20components%20on%20the%20server))1】. Cela simplifie la **fetching strategy** et améliore la performance (pas d’aller-retour inutile client-serveur pour obtenir les données puis re-envoyer un rendu).
- **Streaming et interactivité progressive** : Les RSC, combinés à Suspense, permettent d’envoyer le HTML au client **en flux**. On n’a plus besoin d’attendre que *toutes* les données soient prêtes pour renvoyer quelque chose. Le serveur peut envoyer un shell HTML immédiat, puis streamer les morceaux de UI des RSC dès qu’ils sont prê ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=Suspense%20boundaries%20split%20up%20the,again%20using%20the%20open%20stream))9】. Le client reçoit ainsi du contenu par morceaux, améliorant l’expérience utilisateur (on voit la page se compléter progressivement plutôt que de rester blanche).
- **Moins de dépendances dupliquées** : Avec RSC, on peut utiliser des libs côté serveur sans impacter le bundle client (ex : utiliser `axios` ou même des SDK Node dans un composant serveur). Cela évite d’alourdir le front. Idem pour la **sécurité** : si un RSC utilise, disons, une clé API tierce pour fetch des données, cette clé ne se retrouvera jamais dans le JS public du navigateur.

En résumé, les RSC combinent les avantages du SSR (HTML prêt à l’emploi, SEO-friendly) et du CSR modulable (composants interactifs au besoin), sans le coût JavaScript habituel du SSR (puisque pas d’hydratation pour la partie RSC). C’est un **changement de paradigme** : le rendu React n’est plus *tout ou rien* (tout client ou tout serveur), il peut être **hybride par composant ([React Server Components: A comprehensive guide - LogRocket Blog](https://blog.logrocket.com/react-server-components-comprehensive-guide/#:~:text=With%20RSCs%2C%20server%20rendering%20can,side%20interactivity))7】.

### 5.2 Utilisation concrète avec Next.js 13+

Next.js est le premier framework à avoir intégré les RSC de façon concrète. Dans Next 13 (mode *app directory*), les fichiers des pages et layouts sont **par défaut des RSC** – à moins d’indiquer `'use client'` en haut du fichier. Cela veut dire que, par défaut, votre code de page s’exécute côté serveur.

**Exemple :** Dans Next.js 13+ (app router), on pourrait avoir :

```jsx
// app/page.jsx – Composant serveur par défaut
import AddPostButton from './AddPostButton';

export default async function HomePage() {
  const posts = await fetch('https://jsonplaceholder.typicode.com/posts').then(res => res.json());
  return (
    <div>
      <h1>Liste de posts</h1>
      <ul>
        {posts.slice(0,5).map(post => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
      <AddPostButton />
    </div>
  );
}
```

```jsx
// app/AddPostButton.jsx – Composant client
'use client';
import { useState } from 'react';

export default function AddPostButton() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(c => c+1)}>
      Ajouter un post (cliqué {count} fois)
    </button>
  );
}
```

Dans cet exemple, `HomePage` est un **Server Component** (pas de `'use client'`). Il peut faire un `await fetch` directement (Note: Next en 2025 fournit même un fetch amélioré en RSC qui utilise le caching automatique). Le HTML généré contiendra la liste de posts. Le composant `<AddPostButton />` importé est quant à lui déclaré comme `'use client'` – c’est un **Client Component** (il utilise un state et un handler d’événement, choses impossibles en RSC). Next.js va donc inclure ce bouton de manière interactive. Concrètement, le rendu serveur insère un marqueur où le bouton doit s’intégrer, et envoie aussi un bundle JS contenant le code de `AddPostButton` au client. React sur le client hydratera juste ce bouton (et non toute la page) – on parle d’**hydratation sélective**. 

Ainsi, la liste de posts est purement serveur (aucun JS envoyé pour la liste), alors que le bouton est interactif. Le tout cohabite harmonieusement car React gère un arbre mixte serveur/client. 

**Contraintes des RSC :** Un composant serveur **ne peut pas** utiliser de Hook interactif comme `useState` ou `useEffect` (puisqu’il n’y a pas de cycle de vie DOM côté serveur de la même manière). Il ne peut pas non plus accéder à l’`window` ou au `document` (logique, il est sur le serveur). En revanche, il peut lire depuis des bases de données, des fichiers, appeler des API tierces sécurisées, etc. On peut considérer un RSC comme une sorte de **rendue statique paramétrée** : il reçoit des props, fait des calculs/requêtes, et renvoie du JSX. 

**Intégration avec Suspense :** Next.js encourage l’utilisation de `<Suspense>` pour englober des composants serveurs potentiellement longs. Par exemple, si le composant serveur enfant attend des données, on peut montrer un spinner en attendant. Grâce au rendu **en streaming**, Next enverra d’abord la partie de la page dispo puis streamera le contenu du Suspense lorsque pr ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=Suspense%20boundaries%20split%20up%20the,again%20using%20the%20open%20stream))9】. L’expérience s’améliore, surtout sur des réseaux lents.

**Mise en cache :** Étant côté serveur, on peut facilement mettre en cache les résultats de RSC pour éviter de recomputer ou refetch trop souvent. Next.js introduit des mécanismes (via le segment d’URL ou des options de fetch) pour contrôler la cache. Par exemple, on peut rendre un composant RSC *dynamique* (revalidé à chaque requête) ou *statique* (mis en cache pendant le build ou un certain temps). On peut également utiliser la directive `use cache` (selon les évolutions de React) pour mémoïser des appels. En 2025, Next.js travaille sur un système de cache fine-graine pour RSC (Next 14/15 devraient apporter des améliorations sur ce poi ([How to start a React Project [2025]](https://www.robinwieruch.de/react-starter/#:~:text=Personally%2C%20I%20think%20there%20were,are%20supported%20at%20the%20moment))4】).

**RSC et Server Actions :** Un autre concept lié est celui des **actions serveur** (React Server Actions ou Functions). C’est la possibilité de passer des fonctions du composant client qui, lorsqu’appelées (ex: au submit d’un formulaire), s’exécuteront sur le serveur. Next.js 13 propose cela via le mécanisme de formulaires without JavaScript (API Route) ou expérimentalement via `useOptimistic` et actions. En 2025, on peut s’attendre à ce que Next.js 15 stabilise ces *Server Actions* pour avoir un **aller-retour complet server <-> client sans écrire d’API manuellement**. Cela, combiné aux RSC, pourrait rendre le développement full-stack encore plus fluide, rapprochant React d’un vrai « framework » backend+frontend.

**En résumé, les React Server Components changent la donne :** on peut désormais construire des applications React où **la majeure partie du rendu se fait côté serveur**, sans sacrifier l’interactivité là où on en a besoin. Cela se traduit par des applications plus performantes (moins de JS à charger, exécution lourde côté serveur), plus simples à sécuriser (la logique sensible reste serveur), tout en conservant l’ergonomie de développement de React (composition de composants, etc.). En 2025, toute application Next.js devrait exploiter ce paradigme pour optimiser son rendu. On s’attend à ce que d’autres frameworks (Remix, Gatsby nouvelle génération, etc.) intègrent aussi cette approche ou que React la rende plus accessible hors Next. C’est sans doute l’axe d’évolution majeur de React pour les années à venir.

## 6. Performance et Optimisation – Suspense, Lazy Loading, Memoization, Streaming, Cache

Construire une application fonctionnelle n’est que la première étape : il faut ensuite s’assurer qu’elle reste **performante** et fluide, surtout en production face à de nombreux utilisateurs. React offre divers mécanismes et patterns pour optimiser les rendements, de la réduction du poids du bundle à l’accélération du rendu UI. Voici les principaux leviers en 2025 :

### 6.1 Code Splitting et Lazy Loading – Ne charger que le nécessaire

À mesure qu’une application grandit, le bundle JavaScript peut devenir massif. Or, un bundle trop lourd ralentit l’affichage initial. La solution est le **Code Splitting** : couper l’application en chunks chargés à la demande. *« Le code-splitting permet de *lazy-load* uniquement les éléments nécessaires à l’instant t, ce qui peut améliorer drastiquement les performances  ([Code-Splitting – React](https://legacy.reactjs.org/docs/code-splitting.html#:~:text=Code,needed%20during%20the%20initial%20load))2】. En pratique, cela signifie par exemple séparer chaque page en un chunk, ou isoler des dépendances lourdes (chart, rich text editor…) pour ne les charger que quand on en a besoin.

**React.lazy + Suspense :** React fournit le Hook de chargement asynchrone `React.lazy()`, combiné à `<Suspense>`, pour faciliter le code splitting des composants. Exemple :

```jsx
import { Suspense, lazy } from 'react';
// Import dynamique du composant
const HeavyComponent = lazy(() => import('./HeavyComponent'));

function App() {
  return (
    <div>
      {/* ... */}
      <Suspense fallback={<div>Chargement...</div>}>
        <HeavyComponent />
      </Suspense>
    </div>
  );
}
```

Ici, `HeavyComponent` sera extrait dans un chunk séparé (grâce à webpack ou autre bundler). Il ne sera téléchargé par le navigateur que quand App l’affichera effectivement (peut-être suite à une action user ou navigation). Pendant que ce chunk charge, le `<Suspense>` affiche le fallback (par ex « Chargement... »). Dès que le code est disponible, React rend effectivement `HeavyComponent`. Cela permet de **découper le coût** : on n’inclut pas ce composant dans le bundle initial, il est chargé plus tard, potentiellement quand l’utilisateur en a réellement beso ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=Together%20with%20,fixing%20the%20remaining%20waterfall%20drawbacks))4】.

**Exemple typique :** dans une appli multi-pages, on ne veut pas charger le code de toutes les pages dès l’accueil. Les frameworks comme Next.js le font automatiquement (chaque page = chunk). Si on est en SPA, on peut manuellement lazy-load les pages en fonction de la route. De même, pour un composant modal lourd qui ne s’ouvre que rarement, `React.lazy` est approprié.

**Outils côté bundler :** Vite et webpack supportent nativement l’import dynamique via `import()` (ES2020) pour créer des chunks. Le développeur doit identifier les zones où c’est bénéfique. En 2025, on dispose aussi d’analyses (Webpack Bundle Analyzer, etc.) pour repérer les gros modules et décider de les splitter. L’objectif est que **le bundle initial** (ce qui est téléchargé sur la première page) reste le plus petit et rapide possible, et que le reste du code soit chargé au fur et à mesure, sans impacter l’expérience (grâce aux fallbacks Suspense).

### 6.2 Suspense et gestion asynchrone – Affichage gracieux des chargements

**Suspense**, déjà abordé pour le lazy loading, est un mécanisme clé introduit avec React 18 pour gérer tous types d’attentes asynchrones dans l’UI. *« Suspense est une fonctionnalité de React permettant d’afficher temporairement une UI de repli (fallback) en attendant que le contenu réel soit prêt  ([The Complete Guide To React Suspense - DebugBear](https://www.debugbear.com/blog/guide-to-react-suspense#:~:text=The%20Complete%20Guide%20To%20React,waiting%20for%20data%20to%20load))7】. 

Initialement pensé pour le lazy loading de code, Suspense s’étend désormais à la **récupération de données** (data fetching) via les RSC ou des librairies tierces. Par exemple, en Next.js App Router, on peut faire :

```jsx
<Suspense fallback={<Spinner />}>
  <CommentsSection />
</Suspense>
```

Si `<CommentsSection />` est un composant (potentiellement serveur) qui charge des données, React va **suspendre** son rendu jusqu’à ce que les données arrivent, en affichant à la place `<Spinner / ([<Suspense> – React](https://react.dev/reference/react/Suspense#:~:text=))9】. Dès que `CommentsSection` a fini (par ex, fetch résolu), la Suspense boundary se remplace par le contenu réel.

Cela offre une expérience utilisateur nette : on voit un loader pour la section commentaires tandis que le reste de la page (peut-être déjà prêt) s’affiche. Sans Suspense, on aurait dû soit attendre que tout soit prêt pour montrer la page (moins bon TTFB), soit afficher un bout de page vide puis plus tard remplir (plus complexe à gérer manuellement). Suspense simplifie ce patron.

**Suspense SSR et hydration sélective :** En couplant Suspense avec les RSC, comme mentionné, on obtient du **SSR en streaming**. React 18 supporte en effet que le serveur envoie le HTML par segments en insérant des marqueurs pour combiner plus ta ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=Suspense%20boundaries%20split%20up%20the,again%20using%20the%20open%20stream))9】. Ce sont des détails internes, mais le développeur lui se contente de placer des `<Suspense>` aux bons endroits de l’arborescence selon la criticité du contenu.

**Limites actuelles :** Suspense natif pour le data fetching côté client n’est pas encore trivial sans lib tierce. React expérimente un Hook `use` (non stable) pour lire directement des promesses dans le rendu et déclencher Suspense. En attendant, on utilise souvent Suspense via des frameworks (Next) ou via des bibliothèques comme Relay (pour GraphQL) ou React Query + `React.lazy` wrappers. L’essentiel est de retenir l’idée : **ne jamais bloquer tout le rendu sur une ressource lente** ; entourez le contenu dépendant d’un fallback Suspense, ainsi l’utilisateur voit *quelque chose* rapidement.

### 6.3 Memoization et évitement des re-rendus inutiles

React ré-évalue un composant à chaque changement de state ou de props par défaut. C’est normal et généralement performant grâce au Virtual DOM qui n’applique que les diff nécessaires. Cependant, dans certains cas, un composant peut re-render très souvent sans que ce soit nécessaire (ex: un parent qui se re-render cause le re-render de tous ses enfants, même ceux qui n’ont pas changé de props). Pour mitiger cela, on peut utiliser :

- **React.memo :** C’est un HOC (Higher Order Component) qui **mémorise le rendu d’un composant fonctionnel** tant que ses props n’ont pas changé. *« `React.memo` vous permet de ne pas re-render un composant si ses props sont inchangées  ([memo - React](https://react.dev/reference/react/memo#:~:text=memo%20,SomeComponent%2C%20arePropsEqual))3】. On l’utilise ainsi :

  ```jsx
  const MyComponent = React.memo(function MyComponent(props) {
    // ... render avec props ...
  });
  ```

  Désormais, si le parent re-render MyComponent avec exactement les mêmes props qu’avant, React réutilisera le résultat du précédent rendu au lieu d’appeler MyComponent à nouve ([memo - React](https://react.dev/reference/react/memo#:~:text=memo%20,SomeComponent%2C%20arePropsEqual))3】. C’est très utile pour des composants purement visuels ou lourds, dont les props changent peu souvent.

  Optionnellement, on peut passer une fonction de comparaison personnalisée à `React.memo` pour définir précisément la condition de mise à jour (par défaut c’est une shallow compare des props).

- **useMemo et useCallback :** (déjà décrits section Hooks) servent à éviter de recalculer des valeurs ou de redéfinir des fonctions d’un rendu sur l’autre, à moins que les dépendances ne changent. Ils aident en interne du composant pour que ses sous-composants ne voient pas toujours de nouvelles références. Par exemple, si on passe un gros objet en prop à un enfant, le mémoïser avec useMemo évite qu’il soit recréé à chaque fois, ce qui pourrait déclencher un re-render de l’enfant.

- **Eviter les re-rendus globaux :** L’arme ultime est de structurer l’application de sorte qu’un changement d’état local ne remonte pas trop haut dans l’arborescence. Par exemple, si tout votre état global est dans un composant parent unique, chaque modif re-rendra toute l’app. En découpant l’état en contextes ou stores plus granulaires, on limite la surface de re-render. C’est ce que propose Jotai par exemple (seuls les composants abonnés à un atome qui change sont rendus). 

**Exemple d’optimisation avec React.memo :**

Supposons une liste d’items où chaque item est un composant complexe. Si on a un état (un filtre par ex) qui change fréquemment dans la liste, on risque de re-render tous les items à chaque frappe alors qu’ils n’ont pas changé. On pourrait faire :

```jsx
const Item = React.memo(({ data }) => {
  // rendu coûteux de l'item
});
```

Et dans la liste :

```jsx
{filteredItems.map(item => <Item key={item.id} data={item} />)}
```

Ainsi, tant que `filteredItems` contient les mêmes objets pour les mêmes `key`, chaque `<Item>` conservera son rendu. Sans `memo`, chaque frappe (changement de filtre) recalcule tous les items même si la liste ne change pas trop. Avec `memo`, seuls les ajouts/suppressions ou modifications de données provoqueront un re-render de l’Item correspondant.

**Attention aux micro-optimisations :** On rappelle qu’il ne faut pas abuser de `useMemo/useCallback`. Si vos composants sont petits, React est très rapide et parfois la mémoïsation coûte plus cher en overhead que recalculer. Une règle empirique : optimisez quand vous constatez un problème de perf (via le Profiler React par ex). Ne prématurons pas l’optimisation de chaque composant.

### 6.4 Streaming SSR et hydration progressive – Performances du premier rendu

Avec React 18+ et Next 13+, on a mentionné le **SSR en streaming** et l’**hydration progressive** (sélective). Ce sont des optimisations importantes du côté serveur :

- **Streaming SSR :** Au lieu de générer tout le HTML d’un coup, React 18 permet de le **envoyer par morceaux**. Par exemple, la structure de page générale peut être envoyée tout de suite, tandis qu’une partie plus lente (sous Suspense) est envoyée en second flux. Cela réduit le *Time To First Byte* (TTFB) ressenti. L’utilisateur voit quelque chose plus vite. Cette technique s’active automatiquement si on utilise Suspense sur le serveur. Next.js utilise `ReactDOMServer.renderToPipeableStream` pour ce ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=let%20didError%20%3D%20false%3B%20const,type%27%2C%20%27text%2Fhtml%27%29%3B%20stream.pipe%28res))9】. Côté Node, on pipe directement le stream au client dès que possible.

- **Selective Hydration :** Avec du SSR classique, le navigateur devait charger tout le JS de la page et hydrater de haut en bas. Désormais, React marque les îlots interactifs et peut hydrater en priorité certaines parties. Par exemple, un bouton en footer pas encore visible à l’écran peut être hydraté plus tard, alors qu’un menu déroulant visible sera hydraté en premier. Tout cela améliore la **réactivité initiale** perçue. L’utilisateur peut interagir plus tôt avec les éléments importants pendant que le reste se charge en arrière-pl ([A guide to streaming SSR with React 18 - LogRocket Blog](https://blog.logrocket.com/streaming-ssr-with-react-18/#:~:text=Suspense%20boundaries%20split%20up%20the,again%20using%20the%20open%20stream))9】. Next.js App Router bénéficie de cette approche d’**îlots**.

Pour tirer parti de ces avancées, peu d’effort côté dev : principalement structurer votre application avec des Suspense boundaries logiques, et marquer `'use client'` judicieusement pour ne pas envoyer plus de JS qu’il n’en faut. 

### 6.5 Caching et stratégies de données – Moins de requêtes, données plus fraîches

Côté données, la performance consiste souvent à **réduire les requêtes réseau** inutiles et à **réutiliser les résultats** déjà obtenus. Deux approches :

- **Cache côté client (SWR, React Query) :** Des bibliothèques comme **React Query (TanStack Query)** ou **SWR** de Vercel gèrent le state des données asynchrones avec cache et mise à jour. Par exemple, React Query maintient un cache de requêtes par clé. Si un composant refait la même requête, on la sert depuis le cache immédiatement (et éventuellement on la rafraîchit en arrière-plan). Cela améliore la réactivité de l’UI (les données sont souvent instantanées) et réduit la charge serveur. *« React Query facilite la récupération, la mise en cache, la synchronisation et la mise à jour de l’état serveur dans vos apps web  ([Enhancing Performance with React Query's Caching](https://blog.openreplay.com/enhancing-performance-with-react-query-caching/#:~:text=React%20query%2C%20like%20the%20documentation,aspects%20we%20will%20discuss%20in))0】. Ces libs offrent aussi des stratégies comme stale-while-revalidate, des outils de pagination, etc. 

  Ex: 
  ```js
  const { data, isLoading } = useQuery(['todos'], fetchTodos, { staleTime: 5000 });
  ```
  Ici `useQuery` va chercher les todos via `fetchTodos` et les garder en cache 5s. Si le composant s’unmount et remount rapidement, il reprendra les données du cache sans refetch. Ce genre de lib s’intègre très bien avec React (beaucoup utilisent Suspense également pour un rendu plus simple).

- **Cache côté serveur (ISR, CDNs) :** Si on utilise Next.js ou un SSR, on peut exploiter la mise en cache au niveau serveur ou CDN. Par exemple, Next peut générer une page en SSG et la revalider toutes les X secondes (ISR). Ou un RSC peut être marqué cacheable pour un certain temps. Cela réduit le calcul serveur pour les pages peu dynamiques. De plus, déployer sur des plateformes comme Vercel ou Netlify signifie profiter de leur CDN global : vos pages statiques ou images sont servies depuis l’emplacement géographique le plus proche de l’utilisateur, améliorant les temps de chargement.

**Exemple Next.js caching :** On peut ajouter dans un RSC :

```js
export const revalidate = 60;  // revalidar cette page toutes les 60s
```

Next sauvegardera le rendu pendant 60s, le servira rapidement aux prochains visiteurs, puis au bout de 60s la prochaine requête régénérera la page. Ce genre de caching diminue la charge tout en garantissant une relative fraicheur des données.

**CDN et assets :** Veillez aussi à servir vos assets (images, polices, JS, CSS) via un CDN ou au moins avec des bons en-têtes de cache. Next et Gatsby le font par défaut. Si vous utilisez Create React App/Vite statique, configurez votre serveur pour mettre de longs cache sur les assets fingerprintés.

### 6.6 Autres optimisations et bonnes pratiques de perf

- **Éviter de trop gros arbres DOM :** Parfois des ralentissements viennent de trop de nœuds à gérer. Utilisez des listes virtuelles (ex: `react-window` pour des longues listes scrollables) – cela monte/démonte les éléments hors écran et soulage le DOM.

- **Throttling/débounce d’événements :** Par exemple, une fonction appelée à chaque mouvement de souris ou à chaque frappement de touche pourrait être *debounced* (utiliser Lodash debounce ou un Hook maison) pour ne pas saturer le thread principal.

- **Web Workers ou WASM :** Pour des calculs vraiment lourds côté client, envisagez de les déplacer dans un Web Worker pour ne pas bloquer le rendu. Ou utilisez WebAssembly pour accélérer certains calculs (voir section futur sur WASM).

- **Profiling et monitoring :** Utilisez l’onglet Profiler de React DevTools en mode développement pour repérer les composants qui re-rendent trop souvent ou prennent beaucoup de temps. En prod, des outils comme Chrome Lighthouse, SpeedCurve ou New Relic peuvent aider à traquer les bottlenecks (y compris hors React, par ex des images lourdes, etc.).

En suivant ces techniques – code-splitting, Suspense, mémoïsation judicieuse, streaming SSR, caching – on peut considérablement améliorer les **Core Web Vitals** d’une application React : **Largest Contentful Paint** plus rapide (grâce au streaming, code splitting), **Interaction to Next Paint** optimisé (grâce à hydration progressive), etc. En 2025, les utilisateurs et moteurs de recherche sont exigeants sur ces métriques, donc l’effort d’optimisation en vaut la peine.

## 7. Testing et Bonnes Pratiques – Tests unitaires, intégration, E2E et CI/CD

La qualité d’une application passe par la **mise en place de tests** robustes. L’écosystème React s’appuie principalement sur **Jest** (tests unitaires et de composant), **React Testing Library** (pour tester les composants comme un utilisateur), et **Cypress** ou autres frameworks E2E (tests end-to-end dans un navigateur réel). Nous aborderons également quelques bonnes pratiques de testing et l’intégration continue.

### 7.1 Tests unitaires et de composants – Jest & React Testing Library

**Jest :** C’est le framework de test le plus répandu pour React (et JavaScript en général). Créé par Facebook, il est configuré pour fonctionner *out-of-the-box* avec React (via jsdom pour simuler le DOM). *« Jest est un framework de test JavaScript conçu pour être agréable et simple d’utilisation  ([Jest: JavaScript Testing Framework Overview - w3resource](https://www.w3resource.com/jest/jest-testing-framework-introduction.php#:~:text=w3resource%20www,correctness%20of%20any%20JavaScript%20codebase))2】. Avec Jest, on peut écrire des tests pour n’importe quelle logique JS (fonctions pures, reducers Redux, etc.) et aussi pour des composants en utilisant un *renderer* adéquat (Enzyme dans le passé, mais aujourd’hui on préfère Testing Library). Jest gère également les **snapshots** (captures du rendu JSX sous forme de fichier texte pour vérifier les changements non désirés).

Un test Jest ressemble à :

```jsx
import { sum } from './math';
test('addition de deux nombres', () => {
  expect(sum(1, 2)).toBe(3);
});
```

Jest offre des *matchers* expressifs (`toBe`, `toEqual`, `toContain`, etc.), et un runner intelligent (il trouve et exécute les tests, avec watch mode pendant le dev). Il gère aussi la simulation de modules (mocks/stubs) pour isoler les tests.

**React Testing Library (RTL) :** Il s’agit d’un ensemble utilitaire pour tester les composants React en se focalisant sur l’**expérience utilisateur**. Contrairement à Enzyme qui permettait d’examiner les détails internes des composants, RTL encourage à **interagir avec le composant comme un utilisateur** : sélectionner des éléments par leur texte, leur label, etc., puis simuler des events, et vérifier le rendu final. Sa philosophie : *« Plus vos tests ressemblent à la façon dont votre logiciel est utilisé, plus ils vous donnent confiance  ([Guiding Principles | Testing Library](https://testing-library.com/docs/guiding-principles/#:~:text=,confidence%20they%20can%20give%20you))6】.

Typiquement, avec RTL on fait :

```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import Counter from './Counter';

test('le compteur incrémente au clic', () => {
  render(<Counter />);
  const btn = screen.getByRole('button', { name: /cliquez-moi/i });
  fireEvent.click(btn);
  expect(screen.getByText(/Vous avez cliqué 1 fois/)).toBeInTheDocument();
});
```

Ici on **rend** le composant dans un DOM simulé (`render` utilise jsdom), on récupère le bouton par son rôle et son texte (accessibilité), on simule un clic (`fireEvent` ou userEvent), puis on vérifie que le texte mis à jour apparaît bien. On ne teste pas l’implémentation (pas de `counter.state` ou autre) – juste le **comportement visible**. Cela rend les tests plus résistants aux changements internes et plus proches d’un test réel. 

**Jest + RTL :** On utilise généralement RTL *avec* Jest – Jest s’occupe du runner et des assertions (`expect(...).toBe(...)`), RTL fournit les outils pour interagir avec le rendu du composant. Create React App et Next incluent Jest + RTL par défaut. Il y a très peu de configuration requise pour démarrer.

**Bonnes pratiques de tests unitaires/composants :**
- **Tester le rendu conditionnel et les interactions :** Vérifiez qu’un composant affiche ce qu’il doit selon ses props ou state, et que les interactions utilisateur produisent l’effet attendu dans le DOM ou les callbacks. Inutile de tester des choses triviales (ex: un `<div>` contient un texte fixé, c’est peu utile à verrouiller).
- **Éviter de tester les implémentations internes :** Par ex, ne pas tester qu’une fonction X a été appelée si on peut plutôt tester le résultat visible de son appel. L’objectif est de pouvoir refactorer l’interne sans casser le test, tant que le comportement externe reste correct.
- **Mock minimalement ce qui sort du scope :** Si votre composant utilise une API externe (ex: un module de localisation), moquez ce module pour renvoyer un résultat fixe afin de tester votre composant isolément. Jest facilite le mocking (`jest.mock('moduleName', () => ... )`).
- **Utiliser des data-testid en dernier recours :** RTL recommande de sélectionner les éléments comme le ferait un utilisateur (par texte, rôle ARIA, label de form…). Si ce n’est pas possible, on peut ajouter `data-testid="nom"` dans le code pour cibler l’élément, mais ce n’est pas la méthode la plus fidèle à l’usage réel.

### 7.2 Tests end-to-end (E2E) – Cypress et consorts

Les tests unitaires seuls ne garantissent pas qu’une application fonctionne de bout en bout (backend + frontend). C’est là que les tests **E2E** interviennent. Ils automatisent un **vrai navigateur** pour reproduire les actions d’un utilisateur sur l’application déployée, vérifiant ainsi l’intégration de tous les systèmes.

**Cypress :** C’est un framework E2E moderne très populaire pour tester les apps web. Son slogan : *« des tests rapides, faciles et fiables pour tout ce qui tourne dans un navigateur  ([cypress-io/cypress: Fast, easy and reliable testing for ... - GitHub](https://github.com/cypress-io/cypress#:~:text=GitHub%20github,Join%20us%2C%20we%27re%20hiring))8】. Cypress lance Chrome/Firefox en mode contrôlé et permet d’écrire des scénarios :

```js
// Exemple Cypress
cy.visit('http://localhost:3000');
cy.contains('Se connecter').click();
cy.get('input[name=email]').type('test@example.com');
cy.get('input[name=password]').type('12345');
cy.get('form').submit();
cy.url().should('include', '/dashboard');
cy.contains('Bonjour, Test User');
```

Cypress offre une API compréhensible (`cy.get`, `cy.contains`, etc.) et intègre un serveur qui peut servir votre app (ou pointer vers une URL de staging). Il fait automatiquement des captures d’écran en cas d’échec, et a une interface graphique utile pour déboguer (on peut voir chaque étape du test, inspecter le DOM à chaque action, etc.). Il gère aussi le *retry* auto : par ex `cy.contains('Bonjour')` réessaie pendant quelques secondes jusqu’à apparaître, ce qui s’adapte bien aux apps asynchrones (évite d’ajouter des wait fixes).

**Playwright** (Microsoft) est une alternative montante, avec support multi-browsers plus poussé, mais Cypress reste un choix sûr en 2025 avec une large communauté.

**RTL vs Cypress :** Ce ne sont pas des concurrents, ils opèrent à des niveaux différents. RTL teste un composant isolé dans un DOM simulé, très rapide et précis. Cypress teste l’application réelle, y compris la communication avec le serveur, le routing, etc. Un bug peut parfaitement ne survenir que dans le contexte global (ex: un bundle mal chargé, un problème de CORS, etc.), d’où l’intérêt des E2E.

**Conseils E2E :**
- **Tester les parcours critiques :** login, inscription, ajout au panier, checkout… Ce sont ces parcours complets qui doivent absolument marcher. Inutile de tout tester en E2E (trop lent), ciblez l’essentiel.
- **Réinitialiser l’état entre tests :** Si possible, script ou API pour remettre la base de test à zéro (ou utiliser une base de test isolée). Cypress peut interagir avec votre backend (via `cy.request`) pour créer des fixtures (ex: créer un utilisateur via API avant de tester login).
- **Veiller aux timings :** Les tests E2E peuvent être instables à cause de timing. Cypress gère beaucoup en interne, mais par exemple attendez la fin d’une requête API avant d’affirmer sur les résultats (Cypress détecte fetch/XHR et propose `cy.wait('@alias')` quand on alias une route).
- **E2E en environnement contrôlé :** Idéalement, faites tourner vos E2E sur un environnement de staging ou en local (ex: démarrer l’app en mode test sur un port). Évitez de les pointer sur une prod live, car les données varient et un test destructif pourrait causer du tort.

### 7.3 Stratégie de test et Intégration Continue (CI/CD)

**Pyramide des tests (ou trophée) :** Une vision classique est d’avoir beaucoup de tests unitaires, quelques tests d’intégration, et peu de tests E2E (car ces derniers sont lents et coûteux à maintenir). Une vision plus moderne (Kent C. Dodds “Testing Trophy”) prône : beaucoup de tests unitaires **et de tests d’interaction DOM (RTL)**, quelques tests d’intégration API, et une pincée d’E2E. L’idée est de couvrir la logique avec Jest/RTL qui est rapide et fiable, puis de valider que les pièces s’assemblent via quelques E2E.

**CI/CD :** Il est crucial d’automatiser l’exécution des tests à chaque changement de code. Des outils comme **GitHub Actions**, GitLab CI, CircleCI, etc., permettent de lancer la suite de tests sur chaque pull request ou merge. Ainsi, aucune régression n’est introduite sans être détectée. 

Pour React, la pipeline typique pourrait être :
1. Installer les dépendances.
2. Lancer `npm run test -- --ci` (Jest en mode CI) pour exécuter tous les tests unitaires/RTL. Générer un rapport de couverture éventuellement.
3. Builder l’application (`npm run build`).
4. Déployer sur un environnement de test et lancer les tests E2E (par exemple, démarrer un serveur local puis `npx cypress run`).
5. (Optionnel) Intégrer les résultats (beau dashboard, envoi Slack en cas d’échec, etc.).

Un tel pipeline assure que, avant de déployer en production, le code a passé tous les feux verts. On peut aussi brancher des outils de qualité comme **ESLint** et **Prettier** dans la CI (ou via husky en pre-commit) pour s’assurer du respect des conventions.

**Bonnes pratiques supplémentaires :**
- **Tester en mode production build :** Les tests unitaires se font en dev, mais pour E2E, il est bien de tester la version buildée minifiée (pour attraper d’éventuels bugs de production, par ex liés à NODE_ENV ou aux assets). Cypress peut pointer sur une URL où l’app est déployée en mode prod.
- **Snapshot testing avec parcimonie :** Jest snapshots peuvent aider pour s’assurer qu’un composant UI n’a pas changé visuellement (structure). Cependant, trop de snapshots deviennent bruyants (chaque changement légitime casse le test). Mieux vaut tester explicitement ce qui compte plutôt que snapshot toute l’arborescence aveuglément.
- **Coverage et points faibles :** Analysez la **couverture de test** (Jest donne un rapport %) pour voir les zones non testées. Mais ne visez pas 100% juste pour la forme – mieux vaut un 80% significatif qu’un 100% avec des tests superficiels.
- **Accessibilité dans les tests :** RTL encourage déjà cela via les sélecteurs ARIA. Vous pouvez intégrer **jest-axe** pour vérifier qu’aucune violation d’accessibilité n’est présente sur vos pages rendues. C’est un plus pour qualité ET SEO.

En définitive, mettre en place un **bon filet de tests** vous permettra de refactorer, ajouter des features ou mettre à jour React sans crainte. En 2025, avec la complexité croissante des applis (et de React lui-même), c’est presque indispensable pour maintenir un rythme de livraison rapide et sûr.

## 8. Déploiement et Sécurité – De la mise en production à la protection des utilisateurs

Avoir une application React performante et testée, c’est génial – encore faut-il bien la **déployer** et la sécuriser en production. Cette section aborde les plateformes d’hébergement modernes (Vercel, Netlify, AWS) ainsi que les bonnes pratiques de sécurité front-end.

### 8.1 Déploiement – Vercel, Netlify, AWS et autres

**Vercel :** Plateforme créée par l’équipe de Next.js (anciennement Zeit). Vercel est devenu extrêmement populaire pour le déploiement d’applications React, surtout Next.js. Il propose un déploiement en continu : vous connectez votre repo GitHub, et à chaque push Vercel build et déploie automatiquement. **Avantages :** support natif de Next.js (SSR, ISR, Edge Functions), CDN intégré, scalabilité automatique, environnement serverless. *« Vercel est une plateforme cloud pour construire et déployer des applications serverless, offrant le scaling automatique, l’optimisation de performance et la collaboration en temps réel  ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=Vercel%20is%20a%20cloud%20platform,need%20to%20follow%20these%20steps))6】. En clair, Vercel est idéal pour les applis React à exigences élevées de performances et de trafic, sans souci de gestion serve ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=time%20collaboration,need%20to%20follow%20these%20steps)) ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=application%20can%20be%20easy%20and,require%20scalability%20and%20fast%20performance))3】. Son plan gratuit suffit pour beaucoup de projets (limites sur le nombre de builds et la taille).

**Netlify :** Autre acteur majeur du déploiement JAMstack. Netlify est très apprécié pour les sites statiques ou générés (React CRA, Gatsby, Next en SSG). Il offre également un CI/CD automatique depuis Git, un CDN mondial, et des **fonctions serverless** faciles à ajouter (Netlify Functions). *« Netlify offre un déploiement facile en continu, des fonctions serverless et un CDN global, le tout via une interface simple  ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=Netlify%20is%20a%20cloud%20hosting,need%20to%20follow%20these%20steps))2】. Netlify est un excellent choix pour des applications **SPA ou statiques** et les projets front-end rapid ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=application%20can%20be%20easy%20and,require%20scalability%20and%20fast%20performance))3】. Pour du SSR, il a moins de fonctionnalités natives que Vercel (mais on peut quand même héberger Next SSR via des fonctions lambda Netlify).

**AWS (S3/CloudFront, Amplify) :** AWS est plus “brut” mais offre une flexibilité maximale pour le déploiement. Une approche classique : héberger le build d’une app React SPA sur **S3** (stockage de fichiers statiques) et le servir via **CloudFront** (CDN d’AW ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=,caching%20data%20at%20edge%20locations)) ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=that%20allows%20you%20to%20store,caching%20data%20at%20edge%20locations))9】. C’est très scalable et pay-as-you-go. AWS a aussi le service **Amplify** qui simplifie le déploiement continu d’app front (un peu comme Vercel/Netlify, branché sur Git). Amplify gère également les backend (Authentification, API GraphQL, stockage) si besoin. Pour des besoins SSR, on peut utiliser **AWS Lambda@Edge** ou **EC2** (machine virtuelle) pour déployer un serveur Node Next.js, mais c’est plus complexe manuellement. Des solutions comme Serverless Framework existent pour Next sur Lambda@Ed ([Serverless Next.js At The Edge](https://www.serverless.com/blog/serverless-nextjs#:~:text=Serverless%20Next,interact%20with%20other%20AWS%20resources)) ([Why you should deploy NextJS on the Edge. | by Dawid Niegrebecki](https://medium.com/@dawid.niegrebecki/why-you-should-deploy-nextjs-on-the-edge-cbfc304b58c#:~:text=Why%20you%20should%20deploy%20NextJS,is%20API%20routes%20or%20pages))7】. Globalement, AWS est un bon choix pour les entreprises ayant déjà des infrastructures AWS ou cherchant à optimiser les coûts à grande échelle, mais demande un peu plus de savoir-faire. *Par exemple :* publier sur S3 + CloudFront implique de configurer les en-têtes, invalidations de cache lors de nouvelles versions, etc. — rien d’insurmontable, et AWS fournit une infrastructure **très flexible et scalable** pour de gros besoi ([A Comprehensive Guide to Deploying ReactJS Applications on AWS, Netlify, and Vercel](https://clouddevs.com/react/deploying-application-to-aws-netlify-vercel/#:~:text=application%20can%20be%20easy%20and,require%20scalability%20and%20fast%20performance))3】.

**Autres options :** On peut citer **Cloudflare Pages** (et bientôt Cloudflare Functions) qui concurrence Vercel/Netlify en apportant un hébergement de sites static/SSR sur l’infrastructure Edge de Cloudflare. **GitHub Pages** est aussi une option simple pour un site React static (CRA/Vite buildés), pour des projets personnels ou docs. **Heroku** ou **Railway** peuvent héberger une app Node (donc SSR possible) en un push de code. **Docker/Kubernetes** pour les environnements custom (on dockerize l’app et on la déploie sur un cluster si on a ces infrastructures). En 2025 toutefois, la tendance est de s’abstraire de la gestion serveur et d’utiliser ces **plateformes serverless et CDN** qui simplifient la vie.

**Bonnes pratiques de déploiement :** 
- **Variables d’environnement :** Utilisez des fichiers `.env` (et des mécanismes comme dotenv, ou les secrets proposés par Vercel/Netlify) pour stocker les config sensibles (clés API, etc.). Ne commitez pas ces secrets. En front, seuls les variables préfixées par ex `REACT_APP_` (CRA) ou exposées dans Next (process.env.NEXT_PUBLIC_*) seront intégrées côté client. Ne mettez jamais de secret qui doit rester privé dans les variables envoyées au front.
- **CDN pour assets :** Comme mentionné, assurez-vous que vos images, polices, etc., soient servies au plus près de l’utilisateur. Netlify et Vercel le font par défaut. Sur AWS, CloudFront est la clé. Sur Cloudflare, c’est natif.
- **Compression et cache :** Vérifiez que la compression gzip/br is activée sur l’hébergement pour les fichiers text (JS, CSS). Vercel/Netlify le font. Pour S3+CloudFront, il faut configurer. Mettez des longs cache (Cache-Control max-age) sur les assets versionnés (ex: main.abcd123.js) et un cache court sur le HTML / les fichiers d’index non versionnés, afin que les nouvelles versions soient vite prises en compte.
- **Monitoring** : après déploiement, utilisez des services de monitoring front-end (par ex Sentry pour capter les erreurs JS runtime en production, ou Analytics/perf (Lighthouse CI, etc.)). Ceci permet de détecter d’éventuels problèmes qui ne se manifestaient pas en dev.

### 8.2 Sécurité front-end – Protéger l’application React

Bien que le gros de la sécurité se joue côté serveur (protection des données, authentification, etc.), le front-end React doit respecter certaines bonnes pratiques pour éviter d’exposer des failles exploitables :

- **Prévention des XSS (Cross-Site Scripting) :** C’est la vulnérabilité phare côté client. La bonne nouvelle, c’est que **React protège d’office contre les XSS** en **échappant automatiquement** les valeurs insérées dans le DOM via JSX. *« React escape automatiquement toutes les chaînes de caractères insérées dans le HTML depuis JSX, ce qui empêche toute exécution de code injecté  ([Understanding React XSS: A Comprehensive Guide for Developers](https://www.dhiwise.com/post/react-xss-advanced-strategies-for-mitigating-security-threats#:~:text=1,secure%20defaults%2C%20such%20as%20using))4】. Ainsi, si un utilisateur malveillant soumet `<img src=x onerror=alert(1)>` dans un champ, et que vous l’affichez dans du JSX comme `{maliciousInput}`, React va convertir `<` en `&lt;` etc., empêchant l’exécution. **Cependant**, cette protection saute si on utilise dangereusement `dangerouslySetInnerHTML`. Il faut donc éviter autant que possible d’insérer du HTML brut fourni par l’utilisateur. Si c’est nécessaire (par ex, CMS qui envoie du HTML), il faut **sanitizer** ce HTML côté serveur ou via une lib comme DOMPurify avant de l’injecter. 

  En résumé : **ne faites confiance à aucune entrée utilisateur**. React vous couvre la plupart du temps, mais soyez vigilants si vous manipulez le DOM directement ou utilisez des libs non-React qui pourraient introduire des risques.

- **Sécurité des dépendances :** Tenez vos packages à jour. Des vulnérabilités peuvent exister dans des libs que vous importez. En 2025, utilisez par exemple `npm audit` régulièrement ou des bots (Dependabot) pour patcher les failles connues. Un exemple célèbre: l’attaque de la supply-chain. Vérifiez aussi les packages douteux.

- **Authentification et tokens :** Si vous stockez un token d’authentification JWT dans le localStorage ou sessionStorage, sachez qu’il est vulnérable aux XSS (si un script injection se produit, il peut voler le token). Une approche plus sûre consiste à utiliser des cookies httpOnly + SameSite pour les tokens (ce qui les protège de l’accès JS, mais attention au CSRF). Quoi qu’il en soit, en React, éviter de faire transiter des informations sensibles en clair dans le code. Par exemple, ne mettez pas de clé API secrète dans le bundle (les variables d’environnement “frontend” seront de toute façon visibles dans le code, donc elles ne doivent pas être secrètes).

- **Policy de contenu CSP :** Vous pouvez configurer sur votre hébergeur des en-têtes CSP (Content Security Policy) pour limiter les sources de scripts, images, etc. Par exemple, empêcher le chargement de scripts depuis un domaine non approuvé, ou interdire l’utilisation de `eval`. Une CSP stricte peut prévenir certaines injections XSS en bloquant l’exécution de code non désiré. Si possible, activez également **Subresource Integrity (SRI)** pour les scripts tiers CDN, afin de s’assurer qu’ils n’ont pas été altérés.

- **Sécurité des formulaires :** Évitez d’exposer des failles de type **CSRF** en étant conscient de comment vos requêtes sont protégées. Si vous utilisez des cookies de session, assurez-vous d’avoir SameSite=Lax/Strict ou un token anti-CSRF. Si vous utilisez des JWT dans localStorage, le CSRF n’est pas un problème direct (car JavaScript doit envoyer le header). 

- **Limiter les données exposées :** Même si c’est du front, attention à ne pas leak des infos sensibles par inadvertance. Par ex, ne passez pas des données sensibles via l’URL (car elles peuvent se retrouver dans les logs). Ne laissez pas traîner des endpoints de build ou des pages d’admin sans protection dans l’app (même si côté front ce n’est pas critique, sauf si ça donne des infos sur le backend).

- **Build de prod optimisé :** Cela touche à la sécurité aussi : le build de prod de React désactive certaines vérifications (propTypes, messages d’erreur clairs) ce qui rend l’application plus rapide et légère. Toujours déployer en mode production (`NODE_ENV=production`). Non seulement pour la perf, mais aussi pour ne pas exposer des messages de debug ou une surface d’attaque plus grande (les devtools React par ex donnent plus d’info en mode dev).

En plus de tout cela, une **revue de sécurité** globale de l’application (pentest) peut être judicieuse si c’est une application critique. Mais généralement, en suivant les bonnes pratiques standard du développement web, on évite le principal.

**Résumé sécurité React :** Par défaut, React a été conçu avec une bonne sécurité (XSS auto-échappé, c’est un énorme plus comparé à du templating manuel). Les développeurs doivent maintenir cette sécurité en :
- Validant/sanitizant les données entrantes,
- Ne pas introduire de zones d’ombres (innerHTML, usage direct de `ref.innerHTML` sans précaution),
- Mettant à jour les dépendances,
- Gérant correctement les credentials (jamais de secret exposé),
- Configurant les en-têtes de sécurité sur le serveur (CSP, etc).

Il est également important de **former les membres de l’équipe** aux risques de sécurité front-end, pour que chacun ait les bons réflexes (ex: ne jamais mettre de données user dans `dangerouslySetInnerHTML` sans nettoyage, comprendre pourquoi on ne fait pas `eval` de code JSON, etc.). La sécurité est l’affaire de tous.

## 9. Checklists et Ressources Avancées – Guide de projet React moderne

Pour conclure ce guide, voici une **checklist** de bonnes pratiques et quelques ressources utiles pour aller plus loin. Cette liste pourra servir de mémo lors de la structuration d’un nouveau projet React en 2025 :

### 9.1 Checklist de démarrage de projet React

- **✅ Configuration de base :**  
  - Utiliser un outil moderne (Vite pour SPA ou Next.js pour SSR/full-stack) plutôt que CRA.  
  - Configurer TypeScript dès le départ pour les projets à moyen/long terme.  
  - Mettre en place ESLint (avec extensions React, Hooks, etc.) et Prettier pour un code propre et homogène.  
  - Définir la structure des dossiers : par fonctionnalité (features) de préférence, au lieu de par type de fichier. Ex: un dossier `Profile/` contenant `Profile.jsx`, `Profile.test.jsx`, `Profile.module.css`, etc. Cela facilite la maintenabilité des composan ([33 React Best Practices For 2025 | Technostacks](https://technostacks.com/blog/react-best-practices/#:~:text=1,various%20React%20Js%20best%20practices)) ([33 React Best Practices For 2025 | Technostacks](https://technostacks.com/blog/react-best-practices/#:~:text=for%20the%20Folder%20Layout,fall%20under%20a%20single%20folder))0】.
  - Configurer un fichier `README.md` pour expliquer comment lancer, builder, tester le projet, ainsi que les conventions spécifiques adoptées.

- **✅ Bonnes pratiques de code :**  
  - Privilégier les **composants fonctionnels** et Hooks plutôt que les classes.  
  - Éviter le *prop drilling* excessif : utiliser le Context API ou un state manager (Redux, Zustand…) pour les données global ([Context - React](https://legacy.reactjs.org/docs/context.html#:~:text=Context%20provides%20a%20way%20to,a%20typical%20React%20application%2C))9】.  
  - Découper les composants en plus petits composants réutilisables si besoin (penser à la composabilité).  
  - Écrire des composants *ouverts* à l’extension (via props, children) plutôt que coder des variantes très spécifiques – cela permet de réutiliser plus facilement.  
  - Documenter les composants complexes via JSDoc ou storybook (voir plus loin).

- **✅ Gestion d’état :**  
  - Si l’application est simple, démarrer avec le **Context** pour un état global minime (ex: utilisateur courant).  
  - Si plusieurs parties de l’application manipulent un état complexe, envisager d’introduire **Redux Toolkit** (structure claire, middleware possible) ou **Zustand**/**Jotai** (approches plus légères) dès que le besoin se présente.  
  - Ne pas abuser de l’état local partout : un état dans un parent peut souvent être suffisant sans devoir le répliquer dans chaque item (ex: sélection d’un élément dans une liste, peut être géré au parent). À l’inverse, ne pas tout mettre global sans raison. Trouver un équilibre.

- **✅ Performance :**  
  - Activer la production build pour tester la performance réelle (`npm run build && serve -s build`).  
  - Utiliser React DevTools Profiler pour repérer les goulots d’étranglement.  
  - Mettre en place le code splitting (via dynamic import ou Next.js automatic splitting) sur les pages ou modules lourds.  
  - Utiliser `React.memo` sur les composants purement présentatifs qui reçoivent des props immuables (par ex, un gros tableau de données qui ne change qu’en prop, un composant de graphique...).  
  - Vérifier le poids du bundle (utiliser Webpack Bundle Analyzer ou le rapport `vite --analyse`). Traquer les dépendances trop lourdes, envisager des alternatives plus légères si possible.  

- **✅ Tests et qualité :**  
  - Écrire des tests unitaires/RTL pour les composants critiques (ceux avec de la logique, ou ceux qui gèrent des interactions importantes).  
  - Mettre en place une pipeline CI pour exécuter ces tests à chaque commit (par ex, GitHub Actions).  
  - Configurer des tests E2E (Cypress) pour les parcours utilisateurs principaux. Même si on en a peu, en intégrer au moins un dès le début permet de s’assurer que l’environnement de test E2E est opérationnel et sert de squelette à enrichir.  
  - Surveiller la couverture de tests, mais viser la qualité plutôt que la quantité : s’assurer que les cas d’usage importants sont couverts.

- **✅ Accessibilité et SEO :**  
  - Toujours utiliser les éléments sémantiques HTML appropriés (`<button>`, `<nav>`, `<header>`, etc.) et attribuer des attributs ARIA si nécessaire pour les composants custom.  
  - Vérifier avec Lighthouse ou axe DevTools qu’il n’y a pas de erreurs d’accessibilité flagrantes.  
  - Si application Next (ou autre SSR), soigner les balises meta, titres de pages, plan de site, etc., pour le SEO. Utiliser Next Head ou le nouveau système de métadonnées pour définir titre/description par page.  
  - Si application SPA, considérer l’ajout de prerendering ou d’un service de rendu côté serveur pour le SEO si c’est un site public (sinon, une SPA non SEO pour application purement webapp authentifiée est acceptable).

- **✅ Sécurité :**  
  - Ne jamais mettre de données sensibles dans le code front ou le repo (clés privées, etc.). Utiliser les var d’env build-time pour les clés publiques (ex: API Google Maps).  
  - Activer HTTPS partout (le front sera de toute façon en HTTPS via Netlify/Vercel…). Vérifier que les cookies sécurisés sont marqués `Secure` et `HttpOnly` si utilisés.  
  - Paramétrer si possible des headers de sécurité sur l’hébergement (CSP, X-Frame-Options, etc., beaucoup de providers le permettent via des fichiers de config ou leur interface).  
  - Effectuer des revues de dépendances (npm audit) et mettre à jour dès qu’une faille importante est signalée.

- **✅ Documentation et maintenance :**  
  - Écrire une documentation pour les développeurs (comment ajouter une route, comment ajouter un module de state global, etc.). Un nouveau contributeur doit pouvoir comprendre les choix structurels rapidement.  
  - Mettre en place du formatage/linting automatisé (pré-commit hook avec lint-staged par exemple) pour garder un style de code uniforme sans effort manuel.  
  - Prévoir un processus de déploiement clair (via CI ou manuellement) et documenté. Idéalement, utiliser les releases Git (tags) ou une convention de commit (Conventional Commits) pour suivre le changelog.  
  - Surveiller l’évolution de React et de l’écosystème (abonnez-vous aux blogs officiels, etc.) pour planifier d’éventuelles migrations (par ex, la future adoption complète de Server Components, ou d’une nouvelle API concurrente…). React en 2025 est stable, mais des nouveautés peuvent toujours arriver.

### 9.2 Ressources recommandées

- **Documentation officielle React (React.dev)** – *Le site officiel mis à jour*, en particulier la section *Apprentissage progressif* et les *références API* pour les Hooks et fonctionnalités récentes. C’est la référence premièr ([Components and Props – React](https://legacy.reactjs.org/docs/components-and-props.html#:~:text=Components%20let%20you%20split%20the,detailed%20component%20API%20reference%20here)) ([Using the State Hook – React](https://legacy.reactjs.org/docs/hooks-state.html#:~:text=What%20is%20a%20Hook%3F%20A,We%E2%80%99ll%20learn%20other%20Hooks%20later))9】

- **Next.js Documentation (nextjs.org/docs)** – *Documentation officielle Next*, très utile pour appréhender les React Server Components, le routage app vs pages, etc. et comment déployer sur Vercel. 

- **Redux Toolkit & React Redux docs** – *Guides officiels sur redux.js.org*, pour apprendre les patterns modernes de Redux (createSlice, etc ([Getting Started with Redux](https://redux.js.org/introduction/getting-started#:~:text=Getting%20Started%20with%20Redux%20Redux,and%20contains%20packages%20and))6】. Le style guide Redux est particulièrement éclairant pour savoir quand (ne pas) utiliser Redux.

- **Zustand et Jotai docs** – sur leurs repositories GitHub ou sites officiels. Les READMEs sont concis et bien faits pour démarrer (ex: exemples de code complets comme l’exemple “bear ([GitHub - pmndrs/zustand:  Bear necessities for state management in React](https://github.com/pmndrs/zustand#:~:text=import%20,zustand)) ([GitHub - pmndrs/zustand:  Bear necessities for state management in React](https://github.com/pmndrs/zustand#:~:text=Use%20the%20hook%20anywhere%2C%20no,render%20on%20changes))4】).

- **Testing Library Docs (testing-library.com)** – *Guide et recettes RTL*, notamment les Guiding Principl ([Guiding Principles | Testing Library](https://testing-library.com/docs/guiding-principles/#:~:text=,confidence%20they%20can%20give%20you))6】. Le site explique comment penser ses tests orientés utilisateur et donne des exemples pour différents cas (formulaires, contexte, etc.).

- **Cypress Documentation (docs.cypress.io)** – *Très bien fournie*, avec des exemples de tests pour à peu près tout (auth, API mocking, etc.). Indispensable pour écrire des E2E robustes.

- **Kent C. Dodds Blog** – Kent est l’auteur de Testing Library et un évangéliste React. Son blog couvre des sujets tests, patterns de components, context, etc., souvent en profondeur.

- **Frontend Mastery / EpicReact.dev** – Des cours avancés (souvent payants) pour approfondir certaines concepts. Par exemple EpicReact de Kent Dodds ou les workshops de React Training.

- **Community**: *Stack Overflow* (très actif pour les problèmes spécifiques), *GitHub Discussions* de React et Next.js, et *Discord Reactiflux* (communauté React sur Discord) pour échanger et obtenir de l’aide rapidement.

- **Articles & Medium** : De nombreux articles Medium/dev.to en 2024/2025 traitent d’expériences concrètes (par ex *“Mastering React Suspense”*, *“Performance tuning React apps”*, *“State management showdown 2025”* etc.). Cherchez des retours d’expérience pour découvrir comment d’autres ont structuré de gros projets, cela peut vous inspirer.

En combinant ce **guide** et ces ressources, vous disposez d’une **référence complète** pour maîtriser React et son écosystème en 2025. Rappelez-vous que l’apprentissage est continu : le monde front-end évolue vite, mais les fondamentaux (composants, état, rendu efficace, tests) restent solides. Avec React, une chose est sûre : en 2025 comme hier, *“apprendre une fois, utiliser partout”* reste d’actualité, que ce soit pour du web, du mobile (React Native) ou d’autres plateformes. Bonne programmation React ! 🎉

