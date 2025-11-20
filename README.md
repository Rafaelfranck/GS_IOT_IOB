Rafael Franck (RM550875); 
Gabriela Trevisan (RM99500);
Eduardo Araújo (RM99758);

## WorkWell IoT – Estação de Bem-Estar para o Futuro do Trabalho

Sistema IoT com ESP32 para monitoramento inteligente de conforto ambiental no home office. Uma solução inteligente para otimizar a saúde e a produtividade no trabalho remoto.

---

### 1. Descrição do Problema

Com a rápida expansão do home office, milhões de profissionais passam longas horas em ambientes com condições inadequadas. Fatores como temperatura extrema, iluminação deficiente e umidade fora da faixa ideal são causas diretas de:

* Queda de Produtividade e Foco.
* Fadiga e Irritação Visual.
* Problemas de Saúde relacionados ao estresse térmico e visual.

Atualmente, a maioria dos trabalhadores não tem um método automático e baseado em dados para monitorar e ajustar seu ambiente de maneira eficiente.

---

### 2. Solução Proposta: WorkWell IoT

O WorkWell IoT é uma estação inteligente desenvolvida com ESP32 e sensores IoT que analisa, em tempo real, os três fatores críticos de bem-estar para o trabalho: Temperatura, Umidade e Luminosidade.

#### Como Funciona:

A solução WorkWell IoT processa os dados em três etapas principais: Leitura, Análise/Feedback Local e Comunicação IoT.

#### 1. Módulos e Funcionalidades

* Leitura de Dados: Utiliza DHT22 (Temperatura/Umidade) e LDR (Luminosidade) para captação contínua e precisa das condições ambientais.
* Análise Central: O firmware do ESP32 classifica o ambiente em OK, Atenção ou Alerta, baseado em faixas ergonômicas de conforto.
* Feedback Imediato: LEDs  Buzzer fornecem notificação visual (cores) e sonora (alerta) direta ao usuário.
* Comunicação IoT: Utiliza MQTT para enviar os dados processados em formato JSON, facilitando a integração com dashboards e sistemas corporativos.

#### 2. Sinalização de Status (Interface do Usuário)

O feedback é instantâneo e intuitivo, baseado na classificação ergonômica:

* Status OK: Indicado pelo LED 🟢 Verde. O Buzzer permanece desligado.
    Ação Sugerida: Ambiente otimizado para foco e produtividade.
* Status Atenção: Indicado pelo LED 🟡 Amarelo. O Buzzer permanece desligado.
    * Ação Sugerida: Condição que requer monitoramento; avaliar pequenos ajustes.
* Status Alerta: Indicado pelo LED 🔴 Vermelho  o Buzzer é ativado
    * Ação Sugerida: Necessidade de pausa imediata ou ajuste urgente no ambiente (ex: ventilação, iluminação).
---

### 3. Componentes e Dependências

#### Componentes Utilizados (Hardware)

* ESP32 DevKit (Placa principal).
* Sensor DHT22 (Temperatura e Umidade).
* Módulo LDR (Sensor de luminosidade analógico).
* LEDs: Verde, Amarelo e Vermelho.
* **Buzzer** (para Alerta).

#### Dependências do Código (Software e Bibliotecas)
1.  WiFi.h
2.  PubSubClient.h 
3.  DHTesp.h

---

### 4. Instruções de Uso e Execução

Para rodar o projeto, siga os passos abaixo:

#### A. Configuração Inicial

1.  Abra o Projeto: Carregue o código no seu Arduino IDE (para ESP32) ou utilize o ambiente de simulação Wokwi (carregando `diagram.json` e `code.ino`).
2.  Rede Wi-Fi (Padrão Wokwi):
    const char* ssid = "Wokwi-GUEST";
    const char* password = "";

    Se estiver usando hardware físico, altere para suas credenciais de rede.

3.  Configuração MQTT: O projeto utiliza um broker público para testes:
    * Broker: `test.mosquitto.org`
    * Porta: `1883`
    * Tópico de Envio: `gs2025/workwell/sensores`

#### B. Execução e Validação

1.  Execute o código no ESP32.
2.  Abra o Serial Monitor para ver as logs de conexão e envio de dados.
3.  Utilize um cliente MQTT (ex: MQTTX ou MQTT Explorer) e assine o tópico `gs2025/workwell/sensores`.
4.  Teste os Sensores:
    * Aproxime o dedo ou sopre no DHT22 para alterar a Temperatura e Umidade.
    * Cubra o LDR para alterar a Luminosidade.
    * Observe as mudanças imediatas nos LEDs e no Buzzer do hardware/simulação, e a chegada do JSON no seu cliente MQTT.

#### Exemplo de Mensagem Publicada (JSON):

```json
{
  "temp": 24.5,
  "hum": 55.0,
  "luz": 2100,
  "status": "OK"
}

### 5. Fluxo do Sistema (Resumo)

* Captação: Sensores captam T°, Umidade e Luz.
* Processamento: ESP32 classifica em OK/Atenção/Alerta com base nas faixas ergonômicas.
* Feedback Local: LEDs e Buzzer notificam o usuário.
* Comunicação IoT: Dados JSON são enviados via MQTT.
* Integração: Os dados podem alimentar *dashboards*, apps de RH e plataformas de bem-estar.

---

### 6. Impacto e Relevância

O WorkWell IoT é um projeto crucial que contribui diretamente para o futuro do trabalho ao focar na saúde e produtividade do colaborador remoto:

* Promove Bem-Estar e Saúde Física.
* Reduz Fadiga, estresse térmico e esforço visual.
* Aumenta Produtividade e Foco.
* Facilita Integração com sistemas corporativos de analytics.

Em um mundo cada vez mais remoto e digital, esta solução torna o ambiente de trabalho **mais seguro, saudável e inteligente.

### 7. Imagem do circuito
<img width="958" height="825" alt="image" src="https://github.com/user-attachments/assets/a57b1df0-e329-4579-ac46-3b45bdba210a" />



### 8. Link do wokwi

https://wokwi.com/projects/447990401345346561
