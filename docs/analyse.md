---
title: Études préliminaires
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Études préliminaires

> :bulb: Cette page sert à documenter les recherches, analyses et explorations réalisées avant ou durant le projet
> Elle ne remplace pas le rapport final, mais permet de conserver une trace de votre démarche et des réflexions ayant guidé le projet.    


### Compréhension du problème

> Présentez votre compréhension du problème ou du besoin auquel le projet cherche à répondre.

Ce projet s'articule autour de deux volets.

#### Volet CERIU
Le partenaire dispose d'un tableau de bord livré à l'automne 2025, fonctionnel mais incomplet. Plusieurs limites ont été documentées par le projet précédent : plusieurs sources prévues ne sont pas intégrées (LinkedIn, Vimeo, Google Search Console), le rafraîchissement n'est pas automatisé, l'authentification GA4 est instable, et la séparation par pôle d'activité (demande prioritaire exprimée par le CERIU) n'a pas été implémentée. Le travail consiste à reprendre ces points et à les ajuster aux retours actuels du CERIU.

#### Volet librairie
Le backend hérité est aujourd'hui un service FastAPI propre au contexte du CERIU. La logique qu'il contient : authentification OAuth, requêtes vers GA4 et Mailchimp, transformation des réponses, est en grande partie générique et pourrait être restructurée en librairie Python. Une telle librairie offrirait une alternative aux solutions tierces payantes (Coupler.io, Windsor.ai, autour de 20-30$/mois) pour les organisations qui souhaitent un backend auto-hébergé. Ce volet est une extension naturelle du travail de restructuration, pas une réponse à un besoin externe déjà exprimé.

### Analyse des solutions ou approches existantes

> Présentez les outils, systèmes, approches ou projets similaires pertinents au projet.
>
> Vous pouvez discuter :
>
> - des forces et limites ;
> - des technologies utilisées ;
> - des fonctionnalités offertes ;
> - des approches de conception.

Le projet hérite d'une base livrée à l'automne 2025 par Ibrahim Ould Saada avec une architecture en trois couches :
1. **Sources externes** APIs des plateformes ciblées (GA4 et Mailchimp)
2. **Backend FastAPI** service Python qui reçoit les requêtes de Power BI, gère l'authentification aux APIs externes, récupères les données et transforme avant de les renvoyer en format JSON.
3. **Power BI** couche dde visualisation structurée en deux volets : un *backend* qui regroupe les tables techniques chargées de récupérer les données via le connecteur web, et un *frontend* qui regroupe les tables utilisées directement dans les visuels.

#### Limites du projet hérité

Le rapport du projet précédent documente eexplicitement plusieurs limites qui constituent une partie du travail à reprendre :
- Trois sources non intégrées : LinkedIn, Vimeo et Google Search Console.
- Rafraîchissement non automatisé sans intervention.
- Instabilité du token GA4 : le token expire après environ une semaine ce qui compromet l'usage opérationnel (solution payante mentionnée)
- Tableaux de bord par pôle non implémentés

### Contraintes et besoins

> Présentez les principales contraintes du projet :
>
> - techniques ;
> - humaines ;
> - matérielles ;
> - organisationnelles ;
> - temporelles.

### Explorations techniques ou conceptuelles

> Présentez les premiers tests, prototypes, validations ou explorations réalisés :
>
> - technologies testées ;
> - essais d’architecture ;
> - expériences ;
> - validation d’idées ;
> - maquettes ou esquisses.

### Choix retenus

> Expliquez les choix effectués pour la suite du projet et les raisons derrière ces décisions.

### Références

> Ajoutez les principales références utilisées :
>
> - documentation ;
> - articles ;
> - tutoriels ;
> - projets similaires ;
> - bibliothèques ;
> - normes ou ressources techniques.