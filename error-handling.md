# Guia para Design de APIs

## Tratamento de Erros

O tratamento de error e exceções são extremamente úteis. Os códigos de erro no estágio de resposta de uma API são a maneira fundamental pela qual um desenvolvedor pode comunicar uma falha a um usuário. Essa resposta, após a requisição, é a comunicação direta entre o cliente e a API, sendo o primeiro e mais importante passo não apenas para notificar o usuário sobre uma falha, mas também para iniciar o processo de resolução de erros. [^1]
 
Na construção de APIs costuma-se utilizar para o tratamento de erros e exceções na resposta das requisições os códigos de estado da família [4xx](#http-status-code.md#4xx---erro-do-cliente) que são os erros que acontecem no cliente e [5xx](#http-status-code.md#5xx---erro-do-servidor) os que acontecem no servidor. 

Porém os códigos de estado de erro excessivamente opacos são extremamente inúteis. Vamos imaginar que você está tentando fazer uma solicitação GET para uma API que lida com inventário de música digital. Você enviou sua solicitação para uma API que você sabe que aceita rotineiramente seu tráfego, você passou as credenciais corretas de autorização e autenticação e, até onde você sabe, o servidor está pronto para responder. Você envia seus dados e recebe o seguinte código de erro – 400 Bad Request. Sem dados adicionais, sem informações adicionais, o que isso realmente diz a você? [^1]

Assim como é feito o planejamento dos contratos da API, recomenda-se que sejam padronizadas o retorno de exceções das aplicações, para facilitar o gerenciamento pelos consumidores e também para que o usuário tenha visão sobre os erros e exceções que são lançados. Recomenda-se que o departamento de desenvolvimento ou arquitetura faça a definição do padrão de retorno utilizando alguns elementos:

- Código de estado de erro HTTP
- Código interno ou outro que possa ser identificado pela equipe
- Mensagem legível

Segue abaixo alguns exemplos, de como pode ser feito o tratamento de erros na construção de APIs.

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

[^1]: [Best Practices for API Error Handling](https://nordicapis.com/best-practices-api-error-handling)
