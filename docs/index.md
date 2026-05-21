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
    **Thème(s)**: <!-- Thèmes principaux abordés dans le projet  -->  
    **Superviseur(s)**: Louis-Édouard Lafontant (DIRO)
    **Collaborateur(s):** CERIU (Centre d'expertise et de recherche en infrastructures urbaines)

## Description du projet

### Contexte
 
Les organisations qui produisent et diffusent du contenu en ligne s'appuient aujourd'hui sur de nombreuses plateformes (sites web, courriel marketing, réseaux sociaux, vidéo) pour atteindre leur public. Chacune de ces plateformes produit ses propres indicateurs et outils de consultation dans sa propre interface, ce qui rend la vue qu'une organisation peut avoir de sa propre activité difficile à interpréter. Mesurer l'efficacité d'une action de communication, identifier les contenus performants ou préparer un bilan mensuel/annuel implique souvent un travail manuel d'extraction de chacune de ces plateformes, ce qui demande du temps et rend un suivi régulier pénible et peu pratique.
 
Les tableaux de bord répondent bien à ce besoin en réunissant les indicateurs de plusieurs sources sur une interface unique. C'est dans ce contexte que s'inscrit ce projet, en partenariat avec le CERIU (Centre d'expertise et de recherche en infrastructures urbaines). Un premier travail mené par Ibrahim Ould Saada a posé les bases d'un système de tableaux de bord centralisant les *key performance indicators* (KPI) provenant de plusieurs plateformes (Google Analytics et Mailchimp).
 
Le projet actuel s'inscrit dans la continuité de ce travail. Il vise à compléter les intégrations manquantes (reseaux sociaux (X, LinkedIN, Facebook), vimeo/youtube), à régler les limites identifiées par le projet précédent, à s'adapter aux retours du partenaire CERIU et à transformer le backend en une librairie Python réutilisable, applicable à d'autres organisations ayant des besoins similaires de suivi multi-plateforme. L'interêt de la librairie est d'offir une alternative aux services tiers comme Coupler.io ou Windsor.ai (~20-30$/mois) permettent de connecter les données à Power BI.

### Problématique
 
Le projet aborde deux problématiques distinctes mais liées.
 
- La première est celle du CERIU : son tableau de bord actuel est fonctionnel mais incomplet. Trois sources prévues (LinkedIn, Vimeo, Google Search Console) ne sont pas intégrées, le rafraîchissement des données n'est pas automatisé, l'authentification GA4 est instable, et la séparation des indicateurs par pôle d'activité (demande prioritaire exprimée par le CERIU) n'a pas été implémentée.
 
- La seconde concerne la forme du backend hérité. Le code est aujourd'hui structuré comme une application FastAPI propre au contexte du CERIU. Une organisation ayant un besoin similaire (vouloir un backend custom plutôt que payer un service tiers d'intégration) devrait repartir du code et l'adapter manuellement, alors que la logique d'intégration des plateformes courantes (GA4, Mailchimp, etc.) est largement générique. Restructurer ce backend en librairie permettrait à un développeur tiers de construire un service équivalent en ne configurant que ce qui est spécifique à son organisation.



### Proposition et objectifs
 
Le projet propose deux livrables complémentaires :

Pour le CERIU : un tableau de bord complété couvrant les sources manquantes, avec une authentification stabilisée, un rafraîchissement automatisé, et un mécanisme de séparation par pôle.
Pour la communauté : une librairie Python qui distille la logique d'intégration multi-sources du backend en un outil réutilisable, accompagnée d'une documentation permettant à un développeur tiers de l'employer dans un autre contexte.

La librairie ne cherche pas forcément à remplacer les solutions existantes (connecteurs natifs, services tiers payants). Elle propose une alternative pour les organisations qui souhaitent un backend auto-hébergé — typiquement pour éviter les abonnements récurrents, garder le contrôle sur les transformations appliquées aux données, ou se libérer des limites des connecteurs tiers.


### Méthodologie

> Sera mis à jour au fil de l'avancement, beaucoup de spéculation pour l'instant
 
Puisque nous serons en contact hebdomadaire avec le CERIU, le projet adopte une démarche itérative. L'idée est d'avancer en cycles courts, chacun intégrant typiquement une source ou une amélioration et permettant d'ajuster l'architecture à la lumière de ce qui a été appris. La méthodologie détaillée sera précisée dans la page Études préliminaires à mesure que les premières itérations clarifient les contraintes techniques.

### Validation et Évaluation

> Sera aussi mis à jour au fil de l'avancement, beaucoup de spéculation pour l'instant


L'évaluation du projet s'appuiera sur deux axes : la satisfaction des besoins exprimés par le CERIU sur le tableau de bord finalisé, et la réutilisabilité de la librairie produite, mesurée par l'effort requis pour intégrer une nouvelle source ou employer la librairie dans un autre contexte. Les critères opérationnels seront détaillés dans la page Évaluation.


## Équipe

> Présentez les membres de l’équipe et le rôle principal de chacun dans le projet.

## Échéancier

!!! info
    Le suivi complet est disponible dans la page [Suivi de projet](suivi.md).

| Activités                      | Début   |   Fin   | Livrable                            | Statut      |
|--------------------------------|---------|---------|-------------------------------------|-------------|
| Ouverture de projet            | 4 mai   | 15 mai  | Proposition de projet               | ✅ Terminé  |
| Études préliminaires           | 4 mai   | 22 mai  | Document d'analyse                  | 🔄 En cours |
| Présentation + Rapport         | 7 aout  | 14 aout | Présentation + Rapport              | ⏳ À venir  |