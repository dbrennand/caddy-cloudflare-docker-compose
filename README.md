# caddy-cloudflare-docker-compose
Use docker-compose to deploy Caddy v2 as a reverse proxy with a Cloudflare managed domain.

## Foreword

This repository was created in conjunction with my [blog post](https://danielbrennand.com/blog/caddy-cloudflare/) which provides prerequisites required before running the docker-compose file.

This repository shows how Caddy can be utilised as a reverse proxy for web applications. In this example, [freshrss](https://www.freshrss.org/) is used. 

## Usage

1. Copy the `ExampleCaddyfile` using the following command: `cp ExampleCaddyfile Caddyfile`.

2. Modify the the following in the `Caddyfile`:

    - **Mandatory**:

        - `email example@example.com`

        - `subdomain.example.com`
    
    - **Optional**:

        - `freshrss:80`: Modify this **only** if you decide to deploy a service with a different name and port exposed.

3. Modify the `CLOUDFLARE_API_TOKEN` environment variable in [docker-compose.yaml](docker-compose.yaml) to your Cloudflare API token.

> [!NOTE]
> **Perform steps 4 and 5 if you want to deploy freshrss.**

4. Modify the `PUID` and `PGID` environment variables for your user:

    - Use the command `id yourusername` to find out your user's PUID and PGID.

5. Modify the `TZ` environment variable (if applicable).

6. Deploy using: `docker-compose up -d`.
