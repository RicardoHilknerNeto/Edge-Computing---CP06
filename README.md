# Projeto de Monitoramento de Dados com Arduino e MQTT

Este projeto combina a funcionalidade de um sensor DHT (umidade e temperatura) com a comunicação MQTT para monitorar e publicar dados de um sensor DHT em um servidor MQTT. Além disso, ele controla um LED com base na temperatura e na luminosidade ambiente.

## Requisitos de Hardware

- Placa Arduino compatível (testado com Arduino Uno)
- Sensor DHT (modelo DHT11)
- Sensor de Luminosidade (LDR)
- LED
- Conexão com a Internet (Wi-Fi)

## Requisitos de Software

- Plataforma Arduino IDE
- Bibliotecas: WiFi, PubSubClient e DHT

## Configuração

Antes de carregar o código no seu Arduino, certifique-se de que os seguintes passos foram seguidos:

1. **Configuração do Hardware:**
   - Conecte o sensor DHT ao pino 13 do Arduino.
   - Conecte o LED ao pino 12 do Arduino.
   - Conecte o sensor de luminosidade (LDR) ao pino 14 do Arduino.

2. **Instalação das Bibliotecas:**
   - Abra a plataforma Arduino IDE.
   - Vá para "Sketch" > "Incluir Biblioteca" > "Gerenciar Bibliotecas".
   - Procure e instale as bibliotecas "WiFi", "PubSubClient" e "DHT".

3. **Configuração do WiFi e MQTT:**
   - Defina o SSID da sua rede Wi-Fi e a senha no código, nas variáveis `SSID` e `PASSWORD`.
   - Configure o endereço IP do servidor MQTT no código, na variável `BROKER_MQTT`.
   - Defina o nome de identificação MQTT no código, na variável `ID_MQTT`.

## Funcionamento

O código realiza as seguintes ações:

1. Inicializa o sensor DHT e os dispositivos de saída (LED).

2. Conecta-se à rede Wi-Fi.

3. Conecta-se ao servidor MQTT.

4. Lê os dados do sensor DHT (temperatura e umidade).

5. Publica os dados no servidor MQTT em três tópicos diferentes:
   - `/TEF/agnelo/attrs/l` para a temperatura.
   - `/TEF/agnelo/attrs/t` para a umidade.
   - `/TEF/agnelo/attrs/u` para ambos os valores.

6. Lê o valor de luminosidade e controla o LED com base na temperatura e na luminosidade.

7. Repete o processo a cada 60 segundos.

## Uso

1. Carregue o código no seu Arduino usando a plataforma Arduino IDE.

2. Certifique-se de que o Arduino esteja conectado à sua rede Wi-Fi.

3. Os dados do sensor DHT serão publicados no servidor MQTT especificado.

4. O LED será ligado se a temperatura for maior ou igual a 38°C e a luminosidade for baixa; caso contrário, o LED permanecerá desligado.

## Licença

Este código é fornecido sob a [licença MIT](LICENSE).
