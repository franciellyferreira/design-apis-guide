# Guia para Design de APIs

## HTTP: Status Code

Como citamos no tópico de [introdução](introduction.md#rest) as APIs REST operaram sobre o protocolo HTTP. A transferência de dados entre cliente e servidor roda em cima do protocoloco HTTP, onde o cliente solicita ao final de cada requisição o código de estado da requisição, este código é composto por três números. [^1]

### 1xx - Informativo

Código | Nome | Descrição
--- | --- | ---
100 | Continue | Resposta provisória indica que tudo ocorreu bem até agora e que o cliente deve continuar com a requisição ou ignorar se já concluiu o que gostaria [^2].

### 2xx - Sucesso

### 3xx - Redirecionamento

### 4xx - Erro do cliente

### 5xx - Erro do servidor

<br><br>

Referências:

[^1]: [HostGator - O que significa cada código HTTP?](https://www.hostgator.com.br/guias/http-status-code-como-resolver/#h-o-que-significa-cada-c-digo-http)
[^2]: [Mozilla - Código de status de resposta - Informativas](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status#respostas_informativas)
