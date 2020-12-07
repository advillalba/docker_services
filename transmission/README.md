# Transmission daemon


P2P client wich provide web interface:

*Build:*

```bash
docker build --build-arg transmission_user=user --build-arg transmision_password=password . -t transmission
```

*Start service:*

```bash
docker run  --name transmission -dit -p 9091:9091 -p 51413:51413/tcp -p 51413:51413/udp -v /host/folder/:/transmission/downloads transmission
```