FROM alpine

# Install openvpn
RUN apk --no-cache --no-progress upgrade && \
  apk --no-cache --no-progress add bash curl ip6tables iptables openvpn dante-server bash openresolv openrc \
  shadow tini tzdata && \
  addgroup -S vpn && \
  rm -rf /tmp/*

COPY openvpn.sh /usr/bin/
COPY sockd.sh /usr/local/bin/
COPY sockd.conf /etc/

HEALTHCHECK --interval=60s --timeout=15s --start-period=120s \
  CMD curl -LSs 'https://api.ipify.org'

VOLUME ["/vpn"]

ENTRYPOINT ["/sbin/tini", "--", "/usr/bin/openvpn.sh"]