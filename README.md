# NF16 - Projet NoSQL (Redis) 🚀

Ce projet fournit une image Redis prête à l'emploi avec Docker ⚙️

## Installation / Configuration

### Démarrage rapide des services ▶️

```bash
docker compose up -d
```

### Arrêt des services

```bash
docker compose down
```

### Accès à Redis (CLI) 🖥️

Vous pouvez exécuter des commandes classiques (GET, SET, KEYS, etc.) directement dans cette console.

```bash
docker exec -it redis redis-cli
```

## Visualisation des données

Il existe différents outils Open-source qui permettentent de visualiser, manipuler des données ainsi qu'exécuter des commandes dans un serveur Redis.

Par défaut sur ce projet, l'outil Redis Insight est configuré dans le fichier docker-compose.yaml

### Redis Insight🌐

Remplacer le contenu du fichier docker-compose.yaml par celui ci-dessous

```bash
services:
  redis:
    build:
      context: .
    container_name: redis
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    networks:
      - redisNetwork

  redis-insight:
    container_name: redis-insight
    image: redis/redisinsight:latest
    restart: always
    ports:
      - "5540:5540"
    volumes:
      - redis_insight_data:/data
    networks:
      - redisNetwork

volumes:
  redis_data:
  redis_insight_data:

networks:
  redisNetwork:
```

Ouvrir dans le navigateur : <http://localhost:5540/>

Puis cliquer sur **Add redis database** et ajouter l'URL : **redis://redis:6379** et confirmer

### Redis Commander (Web) 🌐

Remplacer le contenu du fichier docker-compose.yaml par celui ci-dessous

```bash
services:
  redis:
    build:
      context: .
    container_name: redis
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    networks:
      - redisNetwork

  redis-commander:
    container_name: redis-commander
    hostname: redis-commander
    image: ghcr.io/joeferner/redis-commander:latest
    restart: always
    environment:
    - REDIS_HOSTS=local:redis:6379
    ports:
    - "8081:8081"
    user: redis
    networks:
      - redisNetwork

volumes:
  redis_data:

networks:
  redisNetwork:
```

Ouvrir dans un navigateur : <http://localhost:8081>

## Auteur : Nathan NICART
