# oatuh2-proxy-traefik-docker-compose
Docker Compose with OAuth2 Proxy and Traefik
This project demonstrates how to secure services using oauth2-proxy to add JWT headers, with services served through a Traefik proxy. It utilizes Docker Compose for orchestration. The setup includes an oauth2-proxy to authenticate users via an OIDC provider and a simple echo-server to act as a backend service.

Overview
The composition includes three main services:

Traefik: Acts as the reverse proxy and load balancer, dynamically routing requests to services.
OAuth2 Proxy: Handles authentication with an OpenID Connect (OIDC) provider and forwards authenticated requests to upstream services.
Echo Server: A simple backend service that echoes back received requests, used here to illustrate the authentication flow.
Traefik Configuration
Traefik is configured to expose its dashboard on port 8088 and to dynamically route requests to services based on path prefixes and headers. It's set up to work with Docker as the provider, reading labels from Docker containers to configure routing rules.

OAuth2 Proxy Configuration
The OAuth2 Proxy is set up to authenticate users with an OIDC provider (e.g., Keycloak). It's configured to redirect users for authentication, handle the callback, validate sessions, and forward requests with added authorization headers to the upstream echo-server.

Echo Server
A simple echo server that responds with details of the request it receives. It's protected by the OAuth2 Proxy, requiring users to be authenticated before they can access it.

Setup and Configuration
Prerequisites
Docker and Docker Compose installed on your machine.
An OIDC provider for authentication (e.g., Keycloak, Google, GitHub).
Configuration values for OAuth2 Proxy, including client ID, client secret, and the OIDC issuer URL.
Starting the Services
Clone this repository to your local machine.
Replace the placeholder values in the docker-compose.yaml with your specific OAuth2 Proxy settings, such as OAUTH2_PROXY_OIDC_ISSUER_URL, OAUTH2_PROXY_CLIENT_ID, and OAUTH2_PROXY_CLIENT_SECRET.
Run docker-compose up -d to start the services in detached mode.
Access the Traefik dashboard at http://localhost:8088/traefik to view the routing configuration.
Visit http://localhost:8088/ to access the echo server, which will redirect you to your OIDC provider for authentication.
Security Considerations
Ensure to replace OAUTH2_PROXY_COOKIE_SECRET with a strong, randomly generated value.
Set OAUTH2_PROXY_COOKIE_SECURE to true in production environments to enforce the use of HTTPS.
Be cautious with the --api.insecure flag for Traefik and consider using HTTPS with proper certificates in production.
Conclusion
This Docker Compose setup illustrates a basic configuration for securing services with OAuth2 Proxy and Traefik. It demonstrates how to authenticate users and securely forward requests to backend services.

