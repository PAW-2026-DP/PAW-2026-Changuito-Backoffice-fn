# Changuito — Backoffice

Frontend de gestión de la aplicación web **Changuito**, orientado a los supermercados adheridos y a los administradores de la plataforma.

## Enlaces del proyecto

- **Documentación:** https://paw-2026-changuito-docs.vercel.app/
- **Wireframes (Figma):** https://www.figma.com/design/ZeL7MqjxUKq20VJu6yR9Us/Changuito
- **Repositorios del TP Integrador:**
  - [Frontend Cliente](https://github.com/PAW-2026-DP/PAW-2026-Changuito-fn)
  - [Frontend Backoffice](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Backoffice-fn) (este repositorio)
  - [Frontend Riders](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Riders-fn)
  - [Backend](https://github.com/PAW-2026-DP/PAW-2026-Changuito-bn)
  - [Documentación](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Docs)

## Objetivo del backoffice

Interfaz web para los roles de gestión de Changuito.

### Panel de supermercado

- Alta, baja y modificación de productos del catálogo.
- Actualización de precios y stock por sucursal.
- Carga de catálogo por planilla.
- Bandeja de pedidos entrantes, con cambio de estado de preparación (confirmado, en preparación, listo para retiro).

### Panel de administrador

- Gestión de usuarios y roles.
- Alta de comercios y sucursales.
- Definición de zonas de cobertura y costos de envío.

> **El Backoffice es una aplicación separada por usabilidad y despliegue, no por seguridad.** Consume la misma API que el resto de los frontends, y toda la autorización se resuelve en el servidor.

## Stack

- HTML5
- CSS3
- JavaScript sin frameworks ni librerías de terceros
- Comunicación con el backend mediante solicitudes HTTP sobre `fetch`

---

## Requisitos

| Componente | Notas |
| :---- | :---- |
| Navegador moderno | Chrome, Firefox, Edge o Safari en versión actual |
| Un servidor HTTP estático | Necesario para desarrollo: abrir los archivos con `file://` rompe las peticiones a la API por política de origen |
| [Backend de Changuito](https://github.com/PAW-2026-DP/PAW-2026-Changuito-bn) | Corriendo y accesible, con al menos un usuario de rol supermercado y uno de rol administrador cargados |

No hay dependencias que instalar ni proceso de build: son archivos estáticos.

---

## Puesta en marcha local

1. **Clonar el repositorio**

   ```bash
   git clone https://github.com/PAW-2026-DP/PAW-2026-Changuito-Backoffice-fn.git
   cd PAW-2026-Changuito-Backoffice-fn
   ```

2. **Configurar la URL de la API** apuntando al backend local (por ejemplo `http://localhost:8000/api`).

3. **Levantar un servidor estático**

   ```bash
   python -m http.server 5501
   ```

   O con la extensión **Live Server** de Visual Studio Code.

4. **Abrir** http://localhost:5501 e ingresar con un usuario de rol supermercado o administrador.

> **Nota:** cada frontend usa un puerto distinto en desarrollo (Cliente 5500, Backoffice 5501, Riders 5502) para poder tenerlos levantados en paralelo. Los tres orígenes deben estar habilitados en la configuración de CORS del backend.

> **TODO equipo:** el archivo de configuración del endpoint todavía no existe. Se define junto con la implementación, en la tercera entrega.

---

## Deployment

Sitio estático: puede publicarse en cualquier hosting de archivos estáticos o en el mismo servidor Apache que sirve la API, bajo su propio subdominio.

**Pasos:**

1. Configurar la URL de la API apuntando al backend de producción (por HTTPS).
2. Subir el contenido del repositorio al directorio público del hosting.
3. Verificar que el origen del sitio esté habilitado en la política de CORS del backend.
4. Servir todo el sitio por HTTPS.

**Checklist previo a publicar:**

- [ ] La URL de la API apunta a producción, no a `localhost`
- [ ] El sitio se sirve por HTTPS
- [ ] El origen está habilitado en el CORS del backend
- [ ] No quedaron usuarios, credenciales ni datos de prueba en el código

---

## Estructura del repositorio

```text
PAW-2026-Changuito-Backoffice-fn/
├── assets/      Imágenes, íconos y recursos visuales
├── components/  Elementos reutilizables de interfaz
├── pages/       Pantallas de gestión (dashboard, ABM, bandeja de pedidos)
├── services/    Comunicación con el backend
├── styles/      Hojas de estilo, variables y reglas responsive
└── utils/       Funciones auxiliares
```

## Estado actual

Wireframes definidos (login, dashboard, usuarios y roles, alta y listado de comercios, sucursales, zonas de cobertura, ABM de catálogo, carga de catálogo, bandeja y detalle de pedido). La maquetación HTML/CSS y la lógica en JavaScript corresponden a la tercera entrega.
