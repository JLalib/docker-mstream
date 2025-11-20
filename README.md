# MStream - Servidor de música personal

![MStream](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/mstream-icon.png)

MStream es un servidor de música personal que te permite transmitir tu biblioteca musical desde tu propio servidor a cualquier dispositivo, en cualquier lugar. Cuenta con aplicaciones móviles para Android e iPhone, y una interfaz web ligera y rápida.

---

## 🚀 Características principales

- Streaming de música desde tu propio servidor.
- Aplicaciones móviles para Android e iOS.
- Interfaz web accesible desde cualquier navegador moderno.
- Soporte para bibliotecas musicales grandes.
- Docker-friendly y fácil de desplegar.
- Compatible con volúmenes locales y rutas personalizadas.

---

## 📦 Despliegue con Docker Compose

A continuación se muestra la configuración recomendada utilizando tu fichero `compose.yml`:

```yaml
services:

  mstream:
    image: lscr.io/linuxserver/mstream:latest
    container_name: mstream
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Madrid
    volumes:
      - ./data:/config
      - ./music:/music
    ports:
      - "8200:3000"
    restart: unless-stopped
```

---

## 📁 Estructura de volúmenes

| Ruta local        | Uso dentro del contenedor |
|------------------|---------------------------|
| `./data`         | Configuración de MStream   |
| `./music`        | Biblioteca musical completa |

---

## ▶️ Puesta en marcha

1. Guarda el archivo `compose.yml` en un directorio.
2. Asegúrate de tener carpetas `data` y `music` creadas.
3. Ejecuta:
   ```bash
   docker compose up -d
   ```
4. Abre MStream en tu navegador:
   ```
   http://TU_IP:8200
   ```

---

## 🔐 Usuarios y seguridad

MStream por defecto no requiere autenticación.  
Si deseas añadir seguridad con proxy inverso (Authelia, Nginx, Caddy, etc.), puedes configurarlo fácilmente utilizando tu proxy habitual.

---

## 🛠 Actualización

Para actualizar MStream:

```bash
docker compose pull
docker compose up -d
```

---

## 👤 Autor del despliegue

Este archivo ha sido generado automáticamente para el usuario **JLalib** siguiendo el método *README Pro GitHub*.

---

## 📘 Recursos

- Página del proyecto: https://mstream.io/
- Imagen Docker (LinuxServer): https://docs.linuxserver.io/images/docker-mstream/

