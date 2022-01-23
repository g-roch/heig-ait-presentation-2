# Redis - Cheat sheet

> Date : 23.01.2022
>
> Autheurs : Cassandre Wojciechowki, Gwendoline Dössegger, Noémie Plancherel, Gaby Roch

### Présentation générale

Redis vient de `Remote Dictionary Server`. C'est un système de gestion de base de données NoSQL structuré en clé-valeur. Ce software stock les bases de données dans la RAM ce qui lui permet d'avoir de très haute performances. Il est opensource, multiplateforme et gratuit.

### Database caching

Redis utilise la stratégie de mise en cache nommée look-aside. 

Quant à la gestion du cache, elle dépend de la taille de mémoire maximales alouée au cache (`maxmemory`) ainsi que des politiques d'expulsions fournient. Ces dernières sont les actions effectuées pour déterminer quelle donnée sera supprimée pour pouvoir ajouter de nouvelles dès lors que la taille du cache atteint son maximum.

Pour cela il existe deux algorithmes qui sont les suivants :

- **LRU approximatif** : est une implémentation approximative de LRU (Least recently used). Cette solution permet d'offrir de meilleurs coût mémoire. Elle consiste donc à déterminer selon un petit échantillon de clés celle ayant le temps d'accès le plus ancien pour la supprimer. Ainsi plus la taille de l'échantillonage est grande plus les performances seront améliorées. 
- **LFU** (Least frequently used) : utilise un compteur pour définir la fréquence d'accès à l'objet. Lors de la création d'un objet, on lui assigne une valeur par défaut qu'on incrémente à chaque fois qu'on accède à la clé. Puis le compteur est décrémenté au fil du temps qui passe. Cette solution indique que plus la valeur du compteur est petite, plus la probabilité que la donnée soit expulsée du cache est grande.















