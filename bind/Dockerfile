FROM internetsystemsconsortium/bind9:9.16
LABEL maintainer="Attila Oláh (atl@google.com)"

COPY ["named.conf.local", "/etc/bind/named.conf.local"]
COPY ["named.conf.options", "/etc/bind/named.conf.options"]
COPY ["galaxite.net.zone", "/var/cache/bind/galaxite.net.zone"]
