# NF16 - Projet NOSQL (Redis) 🚀

Ce projet fournit une image Redis prête à l'emploi avec Docker, accompagnée d'une interface web (Redis Commander). ⚙️

## Installation / Configuration

### Démarrage rapide ▶️

```bash
docker compose up -d
```

### Arrêt 

```bash
docker compose down
```

###  Accès à Redis (CLI) 🖥️

Vous pouvez exécuter des commandes classiques (GET, SET, KEYS, etc.) directement dans cette console.

```bash
docker exec -it redis redis-cli
```

## Redis Commander (Web) 🌐

Ouvrir dans un navigateur :
<http://localhost:8081>

Redis Commander permet de visualiser les clés, éditer les valeurs et exécuter des commandes depuis une interface graphique.

## Auteur : Nathan NICART