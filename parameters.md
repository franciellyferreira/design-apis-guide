# Guia para Design de APIs

## Parâmetros [^1]

Para realizar pesquisas nos recursos utilize o [verbo HTTP GET](http-verbs.md#get) e utilize os parâmetros como filtros.

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

## Pesquisa avançada [^1]

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

Utiliza-se para paginar os recursos retornados e evitar que o volume alto de registros sobrecarregue a busca causando timeout, portanto recomenda-se que os serviços que retornam uma grande quantidade de recursos sejam construídos com paginação. A paginação possui dois parâmetros que devem ser implementados: página (page) e resultados por página (size). [^3]


Busca usuários e retorna a página 3 com 20 registros

```
GET /users?page=3&size=20
```

Os parâmetros podem mudar de acordo com a implementação adotada pela sua API, normalmente encontra-se parâmetros de paginação nas seguintes nomenclaturas [^4]:
- _page and size_
- _offset and limit_
- _page and pagesize_
- entre outros. 

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico HTTP: Status Code](http-status-code.md)

<br><br>

Referências:

[^1]: [API RESTful - Boas práticas](https://www.brunobrito.net.br/api-restful-boas-praticas/)
[^2]: [REST API - Sorting](https://www.taniarascia.com/rest-api-sorting-filtering-pagination/#sorting)
[^3]: [REST API - Pagination](https://www.taniarascia.com/rest-api-sorting-filtering-pagination/#pagination)
[^4]: [Sensedia - Boas práticas: Paginação e filtros](https://br.sensedia.com/post/api-pagination-and-filters)
