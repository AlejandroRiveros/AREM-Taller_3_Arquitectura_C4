# Notas de trabajo — Taller 3

**Equipo:** Adictos al Azúcar  
**Integrantes:** Juan Pablo Luna Zuleta, Alejandro Riveros y Martín Ortega  
**Cliente:** Jefatura de Cultura de Innovación y Servicio — Dirección de Desarrollo Estratégico, Universidad de La Sabana

## Actividades realizadas

1. Se revisó el caso base RedExpress para distinguir correctamente los niveles C1 y C2.
2. Se identificaron los actores que participan en la gestión y consulta del directorio de extensiones.
3. Se identificaron los sistemas y herramientas actuales que soportan el proceso.
4. Se construyó un borrador de la vista C1 para validar límites, actores y sistemas externos.
5. Se construyó un borrador de la vista C2 para representar los principales contenedores tecnológicos actuales.
6. Se contrastó el modelo con la información levantada previamente en Architecture Vision, BPMN y modelo de información.

## Decisiones de modelado

- El alcance se mantiene en el estado **AS-IS**.
- El sistema de interés se denomina **Gestión actual del directorio de extensiones**.
- Microsoft Excel y OneDrive se representan como los principales contenedores que soportan el directorio.
- El Sistema de Desarrollo Humano, Microsoft Teams y la plataforma PBX se mantienen como dependencias externas al sistema de interés.
- No se modela Power Automate como componente actual porque pertenece a una propuesta futura.
- Las relaciones se etiquetan con la interacción principal para evitar conexiones ambiguas.

## Puntos críticos identificados

- Dependencia de un archivo Excel como fuente operativa.
- Actualización y comparación manual de información.
- Ausencia de integración automática con Desarrollo Humano.
- Coordinación manual con Tecnología.
- Falta de retroalimentación automática desde el aprovisionamiento de extensiones hacia el directorio.
- Riesgo de desactualización y baja trazabilidad.

## Estado de las tareas

| Tarea | Estado |
|---|---|
| C1 borrador | Completado |
| C2 borrador | Completado |
| C1 final | Completado |
| C2 final | Completado |
| Informe | Completado |
| Referencias | Completado |
