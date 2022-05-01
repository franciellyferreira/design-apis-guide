# Guia de Design de APIs

## Documentação

Uma API pode ser usada sem uma boa documentação? Com certeza, embora seja por meio das práticas recomendadas da documentação da API que os desenvolvedores experimentam pela primeira vez uma API e conhecem sua funcionalidade.[^1]

Portanto, além das documentações de APIs orientarem os trabalhos dos usuários estão em contato direto com elas, elas também são utilizadas para decisões de negócio, ou seja, através das documentações das APIS é possível explorar quais produtos e serviços existem no portifólio da empresa, por pessoas como CTOs and Product Owners e tomar diversas decisões. [^2]

### O que precisa ter na minha documentação?

- **Autenticação**: Devem ser fornecidas as informações sobre como utilizar o esquema de autenticação. A maioria das APIs possui sistema de autenticação, em que os consumidores precisam se autenticar para obter acesso. Certifique-se de realizar uma boa documentação dessa sessão para que os usuários consigam se autenticar. [^2]

- **Recursos**: Liste todos os recursos e procure entender qual a melhor forma dos consumires se integrarem com os recursos que você oferece e montar exemplos de uso dos seus recursos. [^2]

- **Requisições e Respostas**: Forneça na documentação o ciclo de requisição e resposta que o recurso merece. Ter muita informação disponível para o consumidor final nunca é um problema, especialmente quando eles estão tentando integrar seus serviços, então descreva os ciclos dos recursos em detalhes. Documente cada chamada que sua API pode oferecer, com contexto em torno dos parâmetros e respostas. [^2]

- **[Tratamento de Erros](error-handling.md)**: Não se esqueça de criar um padrão de tratamento de erros e documenta-lo em sua API, dessa forma você ajuda o consumidor a ter uma melhor experiência e mais segurança.


### Tipos de documentação

Existem diversos de tipos de produtos para realizar a documentação de APIs atualmente, abaixo vamos falar sobre alguns deles:

### Documento no Google Drive

Os [documentos do Google](https://www.google.com/intl/pt-BR/docs/about/), são telas em branco, para que sejam criados diversos tipos de documentos diferentes. Caso você queira pode começar a desenhar os contratos dos recursos da sua API, corpos da requisição e resposta, códigos de estado, etc. Mesmo não sendo automatizado ou ideal, ele pode ser compartilhado com os membros do time, para que todos possam interagir com o documento,  até chegar em um padrão de documento que agrade a todos. Após a documentação ser validada, o time pode começar a usar uma ferramenta mais automatizada, o mais importante sempre é que a documentação seja bem completa.

### API Console

### API Blueprint

### RAML

### OpenAPI

<br><br>


Referências:

[^1]: [API Documentation Guide and Best Practices](https://stoplight.io/api-documentation-guide)
[^2]: [Best Practices in API Documentation](https://swagger.io/blog/api-documentation/best-practices-in-api-documentation/)
