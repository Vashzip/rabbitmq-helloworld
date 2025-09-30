# RabbitMQ Hello World Atividade

## 📋 Sobre o Projeto

Esta é um tutorial básico de RabbitMQ implementando o padrão "Hello World" - o exemplo mais simples de mensageria onde um produtor (sender) envia mensagens para uma fila e um consumidor (receiver) recebe e processa essas mensagens.

# Seguindo o padrão de tutorial do próprio RabbitMQ
# Tutorial realizado em Fedora Linux

## 🛠️ Ferramentas Utilizadas

### Software Obrigatório:
- **Python 3.13**
- **Conda Environment** Ambiente e pacotes
- **RabbitMQ Server** Servidor de mensageria RabbitMQ

### Bibliotecas Python:
- **pika** - Cliente Python para RabbitMQ

## 🚀 Passo a Passo Completo

### Configuração do Ambiente Conda

```bash
conda create -n rabbitmq python=3.13

conda activate rabbitmq

cd /home/vash/rabbitmq-hello-world
```

### Instalação do RabbitMQ

```bash
sudo dnf install rabbitmq-server

sudo systemctl start rabbitmq-server
sudo systemctl enable rabbitmq-server

sudo systemctl status rabbitmq-server
```

### Instalação do Cliente Python

```bash
conda install -c conda-forge pika


Criar os arquivos `send.py` e `receive.py` com o código do tutorial básico disponibilizado pelo próprio RabbitMQ.


Para parar as conexões quando necessário:

```bash
sudo systemctl stop rabbitmq-server

sudo systemctl start rabbitmq-server
```
## 🔧 Como Executar

### 1. Ativar Ambiente e Verificar RabbitMQ

```bash
conda activate rabbitmq

sudo systemctl status rabbitmq-server
```

### 2. Iniciar o Consumidor (Receiver)

```bash
python receive.py
```

**Saída esperada:**
```
[*] Waiting for messages. To exit press CTRL+C
```

### 3. Enviar Mensagens (Producer)

Em outro terminal:

```bash
conda activate rabbitmq

python send.py
```

**Saída esperada:**
```
[x] Sent 'Hello World!'
```

### 4. Verificar Recebimento

No terminal do receiver, você verá:
```
[*] Waiting for messages. To exit press CTRL+C
[x] Received b'Hello World!'
```

## 📊 Resultado Esperado

1. **Producer (send.py):**
   - Conecta ao RabbitMQ
   - Declara uma fila chamada 'hello'
   - Envia mensagem "Hello World!"
   - Fecha a conexão

2. **Consumer (receive.py):**
   - Conecta ao RabbitMQ
   - Declara a mesma fila 'hello'
   - Fica aguardando mensagens
   - Processa mensagens recebidas
   - Imprime mensagens no console

## 🔍 Como Funciona

### Conceitos Básicos:

- **Producer**: Aplicação que envia mensagens
- **Queue**: Buffer que armazena mensagens
- **Consumer**: Aplicação que recebe mensagens
- **Connection**: Conexão TCP com RabbitMQ
- **Channel**: Conexão virtual dentro de uma Connection

### Fluxo de Mensagens:

```
Producer → Queue → Consumer
```
