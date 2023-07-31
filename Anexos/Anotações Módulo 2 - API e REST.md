# Tópicos sobre API e REST

## API

- Um conjunto de rotinas e padrões de um software para utilização das funcionalidades por aplicativos que não pretentendem envolver-se em detalhes da implementação do software, mas apenas usar seus serviços.

- APIs web: Requisição de acessos via navegador. (talvez não seja a melhor definição)

    - Padrões de API Web: RPC, Soap, REST

- APIs de código fonte: Requisição no próprio código (Ex.: Solicitação de datas).

## REST

- REST (Representational State Transfer): Possui o princípio de aplicações distribuidas. Trabalha com o principio de client (componente solicitante) / server(componente provedor de serviços), onde ambos nunca são fixos, dependendo sempre do contexto. Tem como princípio fundamental usar o protocolo HTTP para comunicação dos dados.

- Os envios são representativos, utilizando geralmente o JSON.

- Comunicação por métodos HTTP (Ex.: GET, POST, PUT, DELETE)

- Artigo Alura: https://www.alura.com.br/artigos/rest-conceito-e-fundamentos?_gl=1*18xkvfp*_ga*MTM2MDg5MDM4My4xNjc2MzIyMjI1*_ga_59FP0KYKSM*MTY5MDgzMzU0Ni44NS4xLjE2OTA4MzQ5MzQuMzkuMC4w*_fplc*QzNZVjdVWEdWNUZJZExQRFNUSmVzSzJibTE1b0x0MWZzNUM3bnV2SENYc0MlMkJOc2ZiWHNEJTJCclhodHRrYnFRdGloc3prYnF2NGJROVolMkJlOSUyQkNjT05uZHlneXcyaUR2ZlZnOUNmdiUyRjl4emZOUDFNM1FJd0M5b0s1VmJNVzR6QSUzRCUzRA

## Boas práticas na modelagem de APIs REST

- Faça uso de recursos corretamente: 
    - Use pronomes, e não verbos
    - Não misture plural e singular

- Utiliza sub-recursos:
    - Relacionamentos existentes devem estar explícitos na URL

- Entenda sobre idempotência:
    - GET, HEAD, PUT, DELETE

- Não ignore os cabeçalhos HTTP:
    - Existem várias informações que podem ser transmitidas através de cabeçalhos

- Use HATEOAS:
    - Hypermidia As The Engine Of Application State - facilite a interação com a API. Forneça links que informe o que o cliente pode utilizar em sua API.

- Filtro, ordenação, paginação e seleção de campos:
    - Sua API deve ser Flexível

- Versione sua API:
    - Alterações que demandam alteração no cliente DEVEM gerar uma nova versão da API

- Utilize os status HTTP corretamente:
    - 1xx: Informational
    - 2xx: Sucess
    - 3xx: Redirection
    - 4xx: Cliente Error
    - 5xx: Server Error