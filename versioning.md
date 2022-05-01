# Guia para Design de APIs

## Versionamento


O versionamento de uma API é realizar o controle de versão dos endpoints oferecidos aos clientes consumidores. O versionamento normalmente é feito quanto há mudanças impactantes no [contrato](contracts.md) de um endpoint que podem mudar como esses serviços vão ser consumidos.

Já que o software evolui as APIs devem ser versionadas, um serviço disponibilizado hoje pode se tornar um sucesso e em poucos meses ser necessário uma nova re-organização em um contrato de um endpoint existente.

### Exemplo

Vamos analisar o seguinte cenário, onde uma empresa de convênio de saúde, possui uma API que prove endpoints para um site web em que é possível acompanhar financeiro, guia médico e exames.

Essa empresa, vendo outros concorrentes evoluindo os serviços prestados, começou a desenvolvedor uma aplicativo móvel, esse aplicativo que vai atender no momento o cliente com as funcionalidades já existentes e vai passar a atender os médicos que poderão acompanhar diariamente guias, consultas e faturamento.

Como seria necessário mudanças grandes para lançar esse novo produto, optou-se por lançar uma nova versão da API, pois existente já era antiga, não permitia muitas mudanças e sentiu-se a necessidade evoluir.

Dessa forma, criou-se uma versão nova que será consumida pelo aplicativo, enquanto a versão antiga ainda continuara sendo utilizada pelo site. Neste cenário pensando em manutenção, agora os desenvolvedores precisarão manter as duas versões, até que o site também migre para essa nova versão ou um site novo seja criado para atender a nova versão.

Vemos nesse caso que muitas vezes o versionamento tras benefícios, principalmente para a transição das mudanças, sem impactar os consumidos, mas também trazem malefícios, em que é necessário ficar mantendo códigos de versões antigas mas que ainda são utilizados.


### Como fazer o versionamento? [^1]

Existem diversas formas de realizar o versionamento de APIs, vou falar sobre os principais pontos ao escolher uma das abordagens mais comuns:

### Versionamento pela URL

- HTTP GET
- example-health-care.com/api/v2/clients

Fácil de usar, porém alterar a URL não é a melhor prática já que o elemento `v2` não representa uma entidade e além disso fica parecendo que a entidade foi versionada, porém muitas vezes não é o que acontece, como vimos com o cenário descrito no exemplo acima.


### Cabeçalho customizado

- HTTP GET
- example-health-care.com/api/clients
- api-version: 2

Outra opção é utilizar o cabeçalho de solicitação customizado, através do cabeçalho é possível descrever como você quer que um recurso seja representado, devido a isso nem sempre é a melhor prática.


### Cabeçalho Accept

- HTTP GET
- example-health-care.com/apiclients
- Accept: application/vnd.example-health-care.v2+json

Forma mais difícil para testar principalmente para os consumidores que ao obterem o endpoint ainda terão que configurar adequadamente o cabeçalho de aceitação, porém é a forma mais correta segundo o padrão HTTP já que utiliza o cabeçalho de aceitação que define como você gostaria dos dados.

<br>

> Existem muitas discussões por especialistas sobre qual a melhor forma de versionar e até mesmo se realmente o versionamento deve ser feito, portanto não existe a forma sagrada e correta, o que vale é padronizar o versionamento seguindo o estilo de versionamento que você mais considera adequado para o seu dia a dia. ℹ️ Dica de leitura [Google - Versioning in API design](https://cloud.google.com/blog/products/api-management/api-design-which-version-of-versioning-is-right-for-you)

<br><br>

[⬅️ voltar para menu](index.md)

[➡️ próximo tópico Segurança](security.md)

<br><br>

Referências:

[^1]: [Your API versioning is wrong, which is why I decided to do it 3 different wrong ways](https://www.troyhunt.com/your-api-versioning-is-wrong-which-is/)
