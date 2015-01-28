---
layout: post
title: "L'infrastructure technique du M6R"
date: 2015-01-28t08:00:01-01:00
categories: m6r
tag: index
---

Comme je l'ai évoqué dans mon post du mois dernier, je fais ici une présentation
de l'infrastructure technique du [Mouvement 6ème République](https://www.m6r.fr)
et de sa plateforme [Nous le Peuple](https://www.m6r.fr/nouslepeuple). Je le
fais pour plusieurs raisons. Je crois que les sujets techniques nous intéressent
toutes et tous. Les personnes qui participent au M6R ont l'esprit curieux. Je le
fais aussi car nous souffrons du fait que beaucoup ne se rendent pas compte du
travail qu'effectuent les bénévoles. Nous avançons dans les limites de notre
force de travail. Nous avons besoin que plus de personnes mettent leur temps à
la disposition du M6R. C'est la dernière raison d’être de ce post.

J'ai fait deux articles sur le sujet. Celui-ci se
veut accessible à toutes et tous. Le second est plus technique. Vous pouvez <a
href="{{ page.previous.url }}">le lire ici</a>. J'y décris les taches à
effectuer pour celles et ceux qui souhaiteraient apporter leur aide.

----------------------------

1. Table des matières
{:toc}

*Cet article commence par un topo didactique sur le fonctionnement d'un
serveur web. J'y décris ce qui se passe lorsqu'une page web s'affiche dans votre
navigateur. L’intérêt est purement scientifique. Pour lire ce qui concerne
spécifiquement le M6R, vous pouvez sauter à la [dernière section](#travailler-
sur-les-chantiers-existants).*

## Parcours d'une requête

Lorsque vous vous rendez sur [m6r.fr](http://www.m6r.fr), votre navigateur
envoie une **requête** au serveur. Il lui demande de charger une page. Le
**serveur** reçoit cette requête, la traite et renvoie un certain nombre de
données à votre navigateur. Ces données constituent la **réponse** du serveur.
La réponse contient les informations, contenu et style, qui constituent la page
web. Les trois paragraphes suivants détaillent ce qui se passe avant que la page
ne s'affiche sur votre navigateur.

<a href="https://www.m6r.fr/2014/09/je-signe/"><img alt="Je signe pour la 6ème République" src="/images/2015-01-28/partage.png" class="pull-right" /></a>

### Requête

**Une requête** est un message de quelques lignes qui donne les informations sur
ce que vous souhaitez voir. Traduite en français, une requête pourrait s'écrire
: *Bonjour m6r.fr, je suis Guillaume (mon identifiant secret est ---). Je
souhaite voir la liste des posts de la catégorie << Partage des richesses >>,
classés par nombre de commentaires.*[^page] En réalité la requête ressemble à ça
: <a data-toggle="collapse" href="#20150127HTTPRequest" aria-expanded="false"
aria-controls="20150127HTTPRequest">(cliquez pour dérouler)</a>. C'est
évidemment incompréhensible.[^http]

<pre class="collapse" id="20150127HTTPRequest"><code>GET /nouslepeuple/new.php?part=commented&amp;category=partage-des-richesses HTTP/1.1
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:35.0) Gecko/20100101 Firefox/35.0
Host: www.m6r.fr
Cookie :"mnm_user=GuillaumeR; mnm_key=R2VpbGxhdW1lUjoyMjVxa1NudUE5ZrlBOjA2YWJlM2YyODz5ZDdhNDljMDNmOWQ2ZDNlM2E5N2Qy; PHPSESSID=ocs6d5d95svf389rmcpns9gp40;"
Connection: keep-alive
Cache-Control: max-age=0
Accept-Language: fr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8</code></pre>

Le serveur du M6R traite plusieurs de ces requêtes par seconde. N'importe qui
peut ouvrir une connexion avec le serveur pour lui envoyer une requête. On dit
que le serveur **écoute**. Que se passe-t-il lorsqu'une requête est reçue ?

<img alt="Schéma du parcours d'une requete" src="/images/2015-01-28/requete.png" class="pull-left img-zoom" style="max-height: 1000px"/>

### Application

Le **serveur** n'est rien d'autre qu'un ordinateur très puissant. Il est
connecté à Internet. Plusieurs logiciels travaillent ensemble pour générer les
réponses qui sont renvoyées à votre navigateur. Pour chaque requête reçue, une
réponse différente est renvoyée. Le schéma à gauche résume le fonctionnement que
j'explique dans les paragraphes suivants. Il se lit dans le sens inverse des
aiguilles d'une montre. Je m'excuse pour le manque de clarté, je ne suis pas
fort en dessin.

Un premier programme est chargé de réceptionner les requêtes. Il extrait de la
requête les informations essentielles. La plus importante est la partie droite
de l'adresse web, dans notre cas
```/nouslepeuple/new.php?part=commented&category=partage-des-richesses```.

Ces informations sont transmises à un autre programme. C'est l'application
proprement dite, qui est spécifique à notre site. Le travail essentiel de cette
application est de placer des données dans un modèle de page. D'un coté, il y a
en effet la liste des posts classés dans la base de données : leur titre, leur
résumé, leur nombre de vote conservés dans une sorte d'immense tableau. De
l'autre, le modèle de page : toutes les informations sur la taille des titres,
leur couleur, la disposition des données. A chaque fois, l'application réunit
les données et le modèle de page en un seul document. Ce document constituera la
**réponse** du serveur.

Il en va ainsi de Nous le Peuple comme du site principal. Cette application
constitue l'essentiel de ce sur quoi les développeurs doivent travailler lorsque
nous souhaitons apporter de nouvelles fonctionnalité à Nous le Peuple.

Le troisième programme est donc la base de données. C'est elle qui contient les
articles, les votes, les profils utilisateurs, dans des immenses tableaux. Pour
communiquer avec elle, le deuxième programme lui envoie des requêtes, de la
même manière que votre navigateur envoyait des requêtes au serveur web du M6R.
On parle d'ailleurs de serveur de base de données. Contrairement au serveur web
qui écoute les requêtes venant de l'Internet entier, le serveur de base de
données n'écoute que les requêtes provenant de l’application. Une requête à la
base de données ressemble à ça : <a data-toggle="collapse"
href="#20150127SQLRequest" aria- expanded="false" aria-
controls="20150127SQLRequest">(cliquez pour dérouler)</a>.

<pre class="collapse" id="20150127SQLRequest"><code>SELECT link_id, link_votes, link_karma, link_comments FROM links WHERE (link_category=4) GROUP BY link_id LIMIT 30;</code></pre>

### Réponse

L'application a terminé de générer le contenu de la réponse. Elle est écrite
dans un langage informatique appelé HTML. Elle la fait passer au premier
programme, qui avait réceptionné votre requête. Celui-ci a pour tache spécifique
de vous renvoyer cette réponse via Internet. Votre navigateur interprète le code
HTML, la page s'affiche.

## Un réseau de machines virtuelles

Le serveur qui reçoit les requêtes du navigateur consiste en une seule machine.
Cependant, tous les logiciels participant à la génération de la réponse ne se
trouvent pas sur la même machine. Le serveur de base de données a sa propre
machine. Les mails sont gérés sur une seconde machine. Une autre encore sert à
effectuer des tests. Toutes ces machines communiquent entre elles par un réseau
local. Seul le serveur web et le serveur de mail sont connectés à Internet.

Cependant tous ces ordinateurs, tout comme le réseau local, sont virtuels. Ces
machines ne sont que des abstractions simulées par un plus gros ordinateur. Les
programmes exécutés dans ces machines virtuelles fonctionnent exactement comme
si ils disposaient de leur propre machine physique et d'un vrai réseau câblé.
Cependant, lorsqu'ils croient communiquer avec les pièces de l'ordinateur, ils
communiquent en fait avec un plus gros programme. Ce dernier répartit la
puissance de calcul d'une grosse machine physique entre les différentes machines
virtuelles. Cette technologie s'appelle la **virtualisation**. Elle permet par
exemple de créer une nouvelle machine virtuelle rapidement, ou d'augmenter la
puissance d'une machine virtuelle en baissant celle d'une autre.

## Travailler sur les chantiers existants

Une grande partie des dons est utilisée pour cette infrastructure. La location
des serveurs ne constitue pas les seuls frais liés à l'informatique. Il y a
aussi d'autres éléments plus techniques encore. Les comptes complets seront
normalement publiés le mois prochain.

Nous sommes toutes et tous des bénévoles. Nous avons besoin d'informaticiennes
et d'informaticiens. Avant même de proposer de nouveaux chantiers, l'aide de
chacun est donc la bienvenue pour rejoindre l'équipe et travailler sur les
chantiers existants. Plus nous serons nombreux, plus nous pourrons apporter à
Nous le Peuple les améliorations demandées régulièrement.

<img alt="Ma 6ème République combattra les ultra-riches" src="/images/2015-01-28/ultra-riches.jpg" class="pull-right img-zoom">

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

De nombreux petits bugs ont été signalés. Le recensement systématique en a été
fait. A lui seul, il nécessite un travail important. Il faut vérifier à
chaque fois en quoi consiste le bug, dont le signalement n'est souvent que très
sommaire. Il doit être reproduit dans les mêmes circonstances afin d’être
identifié et isolé. La liste de ce qu'il faut corriger n'attend que les
contributions des développeurs pour se raccourcir. Si vous connaissez des
développeurs qui ont signé pour le M6R, n'hésitez pas à leur en parler et à leur
envoyer le lien vers cet article.

Il faut que chacun réalise l'ampleur de notre tache. Comme le soulignent
d'autres informaticiens sur Nous le Peuple, ce que nous faisons est unique. Il
n'y a pas d'application pré-construite qui fasse facilement ce que nous voulons.
Nous expérimentons politiquement et techniquement. Il faut bien comprendre que
chaque modification demande des heures de travail. Nous le Peuple se base sur
une autre application appelée Pligg. La simple modification du processus
d'inscription des utilisateurs pour l'adapter aux besoins du M6R a demandé
plusieurs heures de travail. Il en va de même pour l'outil qui compte les
signatures depuis le lancement du M6R. Il faut additionner les signatures de
[l'appel](https://www.m6r.fr/2014/09/je-signe/) et les inscrits de Nous le
Peuple, puis en retrancher les doublons. Puis, on doit rendre cette donnée
disponible partout où l'on souhaite l'afficher sur le site. Là encore, plusieurs
heures de travail.

Le développement de ces fonctionnalités a lieu sur une plateforme participative
appelée [Github](https://www.github.com/m6r). Chaque développeur peut y proposer
le travail qu'il effectue pour avancer sur les chantiers en cours. L'ensemble du
code informatique qu'utilise le M6R est public, et librement utilisable par
toute personne qui le souhaite.[^donnees] La discussion sur les nouvelles
fonctionnalités à apporter a lieu en permanence sur Nous le Peuple. Les échanges
liés aux questions techniques ont lieu sur une liste mail publique hébergée par
le M6R. À nos claviers !


[^page]:
    Ce qui correspond à [cette page là](https://www.m6r.fr/nouslepeuple/new.php?part=commented&category=partage-des-richesses).

[^http]: Cependant, ce n'est rien que du texte. Un informaticien comme moi peut le lire et le comprendre. Votre navigateur ne communique pas directement en 0 et en 1.
[^donnees]: Il ne s'agit évidemment que du code qui fait fonctionner et non les données confidentielles qu'il manipule.
*[votre navigateur]: Firefox, Chrome, Internet Explorer, Safari...
*[HTTP]: Hypertext Transfer Protocol
*[HTML]: Hypertext Markup Language
