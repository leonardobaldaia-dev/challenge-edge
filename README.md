Grupo:
Leonardo Baldaia, Lorran Santos, Gabriel Caetano, Maria Clara

# Software de Controle de Servo Motores

Este projeto foi desenvolvido para controlar dois servos motores utilizando comunicação MQTT. Os servos são usados para simular o mecanismo de direção de um veículo, onde os ângulos dos servos são ajustados com base em mensagens MQTT, controlando a direção como se fossem os eixos das rodas dianteiras.

## Funcionalidades

- **Conectividade Wi-Fi**: Conecta-se a uma rede Wi-Fi especificada.
- **Comunicação MQTT**: Inscreve-se em um tópico MQTT específico para receber comandos de controle.
- **Controle de Servo Motor**: Ajusta a posição de dois servos motores com base nos comandos recebidos.
- **Registro de Dados**: Armazena os pontos de dados, incluindo o comando e o tempo decorrido desde o início do programa, para análise.

## Requisitos de Hardware

- Microcontrolador ESP32/ESP8266.
- Dois servos motores.
- Protoboard e jumpers para conexões.
- Rede Wi-Fi para conectividade.

## Requisitos de Software

- Firmware MicroPython no microcontrolador.
- Biblioteca `umqtt.simple` para comunicação MQTT.
- Bibliotecas `machine` e `network` para controle de hardware e gerenciamento de rede.

## Instalação

1. **Configurar o MicroPython**: Flash o ESP32/ESP8266 com o firmware do MicroPython se ainda não estiver feito.
2. **Enviar o Script**: Copie o código fornecido para o microcontrolador utilizando uma ferramenta como o Thonny IDE ou `ampy`.
3. **Instalar Dependências**: Certifique-se de que a biblioteca `umqtt.simple` esteja disponível no ambiente do MicroPython.

## Configuração

Modifique os seguintes parâmetros no script conforme necessário:

- `ssid`: O SSID (nome) da sua rede Wi-Fi.
- `password`: A senha da sua rede Wi-Fi.
- `mqtt_server`: O endereço do servidor MQTT (broker).
- `topic_subscribe`: O tópico MQTT para se inscrever e receber comandos de controle dos servos.

## Como Utilizar

1. **Conectar ao Wi-Fi**: O software se conectará automaticamente à rede Wi-Fi especificada.
2. **Conectar ao Broker MQTT**: O script se conectará ao broker MQTT especificado e se inscreverá no tópico designado.
3. **Controlar os Servos**: Envie valores inteiros (`0`, `50` ou `100`) para o tópico MQTT inscrito para controlar as posições dos servos:

   - **0**: Gira os servos para a direita (como se estivesse virando as rodas do veículo para a direita).
   - **100**: Gira os servos para a esquerda (como se estivesse virando as rodas do veículo para a esquerda).
   - **50**: Reseta os servos para a posição neutra.

4. **Registro de Dados**: Cada comando é registrado junto com o tempo decorrido desde o início do programa.

## Visão Geral do Código

- **Conexão Wi-Fi**: A função `connect_wifi()` conecta o ESP32/ESP8266 à rede Wi-Fi especificada.
- **Configuração e Conexão MQTT**: A função `setup_mqtt()` inicializa o cliente MQTT e se conecta ao broker.
- **Controle dos Servos**: Com base no payload recebido do tópico MQTT, os servos são ajustados para ângulos específicos utilizando sinais PWM.
- **Registro de Dados**: A lista `data_log` armazena o comando recebido e o tempo correspondente.

## Tratamento de Erros

O script inclui tratamento básico de erros para:

- **Problemas de Conexão Wi-Fi**: Tenta conectar repetidamente até ser bem-sucedido.
- **Problemas de Conexão ao Broker MQTT**: Tenta reconectar se a conexão com o broker MQTT for perdida.
- **Validação de Payload**: Garante que apenas comandos válidos (`0`, `50`, `100`) sejam processados.

## Configuração dos Pinos

- **Servo 1**: Conectado ao GPIO 17 (Pino 17).
- **Servo 2**: Conectado ao GPIO 18 (Pino 18).

## Exemplos de Comandos MQTT

Utilize um cliente MQTT (como o MQTT Explorer) para enviar comandos ao tópico `/ThinkIOT/Servo-nodered`:

- `0`: Gira ambos os servos para a direita.
- `100`: Gira ambos os servos para a esquerda.
- `50`: Reseta ambos os servos para a posição neutra.

## Solução de Problemas

- **Falha na Conexão Wi-Fi**: Verifique o SSID e a senha.
- **Falha na Conexão ao Broker MQTT**: Certifique-se de que o broker MQTT esteja em execução e acessível.
- **Servos Não Respondem**: Verifique as conexões e os ciclos de trabalho do PWM.

## Licença

Este projeto está licenciado sob a Licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.

## Agradecimentos

Agradecimentos especiais às comunidades de MicroPython e MQTT por fornecerem as bibliotecas e documentações que possibilitaram este projeto.

## Link para video
https://youtu.be/n-91ufoJzDA
