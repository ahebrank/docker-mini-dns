# docker-mini-dns server

This package fires up a tiny DNS server whose sole purpose
is to listen for DNS lookups and try to resolve by matching running container names.

This is specifically for docker native on OSX, where everything is a port on localhost.

## How it works:

  * DNS query for a docker image \*.docker comes in (e.g., you browse to `http://example.docker:9000`)
  * Server tests against `docker ps` to try to match the name and returns 127.0.0.1 if successful

### Setup

1. `sudo mkdir /etc/resolver`
2. `sudo touch /etc/resolver/docker && chown $USER /etc/resolver/docker`
3. `docker-mini-dns &`

You may need to edit your DNS lookup list to list `127.0.0.1` as the first server (System Preferences -> Network -> Advanced -> DNS)
