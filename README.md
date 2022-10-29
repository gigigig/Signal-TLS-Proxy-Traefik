# Signal TLS Proxy

forked from [Signal-TLS-Proxy-Traefik](https://github.com/signalapp/Signal-TLS-Proxy)

If you have [traefik](https://github.com/traefik/traefik) up and running and use [labels](https://doc.traefik.io/traefik/providers/docker/#routing-configuration-with-labels) for dynamic configuration.

A tcp-router and tcp-service `signal-tls-proxy` are created for TLS-Termination. 
nginx-terminate container is removed and nginx-relay nginx.conf is moved to docker build.
Assuming traefik listens on `443/tcp` on your host, has a certresolver named `letsencrypt` and has an entrypoint named `websecure`.

1. Clone this repository
1. Replace `SIGNAL_DOMAIN` in `.env` with your domain
1. Run `docker compose -f "docker-compose.yml" up -d --build`

Your proxy is now running and should be served by traefik! You can share this with the URL `https://signal.tube/#<SIGNAL_DOMAIN>`