# 🏆 Projeto IoT – Monitoramento de Estatísticas do Futebol Feminino

## 👥 Integrantes do Grupo

- **Felipe Otávio Garcia Madeira** – RM: 563521  
- **Murilo Macedo Pina** – RM: 563397  
- **Diego Bondezan Yonamine** – RM: 562013  
- **Alexandre Martins Lucas** – RM: 561732  
- **Vitor Carvalho Alexandre** – RM: 562298  

---

## ⚙️ Detalhes da Implementação

O projeto tem como objetivo **monitorar estatísticas de jogadoras de futebol feminino** em tempo real, utilizando **ESP32**, **protocolo MQTT** e **Node-RED Dashboard** para visualização dos dados.

### 🔹 Estrutura do Sistema

1. **ESP32 (dispositivo IoT)**  
   - Conecta-se ao Wi-Fi (`Wokwi-GUEST`) e ao broker MQTT (`54.172.140.81`, porta `1883`).
   - Gera e envia, de forma simulada, dados das jogadoras:  
     ```json
     {
       "nome": "Ana",
       "jogos": 10,
       "gols": 4,
       "assistencias": 3
     }
     ```
   - Os dados são publicados no tópico **`futFem/jogadoras`**.

2. **Broker MQTT**  
   - Atua como intermediário entre o ESP32 e o Node-RED.
   - Permite o envio e recebimento das mensagens JSON.

3. **Node-RED Dashboard**  
   - Recebe os dados do tópico `futFem/jogadoras`.  
   - Exibe as informações das jogadoras em **widgets visuais**, como `text`, `chart` e `gauge`.  
   - O dashboard foi criado com o **grupo `futfem`** e o **tópico `futFem/jogadoras`**.  

---

## 💻 Tecnologias Utilizadas

| Componente | Função |
|-------------|---------|
| **ESP32 (Arduino IDE / Wokwi)** | Coleta e envia dados simulados |
| **Wi-Fi** | Comunicação com a internet |
| **MQTT (PubSubClient)** | Protocolo de mensageria entre IoT e servidor |
| **Node-RED + Dashboard** | Interface visual e lógica de recebimento |
| **JSON** | Formato dos dados enviados |

---

## 📊 Resultados da PoC (Prova de Conceito)

Durante os testes no **Wokwi** e **Node-RED**, foi possível observar:

- Conexão estável com o broker MQTT (`54.172.140.81`).
- Envio de dados periódicos de 5 jogadoras com estatísticas variadas.
- Recepção em tempo real dos dados pelo Node-RED.  
- Visualização dos valores recebidos em tempo real no dashboard.

Exemplo de saída no **Monitor Serial**:
```
📤 Enviando: {"nome":"Camila","jogos":15,"gols":5,"assistencias":2}
📤 Enviando: {"nome":"Elisa","jogos":19,"gols":9,"assistencias":4}
✅ WiFi conectado!
✅ Conectado ao broker!
```

---

## 🧩 Integração IoT + Node-RED Dashboard

A integração foi feita da seguinte forma:

1. **No ESP32 (Arduino/Wokwi):**  
   O código publica os dados no tópico `futFem/jogadoras`.

2. **No Node-RED:**  
   - Adicionado o nó **MQTT IN** → conectado ao broker `54.172.140.81` e inscrito em `futFem/jogadoras`.  
   - Ligado a um **nó `text`** e um **nó `debug`** para exibição das mensagens recebidas.  
   - Criado um **dashboard** com a aba `futfem` e o grupo `Group 1`.  
   - Exibidas as informações de cada jogadora em tempo real.

---

## 🖼️ Evidências da Integração

### 📸 Print 1 – Node-RED Flow
Mostra o fluxo configurado com os nós **MQTT IN → Debug → Text**.
  
*(imagem anexada acima – “Fluxo Node-RED”)*  

---

### 📸 Print 2 – Instrução README e Configuração do Projeto
Demonstra a exigência e evidência do trabalho com prints de tela, detalhamento e integração.  
  
*(imagem anexada acima – “Requisitos README”)*  

---

## 🚀 Conclusão

O projeto comprovou a **viabilidade da comunicação entre IoT e interface web**.  
Os dados enviados pelo ESP32 via MQTT foram recebidos corretamente e exibidos em um **dashboard dinâmico e acessível**.  
Essa PoC valida o uso de soluções IoT para **monitoramento esportivo**, podendo futuramente ser expandida para:
- Histórico de desempenho das jogadoras;
- Integração com banco de dados;
- Painéis comparativos em tempo real.

Link do vídeo:
https://www.youtube.com/watch?v=mKrK1VIoN04

