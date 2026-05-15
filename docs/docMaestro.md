# Dinamizer Pro — Documento Maestro de Producto

> **Estado:** Discovery / Pre-desarrollo  
> **Última actualización:** Mayo 2026  
> **Versión:** 0.1 — Borrador inicial  
> **Nota:** El nombre "Dinamizer Pro" es provisional y puede cambiar antes del lanzamiento.

---

## Índice

1. [Visión del producto](#1-visión-del-producto)
2. [Negocios piloto](#2-negocios-piloto)
3. [Alcance global del sistema](#3-alcance-global-del-sistema)
4. [Módulos por tipo de negocio](#4-módulos-por-tipo-de-negocio)
5. [Roles y permisos](#5-roles-y-permisos)
6. [Roadmap de MVPs](#6-roadmap-de-mvps)
7. [Flujos de usuario](#7-flujos-de-usuario)
8. [Arquitectura técnica](#8-arquitectura-técnica)
9. [Base de datos — ERD](#9-base-de-datos--erd)
10. [Infraestructura](#10-infraestructura)
11. [Modelo de negocio y precios](#11-modelo-de-negocio-y-precios)
12. [Decisiones técnicas registradas](#12-decisiones-técnicas-registradas)
13. [Pendientes y preguntas abiertas](#13-pendientes-y-preguntas-abiertas)

---

## 1. Visión del producto

**Dinamizer Pro** es una plataforma SaaS multi-tenant, modular y adaptable para pequeños negocios en Monterrey, Nuevo León — con proyección de expansión nacional.

### Propuesta de valor

Una agenda inteligente y planificador todo-en-uno que se adapta a cualquier tipo de negocio: salones de belleza, barberías, restaurantes, talleres mecánicos, vendedores mayoristas, salones de eventos, y más. La IA elimina el mayor problema de los micro-negocios: la falta de tiempo para registrar y organizar información del negocio.

### Diferenciadores clave

| Diferenciador | Descripción |
|---|---|
| **Configuración zero-effort** | El dueño describe su negocio en un chat y la IA crea automáticamente catálogos, empleados y módulos |
| **Registro por voz** | Dicta una venta o gasto y la IA lo registra automáticamente (Whisper API) |
| **Planificador inteligente** | Detecta horas vacías, sugiere tareas y campañas de reactivación de clientes |
| **Inventario predictivo** | Anticipa cuándo un cliente mayorista necesitará reorden |
| **Adaptable a cualquier negocio** | Módulos activables según el giro: servicios, productos, eventos, mayoreo |
| **Nativo para México** | WhatsApp, SPEI, efectivo, lenguaje natural en español |

### Lo que el sistema NO hace (fuera de alcance)

- ❌ No es un sistema de punto de venta (POS) con hardware físico
- ❌ No emite facturas fiscales (CFDI) — versión inicial
- ❌ No tiene contabilidad ni integración con SAT — versión inicial
- ❌ No maneja nómina ni IMSS
- ❌ No es una tienda en línea ni e-commerce
- ❌ No tiene app móvil nativa en MVP 1 (se agrega en Fase 2 con MAUI)
- ❌ No reemplaza un sistema bancario ni integración directa con bancos

---

## 2. Negocios piloto

Beta cerrada con los siguientes 5 tipos de negocio en Monterrey, N.L.:

| # | Tipo de negocio | Necesidades principales | Módulos críticos |
|---|---|---|---|
| 1 | **Salón de uñas / belleza** | Agenda por empleada, citas con duración, inventario de productos, comisiones | Agenda, Caja, Inventario, Clientes, Empleados |
| 2 | **Restaurante** | Registro de ventas por turno, control de inventario de insumos, empleados por turno | Caja, Inventario, Empleados, Clientes |
| 3 | **Vendedor de aceite comestible** | Clientes mayoristas, pedidos recurrentes, inventario de galones, cuentas por cobrar | Clientes, Inventario, Tareas, Caja |
| 4 | **Barbería** | Agenda por barbero, servicios, comisiones, fidelización de clientes | Agenda, Caja, Clientes, Empleados |
| 5 | **Salón de fiestas infantiles** | Reservas de fecha completa, paquetes, anticipos, checklist de evento | Agenda, Caja, Clientes |

---

## 3. Alcance global del sistema

### Módulos definidos

| Módulo | Descripción | MVP |
|---|---|---|
| **Auth & Multi-tenant** | Login, roles, aislamiento de datos por negocio, suscripciones | MVP 1 |
| **Agenda & Citas** | Reservas, horarios por empleado, recordatorios | MVP 1 |
| **Tareas** | Asignación a empleados, seguimiento, estados | MVP 1 |
| **Caja & Ventas** | Registro de ventas, métodos de pago (efectivo / SPEI / tarjeta), corte de caja | MVP 1 |
| **Inventario básico** | Productos y servicios, stock, alertas de stock mínimo, movimientos | MVP 1 |
| **Clientes (CRM simple)** | Ficha, historial de visitas y compras, etiquetas, alerta de inactividad | MVP 1 |
| **Empleados** | Perfiles, permisos, horarios, comisiones | MVP 1 |
| **Configuración por IA** | Onboarding por chat en lenguaje natural, zero-effort setup | MVP 2 |
| **Registro por voz** | Whisper API → extrae datos de un audio y registra venta o gasto | MVP 2 |
| **Planificador IA** | Sugerencias de tareas en horas libres, alertas de clientes inactivos | MVP 2 |
| **Dashboard & Reportes** | Métricas ejecutivas del negocio, exportación PDF / Excel | MVP 2 |
| **WhatsApp Business** | Citas por mensaje, recordatorios automáticos, campañas dirigidas | MVP 3 |
| **Inventario predictivo** | Detección de patrones de consumo, alertas de reorden automáticas | MVP 3 |
| **Pedidos recurrentes** | Para mayoristas: pedidos programados, historial por cliente | MVP 3 |
| **App móvil (MAUI)** | Android e iOS nativo, mismo backend | Fase 4 |

---

## 4. Módulos por tipo de negocio

Matriz de cobertura por piloto:

| Módulo | Salón uñas | Restaurante | Vendedor aceite | Barbería | Salón fiestas |
|---|:---:|:---:|:---:|:---:|:---:|
| Auth & Roles | ✅ | ✅ | ✅ | ✅ | ✅ |
| Agenda & Citas | ✅ | ⚠️ | ❌ | ✅ | ✅ |
| Tareas | ✅ | ✅ | ✅ | ✅ | ✅ |
| Caja & Ventas | ✅ | ✅ | ✅ | ✅ | ✅ |
| Inventario | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Clientes CRM | ✅ | ✅ | ✅ | ✅ | ✅ |
| Empleados | ✅ | ✅ | ⚠️ | ✅ | ⚠️ |
| Comisiones | ✅ | ⚠️ | ❌ | ✅ | ❌ |
| Pedidos recurrentes | ❌ | ❌ | ✅ | ❌ | ❌ |
| Reservas de evento completo | ❌ | ❌ | ❌ | ❌ | ✅ |
| Paquetes con anticipo | ❌ | ❌ | ❌ | ❌ | ✅ |
| Registro por voz | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| WhatsApp | ✅ | ✅ | ✅ | ✅ | ✅ |
| Inventario predictivo | ⚠️ | ✅ | ✅ | ⚠️ | ❌ |

> ✅ Crítico &nbsp;&nbsp; ⚠️ Opcional / parcial &nbsp;&nbsp; ❌ No aplica

---

## 5. Roles y permisos

### Roles del sistema

| Rol | Descripción | Alcance |
|---|---|---|
| **Super Admin** | Equipo interno de Dinamizer Pro | Panel de administración global — todos los tenants |
| **Dueño** | Propietario o administrador del negocio | Acceso completo a su tenant |
| **Empleado** | Staff operativo del negocio | Vista limitada: su agenda, sus tareas, registrar ventas |

### Permisos por módulo

| Módulo | Dueño | Empleado |
|---|---|---|
| Dashboard y métricas | ✅ Completo | ❌ Sin acceso |
| Agenda — ver todas | ✅ | ❌ Solo la suya |
| Agenda — crear / editar | ✅ | ⚠️ Solo las suyas |
| Registrar venta | ✅ | ✅ |
| Ver historial de caja | ✅ | ❌ |
| Hacer corte de caja | ✅ | ⚠️ Si el dueño lo permite |
| Inventario — CRUD | ✅ | ⚠️ Solo consulta |
| Clientes — CRUD | ✅ | ⚠️ Ver y agregar notas |
| Gestión de empleados | ✅ | ❌ |
| Reportes | ✅ | ❌ |
| Configuración del negocio | ✅ | ❌ |
| Tareas — ver las suyas | ✅ | ✅ |
| Tareas — asignar a otros | ✅ | ❌ |

---

## 6. Roadmap de MVPs

### MVP 1 — Core operativo (meses 1–4)
> **Objetivo:** Que el dueño deje de usar su libreta o WhatsApp para operar.

**Incluye:**
- Auth multi-tenant: registro del negocio, login, roles Dueño / Empleado
- Agenda y citas: crear, editar, cancelar, vista semanal por empleado
- Gestión de empleados: perfiles, horarios, comisiones
- Clientes: ficha básica, historial de citas y compras
- Caja y ventas: registrar venta, método de pago, corte de caja diario
- Inventario básico: catálogo de productos y servicios, stock, alertas
- Tareas: crear, asignar a empleado, marcar completada

**Negocios que cubre el MVP 1:**
- Salón de uñas ✅ completo
- Barbería ✅ completo
- Salón de fiestas ⚠️ parcial (sin paquetes ni anticipos)
- Restaurante ⚠️ parcial (sin control de mesas)
- Vendedor de aceite ⚠️ parcial (sin pedidos recurrentes)

---

### MVP 2 — Inteligencia y visibilidad (meses 5–8)
> **Objetivo:** Que el sistema piense por el dueño y le dé información clara de su negocio.

**Incluye:**
- Onboarding por IA: el dueño describe su negocio en chat y la IA lo configura
- Registro por voz: dicta una venta y la IA la registra (Whisper API)
- Planificador inteligente: sugerencias de tareas y alertas de clientes inactivos
- Dashboard ejecutivo: métricas del día, semana y mes
- Reportes exportables: PDF y Excel para el contador

---

### MVP 3 — Automatización y canales (meses 9–12)
> **Objetivo:** Que el sistema trabaje solo en tareas repetitivas y llegue a los clientes.

**Incluye:**
- WhatsApp Business API: recordatorios de cita, campañas de reactivación
- Inventario predictivo: alertas de reorden basadas en patrones de consumo
- Pedidos recurrentes para mayoristas
- Paquetes con anticipos para salones de eventos

---

### Fase 4 — App móvil (mes 13+)
> **Objetivo:** Acceso nativo desde Android e iOS para empleados en campo.

**Incluye:**
- App .NET MAUI: mismo backend, misma lógica
- Vista de empleado optimizada para celular
- Notificaciones push de citas y tareas

---

## 7. Flujos de usuario

> 🔲 **Pendiente** — Se generarán en la Fase 2 del discovery.

Flujos a documentar:
- [ ] Onboarding: registro de negocio y primer login
- [ ] Crear y gestionar una cita (vista dueño y vista empleado)
- [ ] Registrar una venta y hacer corte de caja
- [ ] Dar de alta un producto en inventario y registrar entrada
- [ ] Registrar un cliente nuevo y consultar su historial
- [ ] Asignar una tarea a un empleado y marcarla completada
- [ ] Flujo especial: reserva de evento en salón de fiestas (con anticipo)
- [ ] Flujo especial: pedido recurrente del vendedor de aceite

---

## 8. Arquitectura técnica

### Stack definido

| Capa | Tecnología | Razón |
|---|---|---|
| **Backend** | ASP.NET Core 9 Web API | Ecosistema .NET, familiaridad del equipo |
| **ORM** | Entity Framework Core 9 | Migraciones, multi-tenant con filtros globales |
| **Base de datos** | PostgreSQL 16 | Open source, mejor para SaaS multi-tenant |
| **Frontend** | Blazor Server | C# en todo el stack, sin JavaScript adicional |
| **Componentes UI** | MudBlazor | Gratis, open source, calendario y grids incluidos |
| **IA / LLM** | Semantic Kernel + OpenAI API | Integración oficial Microsoft para .NET |
| **Transcripción de voz** | Whisper API (OpenAI) | Mejor reconocimiento en español |
| **Autenticación** | ASP.NET Identity + JWT | Estándar .NET, probado |
| **IDE** | JetBrains Rider | Soporte completo .NET + PostgreSQL integrado |
| **Control de versiones** | Git + GitHub | Estándar, CI/CD con GitHub Actions |

### Estrategia multi-tenant

- **Enfoque:** Row-level — campo `tenant_id` en cada tabla
- **Implementación:** Filtro global en EF Core por `DbContext`
- **Middleware:** `TenantMiddleware` extrae el tenant del JWT en cada request
- **Aislamiento:** Ninguna query puede acceder a datos de otro tenant

---

## 9. Base de datos — ERD

### Tablas del núcleo (MVP 1)

**Identidad y negocio:**
- `Tenant` — negocio registrado en la plataforma
- `Usuario` — cuenta de acceso (dueño o empleado)
- `Empleado` — perfil operativo, especialidades, comisión
- `HorarioEmpleado` — disponibilidad por día de la semana

**Módulo operativo:**
- `Cliente` — ficha del cliente del negocio
- `Catalogo` — productos y servicios (campo `tipo` los distingue)
- `Cita` — reserva agendada: cliente + empleado + servicio + fecha
- `Venta` — registro de cobro (puede venir de una cita o ser directa)
- `VentaDetalle` — líneas de la venta (producto/servicio + cantidad + precio)
- `CorteCaja` — snapshot diario de cierre de caja
- `MovimientoInventario` — bitácora de entradas y salidas de stock
- `Tarea` — tarea asignada a un empleado con estado y fecha límite

> 📎 Diagrama visual ERD generado en sesión de discovery — ver diagramas en `/docs/diagrams/`

---

## 10. Infraestructura

### Fase 1 — Desarrollo local
- PostgreSQL en Docker Desktop (`localhost:5432`)
- API en Rider (`localhost:5001`)
- Blazor en Rider (`localhost:5000`)
- Costo: **$0/mes**

### Fase 2 — Beta con pilotos
- Hosting: **Railway** (API + PostgreSQL managed)
- Dominio: por definir (`.mx`)
- Email transaccional: **Resend** (free tier)
- Costo estimado: **~$5–10 USD/mes**

### Fase 3 — Producción
- Hosting: **Railway Pro** o **Azure App Service B1**
- PostgreSQL: managed en Railway o Azure Database for PostgreSQL
- IA: OpenAI API (pay-per-use, ~$15–25 USD/mes para 100 negocios activos)
- Costo estimado: **~$50–80 USD/mes**

---

## 11. Modelo de negocio y precios

> 🔲 **Pendiente de definir** — Propuesta inicial a validar con pilotos.

### Modelo: SaaS por suscripción mensual

| Plan | Precio estimado | Incluye |
|---|---|---|
| **Básico** | $299 MXN/mes | 1 dueño + hasta 3 empleados, módulos core |
| **Profesional** | $599 MXN/mes | Hasta 10 empleados + IA + reportes |
| **Negocio** | $999 MXN/mes | Empleados ilimitados + WhatsApp + soporte prioritario |

> ⚠️ Precios a validar con los pilotos antes de lanzamiento público.

---

## 12. Decisiones técnicas registradas

| Fecha | Decisión | Razón | Alternativa descartada |
|---|---|---|---|
| May 2026 | PostgreSQL sobre SQL Server | Open source, gratis en producción, mejor para multi-tenant | SQL Server (costo de licencia) |
| May 2026 | Blazor Server sobre React | Un solo lenguaje C#, familiaridad del dev, sin JS adicional | React (requiere aprender JS/TS) |
| May 2026 | Railway para beta | Deploy en minutos desde GitHub, $5/mes, Postgres incluido | Azure (más fricción inicial) |
| May 2026 | MudBlazor como librería UI | Gratis, open source, tiene calendario y grids listos | Telerik UI ($999/año, innecesario en MVP) |
| May 2026 | Row-level multi-tenant (TenantId) | Más simple de implementar y mantener, suficiente para el MVP | Base de datos separada por tenant (over-engineering en esta etapa) |
| May 2026 | IA en MVP 2, no MVP 1 | Validar primero el core sin complejidad de IA, reducir tiempo de lanzamiento | IA desde el inicio (riesgo de retrasar MVP indefinidamente) |

---

## 13. Pendientes y preguntas abiertas

### Producto
- [ ] ¿El nombre "Dinamizer Pro" es definitivo? — *provisional, puede cambiar*
- [ ] ¿Cómo maneja el restaurante las mesas o comandas? ¿Entra en MVP 1 o MVP 2?
- [ ] ¿El salón de fiestas necesita un módulo de checklist de evento específico?
- [ ] ¿El vendedor de aceite necesita cuentas por cobrar / crédito a clientes?
- [ ] ¿Se necesita un rol intermedio entre Dueño y Empleado (ej. Encargado / Gerente)?

### Técnico
- [ ] Definir estructura de carpetas del proyecto en Rider
- [ ] Generar flujos de usuario por módulo (Fase 2 del discovery)
- [ ] Generar wireframes de pantallas principales (Fase 3 del discovery)
- [ ] Definir convención de nombres de endpoints de la API REST
- [ ] Decidir si el email transaccional usa Resend o SendGrid

### Negocio
- [ ] Validar precios de suscripción con los 5 pilotos
- [ ] Definir condiciones del período de prueba gratuito
- [ ] Redactar aviso de privacidad (obligatorio antes de recibir datos)
- [ ] Definir nombre de dominio definitivo

---

*Documento vivo — se actualiza con cada sesión de trabajo.*  
*Generado con apoyo de Claude (Anthropic) durante sesión de discovery.*
