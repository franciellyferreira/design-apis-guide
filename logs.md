# Guia para Design de APIs

## Logs

Os logs podem ser utilizados para realizar monitoramento e rastreamento, por exemplo, em uma caso onde o servidor está retornando erro 500, porém sem muitas informações no retorno da API, para ajudar nesse rastreamento pode ser feita uma auditoria no processo que está rodando em produção utilizando os logs.

### O que deve ser considerado?

- **Não registrar tudo**: Cada log leva tempo para ser registrado, portanto os logs precisam ser planejados para não atrapalharem o desempenho das aplicações, ou seja, quanto menos logs melhor.

- **Logar exceções/falhas**: Problemas podem acontecer e devido a isso o ideal é que as exceções ou falhas sejam logadas, isso vai facilitar a auditoria e o debug do código fonte.

- **Tipo de log**: Existem diversos tipos de logs `info`, `warning`, `error`, entre outros. Utilizar corretamente os tipos de logs é bem importante para classificação.

- **Decisões e cenários importantes**: Deve ser feito logs completos para decisões importantes de negócio e cenário críticos que podem ser necessários monitorar ao logo do tempo.

- **APIs externas**: Se sua API utilizar a integração com uma API externa, recomenda-se logar o retorno, códigos de estado http, exceções, etc, para que sejam criados monitoramentos para garantir o debug dessa dependência.

- **Banco de dados**: Sempre quando exceções de bancos de dados, os desenvolvedores sofrem muito para encontrar o problema, já que existem muitos contexto possíveis, por isso recomenda-se que exceções de bancos de dados sejam logadas, para facilitar o trabalho dos desenvolvedores.

### Gerenciador de logs

Atualmente com a quantidade 


<br><br>

Referências:

[^1]: [Design application logs](https://prashant-prasannakumaran.co.in/rest-api/logging-best-practices/)
