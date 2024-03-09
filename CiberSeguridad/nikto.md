# Nikto
## Instalación
```bash
sudo apt update
sudo apt install nikto
nikto -h
```
## Uso
```bash
nikto -h <host>
```

- Escaneo básico de un solo host: Escanea un solo host en busca de vulnerabilidades comunes.

```bash
nikto -h <host>
```

- Escaneo de múltiples hosts desde un archivo: Escanea múltiples hosts listados en un archivo.

```bash
nikto -h <archivo>
```

- Escaneo de un solo host en un puerto específico: Escanea un solo host en un puerto específico.

```bash
nikto -h <host> -p <puerto>
```

- Escaneo sin SSL/TLS (HTTP): Escanea un host sin usar SSL/TLS.

```bash
nikto -h <host> -nossl
```

- Escaneo con autenticación básica: Realiza un escaneo utilizando autenticación HTTP básica.

```bash
nikto -h <host> -id "<usuario:contraseña>"
```

- Escaneo en modo silencioso (sin salida en pantalla): Realiza un escaneo sin mostrar la salida en pantalla.

```bash
nikto -h <host> -output <archivo_de_salida>
```

- Escaneo con autenticación por certificado SSL: Escanea un host utilizando autenticación por certificado SSL.

```bash
nikto -h <host> -cert <ruta_al_certificado>
```

- Escaneo con proxy: Escanea a través de un proxy.

```bash
nikto -h <host> -useproxy http://<ip_del_proxy>:<puerto_del_proxy>
```