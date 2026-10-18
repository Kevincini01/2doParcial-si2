# FashionStore

### Plataforma Inteligente de Comercio Electrónico con Recomendación Personalizada y Experiencia de Compra Virtual

**Proyecto académico — Sistemas de Información II · Grupo 49 · Semestre II/2026**  
**Universidad Autónoma Gabriel René Moreno (UAGRM)** · Facultad de Ingeniería en Ciencias de la Computación y Telecomunicaciones (FICCT)

## Descripción

**FashionStore** es una propuesta de plataforma de comercio electrónico **B2C** orientada a la comercialización de prendas de vestir por medio de aplicaciones web y móvil. Su objetivo es facilitar la consulta de productos, la compra, las reservas y la gestión comercial, incorporando experiencias inteligentes como recomendaciones personalizadas y un vestidor virtual.

El proyecto se desarrolla con el enfoque del **Proceso Unificado de Desarrollo de Software (PUDS)** y utiliza modelos **UML** para documentar requisitos, análisis, diseño, implementación y pruebas.

> **Estado del repositorio:** el código compartido aún no corresponde totalmente con el alcance documentado de FashionStore. La aplicación móvil contiene pantallas y servicios de una tienda de moda; el backend y frontend incluidos provienen de un sistema inmobiliario denominado **Raíces**. Por tanto, **no se declara una integración funcional completa** entre las tres aplicaciones.

## Alcance funcional previsto

- **Usuarios y seguridad:** registro, autenticación, perfiles, roles y permisos.
- **Catálogo:** productos de moda, categorías, tallas, colores, precios e imágenes.
- **Inventario:** control de stock por sucursal y movimientos de existencias.
- **Operaciones comerciales:** carrito, compras, pedidos, reservas y ventas presenciales.
- **Administración:** facturación, reportes, indicadores y trazabilidad.
- **Inteligencia artificial:** recomendaciones personalizadas, asistente de compra y vestidor virtual (*Virtual Try-On*).

Estas funciones representan el **alcance establecido en la documentación** y no todas están implementadas o integradas en la versión disponible. Las operaciones de pago y entrega están planteadas para demostración académica, sin requerir pasarelas o servicios logísticos reales.

## Tecnologías

| Componente | Tecnologías identificadas |
| --- | --- |
| API del ZIP | Python, FastAPI, SQLAlchemy, PostgreSQL, JWT |
| Aplicación web del ZIP | Angular 22, TypeScript, HTML y CSS |
| Aplicación móvil | Flutter, Dart, paquetes HTTP y gestión de estado con Provider |
| Documentación y diseño | PUDS, UML y arquitectura C4 |
| Control de versiones | Git y GitHub |

## Estructura del repositorio

```text
2doParcial-si2/
├── README.md
├── .gitignore
└── proyecto/
    ├── SI2-Backend-main/       # API Python/FastAPI (actualmente Raíces)
    ├── SI2-Frontend-main/      # Aplicación Angular (actualmente Raíces)
    └── Si2Exm-Movil-main/      # Aplicación Flutter FashionStore
```

## Requisitos para desarrollo local

- Git
- Python y `pip` para el backend
- PostgreSQL para la base de datos utilizada por el backend incluido
- Node.js y npm para el frontend Angular
- Flutter SDK y un dispositivo o emulador compatible para la aplicación móvil

> Las versiones concretas de Node.js, Python y Flutter deben comprobarse según el entorno utilizado. La aplicación móvil declara **Dart SDK `^3.13.1`** en su `pubspec.yaml`.

## Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/Kevincini01/2doParcial-si2.git
cd 2doParcial-si2
```

### 2. Backend — FastAPI

Desde PowerShell (Windows):

```powershell
cd proyecto/SI2-Backend-main
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn main:app --reload
```

El backend utiliza PostgreSQL y tiene actualmente la conexión configurada en `database/database.py` para una base local denominada `raices_db`. Antes de iniciarlo, debe existir la base de datos y configurarse una conexión válida para el entorno; **no se recomienda conservar contraseñas directamente en el código**.

- API local: `http://127.0.0.1:8000`
- Documentación interactiva: `http://127.0.0.1:8000/docs`
- Verificación: `http://127.0.0.1:8000/api/health`

**Advertencia:** esta API está identificada como *Raíces* y no contiene necesariamente las rutas `/api/v1/products/`, `/api/v1/ai/tryon` y otras requeridas por la app móvil de FashionStore.

### 3. Frontend web — Angular

En otra terminal, desde la raíz del repositorio:

```powershell
cd proyecto/SI2-Frontend-main
npm install
npm start
```

Abrir `http://localhost:4200` si Angular inicia con su configuración habitual. Esta interfaz web también corresponde actualmente al sistema *Raíces*.

### 4. Aplicación móvil — Flutter

En otra terminal, desde la raíz del repositorio:

```powershell
cd proyecto/Si2Exm-Movil-main
flutter pub get
flutter devices
flutter run
```

La app móvil utiliza en `lib/core/services/api_service.dart` la URL `http://127.0.0.1:8000/api/v1`. Es necesario conectar una **API compatible con FashionStore**, configurar su dirección y comprobar la conectividad desde el emulador o dispositivo. En Android físico, el código contempla utilizar `adb reverse tcp:8000 tcp:8000` cuando el teléfono está conectado mediante ADB.

## Estado de implementación

| Componente | Situación identificada al revisar el ZIP |
| --- | --- |
| Backend | Código FastAPI disponible, pero del sistema inmobiliario Raíces |
| Frontend web | Proyecto Angular disponible, pero con pantallas de Raíces |
| Aplicación móvil | Estructura y pantallas para catálogo, carrito, reservas, perfil, compras, chat y vestidor virtual |
| IA / Virtual Try-On | Servicio cliente definido en Flutter; necesita una API que implemente el endpoint correspondiente |
| Integración general | Pendiente de verificar y adaptar al dominio FashionStore |

La presencia de pantallas o servicios no implica por sí sola que sus funcionalidades hayan superado pruebas integrales.

## Metodología y documentación

La documentación académica del Grupo 49 aborda el perfil del proyecto, fundamentación teórica del comercio electrónico, pasarelas de pago, delivery, PUDS y UML, además de la captura de requisitos con **27 casos de uso**, análisis, diseño arquitectónico, implementación y pruebas.

## Equipo académico

- **Kevin Ariel Aranibar Pérez**
- **Raúl Rodrigo Justiniano Coimbra**

**Materia:** Sistemas de Información II  
**Grupo:** 5
**Docente:** MSc. Ing. Angélica Garzón Cuéllar  
**Gestión:** II/2026

## Uso y finalidad

Repositorio destinado a fines **académicos y de demostración**. Las integraciones financieras y logísticas descritas en la propuesta no deben confundirse con servicios reales ya disponibles en el código.
