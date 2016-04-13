# Introduction-VR-AFrame
Introduction à la réalitée virtuelle grâce au framework A-Frame


# Ce que permet A-Frame

A-Frame permet de créer des scenes en VR qui fonctionnent sur Desktop, Oculus et mobile avec seulement de l'HTML.
On peut manipuler nos scènes avec JavaScript comme nous le ferions pour du HTML, et on peut utiliser des framework JavaScript.

A-Frame introduit le modèle entity-component-system, un modèle couramment utilisé dans le développement 3D et jeux vidéo.

## Entity-Component-System

* Une entité (entity) est un objet d'usage général qui fait et rend rien en soi.
* Un composant (component) est un module réutilisable qui est branché sur les entités afin de fournir l'apparence, le comportement et / ou fonctionnalité. ils sont plug- and-play pour les objets .
* Un systeme (A system) fournit une portée globale, des services, et la gestion des classes de composants.

# Entity

Une entité est représenté par l'élément <a-entity>. Une entité est un objet réserver auquel nous appliquons des composants qui, dans l'ordre, vont fournir l'apparence, le comportement et les fonctionnalités.

Dans A-Frame, les entités sont liés aux composants position, rotation et scale.

Une entité de base n'a pas d'apparence, de comportement ou de fonctionnalité, pour dire les choses simplement, il ne fait rien.

<code><a-entity></code>

Nous pouvons lui affecter des composants afin d'afficher quelque-chose ou lui faire faire quelque-chose. Par exemple, pour lui donner une forme et une apparence, nous pouvons lui affecter les composants de géométrie et de matériaux :

<code><a-entity geometry="primitive: box" material="color: red"></code>

Et si nous voulons ajouter de la lumière à notre objet, nous pouvons utiliser le composant <b>light</b> :

<code><a-entity geometry="primitive: box" material="color: red"
                light="type: point; intensity: 2.0"></code>
