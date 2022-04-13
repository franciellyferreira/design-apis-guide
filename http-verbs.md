# Guia para Design de APIs

## Verbos HTTP

> A motivação para o desenvolvimento do REST foi criar um modelo de arquitetura de como a web deveria funcionar. - Roy Fielding [^1]

<br>

Entre os príncípios para a construção de APIs REST, esta a criação de recursos que tenham uma URI única que será usada para identifica-los. Esses recursos podem ser manipulados utilizando requisições HTTP [^2], essas requisições utilizam os famosos Verbos HTTP.

Cada um deles implementa uma semântica diferente, mas alguns recursos são compartilhados por um grupo deles, como por exemplo, qualquer método de requisição pode ser do tipo _safe_, _idempotent_ ou _cacheable_. [^3]

<br>

Verbo HTTP | Safe | Idempotent | Cacheable
--- | --- | --- | ---
GET | ✔️ | ✔️ | ✔️
HEAD | ✔️ | ✔️ | ✔️
OPTIONS | ✔️ | ✔️ | -
TRACE | - | ✔️ | -
PUT | - | ✔️ | -
DELETE | - | ✔️ | -
POST | - | - | *
PATCH | - | - | -
CONNECT | - | - | -

[*] _Somente se as informações de atualização estiverem incluídas_ [^3]

<br>

[^1]: [Roy Fielding - CHAPTER 6 - 6.1 Standardizing the Web](https://www.ics.uci.edu/~fielding/pubs/dissertation/evaluation.htm)
[^2]: [API RESTful - Boas práticas](https://www.brunobrito.net.br/api-restful-boas-praticas/)
[^3]: [Mozilla - Métodos de requisição HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods)
