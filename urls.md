# Guia para Design de APIs

## URLs

Conforme citado no tópico de [verbos HTTP](http-verbs.md), as URLS fazem parte dos princípios da construção de APIs REST. As URLs são responsáveis por referenciar a identificação do recurso dentro da sua API. Recomenda-se seguir alguns padrão para o design dessas URLs:

- As URLS devem ser substantivos e não verbos.
- Use substantivos no plural apenas para consistência (não utilizar substantivos no singular).
- Se um recurso possui um nome composto utilize _kebab-case_.
- Dê preferência para URLs em letras minúsculas.
- Use os [verbos HTTP](http-verbs.md) (HTTP/1.1) para operar estes recursos.
- Use códigos de status HTTP para representar o resultado das operações nos recursos, por exemplo: 200, 201, 404, 500, etc.

<br>

**Exemplo - Events** [^1]

Verbo | URL | Ação
--- | --- | ---
GET | /events | Recupera uma lista de eventos
GET | /events/12 | Recupera um evento específico
POST | /events | Cria um novo evento
PUT | /events/12 | Atualiza o evento #12
PATCH | /events/12 | Atualiza parcialmente o evento #12
DELETE | /events/12 | Exclui o evento #12

<br>

**Exemplo - Events e Tickets (Relacionamento)** [^1]

Verbo | URL | Ação
--- | --- | ---
GET | /events/12/tickets | Recupera a lista de ingressos para o evento #12
GET | /events/12/tickets/5 | Recupera o ingresso #5 para o evento #12
POST | /events/12/tickets | Cria um novo ingresso no evento #12
PUT | /events/12/tickets/5 | Atualiza o ingresso #5 para o evento #12
PATCH | /events/12/tickets/5 | Atualiza parcialmente o ingresso #5 para o evento #12
DELETE | /events/12/tickets/5 | Exclui o ingresso #5 do evento #12

<br><br>

Referências:

[^1]: [Best Practices for Designing a Pragmatic RESTful API - Use RESTful URLs and actions](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api#restful)
