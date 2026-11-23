<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:071925,50:0099A8,100:00E5FF&height=180&section=header&text=Enterprise%20Systems%20Portfolio&fontSize=38&fontColor=ffffff&fontAlignY=38&desc=Full-Stack%20%7C%20Mobile%20Apps%20%7C%20ERP%20Integration%20%7C%20Business%20Intelligence&descSize=16&descAlignY=62&animation=fadeIn" width="100%" />
</div>

# Portafolio de Ingeniería y Sistemas en Producción

Documentación de arquitectura, flujos operativos y decisiones técnicas de los sistemas desarrollados y mantenidos en **Aquasistemas** como **Junior Programmer & Systems Developer**.

> **Nota sobre confidencialidad:** Para resguardar la seguridad y propiedad intelectual de la organización, este repositorio documenta arquitecturas, flujos de datos, patrones de diseño y soluciones técnicas sin exponer código fuente propietario, credenciales, direcciones de red internas ni datos sensibles.

---

## 🗺️ Mapa de Arquitectura General

```mermaid
flowchart TB
    subgraph Clientes["Canales de Usuario"]
        Web["Portal Web AquaVerso<br/>(Angular 22 + SSR)"]
        Mobile["Apps Móviles<br/>(Flutter & Dart)"]
        BIView["Consumo Analítico<br/>(Power BI & Report Builder)"]
    end

    subgraph Infra["Servicios y Servidores"]
        Backend["APIs REST en Node.js / Express<br/>(Servidores Linux / AWS + PM2)"]
        Cache["Redis<br/>(Sesiones y Tokens TTL)"]
        Storage["AWS S3<br/>(Imágenes y Catálogos PDF)"]
        Mail["SMTP / Nodemailer<br/>(Notificaciones y Tokens)"]
        SOAP["Servicio SOAP<br/>(Tipo de Cambio)"]
    end

    subgraph Datos["Motores de Datos y ERP"]
        PG[("PostgreSQL<br/>(Vistas, Funciones y ERP)")]
        SQL[("Microsoft SQL Server<br/>(Operación, SAE y Marcaciones)")]
        ERP["Odoo ERP<br/>(XML-RPC y Módulos)"]
    end

    Web -->|"HTTPS / JSON"| Backend
    Mobile -->|"HTTPS / XML-RPC"| Backend
    Backend --> Cache
    Backend --> Storage
    Backend --> Mail
    Backend --> SOAP
    Backend --> PG
    Backend --> SQL
    Backend --> ERP
    PG --> BIView
    SQL --> BIView
