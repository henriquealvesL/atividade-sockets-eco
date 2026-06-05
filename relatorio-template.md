# Relatório — Atividade Prática: Sockets TCP

**Disciplina:** Sistemas Distribuídos
**Dupla:** Henrique Alves
**Data:** 05/06/2026

---

## Nível 1 — Inspecionar o código

### 1.1 Servidor (`servidor.py`)

Descreva com suas palavras o que cada chamada abaixo faz e por que ela
é necessária:

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | Cria um socket para comunicação. |
| `servidor_socket.bind((HOST, PORTA))` | Define uma porta para o Socket |
| `servidor_socket.listen(5)` | Coloca o socket para receber conexões, aceitando até 5. |
| `servidor_socket.accept()` | Aceita uma conexão de cliente. |
| `conn.recv(TAMANHO_BUFFER)` | Recebe dados pelo socket. |
| `conn.sendall(resposta.encode("utf-8"))` | Envia uma resposta ao cliente. |
| `conn.close()` | Fecha a conexão com o cliente. |

### 1.2 Cliente (`cliente.py`)

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | Cria um socket para comunicação. |
| `cliente_socket.connect((HOST_SERVIDOR, PORTA_SERVIDOR))` | Conecta o socket ao servidor. |
| `cliente_socket.sendall(mensagem.encode("utf-8"))` | Envia uma mensagem ao servidor. |
| `cliente_socket.recv(TAMANHO_BUFFER)` | Recebe dados do servidor. |

### 1.3 Rede e contêineres

Por que o cliente usa o hostname `"servidor"` em vez de `"localhost"`
para se conectar? O que aconteceria se usasse `"localhost"`?

> _Resposta:_ Porque dentro do contêiner docker, é possível acessar outros contêineres usando o nome do serviço definido no `docker-compose.yml`. Se usasse `"localhost"`, o cliente tentaria se conectar a si mesmo, e não ao servidor.

---

## Nível 2 — Modificar o servidor

Descreva as mudanças que você fez no `servidor.py` para:

1. Devolver a mensagem **em maiúsculas**:

   > _O que foi alterado e por quê:_ Adicionei o método `.upper()` à mensagem antes de enviá-la de volta ao cliente.

2. Exibir no log o **contador de mensagens recebidas** acumulado:

   > _O que foi alterado e por quê:_ Usei a variável `total_mensagens` para incrementar em 1 a cada mensagem recebida e exibir o total no log ao encerrar.

Após a modificação, você precisou rodar `docker compose up --build`.
Por que o `--build` é necessário aqui?

> _Resposta:_ O `--build` é necessário para reconstruir a imagem do servidor com as mudanças feitas no código. Sem ele, o Docker usaria a imagem antiga, e as alterações não teriam efeito.

---

## Observações livres

Anote aqui qualquer comportamento inesperado que observaram, erros que
apareceram e como resolveram, ou dúvidas que ainda têm:

>

---

## Dúvida para a próxima aula

Escreva **uma pergunta** que surgiu durante a atividade e que vocês
gostariam de ver respondida na aula seguinte:

>
