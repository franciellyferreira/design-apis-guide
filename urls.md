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

<br>

**E as ações que não se encaixam no mundo CRUD?**

É neste ponto, onde muitas coisas acabam ficando confusas no planejamento da API, para isso existe várias abordagens:

- Reestruturar a ação para que se pareça com o campo de um recurso, isso funciona se a ação não receber parâmetros, por exemplo, ação de ativação pode ser mapeada para um campo booleano _activated_ e atualizada utilizando um PATCH para o recurso.
- Outra possibilidade é tratar como um sub-recurso com os princípios REST, por exemplo, `PUT /events/12/favorite` e `DELETE /events/12/favorite` [^2].
- Contudo em alguns casos, não é possível mapear a ação para uma estrutura REST sensata, por exemplo, fazer uma pesquisa em diversos recursos, neste caso utilizar a URL `/search` faria mais sentido, mesmo não sendo um recurso. Recomeda-se em casos como esse apostar em uma boa documentação e deixar claro para os consumidores da API essa escolha, para evitar confusão.

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico Parâmetros](parameters.md)

<br><br>

Referências:

[^1]: [Best Practices for Designing a Pragmatic RESTful API - Use RESTful URLs and actions](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api#restful)
[^2]: [Github - Docs - Star a Gist](https://docs.github.com/pt/rest/reference/gists#star-a-gist)
