# Session 3

Utilisation d'image, chemins relatifs et absolus, galleries photos.

## Intégrer des contenus externes

En HTML, il est facile d'intégrer des contenus externes à votre page.
Ces contenus peuvent être des images, des sons, des videos, des iframes, etc.

Pour intégrer ces contenus dans votre page, il est important de connaître leur emplacement.
Ils peuvent être hebergé depuis le même repertoire que votre site, dans un repertoire
 parent ou depuis un site externe.

### Chemin relatif

Lorsque vous faites référence à un contenu par rapport à votre page HTML,
on le chemin utilisé est dit "relatif". C'est à dire, relatif à votre page.

Par exemple:

* si l'image est dans le même dossier, son chemin est `chat.jpg`
* si l'image est dans un sous-dossier "images", son chemin est `ìmages/chat.jpg`
* si l'image est dans le dossier parent, son chemin est `../chat.jpg`
* si l'image est dans un dossier adjacent (même parent), son chemin est `../images/chat.jpg`

*:warning: Attention si vous déplacez votre fichier HTML, par exemple dans un sous-dossier,
veillez à ce que les chemins relatifs présents dans votre fichier n'aient pas changé.
Le cas échéant il faudra mettre à jour tous vos chemins relatifs*

### Chemin absolu

Lorsque le contenu auquel vous faites référence est hébergé sur un autre site Internet,
on doit utiliser un chemin absolu. Ce chemin spécifie l'adresse exacte d'un contenu.
Vous êtes habitués à ce genre de chemin puisque se sont les mêmes que ceux utilisés
sur Internet dans n'importe quel lien.

Voici plusieurs exemple de lien absolu:

* https://github.com/pirhoo/v2.pirhoo.com/raw/master/src/assets/images/penguin.jpg
* https://i.imgur.com/WdtOUOb.jpg

### Liens hypertextes

Comme nous l'avons vu auparavant, il est possible de faire un lien (absolu) vers
n'importe quel site Internet en utilisant la balise `a`. Vous pouvez égualement
utiliser des chemins relatifs dans vos lien pour faire référence à d'autres
fichiers HTML.

Par exemple si vous avez cette structure de fichiers et de dossiers:

```
.
├── chapitres
|   ├── chapitre-1.html
|   ├── chapitre-2.html
|   ├── chapitre-3.html
|   └── chapitre-4.html
├── images
|   └── lilbub.jpg
|   ├── penguin-mini.jpg
|   ├── penguin.jpg
└── index.html
```

Voici sa représentation dans `index.html` :

```html
<ul>
  <li>
    <a href="chapitres/chapitre-1.html">Chapitre 1</a>
  </li>
  <li>
    <a href="chapitres/chapitre-2.html">Chapitre 2</a>
  </li>
  <li>
    <a href="chapitres/chapitre-3.html">Chapitre 3</a>
  </li>
  <li>
    <a href="chapitres/chapitre-4.html">Chapitre 4</a>
  </li>
</ul>
```

Chacun des chapitres peut aussi faire référence au sommaire et aux autres chapitres :

```html
<h1>Chapitre 1</h1>

<p>Aliquam erat volutpat. Morbi gravida velit nisl. Duis facilisis aliquam nisi, ut auctor metus. Curabitur ex diam, mollis at odio sit amet, posuere hendrerit massa. Cras mi nisl, gravida quis orci sed, consequat sagittis est. Mauris ante magna, sagittis sit amet maximus nec, accumsan non urna. Aenean eget ipsum pretium, pretium tortor non, aliquet elit. Phasellus tempor quam ante, id scelerisque felis commodo et. Nulla vehicula sodales sapien vel scelerisque. Duis vestibulum a lacus in euismod. Etiam tincidunt elementum mattis. Nulla iaculis pellentesque consectetur.</p>

<ul>
  <li>
    <a href="chapitre-2.html">Chapitre suivant</a>
  </li>
  <li>
    <a href="../index.html">Retour au sommaire</a>
  </li>
</ul>
```

### Intégrer des images

La base `img` est très proche de la balise `a`. Elle accepte des chemins absolus
ou relatifs via l'attribut `src` :

```html
<img src="images/penguin.jpg" />
<img src="https://github.com/pirhoo/v2.pirhoo.com/raw/master/src/assets/images/penguin.jpg" />
```

En théorie, il faut systématiquement utiliser l'attribut `alt` pour décrire l'image.
Cette description est utilisée par les liseuses d'écran pour les mal-voyants. Ce
texte *alternatif* est aussi affiché à la place de l'image lorsque celle-ci ne
se charge pas correctement (mauvais lien, image corrompue, etc).

```html
<img src="images/penguin.jpg" alt="Un bébé manchot sur la banquise" />
```

### Faire une image cliquable

Dans de nombreuses situations, vous pouvez avoir besoin de créer une images cliquable.
Cela peut être utile lorsque par exemple vous voulez afficher une miniature et la
rendre cliquable pour afficher l'image dans sa taille originale.

Pour redimensionner l'image, il est possible d'utiliser une hauteur ou une largeur fixe
à l'aide des attributs `width` et `height` qui définissent la taille de l'image en pixels.
Si vous définissez uniquement l'un de ces deux attributs, l'image sera redimensionnée de manière
homotétique, c'est à dire sans la déformer.

```html
<p>Aliquam erat volutpat. Morbi gravida velit nisl. Duis facilisis aliquam nisi, ut auctor metus. Curabitur ex diam, mollis at odio sit amet, posuere hendrerit massa. Cras mi nisl, gravida quis orci sed, consequat sagittis est.</p>

<a href="images/penguin.jpg" target="_blank">
  <img src="images/penguin.jpg" alt="Un bébé manchot sur la banquise"  width="100" />
</a>
```

Redimensionner l'image directement en HTML n'est pas un bonne pratique, surtout
si votre image est très grande et longue à télécharger. Par conséquent il est recommandé
d'utiliser une image redimensionnée au préalable avec Photoshop ou n'importe quel
site d'édition d'images (comme [ResizeImage](http://resizeimage.net)).


```html
<p>Aliquam erat volutpat. Morbi gravida velit nisl. Duis facilisis aliquam nisi, ut auctor metus. Curabitur ex diam, mollis at odio sit amet, posuere hendrerit massa. Cras mi nisl, gravida quis orci sed, consequat sagittis est.</p>

<a href="images/penguin.jpg" target="_blank">
  <img src="images/penguin-mini.jpg" alt="Un bébé manchot sur la banquise"  width="100" />
</a>
```

### Les formats d'images

Sur Internet, on utilise principalement 3 formats d'images:

* `JPG` pour des images sans transparence plus ou moins compressées
* `PNG` pour des images avec des zones transparentes mais moins bien compressés
* `GIF` pour des images animées, avec des zones transparentes, très peu compressées et avec peu de couleurs.

Libre à vous de choisir le meilleur format pour une image. Tout dépend de vos besoin en terme de poids, transparence et animation.

## Intégrer des vidéos et du sons

Il est très facile d'intégrer un player vidéo ou sonore à votre page grâce aux
balises `video` et `audio` qui ont un fonctionnement très similaire:

```html
<video src="videos/penguin.mp4" poster="images/penguin.jpg" autoplay controls loop />
```

Le problème, c'est que pour les vidéos comme pour les sons, les formats suportés
par les navigateurs sont très différents. [Voir la listes des formats](https://developer.mozilla.org/fr/docs/Web/HTML/Formats_pour_audio_video).

Pour être certains que votre vidéos sera lisible, il faut donc la proposer en
plusieurs formats.

```html
<video autoplay loop controls poster="images/penguin.jpg">
  <source src="videos/penguin.mov" type="video/mov">
  <source src="videos/penguin.mp4" type="video/mp4">
  <source src="videos/penguin.ogv" type="video/ogv">
  <source src="videos/penguin.webm" type="video/webm">
  Votre navigateur ne permet pas de lire les vidéos HTML5.
</video>
```

## Intégrer des iframes

Comme vous pouvez l'observer, intégrer une vidéo à un site peut s'avérer complexe.
Pour cette raison on utilise la plupart du temps un service externe qui se chargera
de convertir votre vidéos dans de multiples formats et l'optimiser pour la rendre
lisible sur un maximum d'utilisateurs.

YouTube, Dailymotion Vimeo sont parmi les plus connus. Depuis une vidéo sur l'un
de ces site, vous pouvez trouver un code d'iframe en quelques clicks:

![Youtube video sharing](./images/youtube.png)

Vous n'aurez ensuite qu'à copier coller le code `iframe` pour l'intégrer dans votre site:

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/Tcx6YyXvvRI" frameborder="0" allowfullscreen></iframe>
```
