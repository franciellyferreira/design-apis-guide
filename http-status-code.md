# Guia para Design de APIs

## HTTP: Status Code

Como citamos no tópico de [introdução](introduction.md#rest) as APIs REST operaram sobre o protocolo HTTP. A transferência de dados entre cliente e servidor roda em cima do protocoloco HTTP, onde o cliente solicita ao final de cada requisição o código de estado da requisição, este código é composto por três números [^1]. Segue alguns códigos de estado tirado de referência do Mozilla[^2].

### 1xx - Informativo

Código | Nome | Descrição
--- | --- | ---
100 | Continue | Essa resposta provisória indica que tudo ocorreu bem até agora e que o cliente deve continuar com a requisição ou ignorar se já concluiu o que gostaria.
101 | Switching Protocol | Esse código é enviado em resposta a um cabeçalho de solicitação Upgrade pelo cliente, e indica o protocolo a que o servidor está alternando.
102 | Processing | Este código indica que o servidor recebeu e está processando a requisição, mas nenhuma resposta está disponível ainda.
103 | Early Hints | Este código tem principalmente o objetivo de ser utilizado com o cabeçalho Link, indicando que o agente deve iniciar a pré-carregar recursos enquanto o servidor prepara uma resposta.

**100 Continue**
Essa resposta provisória indica que tudo ocorreu bem até agora e que o cliente deve continuar com a requisição ou ignorar se já concluiu o que gostaria.

**101 Switching Protocol**
Esse código é enviado em resposta a um cabeçalho de solicitação Upgrade pelo cliente, e indica o protocolo a que o servidor está alternando.

**102 Processing**
Este código indica que o servidor recebeu e está processando a requisição, mas nenhuma resposta está disponível ainda.

**103 Early Hints**
Este código tem principalmente o objetivo de ser utilizado com o cabeçalho Link, indicando que o agente deve iniciar a pré-carregar recursos enquanto o servidor prepara uma resposta.


### 2xx - Sucesso

200 OK

201 Created

202 Accepted

203 Non-Authoritative Information

204 No Content

205 Reset Content

206 Partial Content

207 Multi-Status

208 Multi-Status

209 IM Used


### 3xx - Redirecionamento




### 4xx - Erro do cliente


### 5xx - Erro do servidor


<br><br>

Referências:

[^1]: [HostGator - O que significa cada código HTTP?](https://www.hostgator.com.br/guias/http-status-code-como-resolver/#h-o-que-significa-cada-c-digo-http)
[^2]: [Mozilla - Código de status de resposta - Informativas](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
