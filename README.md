PetCare IoT — Pet Health Monitor

> Projeto desenvolvido para a disciplina **Disruptive Architectures: IoT, IoB & Generative IA** — FIAP  
> **1º Sprint**

---

Sobre o Projeto

O **PetCare IoT** é um sistema de monitoramento ambiental para pets desenvolvido em parceria com a empresa **Clyvo**, que busca tornar seu aplicativo de pets genuinamente útil e adotado pelos clientes.

O problema central: Tutores de pets precisam sair de casa para trabalhar e não têm como saber se o ambiente onde o pet fica está seguro e confortável. Nossa solução resolve isso através de uma assinatura premium do app Clyvo: o assinante recebe um dispositivo físico em casa que monitora temperatura, umidade e presença do pet em tempo real, enviando alertas automáticos direto para o celular do tutor.

> *"Trazer para os clientes o app de pets que eles precisam e não sabiam que precisavam."*

---

Tecnologias Utilizadas

| Tecnologia | Aplicação |
|---|---|
| ESP32 | Microcontrolador principal |
| DHT22 | Sensor de temperatura e umidade |
| PIR HC-SR501 | Sensor de movimento/presença do pet |
| LED | Indicador visual de alerta |
| MQTT (HiveMQ) | Protocolo de comunicação IoT |
| Node-RED | Dashboard de monitoramento em tempo real |
| Wokwi | Simulação do circuito |

---

Circuito

| Componente | Pino ESP32 |
|---|---|
| DHT22 | GPIO 15 |
| PIR | GPIO 14 |
| LED | GPIO 2 |

---

Tópicos MQTT

| Tópico | Descrição |
|---|---|
| `petcare/ambiente/temperatura` | Temperatura em °C |
| `petcare/ambiente/umidade` | Umidade relativa em % |
| `petcare/ambiente/movimento` | Presença do pet (0 ou 1) |
| `petcare/alerta` | Status do ambiente (OK ou motivo do alerta) |

---

Lógica de Alertas

| Condição | Alerta |
|---|---|
| Temperatura > 28°C | `CALOR_EXCESSIVO` |
| Temperatura < 18°C | `FRIO_EXCESSIVO` |
| Umidade > 70% | `UMIDADE_ALTA` |
| Umidade < 40% | `UMIDADE_BAIXA` |
| Tudo normal | `OK` |

---

Dashboard Node-RED

O dashboard exibe em tempo real:
- Gauge de temperatura (0–50°C)
- Gauge de umidade (0–100%)
- Histórico de temperatura (gráfico de linha)
- Status de movimento do pet
- Status de alerta do ambiente

**Broker:** `broker.hivemq.com:1883`

---

Como Executar

### Simulação (Wokwi)
1. Acesse o projeto no Wokwi: [link do projeto](https://wokwi.com/projects/463315521353108481)
2. Clique em **Play** para iniciar a simulação

### Node-RED Dashboard
1. Instale o Node-RED: `npm install -g node-red`
2. Instale o dashboard: `npm install node-red-dashboard`
3. Inicie: `node-red`
4. Importe o arquivo `flows.json` via **Menu → Import**
5. Clique em **Deploy**
6. Acesse o dashboard em `http://localhost:1880/ui`

---

Integrantes

| Nome | RM |
|---|---|
| Artur Pioli Silva | 565597 |
| Matheus Arazin de Oliveira | 556649 |
| Pedro Gabriel Claes | 566058 |
| Kevin Martins Campos | 563454 |

---

Resultados Parciais

- ✅ Protótipo simulado funcional no Wokwi
- ✅ Comunicação MQTT estabelecida com broker público HiveMQ
- ✅ Dashboard Node-RED recebendo dados em tempo real
- ✅ Sistema de alertas automáticos por temperatura e umidade
- ✅ Detecção de movimento do pet via sensor PIR




