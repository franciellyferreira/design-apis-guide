# Guia para Design de APIs

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
