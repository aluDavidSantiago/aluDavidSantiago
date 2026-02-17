Aquí la tienes, Santi:
la guía completa en formato Markdown, limpia, ordenada y lista para guardar, imprimir o usar como referencia cuando quieras.

---

# ⭐ Guía definitiva para crear un servidor Minecraft en una VM y hacerlo accesible desde Internet (con Playit)

Versión Markdown — completa, clara y lista para usar.

---

## 🟦 1. Crear la máquina virtual

Requisitos

• VirtualBox
• Lubuntu / Ubuntu Desktop / Ubuntu Server


Pasos

1. Crear una VM con:• 4 GB RAM
• 2 núcleos
• 20 GB de disco

2. Configurar red en Adaptador puente (recomendado).
3. Instalar Lubuntu/Ubuntu.
4. Actualizar el sistema:


sudo apt update && sudo apt upgrade -y


---

## 🟦 2. Instalar Java (OpenJDK)

Minecraft requiere Java 17 o superior.

sudo apt install openjdk-17-jre -y


Comprobar:

java -version


---

## 🟦 3. Crear la carpeta del servidor

mkdir ~/minecraft
cd ~/minecraft


---

## 🟦 4. Instalar Fabric Server

Descargar el instalador:

wget https://meta.fabricmc.net/v2/versions/loader/1.20.1/0.14.21/0.11.2/server/jar -O fabric-installer.jar


Instalar:

java -jar fabric-installer.jar server -downloadMinecraft


Aceptar el EULA:

nano eula.txt


Cambiar:

eula=false


por:

eula=true


Guardar y salir.

---

## 🟦 5. Arrancar el servidor por primera vez

cd ~/minecraft
java -Xmx4G -Xms2G -jar fabric-server.jar nogui


Esto generará:

• world/
• server.properties
• mods/
• ops.json
• whitelist.json


---

## 🟦 6. Obtener la IP local de la VM

ip a


Buscar una IP tipo:

192.168.1.149


---

## 🟦 7. Comprobar si estás en CG‑NAT

Entra en tu router → Estado WAN.

Si la IP WAN es algo como:

• 100.x.x.x
• 10.x.x.x
• 172.16–31.x.x
• 192.168.x.x


➡ Estás en CG‑NAT
➡ No puedes abrir puertos
➡ Necesitas Playit.

---

## 🟦 8. Instalar Playit (para saltar CG‑NAT)

wget https://github.com/playit-cloud/playit-agent/releases/latest/download/playit-linux-amd64 -O playit
chmod +x playit


Ejecutar:

./playit


Te dará un enlace tipo:

https://playit.gg/claim/XXXXXXXX


Ábrelo en tu PC real.

---

## 🟦 9. Crear el túnel en Playit

En la web de Playit:

1. Crear túnel nuevo
2. Tipo: Minecraft Java
3. Local IP: IP de tu VM192.168.1.149

4. Local Port:25565

5. Proxy Protocol: None
6. Guardar


Playit te dará una dirección tipo:

pc-hanging.gl.joinmc.link


---

## 🟦 10. Mantener todo encendido

Terminal 1 → Servidor Minecraft

cd ~/minecraft
java -Xmx4G -Xms2G -jar fabric-server.jar nogui


Terminal 2 → Playit

cd ~
./playit


---

## 🟦 11. Conectarse desde Internet

Tus amigos deben usar:

pc-hanging.gl.joinmc.link


o si Playit da puerto:

pc-hanging.gl.joinmc.link:PORT


---

## 🟦 12. Darte permisos de administrador (OP)

En la consola del servidor:

op tucat


(Usa tu nombre exacto de Minecraft)

---

## 🟦 13. Añadir mods (opcional)

Colocar los mods en:

~/minecraft/mods/


Reiniciar el servidor.

---

## 🟦 14. Resumen rápido

Paso	Acción	
1	Crear VM	
2	Instalar Java	
3	Crear carpeta del servidor	
4	Instalar Fabric	
5	Aceptar EULA	
6	Arrancar servidor	
7	Ver IP local	
8	Detectar CG‑NAT	
9	Instalar Playit	
10	Crear túnel	
11	Ejecutar servidor + Playit	
12	Conectarse desde Internet	
13	Dar OP	


---

## 🟦 15. ¿Quieres que te genere también una versión PDF o TXT para descargar?

Puedo prepararte una versión lista para guardar en tu PC o móvil.