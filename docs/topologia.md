# Topología del laboratorio

El laboratorio fue implementado sobre una red NAT de VMware con tres máquinas virtuales:

- **Wazuh-Server** — `192.168.254.133`
- **Ubuntu Suricata** — `192.168.254.131`
- **Windows 10 Agent** — `192.168.254.132`

## Descripción funcional

### 1. Wazuh-Server
Actúa como servidor principal de monitoreo y correlación de eventos.  
Centraliza la información recibida desde los agentes y permite visualizar alertas, eventos y estado de los endpoints desde el dashboard web.

### 2. Ubuntu Suricata
Esta máquina cumple una doble función:
- Endpoint Linux monitoreado por Wazuh Agent
- Sensor de red con Suricata

Suricata genera eventos en formato JSON dentro del archivo `eve.json`, y dichos eventos son leídos por Wazuh para su análisis y visualización.

### 3. Windows 10 Agent
Funciona como endpoint Windows monitoreado por Wazuh mediante el agente oficial.  
Permite validar el registro de un segundo sistema operativo dentro del mismo entorno de monitoreo.

## Relación entre componentes

- `Wazuh-Server` recibe eventos desde Ubuntu y Windows.
- `ubuntu-suricata` envía eventos del sistema y también eventos IDS generados por Suricata.
- `DESKTOP-35HVUL9` envía eventos del sistema mediante el servicio `wazuhsvc`.

## Esquema simplificado

```text
[ Wazuh-Server ] 192.168.254.133
        |
        |---- [ ubuntu-suricata ] 192.168.254.131
        |
        |---- [ DESKTOP-35HVUL9 ] 192.168.254.132