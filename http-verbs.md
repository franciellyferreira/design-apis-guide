# Guia para Design de APIs

## HTTP: Verbos

<br>

> A motivação para o desenvolvimento do REST foi criar um modelo de arquitetura de como a web deveria funcionar. - Roy Fielding [^1]

<br>

Entre os príncípios para a construção de APIs REST, está a criação de recursos que tenham uma URI única que será usada para identifica-los. Esses recursos podem ser manipulados utilizando requisições HTTP [^2], essas requisições utilizam os famosos Verbos HTTP.

Cada um deles implementa uma semântica diferente, mas alguns recursos são compartilhados por um grupo deles, como por exemplo, qualquer método de requisição pode ser do tipo _safe_, _idempotent_ ou _cacheable_. [^3]

**_Safe_**: um verbo HTTP é seguro se ele não altera o estado do recurso, ou seja, um verbo seguro leva a uma operação de somente leitura. Todos os métodos seguros também são idempotentes, porém nem todos idempotentes são seguros. [^4]

**_Idempotent_**: um verbo HTTP é idempotente se uma requisição idêntica pode ser feita uma ou mais vezes em sequência, com o mesmo efeito enquanto deixa o recurso no mesmo estado. [^5]

**_Cacheable_**: um verbo HTTP armazenável em cache é uma resposta que pode ser cacheada. Nem todas as respostas HTTP podem ser cacheadas, para esses casos permite-se a indicação no cabeçalho da requisição. [^6]

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

### GET

Requisições utilizando verbos GET solicita um recurso específicado, além disso, essas requisições só devem recuperar dados. [^7]
- Requisição não tem corpo
- Resposta bem-sucedida tem corpo

### HEAD

O verbo HEAD solicita os cabeçalhos retornados de um recurso específico que foi requisitado por um verbo HTTP. Este tipo de solicitação pode ser realizada antes de baixar um recurso muito grande para economizar largura de banda. [^8]
- Requisição não tem um corpo
- Resposta bem sucedida não tem um corpo

### OPTIONS

O verbo OPTIONS é utilizado para que um cliente possa descobrir quais as opções de requisição são permitidas para um determinado recurso do servidor.[^9]
- Requisição não tem um corpo
- Resposta bem sucedida não tem um corpo

### TRACE

O verbo TRACE é utilizado para fazer debug para o recurso de destino, ele realiza um teste de loopback enviando uma mensagem por todo o caminho até o recurso alvo no qual foi destinado. O destinatário deve responder a mensagem, removendo alguns campos e devolvendo HTTP Status Code 200 e o cabeçalho necessário. [^10]
- Requisição não tem um corpo
- Resposta bem sucedida não tem um corpo

### PUT

O verbo PUT é utilizado para atualizar um recurso ou substitui a representação do recurso com novos dados (atualizada todas as informações). [^11]
- Requisição tem um corpo
- Resposta bem sucedida não tem um corpo

### DELETE

O verbo DELETE é utilizado para remover um recurso específico. [^12]
- Requisição talvez tenha corpo
- Resposta bem sucedida talvez tenha corpo

### POST

O verbo POST é utilizado para enviar os dados para ser criado um novo recurso. O tipo de corpo da requisição deve ser especificado no cabeçalho _Content-Type_, por exemplo, `Content-Type: application/json`.
A diferença entre o PUT e o POST é que o PUT é idempotente, ou seja, chama-lo diversas vezes vai ter o mesmo resultado, enquanto chamar o POST diversas vezes pode ocasionar a criação de diversos recursos, como por exemplo, criar várias ordens de pagamento. [^13]
- Requisição tem corpo
- Resposta bem sucedida tem corpo

### PATCH

O verbo PATCH é utilizado para realizar atualizações parciais em um recurso. [^14]
- Requisição tem corpo
- Resposta bem sucedida tem corpo

### CONNECT

O verbo CONNECT começa a comunicação bidirecional com o recurso solicitado. Ele pode ser usado para abrir um túnel. [^15]
- Requisição tem corpo
- Resposta bem sucedida tem corpo

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico URLs](urls.md)

<br><br>

Referências:

[^1]: [Roy Fielding - CHAPTER 6 - 6.1 Standardizing the Web](https://www.ics.uci.edu/~fielding/pubs/dissertation/evaluation.htm)
[^2]: [API RESTful - Boas práticas](https://www.brunobrito.net.br/api-restful-boas-praticas/)
[^3]: [Mozilla - Métodos de requisição HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods)
[^4]: [Mozilla - Glossário - Seguro](https://developer.mozilla.org/pt-BR/docs/Glossary/safe)
[^5]: [Mozilla - Glossário - Idempotente](https://developer.mozilla.org/pt-BR/docs/Glossary/Idempotent)
[^6]: [Mozilla - Glossário - Cacheable](https://developer.mozilla.org/en-US/docs/Glossary/cacheable)
[^7]: [Mozilla - GET](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/GET)
[^8]: [Mozzila - HEAD](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/HEAD)
[^9]: [Mozzila - OPTIONS](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/OPTIONS)
[^10]: [Mozzila - TRACE](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/TRACE)
[^11]: [Mozilla - PUT](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/PUT)
[^12]: [Mozzila - DELETE](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/DELETE)
[^13]: [Mozilla - POST](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/POST)
[^14]: [Mozzila - PATCH](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/PATCH)
[^15]: [Mozzila - CONNECT](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/CONNECT)
