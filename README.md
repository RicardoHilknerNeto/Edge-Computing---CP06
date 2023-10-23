# README - Vinheria IoT Solution

## Arquitetura da Solução

A solução da Vinheria é um sistema de monitoramento IoT que coleta dados de temperatura, umidade e luminosidade e os publica em um servidor MQTT. A arquitetura da solução envolve os seguintes componentes:

- **Hardware:**
  - **ESP32**: O código fornecido é projetado para ser executado em um ESP32, um microcontrolador WiFi/Bluetooth que lê dados de sensores DHT e um sensor de luminosidade.
  - **DHT Sensor (DHT11)**: O sensor de temperatura e umidade é conectado ao ESP32 para medir as condições do ambiente.
  - **LDR (Light-Dependent Resistor)**: Um sensor de luminosidade é usado para medir a quantidade de luz no ambiente.
  - **LEDs**: Três LEDs são usados para indicar a condição do ambiente com base na temperatura.

- **Software:**
  - **Arduino IDE**: O código é desenvolvido e carregado no ESP32 usando o ambiente de desenvolvimento Arduino IDE.
  - **PubSubClient Library**: Esta biblioteca é utilizada para conectar-se ao servidor MQTT e publicar dados.
  - **WiFi Library**: A biblioteca WiFi é usada para configurar e estabelecer a conexão Wi-Fi.

- **Servidor MQTT:**
  - A solução se comunica com um servidor MQTT externo (definido no código como `BROKER_MQTT` e `BROKER_PORT`).

## Manual de Utilização

Para utilizar a solução da Vinheria, siga estas etapas:

1. **Hardware Setup:**
   - Conecte o sensor DHT11 ao pino 13 do ESP32.
   - Conecte o sensor de luminosidade ao pino 14 do ESP32.
   - Conecte os LEDs aos pinos 12, 27 e 26 para vermelho, amarelo e verde, respectivamente.

2. **Configuração do Software:**
   - Abra o código fornecido na Arduino IDE.
   - Configure as constantes `SSID` e `PASSWORD` com as informações da sua rede Wi-Fi.
   - Configure `BROKER_MQTT` e `BROKER_PORT` com as informações do servidor MQTT.

3. **Carregamento do Código:**
   - Carregue o código no ESP32 usando a Arduino IDE.

4. **Monitoramento:**
   - O ESP32 irá ler os sensores periodicamente e publicar dados no servidor MQTT.
   - Os dados são publicados em três tópicos: `TOPICO_PUBLISH` (luminosidade), `TOPICO_PUBLISH_2` (temperatura) e `TOPICO_PUBLISH_3` (umidade).

5. **Visualização dos Dados:**
   - Configure um cliente MQTT para se inscrever nos tópicos mencionados e visualize os dados coletados.

6. **Controle dos LEDs:**
   - Com base na temperatura medida, os LEDs indicarão a condição do ambiente:
     - Temperatura <= 10: LED verde aceso.
     - Temperatura entre 11 e 20: LED amarelo aceso.
     - Temperatura > 20: LED vermelho aceso.

## Observações

Certifique-se de configurar as informações da rede Wi-Fi e do servidor MQTT antes de carregar o código no ESP32. Além disso, verifique se os pinos dos componentes estão corretamente conectados ao ESP32.

A solução da Vinheria oferece monitoramento ambiental em tempo real e pode ser estendida para integração com sistemas de automação ou notificação. Certifique-se de adaptar e personalizar o código e a arquitetura conforme necessário para atender aos requisitos específicos do seu projeto.
