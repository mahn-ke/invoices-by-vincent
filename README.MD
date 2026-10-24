# invoices.by.vincent.mahn.ke

Hosts the container serving [invoices.by.vincent.mahn.ke](https://invoices.by.vincent.mahn.ke).

## Container configuration

The shared deployment workflow builds `docker-bake.hcl` and publishes
`ghcr.io/mahn-ke/invoices-by-vincent/nginx:latest` before running Compose.
The image contains only the repository's NGINX configuration (the upstream
default site is removed). Application files, storage, and database data remain
in named volumes; secrets remain runtime environment variables.
Deploy once to recreate NGINX without its checkout bind mount. For local builds,
run `docker buildx bake --file docker-bake.hcl --load`.