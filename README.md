<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:071925,50:0099A8,100:00E5FF&height=180&section=header&text=Enterprise%20Systems%20Portfolio&fontSize=38&fontColor=ffffff&fontAlignY=38&desc=Full-Stack%20%7C%20Mobile%20Apps%20%7C%20ERP%20Integration%20%7C%20Business%20Intelligence&descSize=16&descAlignY=62&animation=fadeIn" width="100%" />
</div>

# Portafolio de Ingeniería y Sistemas en Producción

Documentación de arquitectura, flujos operativos y decisiones técnicas de los sistemas desarrollados, migrados y mantenidos en **Aquasistemas** como **Junior Programmer & Systems Developer**.

> **Nota sobre confidencialidad:** Para resguardar la seguridad y propiedad intelectual de la organización, este repositorio documenta arquitecturas, flujos de datos, patrones de diseño y soluciones técnicas sin exponer código fuente propietario, credenciales, direcciones de red internas ni datos sensibles.

---

## 🗺️ Mapa de Arquitectura General

```mermaid
flowchart TB
    subgraph Clientes["Canales de Usuario"]
        Web["Portal Web AquaVerso<br/>(Angular 22 + SSR)"]
        Mobile["Apps Móviles (Flutter & Dart)<br/>Aqua Servicios (Play Store) · Ferrecity"]
        BIView["Consumo Analítico<br/>(Power BI & MS Report Builder)"]
    end

    subgraph Infra["Servicios Backend y Cloud"]
        Backend["APIs REST en Node.js / Express<br/>(Instancias AWS EC2 Ubuntu + PM2)"]
        Cache["Redis<br/>(Sesiones y Tokens 2FA TTL)"]
        Storage["AWS S3<br/>(Imágenes y Catálogos PDF)"]
        CloudSvcs["Firebase (FCM) · Google Maps APIs<br/>SMTP (Nodemailer) · SOAP (Banguat)"]
    end

    subgraph Datos["Motores de Datos y ERP"]
        PG[("PostgreSQL<br/>(Vistas Analíticas y ERP Odoo)")]
        SQL[("Microsoft SQL Server<br/>(Operación, SAE y Marcaciones)")]
        ERP["Odoo ERP<br/>(REST / XML-RPC y Reportes QWeb)"]
    end

    Web -->|"HTTPS / JSON"| Backend
    Mobile -->|"HTTPS / JSON / JWT"| Backend
    Mobile -.->|"Push & Auditoría GPS"| CloudSvcs
    Backend --> Cache
    Backend --> Storage
    Backend --> CloudSvcs
    Backend --> PG
    Backend --> SQL
    Backend --> ERP
    PG --> BIView
    SQL --> BIView

```

---

## 📚 Índice de Casos de Estudio

| # | Documento | Sistema / Dominio | Stack Clave | Enfoque Técnico |
| --- | --- | --- | --- | --- |
| 01 | [`docs/01-aquaverso-platform.md`](https://www.google.com/search?q=docs/01-aquaverso-platform.md) | **Plataforma Web AquaVerso** | `Angular 22 (SSR)` `Node.js` `Express` `SQL Server` `PostgreSQL` `Redis` `AWS S3` | Migración web, autenticación 2FA con Redis, inventarios multi-almacén, Fundeleasing, cheques, RRHH y backend multi-BD. |
| 02 | [`docs/02-mobile-aws-ecosystem.md`](https://www.google.com/search?q=docs/02-mobile-aws-ecosystem.md) | **Ecosistema Móvil & AWS** | `Flutter` `Dart` `Google Play` `Google Maps APIs` `FCM` `AWS EC2` `PM2` `Odoo` | App `Aqua Servicios` en Play Store (escudo anti-Fake GPS, 9 formularios, firmas), app B2B `Ferrecity` y servidores AWS. |
| 03 | [`docs/03-powerbi-telemetry-bi.md`](https://www.google.com/search?q=docs/03-powerbi-telemetry-bi.md) | **Business Intelligence (Power BI)** | `Power BI` `DAX` `PostgreSQL` `SQL Server` | Vistas de telemetría GPS (`America/Guatemala`), holgura de agenda, control de manufactura y cortes temporales DAX. |
| 04 | [`docs/04-ssrs-report-builder.md`](https://www.google.com/search?q=docs/04-ssrs-report-builder.md) | **Reportería Paginada (Report Builder)** | `MS Report Builder` `T-SQL` `SQL Server` `Window Functions` `Odoo XML` | Auditoría biométrica de asistencia/retardos, optimización de datasets de crédito/facturación y reportes ERP. |

---

## 🛠️ Stack Consolidado del Entorno Productivo

* **Frontend & Móvil:** Angular 22 (SSR), TypeScript, Flutter, Dart, Provider, HTML5, SCSS/CSS3, JavaScript.
* **Backend & Integraciones:** Node.js, Express, Odoo ERP (REST / XML-RPC), Redis, AWS S3, Firebase Cloud Messaging (FCM), Google Maps APIs, Nodemailer, SOAP.
* **Bases de Datos & BI:** PostgreSQL, Microsoft SQL Server, Power BI Desktop / Report Server, DAX, Microsoft Report Builder (SSRS).
* **Infraestructura & Herramientas:** AWS EC2 (Ubuntu Linux), administración remota SSH / PuTTY, PM2, Google Play Console, Git.

```
