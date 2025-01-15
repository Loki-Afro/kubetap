FROM docker.io/mitmproxy/mitmproxy:9.0.1

# HACK: the security context of the injected pod could be run as any user, therefore
# all users must be able to write to the directory.
RUN chmod -R 777 /home/mitmproxy/.mitmproxy/

# Hijack the mitmproxy entrypoint (docker-entrypoint.sh) so that
# configuration can be built from within the container using the
# kubetap binary.

COPY kubetap-entrypoint.sh /usr/local/bin/
ENTRYPOINT ["kubetap-entrypoint.sh"]