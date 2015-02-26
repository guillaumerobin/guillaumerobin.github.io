---
layout: post
title:  "Ouverture des candidatures"
date:   2015-02-25
categories: m6r
tag: index
---

La plateforme de vote pour l'Assemblée Représentative a été lancée ce weekend.
C'est déjà un succès avec plusieurs centaines de candidatures postées. Un bémol,
la proportion trop importante d'hommes dans les candidat-e-s. Nous avons bien
fait d'organiser une élection paritaire.

C'est une nouvelle étape pour le M6R et Nous le Peuple. Cette assemblée
permettra au mouvement d'avoir une existence nationale. Car nous commençons à
nous faire connaître. Nous enregistrons un grand nombre d'inscriptions ces
derniers jours. Le processus a même intéressé quelques journalistes, qui ont
demandé des informations sur son déroulement. Il faut dire que c'est
radicalement nouveau. Les candidatures sont ouvertes à toutes et tous. Tout le
monde pourra voter. Je crois que personne ne réalise encore de ce que nous
sommes en train d'accomplir.

<img alt="Votez !" src="/images/2015-02-25/votez.png" class="pull-right img-zoom">

Si nous réunissons à nous réunir rapidement, nous aurons déjà franchi une étape.
L'assemblée devra se mettre au travail dès que possible. Nous le Peuple a un
objectif que nous partageons tous : rendre majoritaire l'idée de 6ème République
dans notre pays. Il ne s'agit pas d'ajouter un nombre au compteur.
C'est une manière de changer radicalement le système, auquel plus personne ne
croit. Voici pour rappel le texte signé par presque 80 000 personnes
(sur [cette page](https://www.m6r.fr/je-signe/)) :

> <<Je demande l’élection d’une assemblée constituante qui fonde avec les citoyens
> la 6e République. Une République débarrassée de la monarchie présidentielle et
> fondant les nouveaux droits personnels, écologiques et sociaux dont notre pays
> a besoin.>>

Plusieurs choses nous feront progresser. Les partages sur les réseaux sociaux
et le bouche à oreille sont importants. C'est encore plus efficace lorsque
cela s'appuie sur des productions faites par toutes et tous, comme pour les
visuels proposées ces derniers mois.

Surtout, il est important que les signataires se rencontrent ailleurs que sur
Nous le Peuple, c'est-à-dire puissent échanger de vive voix. L'outil
d'organisation de réunion locale est en retard, le calendrier ayant été bousculé
par le vote. Une solution de secours, provisoire, sera mise en place dans les
prochains jours.

# L'outil de vote

J'ai écrit l'outil de vote la semaine dernière. Ces quelques 2300 lignes de code
constituent aussi la base d'une nouvelle version de la plateforme pour Nous le
Peuple, qui sera plus facilement extensible par l'équipe de développeurs et
développeuses bénévoles.[^1] J'ai <<libéré>> l'outil hier, en publiant le [code
source](https://github.com/m6r/nlp). Il est mis à disposition sous licence
AGPL : cette licence de logiciel libre autorise n'importe qui à le copier et le
modifier, à la condition de redistribuer les modifications sous les mêmes
termes.

Autre bonne nouvelle côté informatique : l'acquisition d'un
petit bloc d'adresses IP (les numéros identifiants un ordinateur sur internet).
Cela va permettre de créer plus de machines virtuelles et de les relier à
Internet[^2]. Cela a un intérêt : les machines virtuelles peuvent faire office de
<<bac à sable>> et peuvent être prêtées à un-e développeur-se bénévole pour y
faire des essais, sans mettre en danger la sécurité des serveurs où sont
hébergées Nous le Peuple et la base de données. Cela me permettra peut-être de
consacrer moins de temps à administrer les serveurs, et ainsi passer plus de
temps sur [Nous le Peuple](https://www.m6r.fr/nouslepeuple). J'ai pris aussi
quelques heures pour installer un logiciel permettant d'administrer facilement
nos machines virtuelles.[^3] Sur tous les plans, nous avançons&nbsp;!

[^1]:
    Il est développé entre autre grâce à [Symfony](http://symfony.com/), un
    outil [libre](https://fr.wikipedia.org/wiki/Logiciel_libre) développé par
    l'entreprise française Sensio Labs.

[^2]:
    Voir
    [cette note](http://localhost:4000/m6r/2015/01/28/l-infrastructure-technique-du-m6r.html)
    pour une explication sur les machines virtuelles.

[^3]:
    Ce logiciel, [Xen Orchestra](https://xen- orchestra.com/), est aussi
    développé par une entreprise française, basée à Grenoble. La France
    n'est pas en retard concernant l'innovation en informatique !
