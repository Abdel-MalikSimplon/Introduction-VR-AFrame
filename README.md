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

<pre><code><a-entity></code></pre>

Nous pouvons lui affecter des composants afin d'afficher quelque-chose ou lui faire faire quelque-chose. Par exemple, pour lui donner une forme et une apparence, nous pouvons lui affecter les composants de géométrie et de matériaux :

<pre><code><a-entity geometry="primitive: box" material="color: red"></code></pre>

Et si nous voulons ajouter de la lumière à notre objet, nous pouvons utiliser le composant <b>light</b> :

<pre><code><a-entity geometry="primitive: box" material="color: red"
                light="type: point; intensity: 2.0"></code></pre>
                
<b>geometry</b> --> La composante de la géométrie fournit une forme de base pour une entité. La géométrie générale est définie par la propriété <b>primitive</b>
La géométrie primitive en infographie, signifie une forme extrêmement basique.

Une fois la primitive définie, des propriétés supplémentaires sont utilisées pour mieux définir la géométrie.
Un composant <b>material</b> est généralement définie à côté pour donner une apparence aux côtés de la forme pour créer un maillage complet.

## Les propriétés de la géométrie primitive
### Les propriétés de base :

buffer -> transforme la géométrie dans un BufferGeometry pour réduire l'utilisation de la mémoire au prix d'être plus difficile à manipuler. Valeur par défault : true.

primitive -> peut-être : box, circle, cone, cylinder, plane, ring, sphere, torus, torusKnot. Valeur par défaut : None.

skipCache -> désactive la récupération de l'objet de la géométrie partagée à partir du cache. Valeur par défault : false.

Box : La primitive box définie une boite (un quadrilatère quelconque, pas seulement un cube).

<a-entity geometry="primitive: box; width: 1; height: 1; depth: 1"></a-entity>

Les valeurs possbles pour la box sont width, height et depth :

width -> Largeur (en mètres) des côtés sur l'axe x. Valeur par défaut -> 1.
height -> Hauteur (en mètres) des côtés de l'axe y.
depth -> Profondeur (en mètres) des côtés de l'axe Z.

Circle : La primitive circle définie les cercles en deux dimensions, qui peuvent être des cercles complets ou des cercles partiels (comme pac-man).
Note : de base le cercle est plat, un seul côté du cercle est donc rendu, si “side: double” (côté double) est pas spécifié sur le composant material.

<a-entity geometry="primitive: circle; radius: 1" material="side: double"></a-entity>

