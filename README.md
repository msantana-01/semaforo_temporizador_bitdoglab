# Semáforo com a placa Bitdoglab

Este projeto implementa um semáforo simples utilizando a placa Bitdoglab. Devido à disponibilidade de LEDs na placa Bitdoglab (vermelho, azul e verde), a cor amarela foi simulada ligando simultaneamente os LEDs vermelho e verde. O semáforo alterna entre as luzes vermelha, "amarela" (simulada) e verde em intervalos regulares de 3 segundos.

---

## Componentes Necessários

- Raspberry Pi Pico
- Placa Bitdoglab (com LEDs vermelho, azul e verde integrados)

---

## Conexões

A placa Bitdoglab já possui LEDs integrados conectados aos seguintes GPIOs do Raspberry Pi Pico:

| LED       | GPIO no Raspberry Pi Pico |
|-----------|---------------------------|
| Vermelho  | GPIO 13                   |
| Verde     | GPIO 11                   |

> **Nota**: O LED azul da placa Bitdoglab não foi utilizado neste projeto, pois o foco foi simular um semáforo tradicional com as cores vermelho, amarelo e verde.

---

## Como Funciona

O código utiliza um temporizador para alternar entre as luzes do semáforo a cada 3 segundos. O estado atual do semáforo é impresso no console a cada segundo.

### Estados do Semáforo

1. **Vermelho**: LED vermelho ligado, LED verde desligado.
2. **Amarelo (simulado)**: LEDs vermelho e verde ligados simultaneamente para simular a cor amarela.
3. **Verde**: LED verde ligado, LED vermelho desligado.

---

## Simulação da Cor Amarela

Como a placa Bitdoglab não possui um LED amarelo, a cor amarela foi simulada ligando os LEDs vermelho e verde ao mesmo tempo. Essa combinação de cores cria uma tonalidade próxima ao amarelo, permitindo que o semáforo funcione de maneira semelhante a um semáforo real.

## Uso do add_repeating_timer_ms() e repeating_timer_callback()

O código utiliza duas funções importantes da SDK do Raspberry Pi Pico para criar um temporizador repetitivo: add_repeating_timer_ms() e repeating_timer_callback(). Essas funções são essenciais para controlar a alternância entre os estados do semáforo em intervalos regulares.
add_repeating_timer_ms()

A função add_repeating_timer_ms() é usada para configurar um temporizador que dispara repetidamente em um intervalo de tempo especificado. No código, ela é configurada para chamar a função de callback a cada 3000 milissegundos (3 segundos).
Parâmetros:

**Intervalo de tempo:** O tempo em milissegundos entre cada chamada da função de callback (no caso, 3000 ms).

**Função de callback:** A função que será executada sempre que o temporizador disparar (timer_callback no código).

**Dados adicionais:** Um ponteiro para dados adicionais que podem ser passados para a função de callback (neste caso, NULL, pois não são necessários).

**Estrutura do temporizador:** Uma estrutura do tipo repeating_timer que armazena o estado do temporizador.

## Demonstração no Wokwi

<https://wokwi.com/projects/421623975266651137>
