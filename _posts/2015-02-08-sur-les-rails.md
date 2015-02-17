---
layout: post
title: "Sur les rails !"
date: 2015-02-08
categories: m6r
tag: index
excerpt: "Mon post de la semaine dernière a permis une belle avancée pour le
M6R. Quelques personnes sont venues renforcer la trop petite équipe de
bénévoles. Contrairement à la dernière fois, peu avant le lancement de Nous le
Peuple, il n'y a pas d'urgence immédiate. Nous prenons donc le temps de nous
organiser. Ce sera utile pour la suite. Voici comment fonctionneront les
contributions de l’équipe de développeurs."
---

Mon post de la semaine dernière a permis une belle avancée pour le M6R. Quelques
personnes sont venues renforcer la trop petite équipe de bénévoles.
Contrairement à la dernière fois, peu avant le lancement de Nous le Peuple, il
n'y a pas d'urgence immédiate.[^1] Nous prenons donc le temps de nous organiser.
Ce sera utile pour la suite. Voici comment fonctionneront les contributions de
l’équipe de développeurs.

La répartition du travail à faire et les discussion techniques se font sur la
liste mail publique. N'importe qui peut la rejoindre. Pour proposer des
modifications du code qui fait fonctionner Nous le Peuple, nous nous basons sur
le système [git](http://git-scm.com/) et la plateforme de développement
collaborative [Github](https://github.com/).

Personne ne peut modifier directement [le dépôt
public](https://github.com/m6r/nouslepeuple) où est stocké le code du M6R.[^2]
Chacun peut copier le dépôt et disposer de son propre exemplaire du code pour y
faire des modifications. Le système git permet de tracer les différences entre
la version du M6R et la version modifiée par le développeur. Les contributeurs
proposent ensuite d'incorporer leur travail dans le dépôt central. Github offre
une interface simple pour effectuer ces propositions et les accepter.

Le développement de la plupart des [logiciels
libres](https://fr.wikipedia.org/wiki/Logiciel_libre) fonctionne sur ce modèle.
Je serai fier du M6R si ce fonctionnement se perpétue pour nous aussi et fait
ses preuves. Il est adapté aux situations où les contributions sont nombreuses
et où l'équipe n'a pas de contours définis. S'il y a lieu, chaque demande de
fusion peut faire l'objet d'une discussion collective.

## Déroulement hebdomadaire

**Chaque jour**, les modifications proposées par les contributrices et les
contributeurs peuvent être intégrées au dépôt central. Elles nécessitent
néanmoins d'être testées avant d’être utilisées sur le site de Nous le Peuple.
Un serveur de test est mis à jour quotidiennement avec les dernières
modification incorporées. Une équipe y vérifie que ces modifications
fonctionnent et qu'elles ne comportent pas de bugs.

<img alt="Schéma du déroulement de la semaine"
src="/images/2015-02-08/schemaworkflow.png" class="pull-right img-zoom" />

**Chaque vendredi soir**, la version sur le serveur de test est gelée : on arrête de
la mettre à jour avec les modifications apportées sur le dépôt central.

**Jusqu'au lundi matin**, les modifications de la semaine sont donc testées. Le
lundi matin, la version testée est transférée sur le serveur du M6R, et devient
visible par toutes et tous. J'ai pour projet que nous publions durant le week-
end les modifications à venir.

Commence alors un nouveau cycle. Les modifications proposées durant le week-end
sont incorporées dans le serveur de test, comme le seront toutes les
modifications proposées jusqu'au vendredi soir suivant. Elles seront visibles
pour tout le monde le lundi suivant.

Exceptionnellement, en cas de bug majeur à réparer urgemment, il est toujours
possible de ramener le serveur de test à la version utilisée actuellement sur le
site. Il faut alors travailler la correction du bug sur le serveur de test. Une
fois prête, on peut la mettre immédiatement en route, avant de revenir au
processus normal de fonctionnement.

Il y a plusieurs avantages à cela. Cela nous permet de nous fixer des horizons
courts, avec des petits objectifs raisonnables. Nous avons ensuite le week-end
pour découvrir un bug majeur dans notre travail. Enfin nous pouvons annoncer sur
Nous le Peuple les modifications de la semaine.


[^1]: L'élection de [l’assemblée représentative](https://www.m6r.fr/2015/02/designation-dune-assemblee-representative-du-m6r/) ne commence que dans deux semaines, une éternité !
[^2]: Pour ma part, ayant créé le dépôt, j'ai la possibilité technique de faire des modifications directement. Je m'obligerai quand même des requêtes de fusion afin que tout le monde soit sur un  pied d'égalité.

