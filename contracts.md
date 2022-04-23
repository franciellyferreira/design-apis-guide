# Guia para Design de APIs

## Contratos

O que chamados de contrato é a documentação da API, normalmente criada pelos desenvolvedores. Neste documento constam as especificações da sua API como [verbo](http-verbs.md), [URLs](urls.md), [parâmetros](parameters.md), respostas, formatos, etc, tudo que a equipe de desenvolvimento acha relevante ser documentado. [^1]

O contrato é definido pelos provedores de serviços e são criados destinados aos consumidores, que podem ser empresas, desenvolvedores e departamentos internos, que utilizarão a API.

### Exemplo

Vamos considerar o cenário em que teremos uma aplicação que exibirá a discografia de diversos artistas, neste caso pensou-se na criação de uma aplicação front-end e uma API responsável pelo back-end. Utilizando a metodologia [API First ou Desing First](desing-firts.md), optou-se por pensar e definir os contratos antes de iniciar o desenvolvimento da API. Segue abaixo alguns cenários para manipular o cadastro dos artistas, álbuns e músicas.

**Criar cadastro de artista**

- Verbo HTTP: POST
- URL: /artists
- Formato: json
- Corpo da requisição:
```
{
  "name": "David Bowie",
  "image: "url-example-image-url"
}
```
- Status Code HTTP da resposta: 201
- Corpo da resposta:
```
{
  "id": 1,
  "name": "David Bowie",
  "image: "url-example-image-url"
}
```

<details>
  <summary>POST - Criar cadastro de álbum</summary>
  <br>

  - Verbo HTTP: POST
  - URL: /artists/1/albums
  - Formato: json
  - Corpo da requisição:
  ```
  {
    "name": "Heroes",
    "year": 1977,
    "image": "url-example-image-url"
  }
  ```
  - Status Code HTTP da resposta: 201
  - Corpo da resposta:
  ```
  {
    "id": 1,
    "name": "Heroes",
    "year": 1977,
    "image": "url-example-image-url"
  }
  ```

</details>


<details>
  <summary>POST - Criar cadastro de música</summary>
  <br>

  - Verbo HTTP: POST
  - URL: /artists/1/albums/1/songs
  - Formato: json
  - Corpo da requisição:
  ```
  {
    "name": "Beauty and the Beast",
    "time": "03:36"
  }
  ```
  - Status Code HTTP da resposta: 201
  - Corpo da resposta:
  ```
  {
    "id": 1,
    "name": "Beauty and the Beast",
    "time": "03:36"
  }
  ```

</details>

<details>
  <summary>GET - Lista todos os álbuns do artista</summary>
  <br>

  - Verbo HTTP: GET
  - URL: /artists/1/albums
  - Formato: json
  - Status Code HTTP da resposta: 200
  - Corpo da resposta:
  ```
  {
    "name": "David Bowie",
    "image: "url-example-image-url",
    "albums": [
      {
        "id": 1,
        "name": "Heroes",
        "year": 1977,
        "image": "url-example-image-url",
        "songs": [
          {
            "id": 1,
            "name": "Beauty and the Beast",
            "time": "03:36"
          }
        ]
      }
    ]
  }
  ```

</details>


<br><br>

Referências:

[^1]: [Development: What is an API Contract?](https://lazaroibanez.com/development-what-is-an-api-contract-683ced58e06f)
