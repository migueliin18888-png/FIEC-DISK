# FIEC-Desk

Sistema web de gestión de tickets de soporte técnico y registro de equipos dañados para la Facultad de Informática, Electrónica y Comunicación (FIEC), Universidad de Panamá.

Proyecto final de **INF 224 – Metodología de Proyectos Informáticos** (noviembre de 2026).

## Problema
Las fallas de proyectores, computadoras de laboratorio, aires acondicionados, red WiFi y cuentas institucionales se reportan por canales informales. Resultado: solicitudes perdidas, sin trazabilidad ni métricas.

## Solución
FIEC-Desk registra cada equipo o servicio dañado desde el reporte hasta la reparación, lo asigna a un técnico, notifica cada cambio de estado y genera indicadores para la administración.

**Estados del ticket:** Abierto → Asignado → En reparación → Cerrado (reparado).
**Roles:** usuario, técnico, administrador.

## Metodología
Híbrida: planificación predictiva (alcance, EDT, riesgos) y ejecución con Scrum en 5 sprints de 2 semanas.

| Sprint | Semanas | Alcance |
| --- | --- | --- |
| 1 | 2-3 | Usuarios y roles |
| 2 | 4-5 | Crear y asignar tickets |
| 3 | 6-7 | Estados, historial y cierre |
| 4 | 8-9 | Notificaciones por correo |
| 5 | 10-11 | Reportes (KPIs) y base de conocimiento |

## Equipo
- Miguel Rios
- Josué Gittens
- Misael Salazar
- Emilio Vega

## Gestión del proyecto
- Jira (proyecto KAN): https://miiguelantoniio18.atlassian.net/jira/software/projects/KAN/boards/2?filter=&groupBy=none
- Canal del equipo: ENLACE_AQUI

## Flujo de trabajo con Git
1. Tomar una tarea de Jira (ej. `KAN-19`).
2. Crear rama desde `main`: `feature/KAN-19-registro-login`.
3. Commits con la clave de Jira: `KAN-19 agrega formulario de registro`.
4. Abrir un Pull Request hacia `main` y pedir revisión a un compañero.
5. Fusionar solo con al menos 1 aprobación.

## Estructura
```
fiec-desk/
├── docs/          # requisitos, diseño, plan de pruebas
├── backend/       # API y lógica (por definir en Sprint 1)
├── frontend/      # interfaz web (por definir en Sprint 1)
└── .github/       # plantilla de pull request
```

## Cómo ejecutar la aplicación
Requisitos: Python 3.10+ y Flask.

```bash
pip install -r backend/requirements.txt
python backend/app.py            # abre http://localhost:5000
python -m unittest discover -s backend   # pruebas del API
```
Cuentas de demostración (se crean al primer arranque):

| Rol | Correo | Contraseña |
| --- | --- | --- |
| Administrador | admin@fiec.up.ac.pa | admin123 |
| Técnico | tecnico@fiec.up.ac.pa | tecnico123 |
| Usuario | usuario@fiec.up.ac.pa | usuario123 |

Correo real (opcional): define `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`, `SMTP_FROM`. Sin SMTP, las notificaciones quedan en la bandeja interna de la app.

## Funcionalidad por sprint
- **Sprint 1:** registro, login por sesión, roles (usuario/técnico/administrador), el admin cambia roles.
- **Sprint 2:** crear tickets (categoría, prioridad, ubicación, equipo), búsqueda y filtros, el admin asigna técnico.
- **Sprint 3:** flujo Abierto → Asignado → En reparación → Cerrado (solo avance válido, cierre exige solución), historial y comentarios.
- **Sprint 4:** notificaciones en cada evento (bandeja interna + correo SMTP opcional).
- **Sprint 5:** reportes (tasa de resolución, tiempo medio de cierre, por estado/categoría/técnico) y base de conocimiento con búsqueda.
