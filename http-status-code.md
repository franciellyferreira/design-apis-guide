# Guia para Design de APIs

## HTTP: Status Code

Como citamos no tópico de [introdução](introduction.md#rest) as APIs REST operaram sobre o protocolo HTTP. A transferência de dados entre cliente e servidor roda em cima do protocoloco HTTP, onde o cliente solicita ao final de cada requisição o código de estado da requisição, este código é composto por três números [^1]. Segue alguns códigos de estado retirados diretamente do site do Mozilla [^2]:

### 1xx - Informativo

Código | Nome | Descrição
--- | --- | ---
100 | Continue | Essa resposta provisória indica que tudo ocorreu bem até agora e que o cliente deve continuar com a requisição ou ignorar se já concluiu o que gostaria.
101 | Switching Protocol | Esse código é enviado em resposta a um cabeçalho de solicitação Upgrade pelo cliente, e indica o protocolo a que o servidor está alternando.
102 | Processing | Este código indica que o servidor recebeu e está processando a requisição, mas nenhuma resposta está disponível ainda.
103 | Early Hints | Este código tem principalmente o objetivo de ser utilizado com o cabeçalho Link, indicando que o agente deve iniciar a pré-carregar recursos enquanto o servidor prepara uma resposta.

### 2xx - Sucesso

Código | Nome | Descrição
--- | --- | ---
200 | OK | Estas requisição foi bem sucedida. O significado do sucesso varia de acordo com o verbo HTTP
201 | Created | A requisição foi bem sucedida e um novo recurso foi criado como resultado. Esta é uma tipica resposta enviada após uma requisição POST.
202 | Accepted | A requisição foi recebida mas nenhuma ação foi tomada sobre ela. Isto é uma requisição não-comprometedora, o que significa que não há nenhuma maneira no HTTP para enviar uma resposta assíncrona indicando o resultado do processamento da solicitação. Isto é indicado para casos onde outro processo ou servidor lida com a requisição, ou para processamento em lote.
203 | Non-Authoritative Information | Esse código de resposta significa que o conjunto de meta-informações retornadas não é o conjunto exato disponível no servidor de origem, mas coletado de uma cópia local ou de terceiros. Exceto essa condição, a resposta de 200 OK deve ser preferida em vez dessa resposta.
204 | No Content | Não há conteúdo para enviar para esta solicitação, mas os cabeçalhos podem ser úteis. O user-agent pode atualizar seus cabeçalhos em cache para este recurso com os novos.
205 | Reset Content | Esta requisição é enviada após realizanda a solicitação para informar ao user agent redefinir a visualização do documento que enviou essa solicitação.
206 | Partial Content | Esta resposta é usada por causa do cabeçalho de intervalo enviado pelo cliente para separar o download em vários fluxos.
207 | Multi-Status | Uma resposta Multi-Status transmite informações sobre vários recursos em situações em que vários códigos de status podem ser apropriados.
208 | Multi-Status | Usado dentro de um elemento de resposta <dav:propstat> para evitar enumerar os membros internos de várias ligações à mesma coleção repetidamente.
209 | IM Used | O servidor cumpriu uma solicitação GET para o recurso e a resposta é uma representação do resultado de uma ou mais manipulações de instância aplicadas à instância atual.

### 3xx - Redirecionamento

Código | Nome | Descrição
--- | --- | ---
300 | Multiple Choice | A requisição tem mais de uma resposta possível. User-agent ou o user deve escolher uma delas. Não há maneira padrão para escolher uma das respostas.
301 | Moved Permanently | Esse código de resposta significa que a URI do recurso requerido mudou. Provavelmente, a nova URI será especificada na resposta.
302 | Found | Esse código de resposta significa que a URI do recurso requerido foi mudada temporariamente. Novas mudanças na URI poderão ser feitas no futuro. Portanto, a mesma URI deve ser usada pelo cliente em requisições futuras.
303 | See Other | O servidor manda essa resposta para instruir ao cliente buscar o recurso requisitado em outra URI com uma requisição GET.
304 | Not Modified | Essa resposta é usada para questões de cache. Diz ao cliente que a resposta não foi modificada. Portanto, o cliente pode usar a mesma versão em cache da resposta.
305 | Use Proxy Deprecated | Foi definida em uma versão anterior da especificação HTTP para indicar que uma resposta deve ser acessada por um proxy. Foi depreciada por questões de segurança em respeito a configuração em banda de um proxy.
306 | Unused Deprecated | Esse código de resposta não é mais utilizado, encontra-se reservado. Foi usado numa versão anterior da especificação HTTP 1.1.
307 | Temporary Redirect | O servidor mandou essa resposta direcionando o cliente a buscar o recurso requisitado em outra URI com o mesmo método que foi utilizado na requisição original. Tem a mesma semântica do código 302 Found, com a exceção de que o user-agent não deve mudar o método HTTP utilizado: se um POST foi utilizado na primeira requisição, um POST deve ser utilizado na segunda.
308 | Permanent Redirect | Esse código significa que o recurso agora está permanentemente localizado em outra URI, especificada pelo cabeçalho de resposta Location. Tem a mesma semântica do código de resposta HTTP 301 Moved Permanently  com a exceção de que o user-agent não deve mudar o método HTTP utilizado: se um POST foi utilizado na primeira requisição, um POST deve ser utilizado na segunda.

### 4xx - Erro do cliente


### 5xx - Erro do servidor


<br><br>

Referências:

[^1]: [HostGator - O que significa cada código HTTP?](https://www.hostgator.com.br/guias/http-status-code-como-resolver/#h-o-que-significa-cada-c-digo-http)
[^2]: [Mozilla - Código de status de resposta - Informativas](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
