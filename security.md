# Guia para Design de APIs

## Segurança

A segurança de uma API deve ser pensada desde a concepção do projeto e existem muitas maneiras de proteger uma API, por exemplo, utilizando autenticação básica, OAuth, entre outros, essa aunteticação/autorização não deve ser sem estado e não depender de sessão. Além disso, cada requisição de uma API deve possuir algum tipo de credencial de autenticação que deve ser validada no servidor de cada solicitação [^1].

Além da autenticação existem outros fatores importantes a serem considerados, como:

### Sempre utilize TLS

Toda API deve utilizar TLS (Transport Layer Security). O TLS protege com criptografa as informações que sua API traféga. Sem o uso do TLS, terceiros pode interceptar e ler informações confidenciais em trânsito, como credenciais de API e dados privados. Você pode conhecer o TLS pelo nome de seu predecessor, SSL. Você saberá que um site tem TLS ativado quando seu URL começa com `https://` em vez de `http://`. [^2]


### Criptografe dados sensíveis

A criptografia é um elemento chave do protocolo de segurança, portanto os desenvolvedores devem garantir que dados sensíveis sejam criptografados na fonte de dados. [^3]


### Identificar vulnerabilidades

Um dos pontos importantes para fortalecer suas APIs é descobrir as vulnerabilidades, para isso realize testes rigorosos. Você deve tentar descobrir vulnerabilidades na fase inicial de desenvolvimento, para que possa corrigi-las de maneira rápida e fácil. [^3]


### Use uma autenticação forte

No mundo digital, a autenticação é o processo de verificação da identidade de um usuário. Essencialmente, retira a máscara de qualquer usuário que queira ver suas informações. Portanto, você deve sempre saber quem está chamando suas APIs. Existem vários métodos para autenticar:

- Autenticação básica HTTP em que um usuário precisa fornecer ID de usuário e senha
- Chave de API em que um usuário precisa de um identificador exclusivo configurado para cada API e conhecido pelo API Gateway
- Um token que é gerado por um servidor de provedor de identidade (IdP). OAuth 2 é o protocolo mais popular que oferece suporte a esse método.

No mínimo, você deve usar uma chave de API (chave assimétrica) ou autenticação de acesso básico (usuário/senha) para aumentar a dificuldade de invadir seu sistema. Mas você deve considerar o uso do OAuth 2 como seu protocolo de escolha para uma segurança robusta de suas APIs. [^4]


### Princípios de Design para segurança de APIs

A segurança de uma aplicação não se restringe apenas a autenticação e autorização. No artigo "The Protection of Information in Computer Systems"[^3], Jerome Saltzer e Michael Schroeder apresentam oito princípios de design para proteção de informação em sistema de software, esses princípios podem ser utilizados para diversos típicos de aplicação, não se restringindo apenas as APIs.

- **Privilégio mínimo**: uma entidade deve ter apenas o conjunto necessário de permissões para executar as ações para as quais está autorizada e nada mais. As permissões podem ser adicionadas conforme necessário e devem ser revogadas quando não estiverem mais em uso.

- **Padrões à prova de falhas**: O nível de acesso padrão de um usuário a qualquer recurso no sistema deve ser "negado", a menos que tenha recebido uma "permissão" explicitamente.

- **A economia do mecanismo**: O projeto deve ser o mais simples possível. Todas as interfaces de componentes e as interações entre eles devem ser simples o suficiente para serem entendidas.

- **Mediação completa**: um sistema deve validar os direitos de acesso a todos os seus recursos para garantir que eles sejam permitidos e não devem depender da matriz de permissões em cache. Se o nível de acesso a um determinado recurso estiver sendo revogado, mas isso não for refletido na matriz de permissão, isso violaria a segurança.

- **Design aberto**: Este princípio destaca a importância de construir um sistema de maneira aberta – sem algoritmos secretos e confidenciais.

- **Separação de privilégios**: a concessão de permissões a uma entidade não deve ser puramente baseada em uma única condição, uma combinação de condições com base no tipo de recurso é uma ideia melhor.

- **Mecanismo menos comum**: diz respeito ao risco de compartilhamento de estado entre diferentes componentes. Se alguém pode corromper o estado compartilhado, pode corromper todos os outros componentes que dependem dele.

- **Aceitabilidade psicológica**: afirma que os mecanismos de segurança não devem tornar o recurso mais difícil de acessar do que se os mecanismos de segurança não estivessem presentes. Em suma, a segurança não deve piorar a experiência do usuário.

<br><br>

Referências

[^1]: [REST API Security Essentials](https://restfulapi.net/security-essentials/)
[^2]: [Best practices for REST API security: Authentication and authorization](https://stackoverflow.blog/2021/10/06/best-practices-for-authentication-and-authorization-for-rest-apis/)
[^3]: [Encrypt Your Data](https://brightsec.com/blog/api-security-best-practices/)
[^4]: [Securing APIs: 10 Ways to Keep Your Data and Infrastructure Safe](https://www.f5.com/labs/articles/education/securing-apis--10-best-practices-for-keeping-your-data-and-infra)
[^5]: [The Protection of Information in Computer Systems - BASIC PRINCIPLES OF INFORMATION PROTECTION](http://web.mit.edu/Saltzer/www/publications/protection/Basic.html)
