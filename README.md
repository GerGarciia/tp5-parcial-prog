# TP5 / 2do Parcial - Programación IV: Sistema de Gestión Comercial

**Alumno:** Germán Ariel García Núñez  
**Legajo:** 63204  
**Materia:** Programación IV - TUP (Tecnicatura Universitaria en Programación)  

---

## 📁 Estructura del Repositorio

Este repositorio contiene la solución completa al Trabajo Práctico Nº 5 / 2do Parcial, dividida en dos carpetas preparadas para su ejecución y estudio:

- **[`/tp5`](./tp5)**: Código fuente funcional y modularizado de la aplicación web comercial completa. Desarrollado con Next.js 16 (App Router), TypeScript, Tailwind CSS v4, shadcn/ui y Drizzle ORM sobre SQLite local (con soporte para Turso en producción).
- **[`/tp5-comentado`](./tp5-comentado)**: Réplica exacta del código fuente de la aplicación, pero comentada **exhaustivamente línea por línea**. Diseñada específicamente como material de estudio didáctico y guía de defensa para rendir el examen parcial.

---

## 🚀 Requisitos e Instalación

Para ejecutar la aplicación localmente:

1. Ingresar a la carpeta `tp5`:
   ```bash
   cd tp5
   ```

2. Instalar las dependencias (usando `pnpm` o `npm`):
   ```bash
   pnpm install
   ```

3. Aplicar las migraciones de base de datos SQLite:
   ```bash
   pnpm run db:migrar
   ```

4. Poblar la base de datos con los datos iniciales de prueba (usuarios, categorías, 30 productos, 10 clientes y 54 facturas con movimientos reales de stock y cuenta corriente):
   ```bash
   pnpm run db:semilla
   ```

5. Iniciar el servidor de desarrollo:
   ```bash
   pnpm dev
   ```
   Abrir [http://localhost:3000](http://localhost:3000) en el navegador.

---

## 🔐 Usuarios de Prueba para el Parcial

| Rol | Usuario / Email | Contraseña | Capacidades |
|---|---|---|---|
| **Administrador** | `admin` / `admin@comercio.local` | `admin123` | Control total, anulación de facturas, gestión de usuarios, reseteo de claves |
| **Vendedor** | `vendedor` / `vendedor@comercio.local` | `vendedor123` | Emisión de facturas A y B, control de stock, gestión de clientes |
| **Cajero** | `cajero` / `cajero@comercio.local` | `cajero123` | Cobro de cuentas corrientes, emisión de recibos oficiales, consulta de saldos |

---

## 🧪 Verificaciones y Pruebas

Dentro de `/tp5`, se incluyen scripts automatizados de validación:
- `npx tsx basedatos/verificar.ts`: Comprueba la integridad referencial y las invariantes de stock y saldos (debe dar 0 diferencias).
- `npx tsx basedatos/prueba-exhaustiva.ts`: Ejecuta la suite de pruebas funcionales verificando autenticación, autorización por roles (403), duplicados (409), límite de crédito (422), cobros excedentes (422), atomicidad de ventas, anulación con reposición de stock e invariantes contables.
