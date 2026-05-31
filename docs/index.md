---
title: Vue d'ensemble du projet
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Vue d'ensemble du projet

!!! info "Informations générales"
    **Session**: Été 2026  
    **Auteur(s)**: Pierre Emery (20278920) 
    **Thème(s)**: Intégration de données multi-sources, Tableaux de bord KPI, Réutilisabilité logicielle (librairie Python)  
    **Superviseur(s)**: Louis-Édouard Lafontant (DIRO)
    **Collaborateur(s):** CERIU (Centre d'expertise et de recherche en infrastructures urbaines)

## Description du projet

### Contexte
 
Les organisations qui produisent et diffusent du contenu en ligne s'appuient aujourd'hui sur de nombreuses plateformes (sites web, courriel marketing, réseaux sociaux, vidéo) pour atteindre leur public. Chacune de ces plateformes produit ses propres indicateurs et outils de consultation dans sa propre interface, ce qui rend la vue qu'une organisation peut avoir de sa propre activité difficile à interpréter. Mesurer l'efficacité d'une action de communication, identifier les contenus performants ou préparer un bilan mensuel/annuel implique souvent un travail manuel d'extraction de chacune de ces plateformes, ce qui demande du temps et rend un suivi régulier pénible et peu pratique.
 
Les tableaux de bord répondent bien à ce besoin en réunissant les indicateurs de plusieurs sources sur une interface unique. C'est dans ce contexte que s'inscrit ce projet, en partenariat avec le CERIU (Centre d'expertise et de recherche en infrastructures urbaines). Un premier travail mené par Ibrahim Ould Saada a posé les bases d'un système de tableaux de bord centralisant les *key performance indicators* (KPI) provenant de plusieurs plateformes (Google Analytics et Mailchimp).
 
Le projet actuel s'inscrit dans la continuité de ce travail. Il vise à compléter les intégrations manquantes (reseaux sociaux (X, LinkedIN, Facebook, Vimeo)), à régler les limites identifiées par le projet précédent, à s'adapter aux retours du partenaire CERIU et à transformer le backend en une librairie Python réutilisable, applicable à d'autres organisations ayant des besoins similaires de suivi multi-plateforme. L'interêt de la librairie est d'offir une alternative aux services tiers comme Coupler.io ou Windsor.ai (~20-30$/mois) permettent de connecter les données à Power BI.

### Problématique
 
Le projet aborde deux problématiques distinctes mais liées.
 
- La première est celle du CERIU : son tableau de bord actuel est fonctionnel mais incomplet. Trois sources prévues (LinkedIn, Vimeo, Google Search Console) ne sont pas intégrées, le rafraîchissement des données n'est pas automatisé, l'authentification GA4 est instable, et la séparation des indicateurs par pôle d'activité (demande prioritaire exprimée par le CERIU) n'a pas été implémentée.
 
- La seconde concerne la forme du backend hérité. Le code est aujourd'hui structuré comme une application FastAPI propre au contexte du CERIU. Une organisation ayant un besoin similaire (vouloir un backend custom plutôt que payer un service tiers d'intégration) devrait repartir du code et l'adapter manuellement, alors que la logique d'intégration des plateformes courantes (GA4, Mailchimp, etc.) est largement générique. Restructurer ce backend en librairie permettrait à un développeur tiers de construire un service équivalent en ne configurant que ce qui est spécifique à son organisation.



### Proposition et objectifs
 
Le projet propose deux livrables complémentaires :

Pour le CERIU : un tableau de bord complété couvrant les sources manquantes, avec une authentification stabilisée, un rafraîchissement automatisé, un mécanisme de séparation par pôle et une page d'exploration libre permettant à l'utilisateur de choisir lui-même les données et les visualisations à afficher.
Pour la communauté : une librairie Python qui distille la logique d'intégration multi-sources du backend en un outil réutilisable, accompagnée d'une documentation permettant à un développeur tiers de l'employer dans un autre contexte.

La librairie ne cherche pas forcément à remplacer les solutions existantes (connecteurs natifs, services tiers payants). Elle propose une alternative pour les organisations qui souhaitent éviter les abonnements récurrents, garder le contrôle sur les transformations appliquées aux données, ou se libérer des limites des connecteurs tiers.


### Méthodologie

Le projet adopte une démarche itérative plutôt qu'en cascade. Après une phase initiale d'études préliminaires (s'approprier le code hérité, analyser l'architecture livrée, identifier les points d'extension), le travail avance en cycles courts intégrant chacun typiquement une source ou une amélioration. Cette méthode de travail semble spécialement pertinente dans le cadre de ce projet puisqu'elle nous permet, à la fin de chaque nouvelle implémentation, de valider les changements avec le partenaire et nous permet aussi de le questionner afin de pister les améliorations suivantes.

La méthodologie, les choix d'implémentations et leurs facettes plus techniques seront explicitées dans le rapport final et sur la page [Réalisation](realisation.md) à mesure que le projet se concrétise.

### Validation et Évaluation

L'évaluation du projet s'appuie principalement sur la satisfaction du partenaire. Idéalement, le CERIU fera réellement utilisation du tableau de bord s'appropriera l'outil par leurs équipes afin d'analyser leur influence en ligne. Cet axe se valide au fil des cycles, par les retours obtenus à chaque itération sur les fonctionnalités livrées, et en fin de projet, par la capacité du CERIU à utiliser le tableau de bord de façon autonome pour leurs besoins de suivi.
Un second axe, concerne la transformation des scripts python d'Ibrahim est une bibliothèque documentée : un développeur tiers peut-il, en suivant la documentation, intégrer une nouvelle source ou employer la librairie dans un autre contexte sans modifier le code existant? Cet axe se mesure par l'effort requis pour ces opérations (étapes du guide, lignes de code à écrire, configuration à fournir). Il faut tout de même préciser que cet objectif reste secondaire, une librairie élégante mais qui ne sert pas correctement le CERIU manquerait l'objectif du projet.
Les critères opérationnels précis seront détaillés dans la page [Évaluation](evalution.md) à mesure que les cycles avancent.

## Équipe

Projet individuel réalisé par Pierre Emery dans la continuation d'un premier projet réalisé par Ibrahim Ould Saada, en partenariat avec le CERIU et sous la supervision de Louis-Édouard Lafontant (DIRO).

## Échéancier

!!! info
    Le suivi complet est disponible dans la page [Suivi de projet](suivi.md).

| Activités                      | Début   |   Fin    | Livrable                            | Statut      |
|--------------------------------|---------|----------|-------------------------------------|-------------|
| Ouverture de projet            | 4 mai   | 15 mai   | Proposition de projet               | ✅ Terminé  |
| Études préliminaires           | 4 mai   | 26 mai   | Document d'analyse                  | ✅ Terminé  |
| Conception & réalisation       | 26 mai  | 1 aout   | Librairie + dashboard complété      | 🔄 En cours |
| Présentation + Rapport         | 7 aout  | 14 aout  | Présentation + Rapport              | ⏳ À venir  |