# Nginx Stream Dockerfile

1. Based on <https://hub.docker.com/r/tekn0ir/nginx-stream>: Nginx compiled with --with-stream to be able to create proxies or loadbalancers for non http protocols.
2. Nginx module ngx_stream_ssl_preread_module enabled, for sni support.
