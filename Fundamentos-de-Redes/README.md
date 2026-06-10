# 🌐 Fundamentos de Redes Informáticas

> Base sólida para estudiantes que inician en redes y buscan avanzar hacia **CCNA** y automatización.

---

## 📋 Tabla de contenidos

1. [Historia de las redes](#1-historia-de-las-redes)
2. [Conceptos fundamentales](#2-conceptos-fundamentales)
3. [Tarjeta de red (NIC)](#3-tarjeta-de-red-nic)
4. [Sistemas de numeración](#4-sistemas-de-numeración)
5. [Unidades de medida](#5-unidades-de-medida)
6. [Dirección IP](#6-dirección-ip)
7. [Protocolos de red](#7-protocolos-de-red)
8. [Modelo OSI](#8-modelo-osi)
9. [Modelo TCP/IP](#9-modelo-tcpip)
10. [Comandos básicos](#10-comandos-básicos)
11. [Herramienta: PING](#11-herramienta-ping)
12. [Servidores](#12-servidores)
13. [Sistemas operativos de red](#13-sistemas-operativos-de-red)
14. [Terminología básica](#14-terminología-básica)
15. [Prácticas sugeridas](#15-prácticas-sugeridas)

---

## 1. Historia de las redes

La Internet moderna nació de proyectos militares y académicos de los años 60–70.

| Hito | Año | Descripción |
|------|-----|-------------|
| ARPANET | 1969 | Primera red de conmutación de paquetes |
| TCP/IP | 1983 | Protocolo estándar de comunicación |
| World Wide Web | 1991 | Capa de aplicación sobre Internet |
| IETF fundado | 1986 | Organismo que estandariza protocolos |

**Recursos:**
- [Computer History Museum – History of the Internet](https://www.computerhistory.org/internethistory/)
- [Internet Society – Brief History of the Internet](https://www.internetsociety.org/internet/history-internet/brief-history-internet/)

---

## 2. Conceptos fundamentales

Una **red** es un conjunto de dispositivos interconectados que comparten información y recursos.

| Tipo | Alcance | Ejemplo |
|------|---------|---------|
| **LAN** | Local (edificio, campus) | Red de una oficina |
| **WAN** | Geográfico amplio | Red entre ciudades |
| **Internet** | Global | La red de redes |

---

## 3. Tarjeta de red (NIC)

La **NIC** (*Network Interface Card*) es el componente hardware que conecta un dispositivo a la red.

- Cada NIC tiene una **dirección MAC** única grabada en fábrica (48 bits, formato hexadecimal).
- Puede ser cableada (Ethernet) o inalámbrica (Wi-Fi).

```
Formato MAC:  00:1A:2B:3C:4D:5E
              └─────┘ └──────────┘
             Fabricante  Dispositivo
```

**Recurso:** [Cloudflare – ¿Qué es una NIC?](https://www.cloudflare.com/learning/network-layer/what-is-a-network-interface-card-nic/)

---

## 4. Sistemas de numeración

Las redes utilizan tres bases numéricas:

| Base | Nombre | Dígitos | Uso principal |
|------|--------|---------|---------------|
| 10 | Decimal | 0–9 | IPv4 (legible para humanos) |
| 2 | Binario | 0–1 | Procesamiento interno del equipo |
| 16 | Hexadecimal | 0–9, A–F | IPv6, direcciones MAC |

### Ejemplo de conversión

```
Decimal → Binario
  192   =  1  1  0  0  0  0  0  0
         128 64 32 16  8  4  2  1

Hexadecimal
  A = 10   B = 11   C = 12
  D = 13   E = 14   F = 15
```

**Recurso:** [Khan Academy – Criptografía y sistemas numéricos](https://www.khanacademy.org/computing/computer-science/cryptography/)

---

## 5. Unidades de medida

### Velocidad de red

```
1 byte (B) = 8 bits (b)

Escala:
  1 Kbps  =  1,000 bps
  1 Mbps  =  1,000,000 bps
  1 Gbps  =  1,000,000,000 bps
```

> **Nota:** Los proveedores de Internet usan **Mbps** (megabits). El almacenamiento usa **MB** (megabytes). ¡No confundir!

**Recurso:** [Cloudflare – ¿Qué es el ancho de banda?](https://www.cloudflare.com/learning/network-layer/what-is-bandwidth/)

---

## 6. Dirección IP

Un **identificador único** asignado a cada dispositivo en una red.

### IPv4

- **Tamaño:** 32 bits → 4 octetos en decimal
- **Rango total:** ~4,300 millones de direcciones
- **Formato:** `192.168.1.1`

```
192   .  168  .   1   .   1
11000000.10101000.00000001.00000001
```

### IPv6

- **Tamaño:** 128 bits → 8 grupos en hexadecimal
- **Rango total:** 340 undecillones de direcciones
- **Formato:** `2001:0db8:0000:0000:0000:0000:0000:0001`
- **Comprimido:** `2001:db8::1`

| Característica | IPv4 | IPv6 |
|----------------|------|------|
| Bits | 32 | 128 |
| Base | Decimal | Hexadecimal |
| Direcciones | ~4.3 × 10⁹ | ~3.4 × 10³⁸ |
| NAT necesario | Sí | No |

**Recursos:**
- [Cloudflare – Protocolo de Internet](https://www.cloudflare.com/learning/ddos/glossary/internet-protocol/)
- [Cloudflare – ¿Qué es IPv6?](https://www.cloudflare.com/learning/ddos/glossary/what-is-ipv6/)

---

## 7. Protocolos de red

Un **protocolo** es un conjunto de reglas que define cómo se comunican los dispositivos.

| Protocolo | Capa OSI | Característica | Uso típico |
|-----------|----------|----------------|------------|
| **IP** | Red (3) | Direccionamiento y enrutamiento | Toda comunicación en Internet |
| **TCP** | Transporte (4) | Confiable, orientado a conexión | HTTP, correo, SSH |
| **UDP** | Transporte (4) | Rápido, sin garantía de entrega | Streaming, DNS, gaming |
| **ICMP** | Red (3) | Mensajes de control y error | `ping`, `traceroute` |

**Recurso:** [Cloudflare – ¿Qué es un protocolo?](https://www.cloudflare.com/learning/network-layer/what-is-a-protocol/)

---

## 8. Modelo OSI

El modelo **OSI** (*Open Systems Interconnection*) divide la comunicación en 7 capas.

```
┌───┬────────────────┬──────────────────────────────────────┐
│ 7 │  Aplicación    │ HTTP, FTP, DNS, SMTP                 │
├───┼────────────────┼──────────────────────────────────────┤
│ 6 │  Presentación  │ Cifrado, compresión, TLS/SSL         │
├───┼────────────────┼──────────────────────────────────────┤
│ 5 │  Sesión        │ Gestión de sesiones, NetBIOS         │
├───┼────────────────┼──────────────────────────────────────┤
│ 4 │  Transporte    │ TCP, UDP – segmentación de datos     │
├───┼────────────────┼──────────────────────────────────────┤
│ 3 │  Red           │ IP, ICMP – enrutamiento              │
├───┼────────────────┼──────────────────────────────────────┤
│ 2 │  Enlace        │ Ethernet, MAC – tramas               │
├───┼────────────────┼──────────────────────────────────────┤
│ 1 │  Física        │ Cables, señales eléctricas/ópticas   │
└───┴────────────────┴──────────────────────────────────────┘
         ↑ Emisor encapsula      Receptor desencapsula ↓
```

> **Mnemónico (inglés):** *All People Seem To Need Data Processing*

**Recurso:** [Cloudflare – Modelo OSI](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)

---

## 9. Modelo TCP/IP

El modelo práctico que usa Internet, con 4 capas funcionales.

```
┌──────────────────┬────────────────────────────────────┐
│   Aplicación     │ HTTP, FTP, DNS, SMTP, SSH          │
├──────────────────┼────────────────────────────────────┤
│   Transporte     │ TCP, UDP                           │
├──────────────────┼────────────────────────────────────┤
│   Internet       │ IP, ICMP, ARP                      │
├──────────────────┼────────────────────────────────────┤
│   Acceso a red   │ Ethernet, Wi-Fi, drivers           │
└──────────────────┴────────────────────────────────────┘
```

| OSI (7 capas) | TCP/IP (4 capas) |
|---------------|-----------------|
| Aplicación + Presentación + Sesión | Aplicación |
| Transporte | Transporte |
| Red | Internet |
| Enlace + Física | Acceso a red |

**Recurso:** [Cloudflare – ¿Qué es TCP/IP?](https://www.cloudflare.com/learning/network-layer/what-is-tcp-ip/)

---

## 10. Comandos básicos

### Windows

```cmd
ipconfig              # Ver configuración de red (IP, máscara, gateway)
ipconfig /all         # Información detallada incluida MAC y DNS
ipconfig /release     # Liberar IP asignada por DHCP
ipconfig /renew       # Solicitar nueva IP al servidor DHCP

ping 8.8.8.8          # Verificar conectividad
tracert 8.8.8.8       # Trazar ruta hasta el destino
nslookup google.com   # Consultar resolución DNS
netstat -an           # Ver conexiones activas y puertos
```

### Linux

```bash
ip addr               # Ver interfaces y direcciones IP
ip route              # Ver tabla de enrutamiento

ping 8.8.8.8          # Verificar conectividad
traceroute 8.8.8.8    # Trazar ruta hasta el destino
nslookup google.com   # Consultar resolución DNS
netstat -tuln         # Ver puertos en escucha
ss -tuln              # Alternativa moderna a netstat
```

**Recurso:** [Microsoft – Referencia de comandos Windows](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/windows-commands)

---

## 11. Herramienta: PING

`ping` envía mensajes **ICMP Echo Request** y espera **ICMP Echo Reply** para verificar conectividad y medir latencia.

```bash
ping 8.8.8.8
```

**Salida de ejemplo:**

```
PING 8.8.8.8: 56 bytes de datos
64 bytes de 8.8.8.8: icmp_seq=1 ttl=118 time=12.4 ms
64 bytes de 8.8.8.8: icmp_seq=2 ttl=118 time=11.8 ms

--- estadísticas de ping para 8.8.8.8 ---
2 paquetes transmitidos, 2 recibidos, 0% pérdida
tiempo promedio: 12.1 ms
```

| Campo | Significado |
|-------|-------------|
| `ttl` | Saltos máximos restantes |
| `time` | Latencia en milisegundos |
| `% pérdida` | Paquetes que no llegaron |

**Recurso:** [Cloudflare – ¿Qué es ping?](https://www.cloudflare.com/learning/network-layer/what-is-ping/)

---

## 12. Servidores

Un **servidor** es un nodo que provee servicios a otros dispositivos (clientes) en la red.

| Tipo | Función | Puerto común |
|------|---------|-------------|
| **DHCP** | Asigna direcciones IP automáticamente | UDP 67/68 |
| **DNS** | Traduce nombres de dominio a IPs | UDP/TCP 53 |
| **Web** | Sirve páginas HTTP/HTTPS | TCP 80/443 |
| **FTP** | Transferencia de archivos | TCP 21 |
| **SSH** | Acceso remoto seguro | TCP 22 |

**Recurso:** [Cloudflare – ¿Qué es un servidor?](https://www.cloudflare.com/learning/network-layer/what-is-a-server/)

---

## 13. Sistemas operativos de red

| SO | Tipo | Uso típico |
|----|------|------------|
| **Windows Server** | Propietario | Entornos corporativos, Active Directory |
| **Linux** (Ubuntu, CentOS, Debian) | Open source | Servidores web, nube, seguridad |
| **Cisco IOS** | Propietario (CLI) | Routers y switches Cisco |

**Recurso:** [Red Hat – ¿Qué es un sistema operativo?](https://www.redhat.com/en/topics/linux/what-is-an-operating-system)

---

## 14. Terminología básica

| Término | Definición |
|---------|------------|
| **IP** | Dirección lógica única de un dispositivo en la red |
| **MAC** | Dirección física única grabada en la NIC |
| **Gateway** | Dispositivo que conecta redes distintas (puerta de enlace) |
| **DNS** | Sistema que convierte nombres de dominio en direcciones IP |
| **Latencia** | Tiempo de ida y vuelta de un paquete (ms) |
| **Ancho de banda** | Capacidad máxima de transmisión de datos (Mbps/Gbps) |
| **Subred** | División lógica de una red IP |
| **DHCP** | Protocolo que asigna IPs automáticamente |

---

## 15. Prácticas sugeridas

### Práctica 1 — Identificar la IP del equipo

```bash
# Windows
ipconfig

# Linux / macOS
ip addr
```

Anota: IP privada, máscara de subred, gateway predeterminado y servidor DNS.

---

### Práctica 2 — Convertir decimal a binario

Convierte manualmente los siguientes valores y verifica con Python:

```
192 → ?     10 → ?     255 → ?
```

```python
print(bin(192))   # 0b11000000
print(bin(10))    # 0b00001010
print(bin(255))   # 0b11111111
```

---

### Práctica 3 — Usar el comando ping

```bash
ping 8.8.8.8          # Google DNS
ping 1.1.1.1          # Cloudflare DNS
ping google.com       # Prueba resolución DNS + conectividad
```

Documenta la latencia y el porcentaje de pérdida de paquetes.

---

### Práctica 4 — Analizar el modelo OSI

Identifica en qué capa OSI opera cada uno de estos protocolos:

| Protocolo | ¿En qué capa OSI opera? |
|-----------|------------------------|
| HTTP | |
| TCP | |
| IP | |
| Ethernet | |
| TLS | |

---

### Práctica 5 — Comparar IPv4 e IPv6

En tu equipo, ejecuta el comando de red y localiza:
- Tu dirección **IPv4** privada
- Tu dirección **IPv6** local (`fe80::...`)
- Diferencia en formato y cantidad de bits

---

## 📂 Estructura del repositorio

```
Fundamentos-de-Redes/
│
├── 1_Historia/
│   └── notas.md
├── 2_Conceptos/
│   └── notas.md
├── 3_Numeracion/
│   ├── notas.md
│   └── ejercicios.md
├── 4_IP/
│   ├── IPv4.md
│   └── IPv6.md
├── 5_Protocolos/
│   └── notas.md
├── 6_Modelos/
│   ├── OSI.md
│   └── TCP-IP.md
├── 7_Comandos/
│   ├── windows.md
│   └── linux.md
├── 8_Servidores/
│   └── notas.md
└── 9_Practicas/
    ├── practica_01.md
    ├── practica_02.md
    ├── practica_03.md
    ├── practica_04.md
    └── practica_05.md
```

---

## 🎯 Objetivos de aprendizaje

Al completar este repositorio, el estudiante será capaz de:

- [ ] Explicar la evolución histórica de Internet
- [ ] Diferenciar LAN, WAN e Internet
- [ ] Convertir números entre decimal, binario y hexadecimal
- [ ] Comparar IPv4 e IPv6
- [ ] Describir la función de TCP, UDP, IP e ICMP
- [ ] Identificar las capas del modelo OSI y TCP/IP
- [ ] Usar comandos básicos de diagnóstico de red
- [ ] Interpretar la salida del comando `ping`

---

## 📚 Recursos adicionales

| Recurso | Descripción |
|---------|-------------|
| [Cloudflare Learning](https://www.cloudflare.com/learning/) | Guías visuales sobre redes y seguridad |
| [Cisco NetAcad](https://www.netacad.com/) | Cursos oficiales preparatorios para CCNA |
| [Khan Academy](https://www.khanacademy.org/computing) | Fundamentos de computación y redes |
| [Professor Messer](https://www.professormesser.com/) | Videos gratuitos sobre CompTIA y redes |

---

> **Uso educativo.** Este repositorio está diseñado para estudiantes en formación. Se recomienda investigar cada concepto, realizar las prácticas documentando los resultados y avanzar en orden numérico.
