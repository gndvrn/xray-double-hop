# How to setup Cloudflare WARP

## Generate WARP Profile

```bash
# Download wgcf
curl -L https://github.com/ViRb3/wgcf/releases/download/v2.2.30/wgcf_2.2.30_linux_amd64 -o /usr/local/bin/wgcf
chmod +x /usr/local/bin/wgcf

# Register and generate profile
wgcf register
wgcf generate
cat wgcf-profile.conf
```

## Xray WireGuard Outbound

```json
{
  "tag": "wireguard",
  "protocol": "wireguard",
  "settings": {
    "secretKey": "private-key",
    "address": [
      "172.16.0.2/32",
      "2606:4700:110:xxxx:xxxx:xxxx:xxxx:xxxx/128"
    ],
    "peers": [
      {
        "publicKey": "public-key",
        "allowedIPs": ["0.0.0.0/0", "::/0"],
        "endpoint": "162.159.192.1:2408" // one-time dns resolve to avoid dns dependency
      }
    ],
    "mtu": 1280
  }
}
```