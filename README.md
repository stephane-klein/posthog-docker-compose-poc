# Selfhost PostHog powered by docker compose

```sh
$ docker compose build
$ docker compose pull
$ docker compose run web ./bin/migrate
$ docker compose up -d worker plugins web
```

Go to `http://localhost:8000`
