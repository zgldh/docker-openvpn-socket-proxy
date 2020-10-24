# docker-openvpn-socket-proxy

A docker solution to export a openvpn client as a socket5 proxy.

## Made with:
- https://github.com/dperson/openvpn-client (The openvpn launcher code)
- https://github.com/kizzx2/docker-openvpn-client-socks (The sockd launcher code)

## Usage:
```
git pull
cd docker-openvpn-socket-proxy
cp your-openvpn-cfg.ovpn ./vpn/vpn.ovpn

# If your openvpn server requires user/pass auth
cp .env.example .env
# And setup your openvpn username and password.
vim .env

# Else pleaes remove the VPN_AUTH line from the docker-compose.yml

# Finally up the container
docker-compose up
```

After the container is running, you can use any proxy tools (Mellow, SwitchyOmega and so on) to connect to the socket server `socks://127.0.0.1:1080`
