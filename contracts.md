# Guia para Design de APIs

## Contratos

O que chamados de contrato é a documentação da API, normalmente criada pelos desenvolvedores. Neste documento constam as especificações da sua API como [verbo](http-verbs.md), [URLs](urls.md), [parâmetros](parameters.md), respostas, formatos, etc, tudo que a equipe de desenvolvimento acha relevante ser documentado. [^1]

O contrato é definido pelos provedores de serviços e são criados destinados aos consumidores, que podem ser empresas, desenvolvedores e departamentos internos, que utilizarão a API.

### Exemplos

Vamos considerar o cenário em que teremos uma aplicação que exibirá a discografia de diversos artistas, neste caso pensou-se na criação de uma aplicação front-end que consumirá uma API responsável pelo back-end. Utilizando a metodologia [API First ou Desing First](desing-firts.md), optou-se por pensar e definir os contratos da API antes de iniciar o seu desenvolvimento. Segue abaixo alguns cenários para manipular o cadastro dos artistas, álbuns e canções:


### Artista

### POST /artists

Criar cadastro do artista

*Corpo da requisição*
```
{
    "name": "David Bowie",
    "image": "url-example-image-url"
}
```

*Corpo da resposta*
```
{
    "id": 1,
    "name": "David Bowie",
    "image": "url-example-image-url"
}
```

*Códigos de status de resposta*

- 201: Criado
- 400: Requisição inválida
- 500: Erro interno no servidor

### GET /artists/1

Buscar artista {1}

*Corpo da resposta*

```
{
    "name": "David Bowie",
    "image": "url-example-image-url"
}
```

*Códigos de status de resposta*

- 200: Sucesso
- 404: Não encontrado
- 500: Erro interno no servidor

### Álbum

### POST /artists/1/albums

Criar cadastro de álbum no artista {1}

*Corpo da requisição*
```
{
    "name": "Heroes",
    "year": 1977,
    "image": "url-example-image-url"
}
```

*Corpo da resposta*
```
{
    "id": 1,
    "name": "Heroes",
    "year": 1977,
    "image": "url-example-image-url"
}
```

*Códigos de status de resposta*

- 201: Criado
- 400: Requisição inválida
- 500: Erro interno no servidor

### GET /artists/1/albums

Listar todos os álbuns do artista {1}

*Corpo da resposta*
```
{
    "name": "David Bowie",
    "image": "url-example-image-url",
    "albums": [
        {
            "id": 1,
            "name": "Heroes",
            "year": 1977,
            "image": "url-example-image-url"
        },
        ...
    ]
}
```

*Códigos de status de resposta*

- 200: Sucesso
- 404: Não encontrado
- 500: Erro interno no servidor

### Canção

### POST /artists/1/albums/1/songs

Criar cadastro de canção no álbum {1} do artista {1}

*Corpo da requisição*
```
{
    "name": "Beauty and the Beast",
    "time": "03:36"
}
```

*Corpo da resposta*
```
{
    "id": 1,
    "name": "Beauty and the Beast",
    "time": "03:36"
}
```

*Códigos de status de resposta*

- 201: Criado
- 400: Requisição inválida
- 500: Erro interno no servidor

### GET /artists/1/albums/1/songs

Lista todas os canções do álbum {1} do artista {1}

**Corpo da resposta**
```
{
    "name": "Heroes",
    "year": 1977,
    "image": "url-example-image-url",
    "songs": [
        {
            "id": 1,
            "name": "Beauty and the Beast",
            "time": "03:36"
        },
        ...
    ]
}
```

*Códigos de status de resposta*

- 200: Sucesso
- 404: Não encontrado
- 500: Erro interno no servidor


<br>

> **Informativo**: no exemplo acima, optamos pela troca de mensagem no formato json, para facilitar e validar se o payload criado está no formato correto você pode utilizar a ferramenta [JSON Formatter e Validator](https://jsonformatter.curiousconcept.com/).


## Tratamento de Erros

Na construção de APIs costuma-se utilizar para o tratamento de erros e exceções na resposta das requisições os códigos de estado da família [4xx](#http-status-code.md#4xx---erro-do-cliente) que são os erros que acontecem no cliente e [5xx](#http-status-code.md#5xx---erro-do-servidor) os que acontecem no servidor. Além do código de estado, pode ser enviado juntamente na resposta um corpo de resposta, onde pode conter mais informações sobre a exceção.

Assim como é feito o planejamento dos contratos da API, recomenda-se que sejam padronizadas o retorno de exceções das aplicações, para facilitar o gerenciamento pelos consumidores e também para que o usuário tenha visão sobre os erros e exceções que são lançados. Recomenda-se que o departamento de desenvolvimento ou arquitetura faça a definição do padrão de retorno, seguem exemplos abaixo: 


### Exemplo 1 - Recurso não encontrado

Buscar artista {2}

*Requisição: GET /artists/2*

*Corpo da resposta*

```
{
    "code": "NOT_FOUND",
    "message": "Artist not found."
}
```

*Códigos de status de resposta*

**404: Não encontrado**

### Exemplo 2 - Não autorizado

Buscar álbum {2} do artista {1}

*Requisição: GET /artists/1/albums/2*

*Corpo da resposta*
```
{
    "code": "UNAUTHORIZED",
    "message": "Request not unauthorized."
}
```

*Códigos de status de resposta*

**401: Unauthorized**

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico Versionamento](versioning.md)

<br><br>

Referências:

[^1]: [Development: What is an API Contract?](https://lazaroibanez.com/development-what-is-an-api-contract-683ced58e06f)
