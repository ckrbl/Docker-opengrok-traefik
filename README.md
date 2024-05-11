# Docker Opengrok Trafik
Exemplar Opengrok, and Homer, behind a Traefik reverse-proxy.
Configured using docker-compose.yml file.
Extensible to host other services.

## Features
 * HTTP Compression so Opengrok may load large files quickly
 * HTTPS with HTTP-> HTTPS Redirect

## External Ports
 * 80/http - Simple redirect to 443 with https scheme
 * 443/https - Main
 * 8080/http - Traefik dashboard, disable in static.toml

## Application Routing
 * `/` - Homer dashboard
 * `/opengrok` - Opengrok search page

# Setup Instructions

 1. Update traefik/dynamic.toml with the machine's hostname
 1. Input a certificate and private key into traefik/pki at the path indicated in dynamic.toml
