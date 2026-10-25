# DVWA — CTF / Curso de Pentesting

> **Damn Vulnerable Web Application** lista para levantar en un comando.  
> Diseñada para practicar las vulnerabilidades más comunes de OWASP en un entorno controlado.

---

## Requisitos

| Herramienta | Versión mínima |
|---|---|
| Docker | 20.x+ |
| Docker Compose | v2.x+ |

---

## Levantar el entorno

```bash
# 1. Clonar el repositorio
git clone https://github.com/AlecksRguez/DVWA.git
cd DVWA

# 2. (Opcional) Copiar variables de entorno
cp .env.example .env

# 3. Levantar servicios
docker compose up -d

# 4. Esperar ~30 segundos y abrir en el navegador
open http://localhost
```

### Primer acceso — crear la base de datos

1. Abrir **http://localhost**
2. Hacer clic en **"Create / Reset Database"**
3. Serás redirigido al login automáticamente

---

## Credenciales por defecto

| Servicio | Usuario | Contraseña |
|---|---|---|
| DVWA (web) | `admin` | `password` |
| DVWA (web) | `gordonb` | `abc123` |
| DVWA (web) | `1337` | `charley` |
| DVWA (web) | `pablo` | `letmein` |
| DVWA (web) | `smithy` | `password` |
| MySQL root | `root` | `dvwa` |
| MySQL app | `dvwa` | `p@ssw0rd` |

---

## Niveles de seguridad

Desde **DVWA Security** (menú lateral) puedes cambiar el nivel en tiempo real:

| Nivel | Descripción |
|---|---|
| **Low** | Sin protección — ideal para aprender la técnica básica |
| **Medium** | Mitigaciones parciales — bypass intermedio |
| **High** | Protecciones fuertes — requiere técnicas avanzadas |
| **Impossible** | Código seguro de referencia |

El nivel inicial predeterminado es **Low**.

---

## Módulos de vulnerabilidades

| # | Módulo | Tipo de vulnerabilidad |
|---|---|---|
| 1 | Brute Force | Fuerza bruta HTTP |
| 2 | Command Injection | OS Command Injection |
| 3 | CSRF | Cross-Site Request Forgery |
| 4 | File Inclusion | LFI / RFI |
| 5 | File Upload | Unrestricted File Upload |
| 6 | Insecure CAPTCHA | Logic flaws |
| 7 | SQL Injection | SQLi clásico |
| 8 | SQL Injection (Blind) | Blind SQLi |
| 9 | Weak Session IDs | Gestión insegura de sesiones |
| 10 | XSS (DOM) | Cross-Site Scripting DOM |
| 11 | XSS (Reflected) | Cross-Site Scripting Reflejado |
| 12 | XSS (Stored) | Cross-Site Scripting Persistente |
| 13 | CSP Bypass | Content Security Policy bypass |
| 14 | JavaScript | Client-side logic flaws |
| 15 | Open HTTP Redirect | Redirección abierta |

---

## Comandos útiles

```bash
# Ver logs en tiempo real
docker compose logs -f

# Detener y eliminar contenedores
docker compose down

# Detener y eliminar contenedores + base de datos (reset completo)
docker compose down -v

# Reiniciar solo DVWA (sin tocar la BD)
docker compose restart dvwa

# Abrir shell dentro del contenedor
docker exec -it dvwa bash

# Conectar a MySQL
docker exec -it dvwa_db mysql -u dvwa -pp@ssw0rd dvwa
```

---

## Estructura del repositorio

```
DVWA/
├── docker-compose.yml   # Definición de servicios
├── .env.example         # Plantilla de variables de entorno
└── README.md            # Esta guía
```

---

## Advertencia legal

> Este entorno es **intencionalmente vulnerable**.  
> Úsalo **únicamente** en redes privadas o máquinas locales.  
> **Nunca** lo expongas a Internet sin protección adicional (VPN, firewall, etc.).

---

## Recursos adicionales

- [Documentación oficial DVWA](https://github.com/digininja/DVWA)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
