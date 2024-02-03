# OAuth2 Proxy with Traefik in Docker Compose

## Overview

This project demonstrates how to secure your services using OAuth2 Proxy and Traefik as a reverse proxy within a Docker Compose environment. It illustrates adding JWT (JSON Web Tokens) headers to facilitate easier authentication scenarios for your applications. This setup is particularly useful for protecting internal services and implementing a secure authentication flow with OpenID Connect (OIDC) providers like Keycloak.

## Why Use This Setup?

Using OAuth2 Proxy with Traefik enables fine-grained access control to your services, ensuring only authenticated users can access them. This approach simplifies the authentication process, as Traefik handles the routing and OAuth2 Proxy manages authentication, adding JWT headers to requests for downstream services.

## Prerequisites

- Docker and Docker Compose installed on your system
- An OIDC provider (like Keycloak) configured for your domain

## Configuration

Before running the `docker-compose.yaml`, ensure you update the environment variables for the `oauth2-proxy` service:

- `OAUTH2_PROXY_OIDC_ISSUER_URL`: The URL of your OIDC issuer.
- `OAUTH2_PROXY_CLIENT_ID` and `OAUTH2_PROXY_CLIENT_SECRET`: The client ID and secret obtained from your OIDC provider.
- `OAUTH2_PROXY_COOKIE_SECRET`: A random string used to encrypt the cookie.

## Running the Project

1. Clone the repository:
git clone https://github.com/kingjuk/oatuh2-proxy-traefik-docker-compose.git
2. Navigate to the project directory:
cd oatuh2-proxy-traefik-docker-compose
3. Start the services:
docker-compose up -d

## Accessing the Dashboard

The Traefik dashboard is available at `http://localhost:8088/traefik` after starting the services. Ensure you are authenticated through the OAuth2 Proxy to access it.

## Testing the Setup
Opening a browser to `http://localhost:8080` should redirect you to the OAuth2 Proxy login page. After authenticating, you should be able to access the echo service and see the JWT headers added by the OAuth2 Proxy.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any improvements or bug fixes.

## License

[MIT License](LICENSE)





