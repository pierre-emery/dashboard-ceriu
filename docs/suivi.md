---
title: Suivi du projet
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Suivi de projet


---

## Semaine 1 (6-12 mai)

### Objectifs de la période
- Prendre connaissance du projet livré au trimestre précédent.
- Apprendre à utiliser Power BI
- Tester localement ce qui a été livré au trimsestre précédent.
- Mettre à jour les premières versions des documents index.md, analyse.md

### Travail réalisé

!!! abstract "Avancement"
    - [x] Lecture du projet précédent
        - Lecture du code livré
        - Lecture du rapport
    - [x] Tutoriels Power BI


### Décisions et ajustements


!!! info "Cadrage initial du projet"
    - Il faut adapter le projet en fonction des retours de CERIU
    - Transformer les scripts Python en une librairie réutilisable pour que le projet aille une valeur au-delà de l'usage chez CERIU.

### Difficultés rencontrées

---

## Semaine 2 (13-19 mai)

### Objectifs de la période
- Clarifier les attentes du CERIU
- Explorer les limites de Power BI, savoir quelles actions sont possibles (filtres, changements de vues, choisir affichages lors de l'export, dépendances entre tableaux/graphiques)
- Au fur et à mesure qu'on reçoit les accès, tester les endpoints.

### Travail réalisé

!!! abstract "Avancement"
    - [X] Tester plusieurs actions possibles dans Power BI
        - Drill through
        - Filtres
        - Choisir visuels à l'export
    - [ ] Tester les endpoints MailChimp
        - pas accès aux clés d'API

### Décisions et ajustements

!!! info "Attentes de CERIU"
    - Mise à jour des livrables attendus côté CERIU : 
        - Le livrable le plus attendu est de permettre la séparation par pôle.
        - Ajouter des nouvelles données (réseaux sociaux).
        - Changements de certains graphiques qu'ils considèrent inexploitable.

### Difficultés rencontrées


!! warning "Séparation par pôle"
    Aucun élément trivial dans les données (URL, paramètres GA4) ne permet de distinguer les pôles. Plusieurs pistes à explorer : taggage manuel via des dimensions personnalisées GA4, filtrage côté backend selon des règles d'URL, ou ajout d'une table de correspondance maintenue séparément. À discuter avec le CERIU.
---

## Semaine 3 (20–26 mai)

### Objectifs de la période
- Tester les endpoints GA4 et Mailchimp une fois les accès reçus.
- Faire un premier travail de prototypage pour préparer la prochaine rencontre avec le partenaire.

### Travail réalisé

!!! abstract "Avancement"
    - [x] Tests des endpoints
        - Configuration des clés nécessaire.
        - Tests des endpoints fonctionne bien.
    - [ ] Prototypage dans Power BI
        - Début de prototypage dans Power BI.
        - À poursuivre la semaine prochaine.

### Décisions et ajustements

!!! info "Nouvelle direction : page d'exploration interactive"
    - Suite à un échange avec le superviseur, puis avec le partenaire, ajout d'une page d'exploration libre aux livrables envisagés.
    - L'idée : permettre à l'utilisateur de questionner le jeu de données en choisissant lui-même quoi afficher et sous quelle forme, plutôt que de se limiter aux visuels figés.

!!! info "Rencontre avec le partenaire : clarification des attentes"
    - Échange détaillé avec le CERIU sur leurs attentes graphique par graphique et source par source.
    - Plusieurs points ont été mis au clair, notamment des alternatives au problème de la séparation par pôle en attendant la refonte de leur site web : utilisation d'un fichier Excel maintenu manuellement, listant les URLs et publications associées à chaque pôle, qui servirait de table de correspondance côté backend ou Power BI.

### Difficultés rencontrées

!!! warning "Mise à jour des données côté Power BI"
    Le partenaire a partagé qu'ils n'arrivaient pas à faire fonctionner le rafraîchissement automatique des données dans Power BI. Faudrait peut-être planifier un guide ou une démo permettant au CERIU de faire tourner localement le code d'Ibrahim de leur côté.

## Semaine 4 (27 mai–2 juin)

### Objectifs de la période
- Poser l'architecture de la page d'exploration (slicers source/métrique, field parameters, bookmarks)
- Avancer le nettoyage des données Power Query héritées
- Implémenter la catégorisation des campagnes Mailchimp

### Travail réalisé

!!! abstract "Avancement"
    - [x] Page pour Mailchimp retravaillée
        - Filtrage par mots-clés pour les sept catégories définies +  « Autre »
        - Graphiques et tableaux pour la vue générale ainsi que la vue par catégorie
    - [x] Organisation globale du prototype
        - Chaque page précise et générale sont en brouillons, à rendre plus joli.
    - [ ] Page d'exploration
        - [x] Slicer de source + slicer de métrique conditionnel
        - [x] Field parameters pour les dimensions temporelles et catégorielles
        - [ ] Bascule entre sources et changement de type de graphique via bookmarks marche pas encore parfaitement
   

### Décisions et ajustements

!!! info "Décisions"
    - Installer ou copier un thème, il faut rendre le graphique plus joli et plus facilement interprétable. 

### Difficultés rencontrées

!!! warning "Difficultés"
    - Difficultés à rendre la page d'exploration réellement exploitable à cause des limitations des bookmarks. 

## Semaine 5 (3 juin–9 juin)

### Objectifs de la période
- Clarifier l'architecture d'authentification du backend hérité
- Poursuivre le nettoyage des données (noms d'affichage, noms de pages)
- Avancer la navigation et la finition visuelle du dashboard

### Travail réalisé

!!! abstract "Avancement"
    - [x] Menu de navigation entre les pages
    - [x] Nettoyage Power Query
        - Nettoyage du nom des documents
        - Récupération des noms de pages depuis des tables additionnelles
        - Fix de certains problèmes ; voir difficultés
    - [x] Légendes implémentées pour les graphiques de la page principale
    - [ ] Page d'exploration 
        - [x] Fix pour le problème du changement de source, trois pages via boutons
        - [ ] Il y a encore des améliorations à faire pour l'outil. En parler avec le superviseur, limitations de bookmark.

### Décisions et ajustements

!!! info "Décisions"
    - Demande du CERIU, évaluer le passage de Power BI à Google Data Studio
### Difficultés rencontrées

!!! warning "Difficultés"
    - Préfixes GA4 obsolètes dans les requêtes héritées (`keyEvents:`, `customEvent:`) référençant des configurations qui ne correspondent plus ; les événements existent mais doivent être accédés sans ces préfixes.
    - Pour la page d'exploration, la bascule de mode réinitialise le type de graphique au défaut : comportement attendu simplement une limitation de bookmark.

## Semaine 6 (10 juin–16 juin)
> Template, à compléter
### Objectifs de la période
- Clarifier la problématique
- Explorer les solutions existantes
- Produire un premier prototype conceptuel

### Travail réalisé

!!! abstract "Avancement"
    - [x] Analyse de solutions existantes
        - Comparaison de trois outils similaires
    - [x] Prototype basse fidélité (Figma)
    - [ ] Validation utilisateur
        - Reportée à la semaine suivante

### Décisions et ajustements

> À compléter uniquement si des choix structurants ont été faits
> ou si l’orientation du projet a évolué.

!!! info "Décisions"
    - Abandon de l’approche X jugée trop complexe
    - Reformulation de la problématique suite aux premières analyses

### Difficultés rencontrées

> À compléter uniquement si des obstacles ont eu un impact réel
> sur l’avancement du projet.

!!! warning "Difficultés"
    - Problème de configuration du plugin Mermaid
        - Confusion entre `mkdocs-mermaid2-plugin` (pip)
          et `mermaid2` (nom du plugin)
        - Résolu après nettoyage et configuration correcte dans `mkdocs.yml`