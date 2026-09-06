# Registro de Trabajo en Clase - Taller 3

## Fecha de la sesión

29 de agosto 2026

## Integrantes presentes

- Juan Pablo Luna Zuleta
- Alejandro Riveros
- Martín Ortega

## Actividades realizadas en clase

Durante la sesión se trabajó el caso base **RedExpress** siguiendo la metodología de cuatro pasos indicada en la guía del Taller 3.

### Vista C1 — Contexto

1. Se identificaron los actores directos: **Usuario Final, Mensajero y Operador Logístico**.
2. Se definió **Plataforma RedExpress** como único sistema en alcance.
3. Se identificaron como sistemas externos la **API de Notificaciones** y el **Proveedor de Geolocalización**.
4. Se trazaron y etiquetaron todas las relaciones indicando la acción o información intercambiada.
5. Se validó que no hubiera actores o sistemas externos sin conexión y que no aparecieran contenedores internos en el C1.

### Vista C2 — Contenedores

1. Se descompuso Plataforma RedExpress en:
   - App Móvil
   - Portal Web Operadores
   - Módulo de Gestión de Paquetes
   - Motor de Rutas
   - Seguimiento GPS
   - Sistema de Alertas
2. Se agregó la infraestructura de soporte:
   - Balanceador de Carga
   - Base de Datos Distribuida
3. Se conservaron los actores y sistemas externos identificados en C1.
4. Se trazaron las relaciones entre componentes.
5. Se etiquetaron los mecanismos de comunicación relevantes: **HTTPS/JSON, HTTPS, SQL, REST y Push/WebSocket**.
6. Se validó el modelo con la checklist de autoevaluación de la guía.

## Decisiones de modelado

- Se utilizó **draw.io / diagrams.net**.
- Se respetó la notación visual indicada por la guía:
  - Actor: óvalo azul.
  - Sistema en alcance: rectángulo azul oscuro.
  - Sistema externo: rectángulo gris con doble borde.
  - Contenedor: rectángulo azul claro.
  - Infraestructura: gris.
- En C1 se mantuvo Plataforma RedExpress como una sola caja.
- En C2 se realizó el “zoom” de esa caja, manteniendo visibles los actores y sistemas externos del C1.
- Todas las relaciones fueron etiquetadas.
- No se inventaron tecnologías concretas no definidas por el caso; cuando no existe una tecnología específica, se indica el **tipo de contenedor** (aplicación móvil, aplicación web o servicio backend).

## Boceto inicial del modelo

Los archivos digitales elaborados durante el ejercicio son:

- `c1-contexto-borrador.drawio`
- `c2-contenedores-borrador.drawio`

Estos archivos constituyen el boceto/modelo de trabajo de RedExpress para la Parte 1 del taller.

## Validación con checklist

### C1

- [x] El sistema en alcance aparece como una única caja.
- [x] Los tres actores relevantes están identificados.
- [x] Los dos sistemas externos están diferenciados visualmente.
- [x] Cada relación tiene una etiqueta con verbo e intercambio.
- [x] Ningún actor o sistema queda sin conexión.

### C2

- [x] Cada contenedor tiene indicado su tipo.
- [x] Los contenedores tienen responsabilidades separadas.
- [x] Los actores y sistemas externos del C1 siguen visibles.
- [x] Las relaciones indican protocolo o mecanismo de comunicación cuando aplica.
- [x] Se representan el balanceador de carga y la base de datos distribuida como infraestructura de soporte.

## Tareas definidas para complementar el taller

| Tarea asignada | Responsable | Estado |
|---|---|---|
| Adaptar C1 al cliente real | Equipo | Pendiente / entrega |
| Adaptar C2 al cliente real | Equipo | Pendiente / entrega |
| Redactar informe técnico | Equipo | Pendiente / entrega |
| Investigación y referencias | Equipo | Pendiente / entrega |

---

