# LABORATORIO Y HERRAMIENTAS
## Sistema base recomendado:
- Kali Linux (VirtualBox o sistema real)
- Snapshots activos antes de cada experimento
## Herramientas clave por categoría:
### 🛠️ Análisis de tráfico y red:
- Wireshark
- tcpdump
- mitmproxy
- netcat
- Burp Suite (Community)
### 🔍 Reversing e ingeniería inversa:
- Ghidra
- x64dbg
- IDA Free
- Cheat Engine (modo offline)
### 🧪 Automatización y scripting:
- Python 3
- scapy, requests, BeautifulSoup
- C++ (g++ o Visual Studio Community)
- gcc, objdump, strings
### 🧱 Videojuegos para pruebas:
- Juegos en itch.io con licencia libre
- Juegos web (HTML5)
- Juegos Unity open source (ej: OpenSurvivor, FPS Sample)

---

 ### 📂 Formato de Estudio
 Recomiendo guardar cada módulo como un documento Markdown o Word. Dentro de cada módulo habrá:
-	🧠 Teoría explicada sin jerga innecesaria
-	🔍 Ejercicios guiados paso a paso
-	🛠️ Laboratorio específico
-	📓 Glosario técnico aplicable
-	🧩 Estudio de C++/Python

---

# Módulo 0 – Preparación del entorno de trabajo con Kali Linux

## 🎯 Objetivo

Preparar una máquina virtual Kali Linux funcional, organizada y lista para prácticas de pentesting y desarrollo seguro.

---

## 🛠️ Requisitos

- PC con al menos 8 GB de RAM y 40 GB libres
- Sistema operativo Windows
- Acceso a Internet

---

## 1. Instalación de VMware Workstation Player

1. Descargar desde: https://www.vmware.com/go/getplayer-win
2. Instalar el ejecutable `.exe` aceptando la licencia
3. Reiniciar si es necesario

---

## 2. Descarga de Kali Linux

- Ir a: https://www.kali.org/get-kali/#kali-installer-images
- Descargar la ISO de 64 bits (Installer)

---

## 3. Crear la máquina virtual en VMware

1. Abrir VMware y hacer clic en **"Create a New Virtual Machine"**
2. Seleccionar **Installer disc image file (ISO)** y cargar la ISO descargada
3. Asignar nombre: `kali_virtual`
4. Asignar recursos:
   - 2 CPU
   - 4 GB RAM
   - 20+ GB disco (Split recomendado)
5. Finalizar y **no iniciar aún**

---

## 4. Configurar la red

- Editar configuración de la VM
- Seleccionar **"NAT"** como adaptador de red
- (Opcional: cambiar a "Bridged" en ejercicios de red avanzada)

---

## 5. Instalar Kali paso a paso

1. Iniciar VM y elegir **Graphical Install**
2. Seleccionar idioma, zona horaria, teclado
3. Crear usuario y contraseña
4. Particionado: "usar disco completo con LVM"
5. Instalar GRUB en disco detectado
6. Finalizar instalación y reiniciar

---

## 6. Primer arranque

- Iniciar sesión con el usuario creado
- Verificar acceso a Internet (con `ping 8.8.8.8`)
- Abrir terminal y ejecutar:

```bash
sudo apt update && sudo apt full-upgrade -y
