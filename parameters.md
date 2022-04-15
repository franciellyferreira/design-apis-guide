# Guia para Design de APIs

## Parâmetros

Para realizar pesquisas nos recursos utilize o [verbo HTTP GET](http-verbs.md#get) e utilize os parâmetros como filtros. [^1]

Busca todos os usuários

```
GET /users
```

Busca o usuário único pelo id

```
GET /users/{id}
```

Busca todos os usuários ativos e que tem mais que 30 anos de idade

```
GET /users?status=active&older_than=30
```

Busca todos os usuários ativos e que moram no Brasil e na Argentina

```
GET /users?status=active&lives_in=[brazil,argentina]
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

## Ordenação [^2]

A ordenação permite ordenar os recursos por campo, nas ordens ascendente ou descendente

**Coluna única**

Se for necessário ordenar apenas um campo você pode indica-lo no parâmetro `sort_by` e o tipo de ordenação em `order`.

Busca usuários ordenados pelo primeiro nome em ordem ascendente (a -> z)

```
GET /users?sort_by=first_name&order=asc
```

**Múltiplas colunas**

Se for necessário ordernar diversos campos você pode separar por vírgula cada par _coluna:ordem_ e indica-lo no parâmetro `sort`.

Busca usuários ordernados pelo primeiro nome em ordem ascendente e pela idade em ordem descendente

```
GET /users?sort=first_name:asc,age:desc
```

## Paginação

<br><br>

Referências:

[^1]: [API RESTful - Boas práticas](https://www.brunobrito.net.br/api-restful-boas-praticas/)
[^2]: [REST API: Sorting, Filtering, and Pagination](https://www.taniarascia.com/rest-api-sorting-filtering-pagination/#sorting)
