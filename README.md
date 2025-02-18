# Projeto - Aplicação Conversor ADC com Raspberry Pi Pico W

## Discente: Danilo Silveira

### Explicação do Código

Este projeto demonstra como controlar um display SSD1306, LEDs RGB com PWM e um joystick. A seguir, é apresentada a explicação detalhada de cada parte do código:

### 1. **Inicialização do Display SSD1306**

A função `init_display()` é responsável por configurar o display e limpar a tela. O display é usado para exibir um quadrado, que é desenhado utilizando a função `draw_square()`. A posição do quadrado é atualizada conforme os valores lidos do joystick.

### 2. **PWM para LEDs**

A função `pwm_init()` configura os pinos GPIO conectados aos LEDs RGB para controle PWM (Pulse Width Modulation). A intensidade de cada LED pode ser ajustada através da função `update_leds()`, que utiliza os valores lidos do joystick para modificar a cor e o brilho dos LEDs.

### 3. **Interrupções (IRQ)**

O código utiliza interrupções (IRQ) para tratar os botões do joystick e o botão A. As funções `button_irq_handler()` e `button_a_irq_handler()` são responsáveis por lidar com essas interrupções. Quando um botão é pressionado, essas funções alternam o estado dos LEDs e controlam o estilo da borda do display. Para evitar leituras falsas e múltiplos acionamentos seguidos, a técnica de **debouncing** é aplicada. O tempo entre os acionamentos é verificado utilizando a função `to_ms_since_boot()`.

### 4. **Leitura do Joystick**

A leitura do joystick é realizada através do ADC (Conversor Analógico-Digital). As funções `adc_select_input()` e `adc_read()` são usadas para ler os valores do joystick. Esses valores são mapeados para controlar o brilho dos LEDs e a posição do quadrado no display.

### 5. **Debouncing**

A técnica de debouncing é aplicada para garantir que os botões não gerem leituras falsas ou múltiplas em um curto intervalo de tempo. A função `to_ms_since_boot()` é utilizada para verificar o tempo entre os acionamentos dos botões e evitar que eventos de pressão repetidos sejam registrados de forma errada.

---

### Requisitos Atendidos

- **Interrupções (IRQ)**: Implementadas para os botões do joystick e o botão A.
- **Debouncing**: Implementado nas interrupções dos botões para evitar múltiplos acionamentos.
- **Display SSD1306**: Utilizado para exibir o quadrado e a borda modificada com base nas entradas.
- **Controle de LEDs via PWM**: Os LEDs RGB são controlado

### Link do vídeo
https://youtube.com/shorts/aoz3WzUaxyQ?feature=share
