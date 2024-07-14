```markdown
# Comandos de Netdiscover y Nmap

## Listar versión y dispositivos
- Listar versión de GCC: 
  ```bash
  gcc -v
  ```
- Listar dispositivos en la PC:
  ```bash
  lsusb
  ```

## Netdiscover

### Descripción
Netdiscover es una herramienta de descubrimiento de redes.

### Comandos básicos
- Ayuda:
  ```bash
  netdiscover -help
  ```

### Descubrir dispositivos
- Ejecutar netdiscover para descubrir dispositivos en un rango de IP:
  ```bash
  sudo netdiscover -r 192.168.1.1/24
  ```
  - `-r` : Define el rango de IP
  - `192.168.1.1/24` : Especifica el rango de IP a escanear

- Utilizando una interfaz específica:
  ```bash
  netdiscover -i eth0 -r 192.168.43.0/24
  ```
  - `-i` : Define la interfaz de red (ej. eth0)

## Nmap

### Descripción
Nmap es un programa de código abierto que sirve para explorar redes, realizar análisis de seguridad y búsqueda de puertos.

### Comandos básicos
- Ayuda:
  ```bash
  nmap --help
  ```
- Descubrimiento de dispositivos (Ping scan):
  ```bash
  sudo nmap -sn <target_IP>
  ```
- Escaneo de puertos (Mapeo de IP):
  ```bash
  sudo nmap <target_IP>
  ```

### Escanear un puerto específico
- Ejemplo para puertos 80, 135, 2000, 18080 en un rango específico:
  ```bash
  sudo nmap -p 80,135,2000,18080 192.168.1.13
  sudo nmap 192.168.1.1-223.*
  ```

### Ver sistema operativo
- Detectar el sistema operativo de un objetivo:
  ```bash
  sudo nmap -O <target_IP>
  ```

### Evasión de Firewall (Stealth Scans)
- `-sX` (Stealth Xmas Tree Scan): Envía paquetes con los flags FIN, URG, y PUSH activados.
  ```bash
  sudo nmap -sX <target_IP>
  ```
- `-sN` (Stealth Null Scan): Envía paquetes sin flags activados.
  ```bash
  sudo nmap -sN <target_IP>
  ```
- `-sF` (Stealth FIN Scan): Usa paquetes con el flag FIN activado.
  ```bash
  sudo nmap -sF <target_IP>
  ```
- `-P0` : No envía ping al objetivo antes del escaneo para evitar bloqueo del firewall.
  ```bash
  sudo nmap -P0 <target_IP>
  ```

### Evasión de Firewall (II)
- Scan Fragment Packets (`-f`): Envía paquetes pequeños de 8 bytes.
  ```bash
  sudo nmap -f <target_IP>
  ```
- Scan MTU (`--mtu`): Especifica un tamaño de MTU.
  ```bash
  sudo nmap --mtu 16 <target_IP>
  ```
- Scan Decoy (`-D`): Usa hosts señuelo para anonimizar el escaneo.
  ```bash
  sudo nmap -D RND:10 <target_IP>
  ```

### Exportar resultados de escaneos
- Exportar en formato `.txt` o `.xml`:
  ```bash
  sudo nmap -sV 192.168.1.1 -oN Desktop/test.txt
  sudo nmap -sV 192.168.1.1 -oX Desktop/test.xml
  ```

### Escanear los primeros 1000 puertos
- Escaneo rápido de los primeros 1000 puertos:
  ```bash
  sudo nmap -p 1-1000 <ip_address>
  ```

### Escaneo de puertos TCP y UDP
- Escaneo de puertos TCP:
  ```bash
  sudo nmap -sT <target_IP>
  ```
- Escaneo de puertos UDP:
  ```bash
  sudo nmap -sU <target_IP>
  ```

## ARP Spoofing
- Instalación de arpspoof:
  ```bash
  sudo apt install dsniff
  ```
- Ejecutar arpspoof:
  ```bash
  sudo arpspoof -i wlan0 -t 192.168.1.9 192.168.1.1
  ```
