# My-Devices Docker Compose

This repo contains the docker-compose file for setting up the whole My-Devices detector and backend.

## How To

First you will need to configure your MQTT broker and topic. Copy the `mqtt.example.env` file as `mqtt.env` and change the internal settings.

Next launch the services:

```bash
docker-compose up
```

and migrate the database:

```bash
docker-compose exec backend npx sequelize-cli db:migrate
docker-compose exec backend npx sequelize-cli db:seed:all
```
