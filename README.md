# Introduction-VR-AFrame
Introduction à la réalitée virtuelle grâce au framework A-Frame


# Ce que permet A-Frame

A-Frame permet de créer des scenes en VR qui fonctionnent sur Desktop, Oculus et mobile avec seulement de l'HTML.
On peut manipuler nos scènes avec JavaScript comme nous le ferions pour du HTML, et on peut utiliser des framework JavaScript.

A-Frame introduit le modèle entity-component-system, un modèle couramment utilisé dans le développement 3D et jeux vidéo.

## Entity-Component-System

* <b>Une entité</b> (entity) est un objet d'usage général qui fait et rend rien en soi.
* <b>Un composant</b> (component) est un module réutilisable qui est branché sur les entités afin de fournir l'apparence, le comportement et / ou fonctionnalité. ils sont plug- and-play pour les objets .
* <b>Un systeme</b> (A system) fournit une portée globale, des services, et la gestion des classes de composants.

# Entity

Une entité est représenté par l'élément <a-entity>. Une entité est un objet réserver auquel nous appliquons des composants qui, dans l'ordre, vont fournir l'apparence, le comportement et les fonctionnalités.

Dans A-Frame, les entités sont liés aux composants position, rotation et scale.

Une entité de base n'a pas d'apparence, de comportement ou de fonctionnalité, pour dire les choses simplement, il ne fait rien.

<pre>
  <code><a-entity></code>
</pre>

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

<b>buffer</b> -> transforme la géométrie dans un BufferGeometry pour réduire l'utilisation de la mémoire au prix d'être plus difficile à manipuler. Valeur par défault : true.

<b>primitive</b> -> peut-être : box, circle, cone, cylinder, plane, ring, sphere, torus, torusKnot. Valeur par défaut : None.

<b>skipCache</b> -> désactive la récupération de l'objet de la géométrie partagée à partir du cache. Valeur par défault : false.

Box : La primitive box définie une boite (un quadrilatère quelconque, pas seulement un cube).

<pre><code><a-entity geometry="primitive: box; width: 1; height: 1; depth: 1"></a-entity></code></pre>

Les valeurs possbles pour la box sont width, height et depth :

<b>width</b> -> Largeur (en mètres) des côtés sur l'axe x. Valeur par défaut -> 1.
<b>height</b> -> Hauteur (en mètres) des côtés de l'axe y.
<b>depth</b> -> Profondeur (en mètres) des côtés de l'axe Z.

Circle : La primitive circle définie les cercles en deux dimensions, qui peuvent être des cercles complets ou des cercles partiels (comme pac-man).
Note : de base le cercle est plat, un seul côté du cercle est donc rendu, si “side: double” (côté double) est pas spécifié sur le composant material.

<pre><code><a-entity geometry="primitive: circle; radius: 1" material="side: double"></a-entity></code></pre>

Les propriétés de la primitive circle sont :

<b>radius</b> -> rayon (en mètres) du cercle. Valeur par défaut -> 1.

<b>segments</b> -> nombre de triangles pour construire le cercle, comme des tranches de pizza. Un plus grand nombre de segments signifie que le cercle sera plus rond.  Valeur par défaut -> 32.

<b>thetaStart</b> -> L'angle pour le premier segment où il commence. Peut être utilisé pour définir un cercle partiel. Valeur par défaut -> 0.

<b>thetaLength</b> -> L'angle au centre (en degrés), par défaut "360", ce qui en fait un cercle complet. Valeur par défaut -> 360.


Cone : La primitive "cone" est un cylindre primitif avec haut et bas ayant un rayon variables.

<pre><code><a-entity geometry="primitive: cone; radiusBottom: 1; radiusTop: 0.1"></a-entity></code></pre>
Ses propriétés sont :

<b>height</b> -> Hauteur du cône. Valeur par défaut -> 2

<b>openEnded</b> -> Définie si les extrêmités du cône sont ouverts (true) ou plafonnés (false). Valeur par défaut -> false.

<b>radiusBottom</b> -> Le rayon de l'extrémité supérieur du cône. Valeur par défaut -> 1.

<b>radiusTop</b> -> Le rayon de l'extrêmité supérieur du cône. Valeur par défaut -> 1.

<b>segmentsRadial</b> -> Nombre de faces segmentées autour de la circonférence du cône. Valeur par défaut -> 36.

<b>segmentsHeight</b> -> Nombre de rangées de faces le long de la hauteur du cône. Valeur par défaut -> 18.

<b>thetaStart</b> -> Angle de départ en degrés. Valeur par défaut -> 0.

<b>thetaLength</b> -> Angle central en degrés. Valeur par défaut -> 360.

## Cylindre Primitif

Le cylindre primitif peut définir des cylindres dans le sens traditionnel, comme un coca-cola, mais il peut également définir des formes telles que des tubes et des surfaces courbes. Nous allons passer eb revue certaines recette de cylindre ci-dessous.

### Cylindre basic

Un cylindre traditionnel peut être définie en utilisant seulement une hauteure et un rayon :

<pre><code><a-entity geometry="primitive: cylinder; height: 3; radius: 2"></a-entity></code></pre>

### Tube

Les tubes peuvent être définis en rendant le cylindre à l'extrémité ouverte, ce qui supprime les surfaces supérieure et inférieure du cylindre de telle sorte que l'intérieur soit visible. Un matériau à double face sera nécessaire pour afficher correctement.

<code><a-entity geometry="primitive: cylinder; openEnded: true" material="side: double"></a-entity></code></pre>

### Surface incurvée

Les surfaces incurvée peuvent être définies en spécifiant l'angle "thetaLength" telle que le cylindre ne courbe pas tout autour, ce qui rend le cylindre ouvert, puis ajouter un material -> side: double;

<pre><code><a-entity geometry="primitive: cylinder; openEnded: true; thetaLength: 180"
          material="side: double"></a-entity></code></pre>
          
Les propriétés d'un cylindre incurvé sont :

<b>radius</b> -> Le rayon du cylindre. Valeur par défaut -> 1.

<b>height</b> -> Hauteur du cylindre. Valeur par défaut -> 2.

<b>segmentsRadial</b> -> Nombre de faces segmentées autour de la circonférence du cylindre. Valeur par défaut -> 36.

<b>segmentsHeight</b> -> Nombre de rangés de faces le long de la hauteur du cylindre. Valeur par défaut -> 18.

<b>openEnded</b> -> Définie sir les extrémités du cylindre sont ouvertes (true) ou plafonés (false). Valeur par défaut -> false.

<b>thetaStart</b> -> Angle de départ en degrés. Valeur par défaut -> 0.

<b>thetaLength</b> -> Angle central en degrés. Valeur par défaut -> 360.

### Prisme

D'autres types de prismes peuvent êtres définie en faisant varier le nombre de segments radiaux (àsavoir, les côtés). Par exemple, pour faire un prisme hexagonal :
<pre>
  <code><a-entity geometry="primitive: cylinder; segmentsRadial: 6"></a-entity></code>
</pre>

### Plane

La primitive plane définit une surface plane. Noter que parce qu'il est plat, seulement un seul côté du plan sera rendu si "side: double" n'est pas spécifié sur le composant material.

<pre>
  <code><a-entity geometry="primitive: plane; height: 10; width: 10"
          material="side: double"></a-entity>
  </code>
</pre>
Ses propriétés sont :

<b>width</b> -> Largeur le long de l'axe X.
<b>height</b> -> Hauteur le long de l'axe Y.

### Ring

La géométrie ring définit un anneau plat, comme un C. Noter que parce qu'il est plat, seulement un côté de la bague sera rendue si "side: double" n'est pas spécifié sur le composant material.

<pre>
  <code>
    <a-entity geometry="primitive: ring; radiusInner: 0.5; radiusOuter: 1"
              material="side: double"></a-entity>
  </code>
</pre>

Ses propriétés sont :

<b>radius</b> -> Rayon du trou intérieur de l'anneau. Valeur par défaut -> 1.

<b>radiusOuter</b> -> Le rayon du bord extérieur de l'anneau. Valeur par défaut -> 1.

<b>segmentsTheta</b> -> Nombre de segments. Un nombre plus élevé signifie que l'anneau sera plus rond. Valeur par défaut -> 32.

<b>segmentsPhi</b> -> Nombre de triangles dans chaque face définie par des segments theta. Valeur par défaut -> 8.

<b>thetaStart</b> -> Angle de départ en degrés. Valeur par défaut -> 0.

<b>thetaLength</b> -> Angle central en degrés. Valeur par défaut -> 360.
