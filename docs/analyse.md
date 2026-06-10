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

Avant toute chose, il faut rappeler qu'un premier travail a déjà été fait avec de réelles études préliminaires, cette page s'accentuera donc sur l'analyse de cette solution livrée. 


### Compréhension du problème


La problématique à laquelle le CERIU fait face est typique pour toute organisation, ils atteignent un public à travers de nombreuses sources et il est donc difficile d'avoir une vue globale de leur influence. Le projet qui vise à traiter cette problématique s'articule donc en deux volets.

#### Volet CERIU
Le partenaire dispose d'un tableau de bord livré à l'automne 2025, fonctionnel mais incomplet. Plusieurs limites ont été documentées par le projet précédent : plusieurs sources prévues ne sont pas intégrées (LinkedIn, Vimeo, Google Search Console), le rafraîchissement n'est pas automatisé, l'authentification GA4 est instable, et la séparation par pôle d'activité (demande prioritaire exprimée par le CERIU) n'a pas été implémentée. Le travail consiste à reprendre ces points et à les ajuster aux retours actuels du CERIU.

#### Volet librairie
Le backend hérité est aujourd'hui un service FastAPI propre au contexte du CERIU. La logique qu'il contient : authentification OAuth, requêtes vers GA4 et Mailchimp, transformation des réponses, est en grande partie générique et pourrait être restructurée en librairie Python. Une telle librairie offrirait une alternative aux solutions tierces payantes (Coupler.io, Windsor.ai, autour de 20-30$/mois) pour les organisations qui souhaitent un backend auto-hébergé. Ce volet est une extension naturelle du travail de restructuration, pas une réponse à un besoin externe déjà exprimé.

### Analyse des solutions ou approches existantes

Le projet hérite d'une base livrée à l'automne 2025 par Ibrahim Ould Saada avec une architecture en trois couches :
1. **Sources externes** APIs des plateformes ciblées (GA4 et Mailchimp)
2. **Backend FastAPI** service Python qui reçoit les requêtes de Power BI, gère l'authentification aux APIs externes, récupères les données et transforme avant de les renvoyer en format JSON.
3. **Power BI** couche dde visualisation structurée en deux volets : un *backend* qui regroupe les tables techniques chargées de récupérer les données via le connecteur web, et un *frontend* qui regroupe les tables utilisées directement dans les visuels.

#### Limites du projet hérité

Le rapport du projet précédent documente explicitement plusieurs limites qui constituent une partie du travail à reprendre :
- Trois sources non intégrées : LinkedIn, Vimeo et Google Search Console.
- Rafraîchissement non automatisé sans intervention.
- Instabilité du token GA4 : le token expire après environ une semaine ce qui compromet l'usage opérationnel (solution payante mentionnée)
- Tableaux de bord par pôle non implémentés

### Contraintes et besoins



**Contraintes techniques et matérielles**
- L'API tourne sur `localhost`, ce qui rend impraticable le rafraîchissement automatisé via Power BI Service côté utilisateur final. Un hébergement sur une URL publique débloquerait ce point mais demande un budget côté CERIU.
- L'intégration des réseaux sociaux dépend de l'API de chaque plateforme : LinkedIn (tier Development suffisant à court terme), Facebook (dépréciation importante de métriques en juin 2026), X/Twitter (fonctionne en pay-per-use, vraisemblablement non livrable même si les coûts sont assez minimes).
- La refonte de leur siteweb n'a pas encore été finalisée, il n'y a donc toujours rien qui permet de séparer facilement les données par pôles.

**Organisationnelles et humaines**
- Pour pouvoir intégrer les nouvelles sources de données il me faut des accès à leurs plateformes de réseaux sociaux.

**Temporelles**
- Le temps alloué au projet est limité, du 6 mai à la présentation le 7 aout il n'y a que 3 mois, et une partie de se temps sera alloué à s'approprier le projet précédent, s'introduire aux nouvelles technologies et applications utilisé, préparer et presenter le rapport final ainsi que le guide d'utilisation et la demonstration qu'on souhaite livrer au CERIU. Le temps passé à developper le projet est donc restreint.

### Explorations techniques ou conceptuelles

Pour démarrer, la première chose qui a été faite est l'exploration des capacités de Power BI, l'idée est de voir à quel point on peut rendre les pages du tableau de bord dynamiques : field parameters, bookmarks, Selection pane.
Ensuite la construction des premières maquettes et essais d'architecture, le CERIU a fait un document avec tous les changements qu'ils souhaitent implémenter par rapport au premier tableau de bord livré, on a alors commencé à prototyper des nouvelles pages en fonction de ces changements demandés.

### Choix retenus

- **Table de correspondance pour les pôles** comme solution pragmatique pour la séparation par pôle en attendant la refonte de leur site web.
- **Ordre prioritaire des changements** puisque le temps est limité, le CERIU nous a explicité dans le document partagé avec les changements souhaités les nouvelles implémentations voulues et leur ordre de priorité. Ils veulent donc d'abord qu'on tente la séparation par pôles et en deuxième lieu l'implémentation des sources telles que LinkedIn et Facebook.
- **Page d'exploration** proposition par le superviseur que le partenaire à valider. Avoir une page d'exploration sur le tableau de bord leur permettant de questionner leur jeu de données.

### Références

**Documentation des API sources**  
- Google Analytics Data API (GA4) : <https://developers.google.com/analytics/devguides/reporting/data/v1>  
- Mailchimp Marketing API : <https://mailchimp.com/developer/marketing/api/>  
- LinkedIn Marketing API : <https://learn.microsoft.com/en-us/linkedin/marketing/>  
- Vimeo API : <https://developer.vimeo.com/api/reference>  
- Facebook Graph API (Meta) : <https://developers.facebook.com/docs/graph-api/>  

**Projet précédent**
- Rapport de projet, Ibrahim Ould Saada, décembre 2025.