# NF16 - Projet NoSQL (Redis) 🚀

Ce projet fournit une image Redis prête à l'emploi avec Docker, accompagnée d'une interface web (Redis Commander). ⚙️

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

## Redis Commander (Web) 🌐

Ouvrir dans un navigateur :
<http://localhost:8081>

Redis Commander permet de visualiser les clés, éditer les valeurs et exécuter des commandes depuis une interface graphique.

## Auteur : Nathan NICART

## Redis Insight (Web) 🌐

Redis Insight propose une interface plus complète, pour utiliser **insight** à la place de **commander**

docker-compose.yml :

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

Puis cliquer sur "Add redis database" et ajouter l'URL : **redis://redis:6379** et confirmer
