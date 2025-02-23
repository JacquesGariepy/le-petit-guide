# Guide pédagogique sur l’Intelligence Artificielle (IA)

## 1. Introduction générale

L’**Intelligence Artificielle (IA)** désigne un ensemble de techniques permettant de créer des machines capables de simuler l’intelligence humaine ([Intelligence artificielle — Wikipédia](https://fr.wikipedia.org/wiki/Intelligence_artificielle#:~:text=L%27intelligence%20artificielle%20,1)). Concrètement, ces systèmes peuvent **apprendre**, **raisonner** ou **résoudre des problèmes** d’une manière qui rappelle le fonctionnement de l’esprit humain. L’IA est de plus en plus présente dans notre quotidien à travers une multitude de services et d’objets (assistants vocaux, recommandations en ligne, véhicules assistés, etc.), ce qui la rend incontournable. 

Pourquoi l’IA est-elle si importante de nos jours ? C’est surtout en raison de son **potentiel à transformer profondément nos modes de vie et de travail**. En effet, l’IA peut _automatiser_ des tâches répétitives, analyser d’énormes volumes de données bien plus rapidement que ne pourrait le faire un humain et aider à prendre des décisions optimisées. Son **impact économique et sociétal** est considérable : la plupart des industries voient en elle un levier d’innovation et d’efficacité. Par exemple, **83 % des entreprises** considèrent désormais l’IA comme une priorité stratégique pour leur développement ([Qu'est-ce que l'intelligence artificielle et pourquoi est-ce important ? | Talend](https://www.talend.com/fr/resources/what-is-artificial-intelligence/#:~:text=L%27intelligence%20artificielle%20,d%27innovation%20dans%20le%20monde%20du)). Plus globalement, _“l’importance de l’IA réside dans son potentiel de révolutionner les industries, de booster l’efficacité et d’améliorer les processus de prise de décision”_ ([Qu'est-ce que l'intelligence artificielle (IA) ? | Définition | Box](https://www.box.com/fr-fr/resources/what-is-ai#:~:text=L%27importance%20de%20l%27IA%20r%C3%A9side%20dans,processus%20de%20prise%20de%20d%C3%A9cision)). 

Cependant, l’essor de l’IA s’accompagne aussi d’enjeux éthiques et de précautions. Comme toute technologie puissante, elle soulève des questions sur la **vie privée**, la **transparence des algorithmes** ou l’**impact sur l’emploi**. Il est donc crucial de comprendre non seulement **ce qu’est l’IA et comment elle fonctionne**, mais aussi **ses implications** afin d’en tirer le meilleur parti tout en **maîtrisant les risques**.

Dans ce guide, nous vous proposons d’apprendre les bases de l’IA de façon progressive. Nous commencerons par distinguer les concepts clés de *Machine Learning* et *Deep Learning*, puis nous explorerons des exemples d’applications concrètes de l’IA dans différents secteurs. Nous présenterons également deux outils phares du domaine (TensorFlow et PyTorch) et vous guiderons pas à pas dans leur installation. Ensuite, vous réaliserez vos **premiers pas pratiques** en entraînant un modèle simple. Nous aborderons enfin les stratégies d’**optimisation et de bonnes pratiques** (éviter le surapprentissage, ajuster les hyperparamètres, etc.), puis nous conclurons par des **checklists** récapitulatives et des **ressources** pour continuer votre apprentissage. 

Commençons sans plus attendre par les fondations : qu’entend-on par apprentissage automatique et apprentissage profond ?

## 2. Les bases de l’IA

### 2.1 Intelligence Artificielle, *Machine Learning* et *Deep Learning*

Il est courant de voir les termes **Intelligence Artificielle (IA)**, **Machine Learning (ML)** et **Deep Learning (DL)** utilisés de façon interchangeable, bien qu’ils recouvrent des notions distinctes et hiérarchisées. 

- **L’IA** est le domaine général, englobant toutes les techniques visant à imiter l’intelligence humaine. Cela inclut aussi bien des approches basées sur des règles explicites (systèmes experts, logique symbolique) que des approches d’apprentissage automatique. L’IA, au sens large, vise à faire accomplir par des machines des tâches que l’homme réalise avec son intelligence ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=L%E2%80%99intelligence%20artificielle%20,%C2%BB)) ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=Le%20machine%20learning)).

- **Le *Machine Learning***, ou **apprentissage automatique**, est une **branche de l’IA** qui se concentre sur les algorithmes apprenant à partir de données. Arthur Samuel, un pionnier du domaine, le définissait dès 1959 comme « la faculté pour un ordinateur d’apprendre sans avoir été explicitement programmé pour chaque tâche » ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=Le%20machine%20learning%20,de%20ses%20pionniers%2C%20Arthur%20Samuel)). En pratique, au lieu de coder manuellement toutes les règles, on fournit au système de nombreux exemples qu’il analyse pour découvrir des **patrons** (régularités) et construire un **modèle prédictif**. Le Machine Learning permet ainsi à la machine de **généraliser** à partir d’exemples : une fois entraîné sur des données historiques, le modèle peut prédire ou décider sur de nouveaux cas similaires. 

- **Le *Deep Learning***, ou **apprentissage profond**, est un **sous-ensemble spécifique du Machine Learning** ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=Le%20deep%20learning%20,le%20deep%20de%20deep%20learning)). Il s’appuie sur des **réseaux de neurones artificiels** multi-couches, inspirés du cerveau humain, pour apprendre des représentations de données très complexes. “Deep” (profond) fait référence aux **multiples couches de neurones** qui composent ces modèles. Chaque couche apprend à extraire des caractéristiques de plus en plus abstraites des données, ce qui permet au système de traiter des informations très complexes de manière hiérarchisée ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=Le%20deep%20learning%20,affiner%20la%20pr%C3%A9cision%20des%20r%C3%A9sultats)). Le Deep Learning a connu un essor majeur grâce à l’augmentation des puissances de calcul (GPU) et à la disponibilité de grands volumes de données (*Big Data*). Il obtient aujourd’hui des résultats spectaculaires dans des tâches comme la reconnaissance d’images, la compréhension du langage naturel ou le jeu (échecs, go, etc.), souvent à un niveau surhumain. L’envers du décor est qu’il requiert généralement **énormément de données** et de **ressources de calcul** pour entraîner les modèles, plus que des approches de ML plus classiques ([Machine learning, deep learning, IA : quelles différences ?](https://orsys-lemag.com/machine-learning-deep-learning-ia-differences/#:~:text=Les%20algorithmes%20de%20deep%20learning,de%20calcul%20pour%20les%20traiter)).

En résumé, l’IA est le concept large ; le Machine Learning en est une méthode phare (apprentissage par l’expérience à partir de données) ; et le Deep Learning en est une méthode particulière utilisant des réseaux de neurones profonds. On peut retenir l’image suivante : **IA ⊃ ML ⊃ DL** (l’IA comprend le ML, qui comprend le DL).

### 2.2 Catégories d’algorithmes d’apprentissage automatique

En apprentissage automatique, on distingue plusieurs **catégories d’algorithmes**, selon la manière dont ils apprennent et le type de données à disposition :

- **Apprentissage supervisé :** l’algorithme apprend à partir de **données étiquetées**, c’est-à-dire d’exemples dont on connaît déjà le **résultat attendu** (la “bonne réponse”). Par exemple, on peut fournir à un algorithme des milliers d’images de radiographie annotées comme *saine* ou *malade* pour lui apprendre à diagnostiquer de nouvelles images. L’objectif du modèle est de **prédire la sortie** (la catégorie ou une valeur numérique) pour de nouvelles entrées. Les tâches supervisées typiques sont la **classification** (prédire une catégorie : spam ou non-spam, le chiffre écrit à la main sur une image, etc.) et la **régression** (prédire une valeur numérique continue : le prix d’un bien immobilier, la température demain, etc.). Parmi les algorithmes supervisés classiques, on trouve la régression linéaire, les **arbres de décision**, les machines à vecteurs de support (SVM), les **réseaux de neurones** classiques, etc.

- **Apprentissage non supervisé :** ici, le système apprend **sans étiquettes**, c’est-à-dire uniquement à partir de données brutes dont on n’a pas spécifié la réponse attendue. L’algorithme doit découvrir **tout seul des structures ou des régularités** dans les données. C’est utile pour **regrouper** des données similaires (**clustering**), détecter des **anomalies**, ou encore réduire la dimension des données pour les visualiser ou les traiter plus facilement (techniques de **compression** ou réduction de dimension, comme l’analyse en composantes principales PCA). Par exemple, un algorithme non supervisé peut segmenter des clients en groupes de comportements proches sans qu’on lui ait donné au préalable le profil de chaque groupe. Des algorithmes non supervisés courants incluent le **k-moyennes (k-means)** pour le clustering, les algorithmes de regroupement hiérarchique, ou les réseaux de neurones auto-encodeurs en deep learning.

- **Apprentissage par renforcement :** il s’agit d’une approche différente où un **agent** apprend en interagissant avec un **environnement**. L’agent effectue des actions et reçoit en retour des **récompenses** (feedback positif ou négatif). Le but est d’**optimiser une suite d’actions** pour maximiser la récompense cumulée. Ce cadre est inspiré de l’apprentissage par essai-erreur. Par exemple, on peut entraîner un agent à jouer à un jeu vidéo : à chaque mouvement (action) il reçoit un score (récompense) selon qu’il se rapproche de l’objectif (gagner la partie). Au fil de nombreuses parties, il apprend la meilleure stratégie pour gagner. L’apprentissage par renforcement a été à l’origine d’avancées spectaculaires, comme AlphaGo (IA ayant maîtrisé le jeu de go). Les algorithmes typiques incluent **Q-Learning** et les méthodes par politique (Policy Gradient, Deep Q-Network, etc.). C’est un domaine à part, plus complexe à mettre en œuvre, et qui combine souvent des éléments de deep learning pour gérer des environnements à états très nombreux (par exemple, des jeux vidéo complexes, robotique en environnement réel, etc.).

**Résumé :** Le Machine Learning fournit un arsenal d’algorithmes variés. Le choix entre supervisé, non supervisé ou par renforcement dépend du problème et des données dont on dispose. Souvent, la première étape d’un projet IA est de formuler clairement le problème (prédire une valeur ? classer un objet ? découvrir des segments ? apprendre une stratégie ?) afin d’orienter vers la bonne catégorie d’apprentissage et les algorithmes appropriés.

## 3. Applications de l’IA

Les avancées de l’IA ne sont pas que théoriques : elles se traduisent par de **nombreuses applications concrètes** qui révolutionnent divers secteurs d’activité. Voici quelques domaines phares où l’IA est déployée avec succès :

- **Santé :** l’IA connaît de multiples usages en médecine et biologie. Par exemple, en **imagerie médicale**, des algorithmes de vision par ordinateur analysent des radiographies, des IRM ou des scanners pour détecter des tumeurs ou autres anomalies avec une précision parfois comparable à celle d’un expert humain. On l’utilise aussi pour aider au **diagnostic** (analyse de symptômes, détection précoce de maladies), pour la **découverte de médicaments** (criblage de molécules via des modèles prédictifs) ou encore pour la médecine personnalisée (adapter les traitements en fonction des données génétiques et cliniques du patient). En santé publique, des modèles prédictifs peuvent anticiper la propagation d’une épidémie. Ces applications montrent le potentiel de l’IA à **améliorer la qualité des soins** et à **sauver des vies**, tout en posant des questions de responsabilité et d’éthique (l’IA ne remplace pas le médecin, mais l’assiste).

- **Finance :** le secteur financier a été parmi les premiers à adopter l’IA à grande échelle. Des algorithmes intelligents scrutent les transactions bancaires pour **détecter des fraudes** en temps réel (ex : repérer des opérations suspectes sur votre carte bancaire). En **bourse**, l’IA alimente le **trading algorithmique** : des modèles prédisent les évolutions de marché et passent des ordres en quelques microsecondes, bien plus vite qu’un opérateur humain. Les banques et compagnies d’assurances utilisent également des modèles de ML pour l’**évaluation des risques** (score de crédit, risque de défaut) ou la **détection de blanchiment d’argent**. Enfin, les **chatbots** financiers et robo-conseillers permettent d’automatiser la relation client (aide en ligne, conseil d’investissement basique). L’objectif commun est de **gagner en efficacité** (vitesse, coût) tout en gérant mieux les risques grâce à l’analyse prédictive.

- **Industrie et automatisation :** dans l’**industrie manufacturière**, l’IA est un moteur d’optimisation des processus. Par exemple, la **maintenance prédictive** utilise des modèles qui, à partir des données de capteurs sur les machines, prédisent les pannes avant qu’elles ne surviennent, évitant ainsi des arrêts coûteux. Sur les chaînes de production, la **vision par ordinateur** sert au **contrôle qualité automatisé** (détecter automatiquement des défauts sur des pièces). Des **robots intelligents** collaboratifs (cobots) apprennent aux côtés des ouvriers pour accomplir des tâches pénibles ou précises. Plus globalement, l’orchestration d’une usine peut être optimisée par des algorithmes qui gèrent en temps réel l’approvisionnement, le stockage, l’énergie pour gagner en productivité. L’**automatisation intelligente** pilotée par l’IA permet d’augmenter l’efficacité et de réduire les erreurs, tout en transformant profondément les métiers de l’industrie.

- **Vision par ordinateur (image et vidéo) :** il s’agit d’un domaine spécifique de l’IA où les progrès du deep learning ont été fulgurants. La vision par ordinateur permet à des machines de **“voir” et comprendre des images** ou des flux vidéo. Les exemples d’application incluent la **reconnaissance faciale** (déverrouiller son téléphone avec son visage, ou identifier des personnes dans une foule), la **vidéosurveillance intelligente** (détection d’intrusion, analyse de comportements), la **conduite autonome** (un véhicule autonome analyse en temps réel les images de ses caméras pour identifier les autres véhicules, piétons, panneaux...), l’**imagerie satellite** (détection de changements sur des images aériennes pour l’agriculture ou l’environnement), ou encore la réalité augmentée (le système reconnaît l’environnement et y superpose des informations). Ces applications reposent souvent sur des réseaux de neurones spécialisés comme les **réseaux convolutifs (CNN)** pour le traitement d’images. Par exemple, un modèle d’IA bien entraîné peut détecter des objets ou classer des images avec une précision très élevée – on parle désormais de “vision artificielle” pour souligner que la machine _comprend_ la scène visuelle. 

- **Traitement du langage naturel (NLP) :** un autre champ majeur de l’IA consiste à **comprendre et générer du langage humain** (texte ou parole). Les applications du **NLP** sont omniprésentes : les **assistants virtuels** (comme Siri, Alexa, ou les chatbots en ligne) comprennent vos questions et y répondent, les systèmes de **traduction automatique** (Google Traduction, DeepL) convertissent instantanément du texte d’une langue à une autre, les outils de **correction grammaticale** ou d’**écriture assistée** (comme ceux qui suggèrent la suite de votre phrase) facilitent la rédaction. On trouve aussi des IA qui analysent les réseaux sociaux ou des avis clients pour en extraire le **sentiment** (analyse de sentiment positif/négatif) à grande échelle. Plus récemment, les modèles de langage de grande taille (ex : GPT-3, GPT-4) peuvent générer du texte cohérent, rédiger des résumés, du code, ou tenir des conversations complexes (*chatbots* avancés comme ChatGPT). Ces avancées en NLP ouvrent la voie à des interactions homme-machine plus **naturelles** et à un accès facilité à l’information, tout en soulevant des défis (désinformation automatisée, biais dans les modèles, etc.).

- **Autres domaines :** la liste des applications de l’IA est longue et en constante expansion. On peut citer en vrac : les **moteurs de recherche** (qui utilisent des algorithmes intelligents pour classer les résultats pertinents), les **systèmes de recommandation** (par exemple ceux de Netflix, YouTube ou Spotify, qui suggèrent des contenus basés sur vos goûts et vos comportements), les **jeux vidéo** (les personnages non joueurs **“PNJ”** utilisent de l’IA pour adopter des comportements crédibles ; des IA apprennent à maîtriser des jeux complexes comme StarCraft ou Dota), le **secteur public** et la **sécurité** (modèles prédictifs pour optimiser les services urbains, détecter des risques criminels ou accidents), l’**énergie** (prédiction de la consommation, optimisation des réseaux électriques intelligents), l’**éducation** (tutoriels intelligents s’adaptant à l’élève), etc. À peu près **tous les secteurs** peuvent tirer parti de l’IA d’une manière ou d’une autre, que ce soit pour **accroître l’efficacité**, **personnaliser les services** ou même **découvrir de nouvelles connaissances** (par exemple, en science, l’IA aide à découvrir de nouvelles molécules, ou à prouver des théorèmes mathématiques). Les capacités d’apprentissage et de généralisation de l’IA font qu’on lui confie progressivement des missions variées, parfois critiques, autrefois réservées à l’humain ([Intelligence artificielle — Wikipédia](https://fr.wikipedia.org/wiki/Intelligence_artificielle#:~:text=Les%20applications%20de%20l%27IA%20,3)).

En conclusion, l’IA est déjà partout autour de nous, souvent de façon invisible pour l’utilisateur final. Comprendre ses applications permet de mieux appréhender son **potentiel** mais aussi ses **limites**. Après ce tour d’horizon, intéressons-nous aux outils qui rendent possible le développement de ces solutions d’IA : notamment les bibliothèques logicielles de *Deep Learning* utilisées par les chercheurs et ingénieurs du domaine.

## 4. Présentation des outils TensorFlow et PyTorch

Parmi les nombreux outils et bibliothèques disponibles pour développer des projets en IA, deux noms se distinguent particulièrement aujourd’hui : **TensorFlow** et **PyTorch**. Ce sont les frameworks de référence pour le **Deep Learning**. Ils permettent de créer, entraîner et déployer facilement des réseaux de neurones et autres modèles d’apprentissage automatique en profitant de l’accélération GPU. Dans cette section, nous allons présenter chacun brièvement, puis comparer leurs atouts et inconvénients.

### 4.1 TensorFlow

**TensorFlow** est un framework open-source de deep learning initialement développé par Google (sorti en 2015). Il propose un **écosystème très complet** de composants pour concevoir et déployer des modèles de ML de bout en bout. TensorFlow a été pensé dès le départ pour le **passage à l’échelle** et la **production** : on peut entraîner un modèle sur des milliers de machines (Google l’utilise pour ses propres services), puis exporter ce modèle sur divers supports (serveurs, mobiles Android/iOS, navigateurs via TensorFlow.js, etc.). 

Voici quelques **avantages clés de TensorFlow** :

- **Écosystème et outils** : TensorFlow s’accompagne de nombreuses bibliothèques et outils intégrés. Par exemple, **TensorBoard** pour visualiser graphiques et métriques d’entraînement, **TensorFlow Serving** pour déployer un modèle entraîné en service web, ou encore **TensorFlow Lite** pour embarquer des modèles sur mobile et objets connectés. Il existe également Keras (désormais partie intégrante de TF), une API de haut niveau très pratique pour construire des réseaux de neurones en quelques lignes. Cet écosystème facilite le développement **de la recherche jusqu’au déploiement** en production.

- **Performance** : TensorFlow est optimisé pour tirer parti du matériel. Il fonctionne aussi bien sur **CPU** que sur **GPU**, et même sur des **TPU** (Tensor Processing Units, des puces spécialisées développées par Google). Il permet d’entraîner des modèles gigantesques sur d’énormes jeux de données. De plus, il supporte la **compilation optimisée** des réseaux de neurones sous forme de graphe statique (XLA), ce qui peut accélérer l’exécution. 

- **Communauté et documentation** : étant l’un des premiers frameworks largement adoptés, TensorFlow bénéficie d’une **vaste communauté** d’utilisateurs et de contributeurs. La documentation officielle est riche, avec de nombreux tutoriels et exemples. On trouve une multitude de modèles pré-entraînés, de **ressources pédagogiques** et de forums d’aide autour de TensorFlow. Ce support communautaire est précieux, surtout pour les débutants.

Quelques **inconvénients ou points d’attention** pour TensorFlow :

- Son **historique de complexité** : la première version de TensorFlow (1.x) imposait la définition d’un **graphe statique** d’ opérations puis son exécution séparée, ce qui rendait le code parfois difficile à écrire et à déboguer. La **courbe d’apprentissage** a été jugée assez raide pour les débutants, malgré la documentation abondante. Cependant, depuis TensorFlow 2.x, le framework a adopté par défaut un mode **exécution impérative (eager)** beaucoup plus intuitif (on peut exécuter les opérations au fur et à mesure, comme avec PyTorch). L’intégration étroite de Keras a également simplifié la prise en main. Il reste que TensorFlow offre beaucoup d’options avancées, ce qui peut intimider au début.

- **Débogage moins direct** : Relié au point précédent, dans TensorFlow (surtout en graph statique), il pouvait être plus difficile de localiser l’origine d’une erreur dans le modèle. On devait parfois utiliser des outils de débogage propres à TF ou insérer des opérations pour examiner les valeurs pendant l’exécution du graphe. Avec le mode eager, ce problème est moindre car on peut utiliser les outils de débogage Python standards, mais cela mérite d’être noté.

- **Verbosité** : Comparé à PyTorch, le code TensorFlow peut sembler un peu plus **verbeux** ou structuré (surtout si on n’utilise pas Keras). Par exemple, le fait de devoir *compiler* le modèle avec `model.compile()` et ensuite *l’entraîner* avec `model.fit()` est très pratique mais masque un peu le fonctionnement interne, là où PyTorch vous fera tout coder manuellement (ce qui est un avantage pour la flexibilité, mais peut-être un inconvénient en termes de concision). En somme, TensorFlow privilégie une approche **haut-niveau** (Keras) pour la productivité, au prix d’une légère perte de flexibilité dans certains cas très spécifiques.

En pratique, TensorFlow est particulièrement apprécié en **milieu industriel et production** pour sa stabilité et ses outils de déploiement. Il reste également très utilisé en recherche (même si PyTorch a conquis une grande partie de la communauté recherche ces dernières années). Google continue de le faire évoluer, et de nombreuses entreprises l’ont adopté comme socle pour leurs projets d’IA.

### 4.2 PyTorch

**PyTorch** est un framework de deep learning open-source développé à l’origine par Facebook (Meta AI Research) et diffusé depuis 2017. PyTorch a rapidement gagné en popularité grâce à son approche très **flexible et “pythonique”**. Contrairement au TensorFlow d’origine, PyTorch fonctionne d’emblée en mode **impératif** : on écrit du code Python classique et le calcul du réseau s’effectue **au fur et à mesure** de l’exécution du code, ce qui rend le développement **intuitif** et le débogage aisé. 

Voici les **avantages principaux de PyTorch** :

- **Simplicité et intuitivité** : PyTorch est souvent salué pour son **interface facile à prendre en main**. Le code écrit en PyTorch ressemble beaucoup à du Python standard et utilise des constructions familières aux développeurs Python (par exemple, les tenseurs PyTorch se manipulent comme des tableaux NumPy). La définition d’un modèle se fait en créant une classe Python, la boucle d’entraînement est écrite de manière explicite – il n’y a pas de “magie cachée”. Cette transparence est appréciée pour **comprendre ce qui se passe** et pour ajuster finement le comportement si besoin. En outre, on peut utiliser directement les outils de **débogage Python** (comme pdb) pour inspecter le fonctionnement du modèle pas à pas, ce qui simplifie grandement la correction d’erreurs ([PyTorch vs TensorFlow : Quel framework deep learning choisir ?](https://www.mobiskill.fr/blog-posts/pytorch-vs-tensorflow-quel-framework-deep-learning-choisir#:~:text=PyTorch%20vs%20TensorFlow%20%3A%20D%C3%A9bogage)).

- **Flexibilité (graphe dynamique)** : PyTorch repose sur un **graphe de calcul dynamique**, c’est-à-dire que le graphe des opérations est construit à la volée pendant l’exécution ([PyTorch vs TensorFlow : Quel framework deep learning choisir ?](https://www.mobiskill.fr/blog-posts/pytorch-vs-tensorflow-quel-framework-deep-learning-choisir#:~:text=TensorFlow%20travaille%20sur%20un%20concept,graphe%20en%20cours%20de%20route)). Concrètement, cela permet par exemple d’avoir des modèles dont la structure peut varier à chaque itération (très utile pour certains types de réseaux récurrents, ou pour du *deep learning* adaptatif). On peut modifier le comportement en cours de route, insérer facilement des tests, des impressions de valeurs intermédiaires, etc. Cette flexibilité donne aux chercheurs un **contrôle total** sur leurs experiments, et a sans doute contribué à l’adoption massive de PyTorch dans la communauté académique.

- **Communauté en recherche** : PyTorch a été très vite adopté par les laboratoires de recherche en IA (universités, DeepMind, Facebook AI, OpenAI, etc.). En conséquence, **de nombreux modèles d’état de l’art sont publiés avec un code d’exemple en PyTorch**. La bibliothèque a un développement très actif, soutenu par la communauté. On trouve pléthore de tutoriels, de *notebooks* et de forums d’aide (notamment le forum officiel discuss.pytorch). De plus, PyTorch dispose d’extensions spécialisées, par exemple **Torchvision** pour les modèles de vision, **TorchText** pour le NLP, etc., ce qui facilite l’accès à des architectures avancées pré-implémentées.

- **Efficacité et ressources** : Bien que focalisé sur la flexibilité, PyTorch n’en reste pas moins performant. Il utilise aussi l’accélération GPU via CUDA en coulisse, et peut désormais exploiter des solutions de déploiement (il propose par exemple **TorchScript** pour exporter un modèle sous forme semi-statique, ou **TorchServe** pour servir des modèles en production). PyTorch a également une bonne gestion de la **mémoire** (libération automatique des tenseurs non utilisés grâce au garbage collector Python, etc.), ce qui évite certains écueils de TensorFlow où il fallait explicitement gérer les sessions et graphes. En outre, depuis fin 2022, PyTorch est passé sous la gouvernance de la Linux Foundation (projet **PyTorch Foundation**), assurant un développement ouvert et pérenne, soutenu par de grands acteurs (NVIDIA, Meta, Microsoft, Amazon…).

En ce qui concerne les **inconvénients ou limites** de PyTorch :

- **Écosystème de production moins mature** : historiquement, PyTorch a eu du retard sur TensorFlow pour tout ce qui est **déploiement en production**. Par exemple, ce n’est que récemment que des outils comme TorchServe ou l’export ONNX (format d’échange de modèles) ont comblé ce manque. De même, pour les applications mobiles, TensorFlow Lite était bien établi tandis que PyTorch Mobile est arrivé plus tard. Aujourd’hui, la situation s’améliore rapidement, mais TensorFlow conserve une légère avance en termes d’outils "prêts à l’emploi" pour l’industrialisation. Donc, si votre objectif est un déploiement **industrialisé** et multi-plateforme, PyTorch exigera peut-être un peu plus d’efforts ou l’usage de solutions complémentaires.

- **Documentation un peu clairsemée sur certains points** : la documentation officielle de PyTorch est bonne, mais parfois moins détaillée que celle de TensorFlow/Keras sur les bonnes pratiques haut-niveau. PyTorch étant très centré sur la communauté recherche, les débutants complets peuvent être un peu déroutés au départ car on leur donnera souvent directement du code d’entraînement à la main, sans "formalisme" d’un guide étape par étape. Néanmoins, de nombreux tutoriels existent (y compris sur le site PyTorch) pour combler cela. C’est un inconvénient mineur qui s’estompe avec l’expérience.

- **API en évolution** : PyTorch étant plus récent, son API a évolué rapidement. Par exemple, entre la version 0.x et 1.0, il y a eu des changements, puis l’introduction de `torch.nn.Module` et autres abstractions a stabilisé les choses. Aujourd’hui, l’API est **stable** et largement utilisée, donc ce n’est plus vraiment un souci, mais il faut être conscient que certaines ressources plus anciennes en ligne peuvent ne pas être compatibles avec les versions actuelles de PyTorch.

En résumé, **TensorFlow** et **PyTorch** sont tous deux d’excellents outils, largement supportés et capables d’à peu près tout faire en matière de deep learning. TensorFlow a une orientation peut-être plus “entreprise/production” et propose davantage de solutions clef en main pour déployer à grande échelle, tandis que PyTorch offre une expérience de développement plus **organique et flexible**, prisée par les chercheurs et de plus en plus adoptée dans l’industrie également. Le choix entre les deux dépend souvent de **préférences personnelles** (certains trouvent le style PyTorch plus naturel, d’autres préfèreront la simplicité de Keras sur TensorFlow) et de l’**écosystème** déjà en place (par exemple, une équipe qui a déjà beaucoup de code TensorFlow ne va pas tout réécrire en PyTorch, et vice-versa).

*Pour résumer la comparaison :*

- **PyTorch** est apprécié pour sa *simplicité de codage et de débogage*, grâce à son exécution immédiate et ses graphes dynamiques, offrant beaucoup de **flexibilité** au développeur ([PyTorch vs TensorFlow : Quel framework deep learning choisir ?](https://www.mobiskill.fr/blog-posts/pytorch-vs-tensorflow-quel-framework-deep-learning-choisir#:~:text=open,augmente%20la%20vitesse%20de%20traitement)) ([PyTorch vs TensorFlow : Quel framework deep learning choisir ?](https://www.mobiskill.fr/blog-posts/pytorch-vs-tensorflow-quel-framework-deep-learning-choisir#:~:text=TensorFlow%20travaille%20sur%20un%20concept,graphe%20en%20cours%20de%20route)). Il est idéal pour **prototyper rapidement** des idées de modèles et mener des recherches expérimentales. 

- **TensorFlow** brille par son **écosystème complet** et sa *robustesse en production*, avec de nombreux outils pour le suivi d’entraînement, la mise en production, et une grande communauté de support ([PyTorch vs TensorFlow : Quel framework deep learning choisir ?](https://www.mobiskill.fr/blog-posts/pytorch-vs-tensorflow-quel-framework-deep-learning-choisir#:~:text=TensorFlow%20est%20un%20framework%20de,de%20diff%C3%A9rentes%20plateformes%2C%20comme%20Android)). Il favorise une approche plus **structurée**, utile pour des projets industriels de grande envergure.

Dans la pratique actuelle, **les deux frameworks convergent** (TensorFlow 2 a adopté l’eager mode à la PyTorch, et PyTorch développe des outils de déploiement). Beaucoup de compétences sont **transférables** d’un framework à l’autre, et les concepts de base du deep learning restent les mêmes. Dans la suite de ce guide, nous proposerons des exemples de code pour **les deux** afin que vous puissiez vous initier à chacun et choisir celui qui vous convient le mieux.

## 5. Installation et configuration des outils

Après avoir choisi un framework (ou décidé d’explorer les deux), il faut passer à l’**installation** de l’environnement de travail. Les bibliothèques TensorFlow et PyTorch fonctionnent sur les principaux systèmes d’exploitation (Windows, Mac, Linux). Dans cette section, nous détaillons les étapes d’installation et de configuration pour chacune de ces plateformes. 

**Prérequis généraux :** Ces frameworks fonctionnent avec le langage **Python** (généralement Python 3.7 ou plus récent). Assurez-vous d’avoir une version récente de Python installée sur votre machine. Nous recommandons également d’utiliser un **environnement virtuel** (via `venv` ou Anaconda/Miniconda) pour isoler vos packages relatifs à l’IA, évitant les conflits avec d’autres projets. Dans les instructions ci-dessous, nous indiquerons l’installation via l’outil Python **pip** (le gestionnaire de paquets standard de Python). Si vous utilisez Anaconda, vous pouvez équivalemment utiliser `conda` pour installer ces bibliothèques. Enfin, notez que l’installation de base installera les versions **CPU** de TensorFlow/PyTorch ; si vous disposez d’une **carte GPU** NVIDIA et souhaitez l’exploiter, il faudra installer des versions compatibles GPU et possiblement les pilotes/CUDA appropriés – ce point est abordé brièvement à la fin de cette section.

### 5.1 Sous Windows

1. **Installer Python** : Si ce n’est pas déjà fait, téléchargez la dernière version de **Python 3** pour Windows depuis le site officiel (python.org) ou installez la distribution Anaconda (qui inclut Python et de nombreuses bibliothèques scientifiques). Lors de l’installation à partir de l’exécutable Python, cochez l’option *“Add Python to PATH”* pour pouvoir utiliser Python et pip depuis l’invite de commandes. Vérifiez ensuite en ouvrant une **Invite de commandes** (touche Windows, taper "Invite de commandes") et en exécutant `python --version` que Python est bien installé et accessible. 

2. **Mettre à jour pip (optionnel)** : Il est conseillé de disposer d’une version récente de pip. Tapez `python -m pip install --upgrade pip`. 

3. **Créer un environnement virtuel (recommandé)** : (Cette étape est facultative mais conseillée) Toujours dans l’invite de commandes, vous pouvez créer un environnement virtuel dédié. Par exemple, tapez :
   ```
   python -m venv env_ia
   env_ia\Scripts\activate
   ```
   Cela crée un environnement nommé `env_ia` et l’active. Vous devriez voir `(env_ia)` apparaître au début de votre invite de commandes, indiquant que vous êtes dans cet environnement isolé. 

4. **Installer TensorFlow** : Une fois l’environnement activé (ou dans l’environnement global Python si vous n’en utilisez pas), installez TensorFlow via pip :
   ```
   pip install tensorflow
   ```
   Cette commande va télécharger et installer la dernière version stable de TensorFlow compatible avec votre version de Python. Par défaut sur Windows, cela installe la version CPU (si vous avez un GPU NVIDIA et les bons drivers, pip peut aussi installer une version incluant le support GPU – voir note plus bas). 

5. **Installer PyTorch** : L’installation de PyTorch peut se faire également via pip, mais il existe plusieurs variantes (CPU ou différentes versions CUDA pour GPU). Le moyen le plus simple est de laisser pip choisir la version CPU par défaut. Exécutez :
   ```
   pip install torch torchvision torchaudio
   ``` 
   Cela installera PyTorch ainsi que les bibliothèques annexes **Torchvision** (utile pour la vision par ordinateur) et **Torchaudio** (pour l’audio), avec des versions compatibles. Par défaut, pip installera la version CPU-only si aucun CUDA n’est présent.

   *Remarque :* Alternativement, vous pouvez utiliser le *“PyTorch Getting Started”* sur le site officiel pytorch.org qui génère la commande exacte en fonction de votre configuration (OS, version Python, présence d’un GPU CUDA...). Par exemple, pour une installation avec support GPU CUDA 11 sur Windows, il fournirait une commande pip avec `--extra-index-url` pointant vers les paquets PyTorch correspondants. Pour un débutant, la version CPU est généralement suffisante pour apprendre.

6. **Vérifier les installations** : Pour s’assurer que tout est bien installé, lancez une console Python interactive. Dans l’invite de commandes, tapez `python` (ou utilisez un IDE/Notebook). Puis essayez d’importer les bibliothèques :
   ```py
   import tensorflow as tf
   import torch
   print("TensorFlow version:", tf.__version__)
   print("PyTorch version:", torch.__version__)
   ```
   Si ces importations se font sans erreur et que les versions s’affichent, **félicitations** 🎉 : TensorFlow et PyTorch sont installés correctement sur votre machine Windows. Vous pouvez maintenant utiliser ces bibliothèques dans vos scripts ou notebooks Python.

### 5.2 Sous macOS

1. **Installer Python 3** : Les Mac récents n’ont plus de Python 3 préinstallé (seul un Python 2 obsolète peut subsister). La façon la plus simple est de télécharger le **package d’installation Python 3** sur python.org (choisissez la version macOS adaptée à votre architecture : Intel x86_64 ou Apple Silicon arm64). Vous pouvez aussi installer Python via **Homebrew** en tapant dans le Terminal : `brew install python3`. Vérifiez ensuite avec `python3 --version` que l’installation a réussi. Si vous préférez Anaconda, vous pouvez installer **Miniconda** sur macOS et créer un env Python 3. 

2. **Ouvrir le Terminal** : Pour entrer les commandes, utilisez le **Terminal** macOS (Applications > Utilitaires > Terminal). Sur Mac, le Python 3 installé peut s’invoquer soit par `python3` (pour différencier de l’ancien python 2) soit en configurant les alias. Nous utiliserons `python3`/`pip3` pour être explicites.

3. **Environnement virtuel (optionnel)** : Vous pouvez créer un environnement virtuel dédié. Par exemple :
   ```
   python3 -m venv env_ia
   source env_ia/bin/activate
   ```
   (Sous macOS/Linux, on utilise `source .../activate` pour activer l’environnement virtuel.) Une fois activé, les commandes `python` et `pip` référeront à cet env isolé.

4. **Installer TensorFlow** : Utilisez pip pour installer TensorFlow. Assurez-vous d’utiliser pip associé à Python3 (souvent `pip3` par défaut sur Mac si Python2 existe encore). Commande :
   ```
   pip3 install tensorflow
   ```
   Cela installe la version CPU de TensorFlow. **Note pour Mac M1/M2 (Apple Silicon)** : Jusqu’à récemment, TensorFlow n’était pas disponible nativement pour l’architecture ARM d’Apple. Désormais, il existe un paquet spécial `tensorflow-macos`. Si vous êtes sur Mac Apple Silicon, il est recommandé d’installer TensorFlow de cette façon :
   ```
   pip3 install tensorflow-macos
   ```
   et si vous souhaitez exploiter le GPU Apple (via Metal), ajoutez :
   ```
   pip3 install tensorflow-metal
   ```
   Ces paquets fournis par Apple permettent d’accélérer TensorFlow sur les puces M1/M2. Sans cela, vous pourriez être limité à l’utilisation CPU ou devoir utiliser Rosetta. Pour un débutant, CPU ou `tensorflow-macos` conviennent.

5. **Installer PyTorch** : Là encore, pip facilite la tâche. Sur macOS (Intel ou M1), la commande standard :
   ```
   pip3 install torch torchvision torchaudio
   ```
   fonctionne. Pour les Mac **Apple Silicon (M1/M2)**, PyTorch propose depuis la version 1.12 des roues compatibles (le `pip install` devrait automatiquement installer une version adaptée avec support Metal pour GPU via l’accélérateur Apple). Assurez-vous d’avoir **Python 3.8+** et **pip>=20** pour que la roue ARM soit prise. Si un problème survient, la documentation PyTorch recommande soit d’installer via `conda` (Miniforge arm64), soit d’utiliser le binaire nightly spécifique. Mais en 2024, un simple pip3 devrait installer la bonne version.

6. **Vérifier** : Lancez Python (`python3`) dans le Terminal et importez :
   ```py
   import tensorflow as tf
   import torch
   print(tf.__version__, torch.__version__)
   ```
   Si tout est en ordre, vous verrez les versions affichées sans message d’erreur. Vous êtes prêt à développer avec TensorFlow/PyTorch sur macOS. 

### 5.3 Sous Linux (Ubuntu/Debian, etc.)

1. **Installer Python3 et pip** : La plupart des distributions Linux récentes incluent Python3 par défaut. Vérifiez avec `python3 --version`. Si besoin, installez-le via votre gestionnaire de paquets. Par exemple, sur Ubuntu/Debian :
   ```
   sudo apt update
   sudo apt install python3 python3-pip python3-venv
   ```
   (on inclut `python3-venv` si on souhaite créer des env virtuels). Assurez-vous que la commande `pip3` est disponible et à jour (`pip3 --version`). Vous pouvez mettre à jour pip via `python3 -m pip install --upgrade pip`.

2. **Environnement virtuel (optionnel)** : Créez un env virtuel dédié IA :
   ```
   python3 -m venv env_ia
   source env_ia/bin/activate
   ```
   Après activation, `which python` devrait pointer vers votre env. C’est préférable pour ne pas installer globalement les paquets.

3. **Installer TensorFlow** : Sur Linux, TensorFlow se déploie aisément via pip :
   ```
   pip install tensorflow
   ```
   (Dans l’env activé, `pip` référera à pip3 de l’env). Cela installera la version appropriée (CPU par défaut). **Note GPU** : si vous avez une carte NVIDIA avec les drivers CUDA/CuDNN installés, pip peut installer la version GPU (le paquet `tensorflow` standard intègre le support GPU depuis TF 2.0+, à condition que votre environnement système soit prêt). Vérifiez la documentation TensorFlow pour la compatibilité CUDA (versions requises). Pour débuter, ne vous souciez pas du GPU tout de suite.

4. **Installer PyTorch** : Vous pouvez utiliser pip également :
   ```
   pip install torch torchvision torchaudio
   ```
   Par défaut, cela installe la version *CPU*. Si vous voulez explicitement la version avec CUDA, vous pouvez spécifier par exemple (selon la version CUDA souhaitée) :
   ```
   pip install torch==1.x.y+cu116 torchvision==0.x.y+cu116 torchaudio===0.x.y --extra-index-url https://download.pytorch.org/whl/cu116
   ```
   (Ceci est un exemple pour CUDA 11.6, les numéros de version doivent correspondre – PyTorch fournit la commande sur son site pour chaque version). Mais encore une fois, si vous êtes débutant ou que votre but est d’apprendre, la version CPU est suffisante et évite les tracas d’installer les pilotes NVIDIA.

5. **Vérifier** : Lancez une console Python (`python`) et importez TensorFlow/PyTorch comme précédemment :
   ```py
   import tensorflow as tf
   import torch
   print(tf.__version__, torch.__version__)
   ```
   Si aucune erreur ne remonte, c’est bon ! Vous pouvez aussi tester un petit calcul pour être sûr : par exemple 
   ```py
   print(torch.tensor([1.0,2.0]) + 3)
   ```
   pour voir si PyTorch fonctionne, ou `tf.constant(3) + 5` pour TensorFlow.

**Remarques additionnelles :** 

- Quel que soit l’OS, si vous envisagez d’utiliser un **GPU NVIDIA** pour accélérer vos calculs, vous devrez installer les **pilotes CUDA** adéquats et souvent CuDNN (bibliothèque de primitives de deep learning). Sur Windows, cela passe par l’installation du toolkit CUDA de NVIDIA ; sur Linux, via apt ou conda; sur macOS, seuls les GPU AMD/Metal des M1/M2 sont supportés (via `tensorflow-metal` ou PyTorch pour Metal). L’installation GPU peut être délicate – n’hésitez pas à consulter les documentations officielles de TensorFlow et PyTorch pour les instructions spécifiques GPU si vous en avez besoin. Pour débuter, vous pouvez faire l’impasse sur le GPU ou utiliser les GPU dans le cloud si nécessaire.

- En cas de problème d’installation, vérifiez les versions de Python supportées. Par exemple, TensorFlow 2.10+ ne supporte plus Python 3.6 ou inférieur. De même, assurez-vous que pip est suffisamment récent (pip >= 19 ou 20) pour supporter les formats de wheel modernes (par exemple, TensorFlow nécessite un pip récent qui gère les “manylinux2010/2014”). 

À présent, votre environnement est prêt ! Passons à la pratique avec un premier exemple de modèle IA entraîné de bout en bout.

## 6. Premiers pas avec l’IA : création et entraînement d’un modèle simple

Dans cette section, nous allons mettre en œuvre un **exemple concret** de création et d’entraînement d’un modèle de Machine Learning, en utilisant à la fois TensorFlow et PyTorch. L’objectif est de se familiariser avec la **structure d’un programme d’apprentissage automatique** : préparation des données, définition du modèle, entraînement (boucle d’optimisation) et évaluation des performances. 

Pour illustrer cela de manière simple, nous allons entraîner un modèle de **classification d’images** sur le jeu de données classique **MNIST**. MNIST est un jeu de 70 000 petites images en niveaux de gris représentant des **chiffres manuscrits** (0 à 9). Chaque image fait 28x28 pixels. C’est le "hello world" du deep learning, souvent utilisé pour tester que tout fonctionne. Le but du modèle sera de reconnaître quel chiffre (0-9) est écrit à la main sur une image donnée.

### 6.1 Exemple avec TensorFlow (Keras)

Avec TensorFlow, le plus simple est d’utiliser l’API **Keras** qui est haut-niveau et conviviale. Keras nous permet de définir un réseau de neurones en quelques couches, de le compiler avec une fonction de coût et un optimiseur, puis de l’entraîner en une ligne. 

Le réseau que nous allons construire sera un **perceptron multicouche** basique : une couche d’entrée flatten (28x28 -> 784), une couche cachée dense (128 neurones, activation ReLU) et une couche de sortie (10 neurones, activation softmax) pour sortir une probabilité sur chacune des 10 classes de chiffres.

**Code TensorFlow :** création et entraînement d’un modèle sur MNIST. Nous incluons des commentaires pour expliquer chaque étape. Vous pouvez exécuter ce code dans un script ou un notebook une fois TensorFlow installé. 

```python
import tensorflow as tf

# 1. Chargement du jeu de données MNIST (fourni dans Keras)
(X_train, y_train), (X_test, y_test) = tf.keras.datasets.mnist.load_data()
# X_train et X_test contiennent les images, y_train et y_test les labels (chiffres 0-9)

# 2. Prétraitement des données
# On aplati les images 28x28 en vecteurs de 784 pixels, et on normalise les valeurs de pixels en [0,1]
X_train = X_train.reshape(-1, 28*28).astype("float32") / 255.0
X_test  = X_test.reshape(-1, 28*28).astype("float32") / 255.0

# 3. Définition du modèle de réseau de neurones
model = tf.keras.Sequential([
    tf.keras.layers.Dense(128, activation='relu', input_shape=(784,)),  # couche cachée de 128 neurones
    tf.keras.layers.Dense(10, activation='softmax')  # couche de sortie à 10 neurones (classification 10 classes)
])

# 4. Compilation du modèle
# On spécifie la fonction de perte, l'optimiseur et les métriques à suivre
model.compile(loss='sparse_categorical_crossentropy',   # adéquat pour classification multi-classe avec labels entiers
              optimizer='adam', 
              metrics=['accuracy'])

# 5. Entraînement du modèle sur les données d'entraînement
model.fit(X_train, y_train, epochs=5, batch_size=32, validation_data=(X_test, y_test))
# - epochs=5 : on passe 5 fois sur l'ensemble des données d'entraînement
# - batch_size=32 : les images sont traitées par lots de 32 avant mise à jour des poids
# - validation_data : on évalue le modèle sur le jeu de test à chaque epoch pour suivre la performance
```

Quelques explications sur le code TensorFlow ci-dessus : 

- Nous commençons par **charger les données**. `tf.keras.datasets.mnist.load_data()` renvoie deux tuples : le premier pour l’entraînement (X_train, y_train) et le second pour le test. Les images sont initialement de shape (60000, 28, 28) pour X_train, et il y a 60 000 images d’entraînement et 10 000 de test. Les labels y_train/y_test sont des entiers 0-9 indiquant le chiffre.

- On fait un **prétraitement minimal** : aplatir les images 28x28 en vecteur 784 (car notre réseau dense attend un vecteur en entrée), et normaliser les pixels de 0-255 à 0-1 (c’est une bonne pratique pour aider l’apprentissage, les réseaux apprennent mieux avec des valeurs petites).

- On construit le **modèle séquentiel Keras** : c’est une pile de couches appliquées l’une après l’autre. La première couche `Dense(128, activation='relu')` a 128 neurones, reçoit en entrée un vecteur de taille 784 (spécifié par `input_shape=(784,)`). Cette couche aura donc 784*128 poids + 128 biais à entraîner. Elle utilise la fonction d’activation ReLU (Rectified Linear Unit) qui est une fonction standard en hidden layers (f(x) = max(0,x)). La deuxième couche `Dense(10, activation='softmax')` a 10 neurones (un par classe possible) et utilise softmax comme activation – cela transforme le vecteur de sortie en une distribution de probabilité sur 10 classes (somme à 1). Le neurone de sortie avec la plus grande probabilité donnera la prédiction du modèle.

- On **compile** le modèle en spécifiant :
  - la **loss** (fonction de coût) : ici `sparse_categorical_crossentropy` convient pour un problème de classification multi-classes où les labels sont fournis sous forme d’entiers (0-9). C’est l’entropie croisée catégorielle classique.
  - l’**optimizer** : on choisit **Adam**, une variante avancée de descente de gradient stochastique, bien adaptée par défaut.
  - les **métriques** : on demande à suivre l’**accuracy** (taux de bonnes prédictions) pendant l’entraînement et la validation.

- On appelle `model.fit(...)` pour **entraîner** le modèle. On passe les données d’entraînement (X_train, y_train), le nombre d’**epochs** (passes sur les données) – ici 5, ce qui est très peu pour converger sur MNIST, mais suffisant pour l’exemple –, une **taille de batch** (on utilise 32 images à la fois pour calculer le gradient et mettre à jour les poids, cela accélère l’entraînement par rapport à 1 par 1, tout en introduisant un peu de bruit stochastique bénéfique), et `validation_data=(X_test, y_test)` pour que le modèle évalue la loss et l’accuracy sur les données de test à la fin de chaque epoch (sans utiliser ces données pour entraîner, bien sûr). 

En lançant ce code, vous verrez apparaître par epoch quelque chose comme :

```
Epoch 1/5
1875/1875 [==============================] - 4s 2ms/step - loss: 0.2991 - accuracy: 0.9150 - val_loss: 0.1674 - val_accuracy: 0.9522
Epoch 2/5
1875/1875 [==============================] - 3s 2ms/step - loss: 0.1430 - accuracy: 0.9579 - val_loss: 0.1276 - val_accuracy: 0.9618
...
Epoch 5/5
1875/1875 [==============================] - 3s 2ms/step - loss: 0.0809 - accuracy: 0.9762 - val_loss: 0.0925 - val_accuracy: 0.9715
```

Cela montre qu’au fil des epochs, l’accuracy d’entraînement et de validation augmente et atteint ~97% sur le test en seulement 5 epochs (on pourrait faire plus d’epochs pour encore améliorer légèrement). On constate aussi le temps par epoch (quelques secondes ici sur CPU). Vous avez donc entraîné un réseau de neurones simple qui reconnaît les chiffres manuscrits avec une bonne performance.

Avec ce premier exemple TensorFlow/Keras, on apprécie la **simplicité** : très peu de code manuel, tout est géré en interne (optimisation, calcul des gradients, etc.). Dans la section suivante, nous montrons comment réaliser un entraînement similaire avec **PyTorch**, en explicitant davantage les étapes (ce qui offre plus de contrôle).

### 6.2 Exemple avec PyTorch

Avec PyTorch, nous allons refaire essentiellement la même chose : entraîner un modèle de classification sur MNIST. PyTorch n’a pas de fonction `model.fit` haut-niveau équivalente à Keras ; nous devons écrire nous-même la **boucle d’entraînement**. Cela peut paraître un peu plus long, mais c’est très formateur car on voit exactement ce qui se passe.

**Étapes :** 
1. Chargement et prétraitement des données (via Torchvision, qui fournit MNIST).
2. Définition du modèle de réseau de neurones (en héritant de `nn.Module`).
3. Définition de la fonction de coût et de l’optimiseur.
4. Boucle d’entraînement manuelle sur plusieurs epochs, en calculant le loss, en faisant `backward()` et `step()` de l’optimiseur.
5. Évaluation du modèle sur le jeu de test pour mesurer l’accuracy.

Voici le **code PyTorch** pour cela. Les commentaires expliquent chaque partie :

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torchvision import datasets, transforms

# 1. Chargement du jeu de données MNIST
# On utilise torchvision.datasets pour télécharger MNIST et le charger sous forme de Dataset PyTorch
train_dataset = datasets.MNIST(root='./data', train=True, download=True, transform=transforms.ToTensor())
test_dataset  = datasets.MNIST(root='./data', train=False, download=True, transform=transforms.ToTensor())

# Création des DataLoader pour gérer les batchs de données
train_loader = torch.utils.data.DataLoader(train_dataset, batch_size=32, shuffle=True)
test_loader  = torch.utils.data.DataLoader(test_dataset, batch_size=32, shuffle=False)

# 2. Définition du modèle de réseau de neurones
class SimpleNN(nn.Module):
    def __init__(self):
        super(SimpleNN, self).__init__()
        self.flatten = nn.Flatten()                 # couche pour aplatir l'image 28x28 en vecteur 784
        self.fc1 = nn.Linear(28*28, 128)            # couche linéaire (dite "fully connected") 784 -> 128
        self.fc2 = nn.Linear(128, 10)               # couche linéaire 128 -> 10
    def forward(self, x):
        x = self.flatten(x)            # transforme [batch, 1, 28, 28] en [batch, 784]
        x = torch.relu(self.fc1(x))    # applique fc1 puis ReLU
        x = self.fc2(x)               # applique fc2 
        # Pas de softmax ici dans le forward, on utilisera directement la sortie pour la loss (qui intègre un softmax implicite)
        return x

model = SimpleNN()

# 3. Définition de la fonction de coût et de l'optimiseur
criterion = nn.CrossEntropyLoss()         # équivalent à sparse_categorical_crossentropy, attend des scores bruts et des labels entiers
optimizer = optim.Adam(model.parameters(), lr=0.001)

# 4. Boucle d'entraînement
epochs = 5
for epoch in range(epochs):
    model.train()  # met le modèle en mode entraînement (utile si on a BatchNorm, Dropout, etc.)
    total_loss = 0.0
    for batch_X, batch_y in train_loader:
        optimizer.zero_grad()            # réinitialise les gradients accumulés
        outputs = model(batch_X)         # passe avant (forward) du modèle sur le batch
        loss = criterion(outputs, batch_y)  # calcule la perte pour ce batch
        loss.backward()                  # rétropropagation: calcule les gradients
        optimizer.step()                 # mise à jour des paramètres selon l'optimiseur (Adam)
        total_loss += loss.item()
    avg_loss = total_loss / len(train_loader)
    print(f"Epoch {epoch+1}/{epochs} - Perte moyenne entraînement : {avg_loss:.4f}")

# 5. Évaluation du modèle sur les données de test
model.eval()  # met le modèle en mode évaluation (désactive dropout, etc.)
correct = 0
total = 0
with torch.no_grad():  # pas de calcul de gradients pendant l'évaluation
    for X, y in test_loader:
        outputs = model(X)
        # outputs est de taille [batch,10], on prend la classe avec la plus haute probabilité pour chaque
        _, predicted = torch.max(outputs, dim=1)  # indice de la valeur max sur la dimension classes
        total += y.size(0)
        correct += (predicted == y).sum().item()

accuracy = 100 * correct / total
print(f"Accuracy sur le jeu de test : {accuracy:.2f}%")
```

Décortiquons le code PyTorch :

- On charge MNIST via `torchvision.datasets.MNIST`. Le paramètre `transform=transforms.ToTensor()` indique de convertir les images PIL en tenseurs PyTorch et de normaliser les pixels entre 0.0 et 1.0 automatiquement. `download=True` fait que si MNIST n’est pas déjà téléchargé dans le dossier `./data`, il le fera. On obtient ainsi `train_dataset` et `test_dataset` qui contiennent les images et labels.

- On crée des **DataLoader** PyTorch (`torch.utils.data.DataLoader`) pour gérer la génération de batches aléatoires. `train_loader` va nous fournir des batches de 32 images tirées aléatoirement (`shuffle=True` mélange les données à chaque epoch). `test_loader` on peut laisser shuffle=False. Le DataLoader facilitera l’itération sur les données.

- On définit le **modèle** en créant une classe `SimpleNN` héritant de `nn.Module`. Dans `__init__`, on définit les couches : 
  - `nn.Flatten()` pour passer d’une image 2D à un vecteur (PyTorch propose ça).
  - `nn.Linear(28*28, 128)` : couche fully connected qui prend 784 features en entrée et en sort 128 (avec biais). 
  - `nn.Linear(128, 10)` : couche finale qui sort 10 scores (non normalisés). 
  Dans la méthode `forward`, on spécifie comment les couches s’enchaînent pour produire la sortie à partir d’un input `x`. On applique la flatten, puis la fc1 + activation ReLU (`torch.relu` est la fonction d’activation appliquée aux tenseurs), puis fc2. **Remarque :** on n’applique pas de `softmax` dans le `forward` PyTorch car la fonction de perte qu’on va utiliser (`CrossEntropyLoss`) attend directement les **logits** (scores non normalisés) et se charge d’appliquer un softmax et de calculer l’entropie croisée. C’est plus stable numériquement d’utiliser `CrossEntropyLoss` directement sur les logits.

- On instancie le modèle : `model = SimpleNN()`. Par défaut, les paramètres (poids) sont initialisés aléatoirement (selon des règles standards).

- On définit la **loss** : `nn.CrossEntropyLoss()` convient pour un problème de classification multi-classe. Elle combine un `nn.LogSoftmax` et `nn.NLLLoss` en une seule étape. Elle prendra en entrée les `outputs` du modèle (de dimension `[batch,10]`) et les labels `batch_y` (taille `[batch]` avec des entiers 0-9).

- On définit l’**optimiseur** : on choisit Adam avec un taux d’apprentissage (`lr`) de 0.001 (valeur courante par défaut). On lui passe `model.parameters()` pour qu’il sache quels paramètres (poids du modèle) mettre à jour.

- **Boucle d’entraînement :** on itère sur chaque epoch. On met le modèle en mode entraînement (`model.train()`) – cela change le comportement de certaines couches comme dropout ou batchnorm, même si ici on n’en a pas. Puis on initialise `total_loss`. On parcourt chaque batch fourni par `train_loader`. Chaque `batch_X` est un tenseur de taille `[32, 1, 28, 28]` (32 images de 1 canal 28x28), et `batch_y` est de taille `[32]` (les labels). Pour chaque batch :
  - On fait `optimizer.zero_grad()` pour remettre à zéro les gradients calculés lors du batch précédent (par défaut, PyTorch accumule les gradients à chaque `.backward()`, donc on les remet à zéro à chaque itération).
  - On obtient les `outputs = model(batch_X)`. Ici, grâce à notre définition de `forward`, `outputs` sera de shape `[32, 10]`.
  - On calcule la `loss = criterion(outputs, batch_y)`. `criterion` est notre CrossEntropyLoss. Elle compare chaque ligne de `outputs` (qui contient les scores prédits pour les 10 classes) avec le label dans `batch_y`. Elle renvoie une **perte moyenne** sur le batch.
  - `loss.backward()` calcule la **rétropropagation** : il dérive la loss par rapport à chaque paramètre du modèle et stocke ces gradients dans les attributs `.grad` de chaque paramètre.
  - `optimizer.step()` met à jour les paramètres en suivant la règle de Adam : c’est là que les poids du modèle sont ajustés légèrement pour réduire la perte.
  - On additionne `loss.item()` (la valeur scalaire numérique de la perte sur ce batch) dans total_loss.
  
  Après la boucle des batchs, on peut calculer la perte moyenne `avg_loss` sur l’epoch et l’afficher. Cela donne une indication de convergence. On pourrait aussi calculer l’accuracy sur l’ensemble train ici si on voulait.

- **Évaluation sur le test** : une fois l’entraînement fini (5 epochs), on met le modèle en mode évaluation `model.eval()`. Cela désactive certains mécanismes comme dropout (pas présent ici) et indique qu’on ne va plus entraîner. On désactive aussi la gradation avec `torch.no_grad()` car on n’a pas besoin de gradients pour juste faire des prédictions. Ensuite, on itère sur `test_loader` pour obtenir les batches de test. Pour chaque batch, on fait `outputs = model(X)` (forward pass). `outputs` est une matrice [batch,10] de scores. On utilise `torch.max(outputs, dim=1)` pour trouver l’indice de la classe la plus probable (cela renvoie un tuple (values, indices), on prend indices qui est `predicted`). On compare `predicted` à `y` (les labels vrais) pour compter combien sont corrects. On somme sur tous les batches. À la fin, `accuracy = 100 * correct / total` donne le pourcentage de bien classés.

Si vous exécutez ce code, vous verrez s’afficher par exemple :

```
Epoch 1/5 - Perte moyenne entraînement : 0.2985
Epoch 2/5 - Perte moyenne entraînement : 0.1394
Epoch 3/5 - Perte moyenne entraînement : 0.0995
Epoch 4/5 - Perte moyenne entraînement : 0.0791
Epoch 5/5 - Perte moyenne entraînement : 0.0650
Accuracy sur le jeu de test : 97.10%
```

(On obtient des chiffres comparables à TensorFlow, ~97% de précision test après 5 epochs, ce qui est logique car c’est le même modèle entraîné sur les mêmes données.)

Cet exemple PyTorch montre de manière plus détaillée ce qu’il se passe pendant l’apprentissage : on voit la mise à jour manuelle des poids via l’optimiseur, on aurait pu ajouter des impressions ou des conditions personnalisées facilement dans la boucle (par exemple, stopper plus tôt si l’accuracy atteint un seuil, etc.). C’est cette granularité de contrôle que les utilisateurs de PyTorch apprécient souvent. Bien entendu, pour des usages plus poussés, il existe des abstractions (comme **PyTorch Lightning** ou **fast.ai**) qui permettent d’automatiser un peu la boucle d’entraînement tout en gardant PyTorch. Mais connaître la version bas niveau comme ci-dessus est très instructif.

**En résumé :** nous avons entraîné un réseau de neurones simple sur un jeu de données standard en utilisant les deux frameworks. Cela vous donne un aperçu de la façon dont on code un projet de Machine Learning de bout en bout. À partir de ce squelette, vous pouvez essayer d’autres expériences, par exemple : changer l’architecture (ajouter une deuxième couche cachée, augmenter le nombre de neurones), changer le nombre d’epochs, ou essayer un autre petit jeu de données (par exemple **Fashion-MNIST** qui est comme MNIST mais avec des images de vêtements).

## 7. Optimisation et bonnes pratiques

Développer un modèle d’IA performant ne s’arrête pas à écrire le code d’apprentissage de base. Une grande partie du travail consiste à **optimiser** le modèle et à suivre des **bonnes pratiques** pour s’assurer qu’il généralise bien. Deux concepts cruciaux entrent en jeu : **éviter le surapprentissage (overfitting)** et **ajuster correctement les hyperparamètres**. Nous allons aborder ces points et donner d’autres conseils généraux pour mener à bien vos projets d’IA.

### 7.1 Éviter le surapprentissage (*overfitting*)

Le **surapprentissage** (overfitting en anglais) se produit lorsqu’un modèle apprend **trop spécifiquement** les données d’entraînement, au point d’en capturer aussi le bruit ou les détails accidentels, et perd sa capacité de généralisation. En d’autres termes, le modèle a des performances excellentes sur les données qu’il a vues pendant l’entraînement, mais beaucoup moins bonnes sur des données nouvelles qu’il n’a jamais vue ([Comprendre le surapprentissage (overfitting) en machine learning — Picsellia](https://www.picsellia.fr/post/comprendre-overfitting-machine-learning#:~:text=L%27overfitting%20est%20un%20ph%C3%A9nom%C3%A8ne%20courant,qui%20devraient%20bien%20se%20g%C3%A9n%C3%A9raliser))】. C’est comme un étudiant qui aurait appris les réponses d’un examen par cœur sans réellement comprendre : il récite parfaitement les réponses connues (données d’entraînement) mais est incapable de s’adapter à de nouvelles questions.

**Comment détecter le surapprentissage ?** Typiquement, lors de l’entraînement, on surveille la performance du modèle sur un **jeu de validation** (données distinctes de celles d’entraînement). Si on constate que l’erreur d’entraînement continue de baisser tandis que l’erreur de validation remonte (ou stagne à un niveau bien plus haut), c’est un signe d’overfitting. De même, un écart important entre l’accuracy train (par exemple 99%) et l’accuracy test (par exemple 85%) indique que le modèle a trop collé aux données de train.

**Causes principales :** Un modèle trop complexe (beaucoup de paramètres, par ex un réseau très profond) par rapport à la quantité de données disponible a tendance à surapprendre. Un entraînement trop long peut aussi aboutir au surapprentissage une fois que le modèle a “épuisé” ce qu’il pouvait généraliser et commence à mémoriser. 

**Techniques pour réduire l’overfitting (régularisation) :** La **régularisation** désigne l’ensemble des méthodes visant à rendre le modèle plus **généralisable**, quitte à diminuer un peu sa précision sur les données d’entraînemen ([Qu’est-ce que la régularisation ? | IBM](https://www.ibm.com/fr-fr/topics/regularization#:~:text=La%20r%C3%A9gularisation%20est%20un%20ensemble,l%E2%80%99entra%C3%AEnement%20pour%20augmenter%20la%20g%C3%A9n%C3%A9ralisabilit%C3%A9))】. Voici quelques approches éprouvées :

- **Plus de données :** La solution la plus directe, si possible, est d’augmenter la taille du jeu d’entraînement. Plus le modèle voit de diversité de situations, moins il risque de surapprendre des artefacts spécifiques. Cela peut passer par la collecte de nouvelles données ou par de la **data augmentation** (générer artificiellement des données supplémentaires à partir de celles qu’on a, par ex. en appliquant des petites transformations aléatoires sur les images d’entraînement – rotations, recadrages, bruit – ce qui aide le modèle à être robuste).

- **Modèle plus simple :** Si le surapprentissage est prononcé, il peut être utile de **réduire la complexité** du modèle. Par exemple, diminuer le nombre de couches ou de neurones d’un réseau, utiliser un modèle plus simple (un modèle linéaire au lieu d’un réseau profond si cela suffit), ou appliquer une **régularisation L1/L2** sur les poids (pénaliser les poids trop grands dans la fonction de coût, ce que TensorFlow/Keras permet via un `kernel_regularizer`, et PyTorch via l’ajout d’un terme dans la loss ou directement via l’optimiseur en L2, appelé *weight decay*). Une régularisation L2 incite le modèle à avoir des poids plus petits, donc des décisions plus “timides”, évitant de s’ajuster trop précisément sur chaque exemple d’entraînement.

- **Dropout :** Le **dropout** est une technique très répandue en réseaux de neurones. Elle consiste, pendant l’entraînement, à *désactiver aléatoirement* un certain pourcentage de neurones dans le réseau à chaque batch. Par exemple, un dropout de 50% sur une couche cachée va, à chaque passage, mettre à zéro de façon aléatoire la moitié des neurones de cette couche (et la moitié complémentaire lors d’un autre batch, etc.). Ainsi, le réseau ne peut pas trop compter sur un ensemble spécifique de neurones, il doit apprendre des redondances et des patterns plus généraux. En phase de test, on réactive tous les neurones mais en les pondérant par le taux de dropout. Le dropout est facile à utiliser (une simple couche `Dropout(p)` dans Keras, ou `nn.Dropout(p)` dans PyTorch) et souvent très efficace pour améliorer la généralisation du modèl ([Comment les techniques de régularisation telles que l'abandon, la ...](https://fr.eitca.org/intelligence-artificielle/eitc-ai-adl-apprentissage-en-profondeur-avanc%C3%A9/les-r%C3%A9seaux-de-neurones/fondations-des-r%C3%A9seaux-de-neurones/examen-examen-fondations-des-r%C3%A9seaux-de-neurones/comment-les-techniques-de-r%C3%A9gularisation-telles-que-la-r%C3%A9gularisation-dropout-l2-et-l%27arr%C3%AAt-pr%C3%A9coce-aident-elles-%C3%A0-att%C3%A9nuer-le-surapprentissage-dans-les-r%C3%A9seaux-neuronaux/#:~:text=Comment%20les%20techniques%20de%20r%C3%A9gularisation,mani%C3%A8re%20al%C3%A9atoire%20des%20unit%C3%A9s))】. 

- **Early stopping (arrêt anticipé)** : Cela consiste à **stopper l’entraînement** avant qu’il ne sur-apprenne. Concrètement, on surveille la performance sur un jeu de validation au fil des epochs. Dès que cette performance arrête de s’améliorer et commence à se dégrader, on arrête l’entraînement. On considère que le modèle est optimal à l’epoch où la validation était meilleure. Cette technique évite de surentraîner le modèle inutilement. Keras propose un callback `EarlyStopping` pour automatiser cela. Avec PyTorch, on peut coder une boucle qui break lorsqu’une certaine condition sur la validation est remplie. L’early stopping est particulièrement utile si on n’a pas énormément de données et qu’on observe un début d’overfitting après X epochs.

- **Validation croisée (cross-validation)** : Bien que plus coûteuse, la cross-validation (utiliser plusieurs découpages du data set en train/val et moyenner les performances) peut aider à évaluer la robustesse d’un modèle et à éviter qu’on ait eu “de la chance” sur un split. Ce n’est pas exactement une technique pour réduire l’overfitting du modèle lui-même, mais plutôt pour détecter un éventuel surapprentissage dû à un split particulier des données. En pratique pour le deep learning, on utilise moins la cross-val (trop long), mais en ML classique c’est courant.

- **Nettoyage des données et réduction du bruit** : Parfois, certaines données d’entraînement peuvent être erronées ou très bruitées. Le modèle va tenter de les mémoriser au détriment de sa généralisation. Identifier et nettoyer ces données (ou les augmenter pour les diluer) peut aider. 

En appliquant judicieusement ces méthodes, on obtient un modèle qui **généralise** mieux, c’est-à-dire qui a des performances proches sur ses données de train et sur des données qu’il n’a pas vues. L’objectif n’est pas d’obtenir le **score maximum sur train**, mais bien sur le **test** (ou validation), signe que le modèle capture des patterns réels et non du bruit. Il y a souvent un **compromis biais-variance** à gérer : un modèle trop simple aura du biais (sous-apprentissage, il ne fit même pas bien le train), un modèle trop complexe aura de la variance (surfit le train mais pas le test). La régularisation aide à trouver le bon milie ([Qu’est-ce que la régularisation ? | IBM](https://www.ibm.com/fr-fr/topics/regularization#:~:text=La%20r%C3%A9gularisation%20diff%C3%A8re%20de%20l%27optimisation,et%20la%20science%20des%20donn%C3%A9es))】.

### 7.2 Ajustement des hyperparamètres (tuning)

Les **hyperparamètres** sont tous les paramètres du processus d’apprentissage **qu’on ne “learn” pas directement** pendant l’entraînement du modèle et qui doivent être fixés à l’avance. Par exemple : le **taux d’apprentissage (learning rate)** de l’optimiseur, le **nombre de neurones par couche**, le **nombre de couches**, le **taux de dropout** appliqué, le **nombre d’epochs** d’entraînement, la **taille des batchs**, le choix de la **fonction d’activation**, etc. Ce sont autant de boutons que l’on peut tourner et qui peuvent influencer significativement les performances du modèle. Trouver la bonne configuration d’hyperparamètres est souvent un art délicat, d’autant plus qu’ils peuvent interagir entre eux (un learning rate optimal peut dépendre du batch size, etc.).

**Quelques hyperparamètres importants et leur rôle :**

- **Learning rate** (`lr`) : probablement le paramètre le plus crucial. Un `lr` trop élevé empêchera la convergence (l’apprentissage diverge ou oscille), un `lr` trop faible rendra l’entraînement très lent ou piégera dans un minimum local de performance médiocre. Il faut souvent le calibrer finement. Une bonne pratique est de commencer avec des valeurs standards (0.1, 0.01, 0.001 en déclinant par facteur 10) et voir. On peut aussi utiliser des techniques comme le **learning rate scheduling** (décroître le `lr` au cours de l’entraînement pour affiner la convergence) ou des optimisateurs adaptatifs (Adam a déjà un mécanisme adaptatif, mais le paramètre de base reste le `lr` global).

- **Nombre d’epochs** : trop peu d’epochs = sous-apprentissage ; trop d’epochs = risque de surapprentissage. On peut se baser sur l’observation de la courbe de validation pour décider (via early stopping). Parfois on entraîne beaucoup d’epochs mais en baissant le learning rate progressivement.

- **Architecture du modèle** : c’est un hyperparamètre de très haut niveau. Par exemple, choisir 2 ou 3 couches cachées, 50 ou 200 neurones chacune, ou un type de réseau (CNN vs RNN vs MLP) selon la nature des données. Cela se base sur de l’expérience, des publications (on utilise souvent des architectures éprouvées issues de la littérature pour un problème donné). Mais on peut aussi faire de la recherche d’architecture automatique (AutoML, Neural Architecture Search) pour explorer ces hyperparamètres structurels.

- **Hyperparamètres liés aux données** : par exemple, la taille d’image d’entrée (si on peut la modifier), le type de prétraitement (normalisation, etc.). En vision, le choix des augmentations de données (rotations, flips, etc. et leur intensité) sont aussi des hyperparamètres.

**Méthodes pour ajuster/tuner les hyperparamètres :**

- **Recherche manuelle éclairée** : souvent, on commence par essayer différentes valeurs à la main en se basant sur son intuition ou les recommandations connues. Par exemple, tester lr = 0.01 vs 0.001, ou tester avec/ sans dropout, etc., puis ajuster en conséquence. C’est faisable quand le nombre d’hyperparamètres est limité, mais ça peut devenir vite fastidieux s’il y en a beaucoup.

- **Grille de recherche (Grid Search)** : on définit un ensemble de valeurs possibles pour chaque hyperparamètre et on entraîne autant de modèles que toutes les combinaisons possibles. Par exemple, lr dans {0.1, 0.01, 0.001} × nombre de neurones dans {64, 128} -> 3×2 = 6 combinaisons à tester. On évalue chacun sur un set de validation et on choisit la meilleure config. L’inconvénient, c’est que le nombre de combinaisons explose exponentiellement avec le nombre de paramètres à tuner. Donc la grid search pure n’est praticable que pour relativement peu d’hyperparamètres ou en acceptant d’énormes temps de calcul.

- **Recherche aléatoire (Random Search)** : plutôt que de tout combiner systématiquement, on tire aléatoirement des combinaisons d’hyperparamètres dans les espaces définis. Il est prouvé que la random search peut être plus efficace que la grid search quand certains hyperparamètres ont moins d’importance que d’autres. On fixe un budget (par ex tester 20 combinaisons aléatoires). Cela couvre mieux l’espace si certains paramètres sont inutiles (on ne perd pas de temps à tout combiner). Keras Tuner ou scikit-learn proposent ce genre d’approche.

- **Optimisation bayésienne / méthodes séquentielles** : Ce sont des techniques plus avancées qui traitent l’optimisation d’hyperparamètres comme un problème d’optimisation mathématique. L’idée est d’essayer des combinaisons, d’observer la performance, puis d’inférer quelles combinaisons essayer ensuite pour progressivement approcher la configuration optimale. Des librairies comme **Optuna**, **Hyperopt** ou **scikit-optimize** implémentent cela. En gros, on va entrainer disons 1 modèle, voir le résultat, puis un algorithme propose la prochaine combinaison à tester en se basant sur un modèle probabiliste (Processus Gaussien par ex) qui prédit où se trouve le max. C’est efficace mais un peu complexe à mettre en place pour un débutant.

- **Approche multi-échelle** : on peut d’abord faire une recherche grossière pour voir l’ordre de grandeur (par ex tester lr=0.1,0.01,0.001,0.0001, repérer la meilleure zone), puis affiner autour de cette zone (re-tester 0.005,0.001,0.0005 si la zone 0.001 était la meilleure). Pareil pour d’autres paramètres.

- **Ne pas oublier l’humain** : Parfois, visualiser les courbes d’apprentissage (loss vs epochs, accuracy vs epochs) peut guider le tuning. Par exemple, si on voit que dès la première epoch la loss de validation est très mauvaise, peut-être le learning rate est trop grand (le modèle diverge). Ou si la loss diminue mais très lentement, on peut augmenter un peu le learning rate. Si l’accuracy stagne à une valeur basse, peut-être le modèle est trop simple (essayer plus de neurones ou un modèle plus complexe). Bref, l’observation et la compréhension du comportement du modèle vous donnent des indices sur quel “bouton” ajuster.

**Bonnes pratiques supplémentaires :**

- **Séparation train/val/test** : Toujours garder un jeu de test final non utilisé pendant le tuning, afin d’avoir une estimation *réaliste* de la performance sur des données inconnues. Le jeu de validation sert pour le tuning, mais on peut sur-ajuster aux données de validation aussi si on teste trop d’hyperparamètres (phénomène de *overfitting sur le set de validation*). Avoir un test final évite ce biais.

- **Reproductibilité** : Quand vous testez des hyperparamètres, essayez de garder le même environnement, éventuellement fixer les graines aléatoires (`random.seed`, `np.random.seed`, `torch.manual_seed`, etc.) pour pouvoir reproduire les runs. Sinon, la variance aléatoire peut brouiller les comparaisons (surtout si votre dataset est petit ou que l’initialisation aléatoire a un impact significatif).

- **Une chose à la fois** : Si possible, essayez de changer un hyperparamètre à la fois pour voir son effet. Si vous changez tout en même temps et que ça marche ou non, dur de savoir pourquoi. Bien sûr, il faut parfois ajuster deux paramètres conjointement, mais c’est dans des cas avancés.

- **Utiliser des valeurs “standard” comme point de départ** : Par exemple, en réseau de neurones, un taux d’apprentissage initial de 0.001 avec Adam est souvent un bon départ. Un dropout de 0.5 sur les couches denses, ou 0.2 sur les couches convolutionnelles. Des batch size de 32 ou 64. Ces valeurs par défaut fonctionnent dans pas mal de situations, donc on peut s’y fier pour débuter puis affiner.

En suivant ces bonnes pratiques, le processus de développement d’un modèle sera plus **systématique** et **efficace**. Rappelez-vous qu’entraîner un modèle d’IA performant est un **processus itératif** : on essaie une configuration, on évalue, on analyse les résultats (courbes d’apprentissage, métriques, peut-être même on regarde les erreurs du modèle pour comprendre ce qu’il rate), puis on ajuste quelque chose et on recommence. C’est cette expérimentation guidée qui vous mènera à un modèle optimal pour votre problème.

## 8. Checklists et ressources pour aller plus loin

Pour terminer ce guide, nous récapitulons sous forme de **checklist** les points clés à vérifier lors de vos projets en IA, et nous listons des **ressources utiles** pour approfondir vos connaissances et aller plus loin dans ce domaine passionnant.

### 8.1 Checklist de démarrage d’un projet IA

Avant de vous lancer tête baissée dans le codage, assurez-vous de passer en revue les étapes suivantes :

- **✅ Compréhension du problème** : Avez-vous bien défini la tâche que vous voulez résoudre avec l’IA ? (classification, régression, clustering, etc.). Quels sont les objectifs et comment mesurerez-vous le succès (quelle métrique principale) ?

- **✅ Collecte et préparation des données** : Disposez-vous de suffisamment de données pertinentes pour entraîner un modèle ? Les données sont-elles de bonne qualité, étiquetées si nécessaire, sans trop de biais ? Avez-vous effectué un prétraitement approprié (nettoyage des valeurs aberrantes, normalisation des échelles, encodage des variables catégorielles, etc.) ?

- **✅ Découpage des données** : Avez-vous séparé les données en **jeu d’entraînement**, **jeu de validation** (pour le tuning) et **jeu de test** (pour l’évaluation finale) ? Une séparation typique est 70/15/15 ou 80/20 (train/test) avec éventuellement une partie du train mise de côté en validation. Ce découpage est crucial pour évaluer la performance de façon honnête.

- **✅ Choix du modèle/de l’algorithme** : Avez-vous choisi un modèle adapté à votre problématique et à la quantité de données ? (Par ex, un réseau de neurones convolutif pour des images, ou bien un modèle plus simple si peu de données). Parfois, commencer par un modèle simple (régression logistique, SVM linéaire) comme baseline peut être instructif avant de complexifier.

- **✅ Configuration de l’entraînement** : Avez-vous décidé des hyperparamètres de base pour entraîner le modèle ? (learning rate initial, nombre d’epochs, batch size, fonction de perte, etc.). Ce sont vos hypothèses de départ, que vous pourrez ajuster par la suite. Assurez-vous d’inclure des techniques de régularisation si nécessaire (ex : dropout, early stopping).

- **✅ Environnement prêt** : Votre environnement logiciel est-il installé et fonctionnel (Python, TensorFlow/PyTorch, etc.) ? Avez-vous accès au matériel nécessaire (par ex, un GPU si votre modèle est lourd) ou envisagé l’utilisation de ressources cloud/colab si besoin ?

- **✅ Lancement d’un premier entraînement** : Faites un test rapide sur un sous-ensemble de données pour voir si tout fonctionne sans bug (par ex, 1 epoch sur 1000 exemples, juste pour déverminer le pipeline). Vérifiez que la loss diminue bien sur les premières iterations, signe que le modèle apprend quelque chose.

- **✅ Surveillance des métriques** : Pendant l’entraînement, suivez l’évolution de la fonction de coût et de la performance (accuracy, etc.) sur le train **et** la validation. Utilisez éventuellement TensorBoard ou des logs pour visualiser les courbes. Soyez prêt à arrêter si ça diverge ou si vous constatez du surapprentissage flagrant, afin d’ajuster les hyperparamètres.

- **✅ Évaluation et itération** : Une fois l’entraînement terminé, évaluez le modèle sur le jeu de test. Analysez les résultats. Sont-ils satisfaisants par rapport à votre objectif initial ? Identifiez les points faibles : ex. le modèle fait encore beaucoup d’erreurs sur telle catégorie de données. En fonction de ça, décidez de la prochaine itération : dois-je collecter plus de données ? changer l’architecture ? ajuster le learning rate ou autre hyperparamètre ? intégrer une autre source de données ?

- **✅ Documentation et reproductibilité** : Gardez trace de vos expériences (dans un cahier, un fichier Markdown, ou via des outils de suivi d’expériences). Notez pour chaque run les hyperparamètres utilisés, la performance obtenue, etc. Cela vous évitera de “tourner en rond” et facilitera la reproduction du meilleur modèle une fois que vous l’avez trouvé. En production, pensez à versionner le code et éventuellement les données.

- **✅ Considerations éthiques et réglementaires** : Si votre projet IA touche à des données sensibles (données personnelles, médicales) ou a un impact significatif (ex : modèle de conduite autonome, système de recrutement automatisé), assurez-vous de respecter les régulations (RGPD, etc.) et d’évaluer les biais potentiels de votre modèle. Intégrez dès le début des tests pour détecter d’éventuelles discriminations ou erreurs critiques afin de les corriger.

Cette checklist n’est pas exhaustive, mais couvre les étapes principales pour bien structurer votre projet d’IA et mettre toutes les chances de réussite de votre côté.

### 8.2 Ressources pour aller plus loin

L’apprentissage de l’IA et du Machine Learning est un **processus continu** – le domaine évolue vite et il y a toujours de nouvelles techniques à découvrir. Voici une sélection de ressources (en français pour la plupart, ou accessibles) pour approfondir vos connaissances et vous entraîner :

- **Cours en ligne et MOOCs :**
  - *« Objectif IA »* – MOOC gratuit en français créé par OpenClassrooms en partenariat avec l'Institut Montaign ([Objectif IA : initiez-vous à l'intelligence artificielle - francenum.gouv.fr](https://www.francenum.gouv.fr/formations/objectif-ia-initiez-vous-lintelligence-artificielle#:~:text=%C2%AB%20Objectif%20IA%20%3A%20initiez,de%20la%20population%20fran%C3%A7aise))】. Il offre une introduction grand public aux concepts de l’IA et à ses enjeux, idéal pour consolider les bases si vous débutez.
  - *« Initiation au Machine Learning »* sur OpenClassrooms – Un cours plus technique qui couvre les fondamentaux du machine learning (apprentissage supervisé, non supervisé) avec exercices pratiques.
  - *Cours de Machine Learning de Andrew Ng (Stanford/Coursera)* – Un des cours en ligne les plus célèbres (en anglais, mais sous-titré français). Excellente introduction mathématique et pratique au ML classique.
  - *Deep Learning Specialization (deeplearning.ai sur Coursera)* – Série de 5 cours (en anglais, sous-titres FR) par Andrew Ng, centrée sur le Deep Learning avec des exercices en Python/TensorFlow.
  - *Elements of AI* – Un cours en ligne gratuit (disponible en français) initié par l'Université d'Helsinki, qui explique les bases de l’IA sans aller trop dans le code, mais de manière très pédagogique.

- **Lectures et ouvrages :**
  - *« L’apprentissage profond avec Python » de François Chollet* – Traduction française du livre "Deep Learning with Python" par le créateur de Kera ([Nos livres - machinelearning.fr](https://machinelearning.fr/nos-livres/#:~:text=Notre%20premier%20livre%2C%20L%E2%80%99apprentissage%20profond,la%20port%C3%A9e%20de%20tous))】. Ce livre est une excellente introduction pratique au Deep Learning, avec des exemples en Python/Keras, adapté aux débutants motivés comme aux niveaux intermédiaires.
  - *« Hands-on Machine Learning avec Scikit-Learn, Keras et TensorFlow » d’Aurélien Géron* – Un livre (en anglais dans sa 2e édition, mais la 1ère existe en français) très complet qui couvre un large spectre : ML traditionnel (avec scikit-learn) puis deep learning avec TensorFlow. Rempli d’exemples de code concrets.
  - *« Le Deep Learning » par Ian Goodfellow, Yoshua Bengio, Aaron Courville* – Un ouvrage de référence (Deep Learning Book) couvrant en profondeur la théorie du deep learning. Disponible en anglais gratuitement en ligne. Référence pour ceux qui veulent creuser les bases mathématiques.
  - *« Python Machine Learning » de Sébastien Raschka* – Livre (en anglais, certaines éditions traduites en français) orienté code avec scikit-learn, très formateur sur les algorithmes de ML et leurs implémentations.

- **Documentation et tutoriels officiels :**
  - **Documentation TensorFlow** – Le site officiel [tensorflow.org](https://www.tensorflow.org) propose de nombreux tutoriels pas-à-pas, du niveau débutant (ex: introduction à Keras) jusqu’à avancé (personnalisation de training loops, etc.). Parcourez la section *Learn* et *Tutorials*. Il y a notamment des tutoriels en Colab très pratiques.
  - **Documentation PyTorch** – Sur [pytorch.org](https://pytorch.org) vous trouverez la section *Tutorials* avec des exemples variés (classification d’images, NLP, vision, etc.) et la section *Recipes* pour des snippets utiles. Le forum discuss.pytorch et les FAQ sont aussi d’une grande aide en cas de problème.
  - **Scikit-Learn** – Bibliothèque principale pour le machine learning “classique” en Python. Sa documentation (sur scikit-learn.org) contient un guide utilisateur et surtout des **exemples illustrés** pour chaque algorithme. Même si vous vous orientez plus DL, scikit-learn reste utile pour prétraiter les données, faire du clustering, etc.
  - **Kaggle (site)** – Kaggle est une plateforme de compétitions de Data Science, mais propose aussi une section *Courses* (gratuits, format courts interactifs) sur le ML, le Python, la visualisation de données, etc. S’inscrire à Kaggle permet d’accéder à des tonnes de **notebooks publics** réalisés par la communauté sur des datasets variés. C’est une mine d’or pour apprendre en regardant comment d’autres abordent un problème.
  - **Communautés francophones** : Le forum **Machine Learning France** (sur Facebook ou autres), le site **Developpez.com** section AI, ou des communautés comme **datascience.stackexchange.com** (en anglais) pour poser des questions. N’hésitez pas à échanger, poser des questions sur des problèmes précis que vous rencontrez – la communauté IA est vaste et plutôt active pour s’entraider.
  
- **Pratique et projets :**
  - **Kaggle** (encore) – Au-delà des cours, Kaggle offre des **datasets** libres d’accès et un environnement de notebooks en ligne gratuit (avec GPU limité) pour expérimenter. Vous pouvez vous entraîner en participant à des **compétitions débutants** ou en essayant de reproduire des **notebooks** existants puis de les modifier à votre sauce. C’est un excellent moyen de se faire la main sur des cas concrets et variés (vision, NLP, tabulaire…).
  - **Projets personnels** – Rien ne vaut de choisir un petit projet qui vous motive (par ex, classifier vos propres photos, entraîner un bot de jeu, analyser des données publiques d’open data…) et de le réaliser de A à Z. Même modeste, un projet personnel vous fera affronter les vrais défis (collecte de données, debugging, etc.) et consolidera vos compétences. Documentez-le et pourquoi pas partagez-le sur un Github ou un blog, cela peut être valorisant.
  - **Challenges en ligne** – Au-delà de Kaggle, il y a d’autres challenges IA plus ludiques : compétitions de **data science** locales, ou des sites comme **DrivenData** (compétitions orientées ONG/social), ou encore participer à des **hackathons** IA. Ces expériences boostent l’apprentissage et la motivation.

- **Veille et actualités :**
  - Suivez des **blogs** et des chaînes YouTube de vulgarisation en IA (par ex. *Welcome to the Jungle - Le Podcast IA*, *Mr. Bidouille* pour des explications de concepts, etc.).
  - **ArXiv** : si vous vous intéressez à la recherche de pointe en IA, arxiv.org répertorie les articles scientifiques pré-publication. On y voit les nouvelles architectures, etc. Des sites comme **Arxiv Sanity** ou **Papers With Code** résument et classent les articles, souvent avec du code source – utile pour se tenir informé des avancées (attention à l’infobésité quand même !).
  - **Groupes et meetups** : Rejoindre un meetup local sur l’IA / data science, ou des groupes en ligne (Discord, Slack) peut vous exposer à des échanges instructifs et vous permettre de poser des questions de vive voix.

Enfin, n’oubliez pas que la clé est de **pratiquer régulièrement** et de ne pas se décourager face à la courbe d’apprentissage. Commencez par des bases solides, progressez étape par étape, et ce qui vous semblait obscur au début (les matrices de poids, les dérivées partielles, etc.) deviendra clair à force de les manipuler. L’IA est un domaine vaste où l’on apprend tous les jours – même les experts continuent d’apprendre. 

Nous espérons que ce guide vous a apporté un bon panorama pour démarrer. Il ne vous reste plus qu’à appliquer ces connaissances, créer vos modèles et, qui sait, **innover** à votre tour en intelligence artificielle. Bonne exploration et apprentissage ! 

