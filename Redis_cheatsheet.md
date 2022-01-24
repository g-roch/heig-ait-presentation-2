# Redis - Cheat sheet

> Gwendoline Dössegger, Noémie Plancherel, Gaby Roch, Cassandre Wojciechowki, le 24.01.2022
>

Redis vient de `Remote Dictionary Server`. C'est un système de gestion de bases de données NoSQL structuré selon un principe "clé-valeur". Ce software stocke les bases de données dans la RAM ce qui lui permet d'avoir de très hautes performances. Il est opensource, multiplateforme et gratuit.

#### Database caching

Redis utilise la stratégie de mise en cache "look-aside". 

Quant à la gestion du cache, elle dépend de la taille de mémoire maximale allouée au cache (`maxmemory`) ainsi que des politiques d'expulsion fournies. Ces dernières sont les actions effectuées pour déterminer quelle donnée sera supprimée afin d'en ajouter de nouvelles dès lors que la taille du cache atteint son maximum.

Pour cela il existe deux algorithmes :

- **LRU approximatif** : est une implémentation approximative de LRU (Least Recently Used). Cette solution permet d'offrir un meilleur coût mémoire. Elle consiste donc à déterminer selon un petit échantillon de clés celles ayant le temps d'accès le plus ancien pour la supprimer. Ainsi, plus la taille de l'échantillonage est grande plus les performances seront améliorées. 
- **LFU** (Least Frequently Used) : utilise un compteur pour définir la fréquence d'accès à l'objet. Lors de la création d'un objet, on lui assigne une valeur par défaut qu'on incrémente à chaque fois qu'on accède à la clé. Puis le compteur est décrémenté au fil du temps qui passe. Cette solution indique que plus la valeur du compteur est petite, plus la probabilité que la donnée soit expulsée du cache est grande.

#### Installation sous Debian

```bash
sudo apt install redis-server
```

Une installation manuelle est également possible: [redis.io/download](https://redis.io/download)

#### Configuration

La configuration se trouve dans le fichier `/etc/redis/redis.conf` (documentation: [redis.io/topics/config](https://redis.io/topics/config))

```sh
# Créer un snapshot toutes les 5 minutes si au moins 10 entrées ont été modifiées
save 300 10
# Définir la place maximale autorisée pour la DB à 300MiB
maxmemory 300mb
# Définit la politique de suppression (lorsqu'on atteint maxmemory)
maxmemory-policy noeviction
```

#### Test

Avec la commande `redis-cli` on obtient un teminal permettant d’intéragir avec le serveur, [redis.io/commands](https://redis.io/commands)
