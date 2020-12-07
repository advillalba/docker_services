# Samba server


Share local data with Windows computers on same network.

*Build:*

```bash
docker build --build-arg samba_user=user --build-arg samba_password=password . -t samba
```

*Start service:*

```bash
docker run --name samba -dit -p 137:137/udp -p 138:138/udp -p 139:139 -p 445:445 -v /host/folder:/shared samba
```