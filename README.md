# Projeto Arduino - Controle de LED com Botão

&nbsp;&nbsp;&nbsp;&nbsp;Este projeto consiste em controlar o estado de um LED utilizando um botão, implementado com uma placa Arduino UNO. O objetivo é alternar o estado do LED (ligado/desligado) cada vez que o botão for pressionado.

## Componentes Utilizados

- 1x Arduino UNO
- 1x Protoboard
- 1x LED
- 1x Resistor (330 ohms)
- 1x Botão (push-button)

## Montagem do Circuito

&nbsp;&nbsp;&nbsp;&nbsp;O circuito foi montado conforme a imagem a seguir:

<img src="assets/tinkerca-arduino.png">

1. **LED**:
   - O ânodo (perna curta) do LED está conectado ao pino digital 3 do Arduino.
   - O cátodo (perna longa) está conectado ao GND através de um resistor de 330 ohms para limitar a corrente.

2. **Botão**:
   - Um lado do botão está conectado ao pino digital 8 do Arduino.
   - O outro lado está conectado ao GND.
   - Foi utilizada a função `INPUT_PULLUP` no código para simplificar.

## Código

&nbsp;&nbsp;&nbsp;&nbsp;O código foi desenvolvido em C++ utilizando a IDE do Arduino. Ele é responsável por ler o estado do botão e alternar o estado do LED:

```cpp
const int buttonPin = 8;
const int ledPin = 3;
bool ledState = LOW;

const int buttonPin = 8;
const int ledPin = 11;
bool ledState = LOW;

void setup()
{
  pinMode(ledPin, OUTPUT);
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_BUILTIN, HIGH);
  delay(100);
  digitalWrite(LED_BUILTIN, LOW);
  delay(100);
  if (digitalRead(buttonPin) == LOW) {
    ledState = !ledState;
    digitalWrite(ledPin, ledState);
    Serial.println(ledState ? "LED ligado" : "LED desligado");
    
    while (digitalRead(buttonPin) == LOW) {
      delay(10);
    }
  }
}
```

## Demonstração

&nbsp;&nbsp;&nbsp;&nbsp;Abaixo, uma simples demonstração de como o projeto foi aplicado.

[vídeo demonstração Botão](https://drive.google.com/file/d/1y-ZXRZX4C-XjgeYvOfV6OBnX33xb0h8c/view?usp=sharing)

[vídeo demonstração LED interno](https://drive.google.com/file/d/1tqHXYM77FVjX-d0CjG2wVfOj0dwT5uTW/view?usp=sharing)

<video src="assets/vídeo-arduino.mp4" controls width="600"></video>

<video src="assets/vídeo-led-interno.mp4" controls width="600"></video>
