# Wazuh + Suricata Lab en VMware

## Resumen ejecutivo
Este proyecto documenta la implementación de un laboratorio de ciberseguridad basado en VMware, orientado a centralizar eventos de seguridad con Wazuh e integrar detección de eventos de red mediante Suricata. El entorno fue compuesto por tres máquinas virtuales: un servidor Wazuh, un host Ubuntu con Suricata y Wazuh Agent, y un endpoint Windows 10 con Wazuh Agent. Como resultado, se logró registrar ambos agentes, visualizar eventos de seguridad en el dashboard de Wazuh y confirmar la ingestión de alertas generadas por Suricata.

## Objetivo
Implementar un laboratorio funcional que permita:

- Centralizar eventos de seguridad en Wazuh
- Integrar Suricata como IDS en Ubuntu
- Registrar un agente Linux y un agente Windows
- Validar la recepción de eventos y alertas desde el dashboard
- Documentar técnicamente el procedimiento y los resultados

## Tecnologías utilizadas
- VMware Workstation
- Wazuh
- Suricata
- Ubuntu Server
- Windows 10
- Git
- GitHub

## Versiones utilizadas
- VMware Workstation
- Wazuh Server: 4.14.4
- Wazuh Agent Ubuntu: 4.14.4
- Wazuh Agent Windows: 4.14.4
- Suricata: 8.0.4
- Ubuntu Server: 24.04.4 LTS
- Windows 10 Pro: 10.0.19045.3803

## Máquinas virtuales utilizadas

| Rol | Nombre en VMware | Nombre dentro del sistema | IP |
|---|---|---|---|
| Servidor Wazuh | Wazuh-Server | wazuh-server | 192.168.254.133 |
| Ubuntu + Suricata + Wazuh Agent | Ubuntu 2026 | ubuntu-suricata | 192.168.254.131 |
| Windows 10 + Wazuh Agent | Windows 10 2026 | DESKTOP-35HVUL9 | 192.168.254.132 |

## Topología
Las tres máquinas virtuales se conectaron dentro de la misma red NAT de VMware:

- Wazuh-Server → 192.168.254.133
- Ubuntu Suricata → 192.168.254.131
- Windows 10 Agent → 192.168.254.132

## Procedimiento realizado
1. Se desplegó Wazuh Server en VMware.
2. Se instaló Ubuntu Server y se configuró OpenSSH.
3. Se instaló Wazuh Agent en Ubuntu.
4. Se instaló Suricata en Ubuntu.
5. Se configuró Wazuh para leer el archivo `eve.json` generado por Suricata.
6. Se validó la generación de tráfico y eventos desde Ubuntu.
7. Se instaló Wazuh Agent en Windows 10.
8. Se verificó que ambos agentes aparecieran en estado activo dentro de Wazuh.
9. Se validó la visualización de eventos y alertas en Threat Hunting.

## Validaciones realizadas
Se realizaron las siguientes comprobaciones técnicas:

- Conectividad ICMP entre Ubuntu y Wazuh
- Resolución DNS desde Ubuntu
- Generación de tráfico HTTPS desde Ubuntu
- Estado activo del servicio `suricata`
- Estado activo del servicio `wazuh-agent`
- Generación de eventos en `/var/log/suricata/eve.json`
- Configuración de `ossec.conf` para leer el archivo `eve.json`
- Instalación del agente de Wazuh en Windows
- Servicio `wazuhsvc` en estado `Running`
- Visualización de ambos agentes en el panel de Endpoints
- Visualización de alertas y eventos de Suricata en Threat Hunting

## Evidencias principales
Las evidencias del laboratorio se encuentran en la carpeta `evidencias/`.

Capturas destacadas:
- `00_wazuh_overview_general.png`
- `01_wazuh_threat_hunting_dashboard.png`
- `02_wazuh_endpoints_agentes_activos.png`
- `03_wazuh_threat_hunting_ubuntu_suricata.png`
- `06_ubuntu_suricata_activo.png`
- `07_ubuntu_wazuh_agent_activo.png`
- `13_windows_wazuh_agent_running.png`

## Resultados observados
El laboratorio permitió obtener los siguientes resultados:

- Wazuh quedó operativo y accesible desde navegador
- Se registraron dos agentes activos: Ubuntu y Windows
- Suricata generó eventos visibles en Wazuh
- Threat Hunting mostró eventos del agente `ubuntu-suricata`
- El endpoint Windows se conectó correctamente mediante el servicio `wazuhsvc`
- Se logró una arquitectura funcional de monitoreo y centralización de eventos en un entorno virtual simple

## Problemas encontrados y decisiones técnicas
Durante el desarrollo del laboratorio se presentaron algunos inconvenientes:

- Se detectaron problemas al integrar VMware directamente con GNS3
- Para priorizar estabilidad y simplicidad, se decidió completar el laboratorio únicamente con VMware
- Fue necesario validar conectividad, DNS y tráfico antes de completar la integración final
- Durante la subida a GitHub se presentó un problema temporal de resolución DNS, que fue solucionado vaciando la caché DNS local

## Conclusión
Este laboratorio demostró la integración efectiva de Wazuh y Suricata en una arquitectura virtual basada en VMware, combinando monitoreo de endpoints y detección de eventos de red en un entorno controlado. La práctica permitió validar el registro de agentes Linux y Windows, la recepción de alertas de seguridad en el dashboard de Wazuh y la utilidad de Suricata como fuente de eventos IDS. En conjunto, el proyecto representa una implementación pequeña pero técnicamente sólida para prácticas de monitoreo, observabilidad y análisis inicial de eventos de seguridad.

## Autor
Proyecto realizado por GONZALO M. PEREZ