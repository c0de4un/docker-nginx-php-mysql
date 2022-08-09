# Commands
Build and start containers
```sh
    $docker-compose up --build -d
    $docker-compose run -d -p 80:80 www
```
Stop contaienrs and remove images
```sh
    $docker-compose down
```

## App Sources
All sources are in `www/html`, and they are mounted via `volume` feature, so no restart of service is required

## Database
phpMyAdmin is available at `localhost:8080`
Credentials are set in `db/Dockerfile`, host is `db`, which is set in `docker-compose.yml`
Persistent storage is at `db/data`