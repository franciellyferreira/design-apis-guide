# Guia para Design de APIs

## Tratamento de Erros

Na construção de APIs costuma-se utilizar para o tratamento de erros e exceções na resposta das requisições os códigos de estado da família [4xx](#http-status-code.md#4xx---erro-do-cliente) que são os erros que acontecem no cliente e [5xx](#http-status-code.md#5xx---erro-do-servidor) os que acontecem no servidor. Além do código de estado, pode ser enviado juntamente na resposta um corpo de resposta, onde pode conter mais informações sobre a exceção.

Assim como é feito o planejamento dos contratos da API, recomenda-se que sejam padronizadas o retorno de exceções das aplicações, para facilitar o gerenciamento pelos consumidores e também para que o usuário tenha visão sobre os erros e exceções que são lançados. Recomenda-se que o departamento de desenvolvimento ou arquitetura faça a definição do padrão de retorno, seguem exemplos abaixo: 

### Exemplo 1 - Requisição ruim

Criar artista {2}

*Requisição POST /artists*

*Corpo da requisição*
```
{
    "name": "Billie Holiday"
}
```

*Corpo do retorno*:
```
{
    "code": "BAD_REQUEST",
    "message": "Request sintax invalid.",
    "details": [
        {
            "field": "image",
            "required": "Missing data for required field."
        }
    ]
}
```

*Códigos de status de resposta*

**400: Bad Request**

<br>

### Exemplo 2 - Recurso não autorizado

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

<br>

### Exemplo 3 - Recurso não encontrado

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

**404: Not Found**


### Exemplo 4 - Erro interno no servidor

Buscar artista {2}

*Requisição: GET /artists/2*

*Corpo da resposta*

```
{
    "code": "INTERNAL_SERVER_ERROR",
    "message": "An server error ocurred."
} 
```

*Códigos de status de resposta*

**500: Internal Server Error**

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico Versionamento](versioning.md)

<br><br>

Referências:

