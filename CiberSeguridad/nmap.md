# NMap
## Instalación
```bash
sudo apt update
sudo apt install nmap
```
## Uso
- Escaneo de puertos TCP en un solo host:

```bash
nmap <ip_del_servidor>
```

- Escaneo de puertos TCP en un rango de direcciones IP:


```bash
nmap <rango_de_ips>

```

- Escaneo de puertos TCP en un rango de puertos específico:


```bash
nmap -p <rango_de_puertos> <ip_del_servidor>
```

- Escaneo de puertos TCP con detección de servicios y versiones:


```bash
nmap -sV <ip_del_servidor>
```

- Escaneo de puertos TCP con detección de sistemas operativos:


```bash
nmap -O <ip_del_servidor>
```

- Escaneo de puertos TCP con detección de servicios, versiones y sistemas operativos:


```bash
nmap -A <ip_del_servidor>
```

- Escaneo rápido de puertos TCP comunes:


```bash
nmap -F <ip_del_servidor>
```

- Escaneo de puertos TCP en modo sigiloso (stealth):


```bash
nmap -sS <ip_del_servidor>
```