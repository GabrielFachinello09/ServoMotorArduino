# 🤖 Monitor de Ângulo de Servo Motor em Tempo Real

Este projeto consiste em um sistema de monitoramento visual para um Servo Motor controlado por Arduino. O motor realiza um movimento contínuo de varredura entre 0° e 180°, e seus ângulos atuais são transmitidos via comunicação serial diretamente para uma interface web moderna e minimalista, utilizando a **Web Serial API**.

---

## 🚀 Funcionalidades

* **Varredura Automática:** O Servo Motor se move continuamente de 0° a 180° e retorna de 180° a 0°.
* **Conexão Direta via Navegador:** A página HTML se conecta à placa Arduino sem a necessidade de softwares intermediários ou servidores rodando em segundo plano.
* **Interface Futurista:** Painel escuro animado com fontes no estilo *Space Grotesk* e indicadores visuais de conexão.

---

## 🛠️ Componentes e Tecnologias

### Hardware
* 1x Placa Arduino (Uno, Nano, Mega, etc.)
* 1x Micro Servo Motor (ex: SG90)
* Cabos Jumper

### Software e Web
* **Arduino IDE** (C++) com a biblioteca nativa `Servo.h`
* **HTML5 / CSS3** (com animações em Canvas)
* **JavaScript** (Web Serial API)

---

## 🔌 Esquema de Ligação (Hardware)

Conecte o servo motor ao seu Arduino seguindo a tabela abaixo:

| Pino do Servo | Função | Conexão no Arduino |
| :--- | :--- | :--- |
| **Marrom / Preto** | Gnd (Terra) | GND |
| **Vermelho** | VCC (Energia) | 5V |
| **Laranja / Amarelo** | Sinal (PWM) | Pino Digital 3 |

> ⚠️ **Nota:** O pino de sinal deve ser obrigatoriamente um pino do tipo **PWM** (identificado pelo símbolo `~` na placa).

---

## 💻 Como Executar o Projeto

### 1. Preparando o Arduino
1. Abra a **Arduino IDE**.
2. Copie o código presente no arquivo do firmware (código do Arduino) e cole na IDE.
3. Conecte sua placa ao computador através do cabo USB.
4. Selecione a Placa e a Porta corretas no menu *Ferramentas*.
5. Clique em **Carregar (Upload)**.

### 2. Executando a Interface Web
1. Certifique-se de fechar o *Monitor Serial* da Arduino IDE (a porta serial não pode ser usada por dois programas ao mesmo tempo).
2. Abra o arquivo `.html` em um navegador compatível (Recomendados: **Google Chrome**, **Microsoft Edge** ou **Opera**).
3. Clique no botão **Conectar**.
4. Uma janela do navegador se abrirá solicitando que você escolha a porta onde o seu Arduino está conectado. Selecione-a e confirme.
5. Pronto! O painel passará a exibir o ângulo do servo em tempo real.

---

## 📊 Estrutura dos Códigos

### Arduino (`.ino`)
O código utiliza estruturas de repetição `for` para incrementar e decrementar o ângulo enviado ao servo. A cada mudança, o comando `Serial.println(posicao);` envia o valor do ângulo atualizado pela porta USB na velocidade de 9600 bps.

### Web (`.html`)
O script JavaScript utiliza o método `navigator.serial.requestPort()` para escutar as mensagens vindas do cabo USB. Ele processa os dados de texto recebidos linha por linha e atualiza dinamicamente o elemento HTML que mostra os graus ($^{\circ}$).

---
