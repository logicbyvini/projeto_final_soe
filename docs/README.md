# Driver Drowsiness & Distraction Detection System (DMS)

Sistema embarcado autônomo e de alta performance, desenvolvido em C/C++, para detecção de sonolência e distração de motoristas em tempo real. O sistema utiliza a câmera SmartCam S600 integrada a uma Raspberry Pi 4 Model B, executando um pipeline multithreading com atuação local via GPIO e telemetria remota desacoplada.

Este repositório faz parte das avaliações práticas da disciplina **Sistemas Operacionais Embarcados**, da Universidade de Brasília (UnB).

---

## Integrantes da Dupla

- **Vinícius Eduardo Lopes da Silva** — Matrícula: 202024061
- **Gabriel Hajime Yamaoka Sebata** — Matrícula: 200018108

---

## O Cenário: A Threat Behind the Wheel

Imagine um motorista de caminhão enfrentando a terceira hora seguida de viagem em uma rodovia sem iluminação, durante a madrugada. O cansaço se acumula silenciosamente. Aos poucos, as pálpebras começam a pesar e a velocidade de reação diminui drasticamente.

Em um piscar de olhos prolongado — o chamado **microsono** —, o veículo pode percorrer dezenas de metros completamente sem controle. Não há tempo para frear; a colisão pode acontecer antes mesmo que o motorista perceba o perigo.

Segundo dados da Associação Brasileira de Medicina de Tráfego (ABRAMET, 2021), o sono e a fadiga estão associados a até 40% dos acidentes de trânsito no Brasil. A probabilidade de acidentes graves durante a madrugada também é significativamente maior do que no período diurno.

A maioria das soluções convencionais de visão computacional enfrenta desafios justamente nos momentos de maior risco: condições de baixa luminosidade na cabine e latência imprevisível no acionamento dos mecanismos de alerta.

---

## A Solução Embarcada

Para responder a essa ameaça, este projeto propõe o desenvolvimento de um **Driver Monitoring System (DMS)** autônomo, não invasivo e de baixa latência, voltado ao setor de transporte de cargas e à gestão de frotas rodoviárias.

Utilizando a câmera inteligente **SmartCam S600** integrada a uma **Raspberry Pi 4 Model B**, o sistema realiza a captura e o processamento de imagens do motorista por meio de uma interface USB/UVC.

Desenvolvida em C/C++ sobre Linux embarcado, a aplicação processa o fluxo de vídeo utilizando **POSIX Threads (`pthread`)**, sob o modelo Produtor-Consumidor, para monitorar continuamente:

- **Fadiga e microsono:** cálculo da Razão de Aspecto Ocular (*Eye Aspect Ratio — EAR*), com validação temporal de pelo menos 15 frames a 30 FPS (equivalente a 500 ms).
- **Distração:** identificação do desvio angular da cabeça em relação à direção de condução, considerando intervalos superiores a 2 segundos.
- **Telemetria desacoplada:** transmissão de logs e eventos de risco para um servidor central, sem bloquear o processamento visual local.

Ao identificar uma condição crítica, o sistema aciona um **alarme sonoro via GPIO**, buscando uma latência de resposta inferior a 100 ms.

---

## Arquitetura de Hardware

| Componente | Função |
|:---|:---|
| **Raspberry Pi 4 Model B** | Processamento central (Broadcom BCM2711, Quad-Core ARM Cortex-A72 @ 1.5 GHz). |
| **SmartCam S600** | Captura contínua de vídeo por interface USB / V4L2 UVC. |
| **Buzzer Ativo + Transistor** | Atuação do alarme sonoro por meio de pino GPIO, utilizando `libgpiod`. |

---

## Arquitetura de Software & SOE

O software é estruturado em C/C++, utilizando **POSIX Threads (`pthread`)** e o modelo Produtor-Consumidor com buffers circulares.

### Organização das Threads

| Thread | Responsabilidade |
|:---|:---|
| **Thread 1 — Captura** (`capture_thread`) | Interface com V4L2 (Video4Linux2) para aquisição de quadros da SmartCam S600, com configuração de buffers de captura (640 × 480 a 30 FPS). |
| **Thread 2 — Processamento** (`processing_thread`) | Extração de pontos de referência faciais e cálculo geométrico do EAR e da orientação da cabeça. |
| **Thread 3 — Atuação** (`gpio_thread`) | Monitoramento dos eventos de alerta e acionamento do buzzer via GPIO, buscando latência inferior a 100 ms. |
| **Thread 4 — Telemetria** (`server_comm_thread`) | Envio assíncrono de alertas e métricas para um servidor remoto via sockets/HTTP. |

---

## Documentação do Projeto

- [PC1 — Proposta do Projeto (TAP, Requisitos e EAP)](./PC1_Proposta_do_Projeto.md)

---

## Estrutura do Repositório

```text
.
├── docs/                       # Diagramas e documentação adicional
├── include/                    # Arquivos de cabeçalho (.h)
├── src/                        # Código-fonte em C/C++
│   ├── main.c                  # Inicialização e gerenciamento de pthreads
│   ├── capture.c               # Thread de captura de vídeo V4L2
│   ├── detector.c               # Algoritmo de visão computacional (EAR)
│   ├── gpio.c                   # Manipulação dos pinos GPIO (Buzzer)
│   └── telemetry.c              # Thread de telemetria remota
├── Makefile                    # Script de compilação
├── PC1_Proposta_do_Projeto.md  # Documentação da Proposta (PC1)
└── README.md                   # Apresentação principal
```

---

**Universidade de Brasília (UnB)**  
**Disciplina:** Sistemas Operacionais Embarcados
