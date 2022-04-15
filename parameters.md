# Guia para Design de APIs

## Parâmetros

Para relizar pesquisas nos recursos utilize o [verbo HTTP GET](http-verbs.md#get) e utilize os parâmetros como filtros.[^1]

Busca todos os usuários

```
GET /users
```

Busca o usuário único pelo id

```
GET /users/{id}
```

Busca todos os usuário ativos e que tem mais que 30 anos de idade

```
GET /users?status=active&older_than=30
```

## Pesquisa avançada

Em alguns cenários pode ser que a pesquisa se torne muito complexa, com muitos parâmetros, neste caso recomenda-se utilizar `alias`.

Buscar todos os usuários ativos, que moram no Brasil e tem idade entre 18 e 35 anos.

```
GET /users?status=active&lives_in=brazil&older_than=18&younger_than=35
```

Essa consulta pode ser traduzida utilizando `alias` para:

```
GET /users/young-brazilians
```

## Ordenação

## Paginação

<br><br>

Referências:

[^1]: [API RESTful - Boas práticas](https://www.brunobrito.net.br/api-restful-boas-praticas/)
