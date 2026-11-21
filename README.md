# TP 24 – Conteneurisation de Smart House

Application source du TP · [lachgar/smarthouse](https://github.com/lachgar/smarthouse).

`Smart_Home_back/` contient le backend Spring Boot (Java 17). `smartHome-front/` contient le frontend Angular, servi par Nginx. Compose démarre également MySQL et phpMyAdmin.

## Construction et démarrage

Depuis la racine, avec Docker et son extension Compose :

```sh
docker compose config --quiet
docker compose build
docker compose up -d
docker compose ps
```

| Service | Adresse de vérification |
|---|---|
| Angular | http://localhost |
| API Spring Boot | http://localhost:8085/api/controller/categorie/ |
| phpMyAdmin | http://localhost:8081 |

Pour phpMyAdmin, le compte local est `smarthouse` avec le mot de passe de démonstration `smarthouse-local`. Les mots de passe locaux peuvent être remplacés par les variables `MYSQL_PASSWORD` et `MYSQL_ROOT_PASSWORD`.

```sh
curl --fail http://localhost/
curl --fail http://localhost/api/controller/categorie/
docker compose logs backend mysql
docker compose down
```

Nginx transmet les requêtes `/api/` au backend. La base est conservée dans le volume `mysql-data` lors d'un arrêt normal.
