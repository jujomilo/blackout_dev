# PRÁCTICA FINAL – MÓDULO 2
### Laboratorio de enumeración sobre entorno virtual seguro
### 🎯 Objetivo general

Aplicar todo lo aprendido en el Módulo 2 en un ejercicio práctico completo:

Preparar entorno

- Organizar estructura de trabajo

- Comprobar red

- Escanear puertos

- Enumerar servicios

- Exportar y documentar resultados

# Estructura del entorno
Entorno virtual:

- Kali Linux (máquina atacante)

- Metasploitable 2 (máquina víctima)

- Red Host-only (VMnet1)

## 📂 Paso 1 – Crear la estructura de carpetas
En tu directorio de trabajo, ejecuta:
```
mkdir -p pentesting/modulo_2/practica_final/{capturas,exportados,informes}
cd pentesting/modulo_2/practica_final
```
- capturas/: para imágenes y pantallazos

- exportados/: salidas de comandos (nmap, ss, netstat)

- informes/: tu .md y documentación escrita

✅ ¿Qué hace -p?
🟢 Esto:

- crea la ruta completa aunque no exista nada antes

- no lanza error si ya existe (es idempotente)

- Es seguro, limpio y esencial cuando haces estructuras completas




📌 Esto reproduce buenas prácticas de organización profesional

### Paso 2 – Verificar la conectividad
En Metasploitable:
```
ifconfig
```
Anota la IP asignada (ejemplo: 192.168.106.129).

### En Kali:
```
ip a
ping 192.168.106.129
```
✅ Si responde → red funcionando.

### Paso 3 – Ver puertos abiertos localmente
En Kali:
```
ss -tuln > exportados/puertos_tcp_udp_kali.txt
```
En Metasploitable:
```
netstat -tuln > exportados/puertos_tcp_udp_metasploitable.txt
```
📁 Archiva ambas salidas y añade una descripción en tu informe.

### Paso 4 – Escaneo básico de puertos desde Kali
```
nmap -sS 192.168.106.129 -oN exportados/escaneo_tcp.txt
```
```
sudo nmap -sU 192.168.106.129 -oN exportados/escaneo_udp.txt
```
Analiza:

- ¿Qué puertos aparecen abiertos?

- ¿Qué servicios parecen estar corriendo?

### Paso 5 – Escaneo de enumeración
```
nmap -A 192.168.106.129 -oN exportados/enumeracion_avanzada.txt
```
Incluye:

- Detección de OS

- Versiones de servicios

- Scripts NSE ejecutados

- Información útil para explotación futura

### Paso 6 – Informe final .md
En informes/practica_final.md incluye:
### 1. Resumen
- Fecha

- Objetivo de la práctica

- Entorno utilizado (VMware + configuración de red)

### 2. IP de cada máquina
### 3. Salidas clave
- Incluye fragmentos relevantes de ss, netstat, nmap

### 4. Análisis
- Servicios interesantes detectados

- Posibles vectores de ataque

- Observaciones técnicas

### 5. Capturas
- Agrega capturas en capturas/ y enlaza:
```
![nmap_tcp](../capturas/nmap_tcp.png)
```

### 📌 Extras opcionales
### ➕ Bonus: transferir archivo de Metasploitable a Kali
Desde Kali:
```
scp msfadmin@192.168.106.129:/home/msfadmin/servicios_tcp_metasploitable.txt ./exportados/
```
Contraseña: msfadmin

### ✅ Resultado esperado
Un informe completo en Markdown que incluya:

- Evidencia de escaneo

- Capturas organizadas

- Comentarios de análisis real

- Exportaciones reproducibles

Este informe será la base de futuros informes de reconocimiento más complejos.

## Resumen
Aunque el análisis externo desde Kali es prioritario, se realizaron también comandos desde la máquina víctima (Metasploitable) para:

- Comparar lo que se ve desde fuera (Kali) con lo que realmente corre internamente.
- Practicar comandos de enumeración local desde el punto de vista de un atacante post-explotación.
- Aprender a identificar servicios expuestos vs. internos y cómo influye la red en ello.
