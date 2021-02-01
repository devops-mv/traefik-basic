Create a new network with the name `proxy`

Add this to the bottom of all `docker-compose.yml` files

```
networks:
  default:
    external: true
    name: proxy
```

On your project's `docker-compose.yml` file add the following labels variable
```
    labels:
      - "traefik.enable=true"
      - "traefik.frontend.rule=Host:${VIRTUAL_HOST}"
      - "traefik.docker.network=proxy"
      - "traefik.port=${VIRTUAL_PORT}"
```

By default the proxy works on port `80`. To specify a different port add `traefik.port` label along with the `traefik.frontend.rule` label