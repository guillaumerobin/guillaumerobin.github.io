---
layout: post
title: "À nos claviers : il faut coder"
date: 2015-01-28t08:00:00-01:00
categories: m6r
tag: index
excerpt:
    Le M6R dispose de plusieurs machines virtuelles. Elles hébergent serveur web
    (Nginx), bases de données (MySQL), serveur SMTP (psotfix), serveur de test,
    espaces de sauvegarde et autres joyeuseries indispensables. Le site
    principal est un site Wordpress. Le réseau Nous le Peuple est basé sur le
    CMS Pligg.
---

*Après avoir lu cet article, vous pouvez envoyer un mail à
[dev@m6r.fr](mailto:dev@m6r.fr) ou rejoindre directement la [liste mail
publique](http://listes.m6r.fr/wws/info/nouslepeuple- devel).*

-----------

<a href="https://www.m6r.fr/2014/09/je-signe/"><img alt="Je signe pour la 6ème République" src="/images/2015-01-28/partage.png" class="pull-right" /></a>

Comme je l'ai évoqué dans mon post du mois dernier, je fais ici une présentation
de l'infrastructure technique du [Mouvement 6ème République](https://www.m6r.fr)
et de sa plateforme [Nous le Peuple](https://www.m6r.fr/nouslepeuple). Je le
fais pour plusieurs raisons. Je crois que les sujets techniques nous intéressent
toutes et tous. Les personnes qui participent au M6R ont l'esprit curieux. Je le
fais aussi car nous souffrons du fait que beaucoup ne se rendent pas compte du
travail qu'effectuent les bénévoles. Nous avançons dans les limites de notre
force de travail. Nous avons besoin que plus de personnes mettent leur temps à
la disposition du M6R. C'est la dernière raison d’être de ce post.

J'ai fait deux articles sur le sujet. <a href="{{page.next.url }}">Le
premier</a> se veut accessible à toutes et tous. Celui-ci est plus technique. Il
est destiné à être lus par des informaticiennes et des informaticiens. J'y
décris les taches à effectuer pour celles et ceux qui souhaiteraient apporter
leur aide.

## L'infrastructure serveur et le site principal

Le M6R dispose de plusieurs machines virtuelles. Elles hébergent serveur web
(Nginx), bases de données (MySQL), serveur SMTP (psotfix), serveur de test,
espaces de sauvegarde et autres joyeuseries indispensables.

Le site principal [https://www.m6r.fr/](https://www.m6r.fr/) est un site
Wordpress. Le thème a été écrit rapidement à l'aide de [Bootstrap
3](https://getbootstrap.com). Il a besoin selon moi d'un sérieux
rafraîchissement. La pile de liens en haut à droite de la page d'accueil peut
par exemple être améliorée. Toutes les pull requests sont les
bienvenues sur [le dépot github](https://www.github.com/m6r/). Vous pouvez
facilement travailler sur le thème. Installez en local une version vierge de
Wordpress, et clonez le dépôt dans le dossier `wp-content/themes/`.

<img alt="Le M6R en dates" src="/images/2015-01-28/le-m6r-en-dates.png" class="pull-left img-zoom" style="max-height: 1000px" />

## Nous le peuple

Le réseau [Nous le Peuple](https://www.m6r.fr/nouslepeuple) est basé sur le CMS
Pligg. Plusieurs raisons à cela. Inspirés par l'expérience du channel Reddit de
Podemos, nous souhaitions un site similaire où le contenu serait classé en
fonction des votes. Dès le départ, il a paru essentiel de ne pas dépendre de
plateformes externes. Il ne faut pas que la participation au M6R soit
conditionnée à l'inscription à une multitude de services dont il faudrait chaque
fois accepter les conditions d'utilisation. Pour des raisons de confidentialité
et de vie privée, il faut aussi que la liste des signataires ne quitte pas les
serveurs du M6R.

Nous avons envisagé de faire tourner notre propre instance de Reddit. Nous nous
sommes détournés de cette plateforme devant l'absence de garantie de
maintenabilité. Reddit peut en effet modifier sa structure de base de données
quand bon lui semble sans fournir les outils de migration adaptés. Leur
politique de sources libres semble avoir pour principal but de récolter les
contributions, et pas de permettre la création de clones.

Pligg est une application beaucoup plus légère, et fait le travail attendu. Elle
a subit quelques modifications pour être utilisable. Cela a nécessité un travail
important dans les jours qui ont précédé le lancement de Nous le Peuple. Le code
est disponible dans [ce dépôt](https://www.github.com/m6r/nouslepeuple).

### L'outil d'organisation de réunions locales

L'administration et la maintenance des serveurs prennent à elle seule un temps
considérable. Or il reste beaucoup à faire. La première des fonctionnalités à
ajouter est un outil pour permettre l'organisation de réunions locales et
l'affichage d'un agenda de ces réunions. Actuellement, les catégories locales
permettent de faire cela de manière rudimentaire. Certaines personnes le
demandent, mais il est évidemment interdit de donner à qui le veut la liste des
signataires de sa localité. Il faudrait que chacun puisse proposer un événement
et que la liste des événements proposés apparaisse publiquement. Celles et ceux
qui le souhaitent pourraient s'inscrire à ces événements. De cette manière,
chacun saurait à l'avance si un événement est suivi par les autres signataires
ou non.

Techniquement, il s'agirait probablement de créer une entité événement liée aux
posts. Sur la page de soumission d'un post, un certain nombre de champs
concernant l’événement pourrait être affichés et soumis si l'utilisateur le
souhaite. Une page devrait ensuite lister les événements et les faire apparaître
sur une carte. Vous pouvez venir discuter de ces questions techniques sur [la
liste mail publique](http://listes.m6r.fr/wws/info/nouslepeuple-devel).

### Bugs et améliorations marginales

Comme dans toute application, de nombreux petits bugs ont été recensés par les
utilisateurs. Les corriger permettrait d'améliorer l'expérience de chacun sur la
plateforme. N'importe qui peut proposer une pull request. Lisez simplement [les
règles à
suivre](https://github.com/m6r/nouslepeuple/blob/master/CONTRIBUTING.md) pour
contribuer.[^github] Je propose que la résolution des issues sur Github et la
liste des petites améliorations quotidiennes soient visibles quelque part sur le
site. Il est important que le mouvement se montre avançant.

### Maintenabilité

À moyen terme, il me parait nécessaire de s'affranchir de la branche originale
de Pligg. C'est déjà le cas depuis que nous avons uniformisé le coding style,
grâce à [php-cs-fixer](http://cs.sensiolabs.org/). Les modifications upstream
sont assez peu importantes pour être intégrées manuellement si besoin.

Basculer sur un framework de type Symfony2 serait l'idéal. Nous pouvons le faire
sans modifier le schéma de base de données. Le nombre d'entités est extrêmement
réduit. La première étape est cependant de changer de système de template.
Smarty peut être remplacé par Twig en ne modifiant qu'à minima le reste du code.
La bascule de la vingtaine de contrôleurs n'est pas le travail le plus
important.

Il faut que chacun réalise l'ampleur de notre tâche. Comme le soulignent
d'autres informaticiens sur Nous le Peuple, ce que nous faisons est unique. Il
n'y a pas d'outil qui offre facilement ce que nous voulons. Je ne dis pas que
des outils n'existent pas. Je dis qu'il faudrait de toute façon les adapter, et
qu'il vaut mieux tout développer sur la même plateforme. Si celle-ci est
construite sur un framework souple et solide, cela ne peut que bien se passer.
Il faut coder, à nos claviers !

[^github]:
    J'ai appris à programmer avec Github. Tout le monde n'a pas
    l'habitude du modèle fork and pull. C'est le plus adapté à un développement
    ouvert tel que le notre. On peut envisager d'organiser des formations si
    cela est vraiment un obstacle.
