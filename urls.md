# Guia para Design de APIs

## URLs

Conforme citado no tópico de [verbos HTTP](http-verbs.md), as URLS fazem parte dos princípios da construção de APIs REST. As URLs são responsáveis por referenciar a identificação do recurso dentro da sua API. Recomenda-se seguir alguns padrão para o design dessas URLs:

1) As URLS devem ser substantivos e não verbos.
2) Use substantivos no plural apenas para consistência (não utilizar substantivos no singular).
3) Se um recurso possui um nome composto utilize _kebab-case_.
4) Dê preferência para URLs em letras minúsculas.
5) Use os [verbos HTTP](http-verbs.md) (HTTP/1.1) para operar estes recursos.
6) Use códigos de status HTTP para representar o resultado das operações nos recursos, por exemplo: 200, 201, 404, 500, etc.

<br>

**Exemplo - Tickets** [^1]

Verbo HTTP | URL | Ação
--- | --- | ---
GET | /ingressos | Recupera uma lista de tickets
GET | /tickets/12 | Recupera um ticket específico
POST | /tickets | Cria um novo ticket
PUT | /tickets/12 | Atualiza o ticket #12
PATCH | /tickets/12 | Atualiza parcialmente o ticket #12
DELETE | /tickets/12 | Exclui o ticket #12

<br>

**Exemplo - Tickets e Messages (Relacionamento)** [^1]

Verbo HTTP | URL | Ação
--- | --- | ---
GET | /tickets/12/messages | Recupera a lista de mensagens para o ticket #12
GET | /tickets/12/messages/5 | Recupera a mensagem #5 para o ticket #12
POST | /tickets/12/messages | Cria uma nova mensagem no ticket #12
PUT | /tickets/12/messages/5 | Atualiza a mensagem #5 para o ticket #12
PATCH | /tickets/12/messages/5 | Atualiza parcialmente a mensagem #5 para o ticket #12
DELETE | /tickets/12/messages/5 | Exclui a mensagem #5 do ticket #12

<br><br>

Referências:

[^1]: [Best Practices for Designing a Pragmatic RESTful API - Use RESTful URLs and actions](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api#restful)
