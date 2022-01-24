# Redis - Cheat sheet

> Date : 24.01.2022
>
> Auteurs : Gwendoline Dössegger, Noémie Plancherel, Gaby Roch, Cassandre Wojciechowki

### Présentation générale

Redis vient de `Remote Dictionary Server`. C'est un système de gestion de bases de données NoSQL structuré selon un principe "clé-valeur". Ce software stocke les bases de données dans la RAM ce qui lui permet d'avoir de très hautes performances. Il est opensource, multiplateforme et gratuit.

### Database caching

Redis utilise la stratégie de mise en cache "look-aside". 

Quant à la gestion du cache, elle dépend de la taille de mémoire maximale allouée au cache (`maxmemory`) ainsi que des politiques d'expulsion fournies. Ces dernières sont les actions effectuées pour déterminer quelle donnée sera supprimée afin d'en ajouter de nouvelles dès lors que la taille du cache atteint son maximum.

Pour cela il existe deux algorithmes :

- **LRU approximatif** : est une implémentation approximative de LRU (Least Recently Used). Cette solution permet d'offrir un meilleur coût mémoire. Elle consiste donc à déterminer selon un petit échantillon de clés celles ayant le temps d'accès le plus ancien pour la supprimer. Ainsi, plus la taille de l'échantillonage est grande plus les performances seront améliorées. 
- **LFU** (Least Frequently Used) : utilise un compteur pour définir la fréquence d'accès à l'objet. Lors de la création d'un objet, on lui assigne une valeur par défaut qu'on incrémente à chaque fois qu'on accède à la clé. Puis le compteur est décrémenté au fil du temps qui passe. Cette solution indique que plus la valeur du compteur est petite, plus la probabilité que la donnée soit expulsée du cache est grande.















