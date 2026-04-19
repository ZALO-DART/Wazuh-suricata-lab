# Wazuh + Suricata Lab en VMware

## Descripción
Este proyecto documenta un laboratorio de ciberseguridad implementado en VMware con las siguientes máquinas virtuales:

- Wazuh Server
- Ubuntu Server con Suricata y Wazuh Agent
- Windows 10 con Wazuh Agent

## Objetivo
Centralizar eventos de seguridad en Wazuh, integrar Suricata como IDS y visualizar alertas desde el dashboard.

## Entorno utilizado
- VMware Workstation
- Wazuh Server
- Ubuntu 24.04.4 LTS
- Windows 10 x64

## Topología
Las tres máquinas virtuales se conectaron en la misma red virtual NAT de VMware:

- Wazuh Server: 192.168.254.133
- Ubuntu Suricata: 192.168.254.131
- Windows 10 Agent: 192.168.254.132

## Componentes implementados
### Wazuh Server
Se desplegó el servidor Wazuh en VMware y se validó el acceso al dashboard web.

### Ubuntu + Suricata
En Ubuntu se configuró:
- Wazuh Agent
- Suricata
- integración de `eve.json` con Wazuh mediante `ossec.conf`

### Windows 10
En Windows 10 se instaló el agente Wazuh y se validó el servicio `wazuhsvc` en estado `Running`.

## Evidencias del laboratorio
Las evidencias se encuentran en la carpeta `evidencias/`.

Se validó:
- Wazuh operativo con dos agentes activos
- eventos de Suricata visibles en Threat Hunting
- conectividad entre Ubuntu y Wazuh
- resolución DNS y tráfico HTTP/HTTPS desde Ubuntu
- agente Wazuh instalado y activo en Windows

## Resultados
- El agente `ubuntu-suricata` apareció activo en Wazuh
- El agente Windows apareció activo en Wazuh
- Suricata generó eventos que fueron leídos por Wazuh
- Se observaron alertas de seguridad en Threat Hunting

## Conclusión
El laboratorio permitió integrar monitoreo de endpoints y detección de eventos en una arquitectura simple basada en VMware, demostrando el funcionamiento conjunto de Wazuh, Suricata, Ubuntu y Windows 10.