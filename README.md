# My-Devices Docker Compose

This repo contains the docker-compose file for setting up the whole My-Devices detector and backend.

![./img/my-devices.png]

## How To

First you will need to configure your MQTT broker and topic. Copy the `mqtt.example.env` file as `mqtt.env` and change the internal settings.

You will also need to clone all the other repos so they have the same parent directory as this repo:

```bash
git clone git@github.com:BioBoost/dhcp-request-detector.git
git clone git@github.com:BioBoost/ip-report-listener.git
git clone git@github.com:BioBoost/my-devices-backend.git
```

Next launch the services:

```bash
docker-compose up
```

and migrate the database (first time):

```bash
docker-compose exec backend npx sequelize-cli db:migrate
docker-compose exec backend npx sequelize-cli db:seed:all
```

### Reset the database

```bash
docker-compose exec backend npx sequelize-cli db:migrate:undo:all
docker-compose exec backend npx sequelize-cli db:migrate
docker-compose exec backend npx sequelize-cli db:seed:all
```
