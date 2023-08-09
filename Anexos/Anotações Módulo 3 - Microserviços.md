# Tópicos sobre Microserviços

## Conteúdo de artigos e Alura+

### Microserviços

- Monolitos: Aplicações que possuem todas as regras e códigos em um único lugar.

- Microserviços: Trabalha com partes isoladas no sistema (independentes).

### Tipos de Microserviços

- Data Service: Serviço que fornece acesso direto a dados.

- Bussines Service: Aglomerado de data services. Conjunto de regras de negócio.

- Translation Service: Fornece serviços de tradução de dados/informações.

- Edge Service: Permite que forneça algumas especificidades para o cliente.

### API Gateway

- API Gateway é considerada a porta de entrada de uma API

- Ele centraliza o acesso aos vários serviços.

    ![Imagem representativa do API Gateway](img/ApiGateway.png)

- Importante o cuidado com a API Gateway, pois se ele cai, não se conseguirá mais ter acesso com os serviços.

- Comportamentos da API Gateway:

    ![Imagem representativa do Comportamento da Api Gateway](img/ComportamentoApiGateway.png)

### Service Mesh (Malha de Serviços)

- Uma malha de serviços é um termo relativo à infraestrutura de comunicaçõa existente entre vários serviços que compõem uma determinada aplicação/solução.

    ![Imagem representativa do Service Mesh](img/ServiceMesh.png)

## Conteúdo dos módulos de treinamento

### Microserviços: Padrões de projeto

#### 1.0 Conhecendo a arquitetura

- Microsserviços são uma abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software consiste em pequenos serviços independentes que se comunicam usando APIs bem definidas.

- Vantagens de microserviços:

    - Projetos independentes e com possibilidade de linguagens independentes

    - Falhas serão sempre isoladas

    - Deploys menores e mais rápidos

- Desvantagens de microserviços:

    - Maior complexidade de desenvolivmento e infra

    - Debug mais complexo

    - Comunicação entre serviços deve ser bem pensada

    - Diversas tecnologias podem ser um problma

    - Monitoramento é crucial e mais complexo

- Tipos de serviços:

    - Data service

    - Bussines service

    - Translation service

    - Edge service 

#### 2.0 Separando serviços

- Separar um Data Service utilizando um serviço de domínio (DDD - Domain-Driven Design):

    - Para estruturar comece modelando seu domínio, não pensando na persistência

    - Avalie as ações que serão disponibilizadas

    - Construa o serviço, pensando primeiro no contrato

    - [REST](/Anexos/Anotações%20Módulo%202%20-%20API%20e%20REST.md) e [RPC](https://pt.wikipedia.org/wiki/Chamada_de_procedimento_remoto) podem andar juntos.

- Serviços de negócio:

    - Em determinados momentos as operações precisam de um modelo do nosso domínio para serem corretamente representadas em um serviço.

    - Proveem uma funcionalidade do negócio de mais alto nível.

    - Permite encapsular domínios relacionados.

- Padrões:

    - Strangler pattern: Quebrar um monolito tirando as funcionalidades, isolando os dados ou isolando os domínios.

    - Sidecar pattern: Determina um processo comum para construir um módulo compartilhável. (Atualização que replica nos serviços existentes)

#### 3.0 Integrando serviços

- API Gateway: Fornece um proxy, para as necessidades reais do cliente (usuário).

- Agregador de processos: Agrega serviços de negócios, ele faz as chamadas para os serviços necessários e montam a resposta correta.

- Edge pattern: Gateway específico para determinados clientes. Foco na real necessidade do solicitante.

### 4.0 Lidando com dados

- Tipos de organização:

    - Single service database: Um serviço para apenas um banco de dados.

    - Shared service database: Um banco de dados (que internamente trabalha como se fossem bancos separados) compartilhado entre os serviços.

- Padrões de codificação:

    - CQS (Command Query Segregation): Um padrão que define que um método deve ser um comando ou uma consulta, nunca os dois ao mesmo tempo.

    - CQRS (Command Query Responsibility Segregation): Um padrão que separa as operações de leitura e atualização de um armazenamento de dados.

    * Entende-se por commando(estrutura de dados) toda a alteração de um estado no servidor (PUT, DELETE)

    ![Representação do CQRS](/Anexos/img/CQRS.png)

- Eventos assíncronos: Eventos que não se realizam ao mesmo tempo.

    - Tecnologias como mensagerias e serviços de stream de dados tem relação direta com eventos assíncronos.

### 5.0 Operações

- Agregação de logs: Log de dados é uma expressão utilizada para descrever o processo de registro de eventos relevantes num sistema computacional.

    - Para pensar em logs, no cenário de microserviços é preciso pensar que os formatos DEVEM ser compartilhados entre os serviços (pensando em formato padrão e taxonomia(identificação)).

    - Também é importante entender e rastrear a fila de chamadas de execução entre serviços. (Existem ferramentas de gerenciamento (APMs) para visualizar essas chamadas)

- Agregando métricas: 

    - Entenda: Enquanto logs precisam de desenvolvimento, métricas só precisam de instrumentação.

    - Baseie as visualizações de status com dashboards para ter uma visão de alto nível. Isso facilita a tomada de decisão e visualização do ambiente e sistema como um todo.