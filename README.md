# 🌡️ WorkWell IoT – Estação de Bem-Estar

> **Global Solution 2025 (FIAP)** > Sistema inteligente com ESP32 para monitoramento de conforto ambiental e saúde no home office.

---

## 👨‍💻 Integrantes

| Nome | RM |
| :--- | :--- |
| **Rafael Franck** | RM550875 |
| **Gabriela Trevisan** | RM99500 |
| **Eduardo Araújo** | RM99758 |

---

## 📋 Sobre o Projeto

O **WorkWell IoT** é uma estação inteligente baseada em **ESP32** que analisa, em tempo real, três fatores críticos para o bem-estar no trabalho remoto: Temperatura, Umidade e Luminosidade.

### 🚨 O Problema
Com a expansão do home office, profissionais enfrentam condições inadequadas que geram:
- ⚠ **Queda de produtividade e foco.**
- ⚠ **Fadiga e irritação visual.**
- ⚠ **Estresse térmico.**

### ✅ A Solução
Uma estação de monitoramento que processa dados e fornece feedback imediato:
1.  **Leitura:** Sensores captam condições ambientais.
2.  **Análise:** O firmware classifica o ambiente em OK, Atenção ou Alerta.
3.  **Feedback:** LEDs e Buzzer notificam o usuário instantaneamente.
4.  **Conectividade:** Envia dados via **MQTT** para integração com dashboards.

---

## ⚙️ Componentes e Hardware

### Hardware Utilizado
| Componente | Função |
| :--- | :--- |
| **ESP32 DevKit** | Microcontrolador principal e conexão Wi-Fi/MQTT. |
| **DHT22** | Sensor digital de Temperatura e Umidade. |
| **LDR** | Sensor analógico de luminosidade (fotorresistor). |
| **LEDs (RGB/Separados)** | Feedback visual (Verde, Amarelo, Vermelho). |
| **Buzzer** | Feedback sonoro para alertas críticos. |

### Dependências (Software)
* `WiFi.h` (Conexão de rede)
* `PubSubClient.h` (Comunicação MQTT)
* `DHTesp.h` (Leitura do sensor DHT)

---

## 🚦 Lógica de Feedback (Status)

O sistema utiliza uma classificação ergonômica para alertar o usuário:

| Status | LED Indicador | Buzzer | Ação Sugerida |
| :--- | :---: | :---: | :--- |
| **OK** | 🟢 Verde | 🔇 Off | Ambiente otimizado para foco e produtividade. |
| **Atenção** | 🟡 Amarelo | 🔇 Off | Requer monitoramento; avaliar pequenos ajustes. |
| **Alerta** | 🔴 Vermelho | 🔊 **ON** | **Pausa imediata** ou ajuste urgente (ventilação/luz). |

---

## 🔧 Como Executar o Projeto

### 1. Simulação Online (Wokwi)
Você pode rodar o projeto imediatamente no navegador através do simulador Wokwi:

🔗 **[Acessar Simulação no Wokwi](https://wokwi.com/projects/447990401345346561)**

### 2. Execução Física ou IDE
1.  **Configuração Wi-Fi:**
    No código, configure as credenciais (se usar Wokwi, mantenha o padrão):
    ```cpp
    const char* ssid = "Wokwi-GUEST"; // Ou sua rede real
    const char* password = "";        // Sua senha
    ```

2.  **Configuração MQTT:**
    O projeto usa um broker público para facilitar testes:
    * **Broker:** `test.mosquitto.org`
    * **Porta:** `1883`
    * **Tópico:** `gs2025/workwell/sensores`

3.  **Teste dos Sensores:**
    * Aproxime o dedo do DHT22 (físico) ou clique nele (simulação) para alterar Temperatura/Umidade.
    * Cubra ou ilumine o LDR para alterar a luminosidade.
    * Observe a mudança dos LEDs e o acionamento do Buzzer.

---

## 📡 Exemplo de Payload (JSON)

Ao rodar, o dispositivo envia periodicamente um JSON para o tópico MQTT:

```json
{
  "temp": 24.5,
  "hum": 55.0,
  "luz": 2100,
  "status": "OK"
}
```

---

## 📸 Circuito e Diagrama
Abaixo, o esquema de ligação utilizado no projeto:

<img width="800" height="689" alt="image" src="https://github.com/user-attachments/assets/f18e45e5-0567-43c2-9d62-58c8505373a0" />

---

## 🎥 Evidência de Funcionamento
Confira o vídeo de demonstração do funcionamento do circuito e da integração MQTT:

🔗 **[Assista ao vídeo no GoogleDrive]([https://drive.google.com/file/d/14Q5jP9UzxflTX27oOjZNPT0GIFmHNdqm/view?usp=sharing](https://drive.google.com/file/d/1uNR6tV9OHQdWZrjAYETZVNBj819WF7HK/view?usp=sharing))**
