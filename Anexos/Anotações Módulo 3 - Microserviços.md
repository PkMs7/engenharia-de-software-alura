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

#### 4.0 Lidando com dados

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

#### 5.0 Operações

- Agregação de logs: Log de dados é uma expressão utilizada para descrever o processo de registro de eventos relevantes num sistema computacional.

    - Para pensar em logs, no cenário de microserviços é preciso pensar que os formatos DEVEM ser compartilhados entre os serviços (pensando em formato padrão e taxonomia(identificação)).

    - Também é importante entender e rastrear a fila de chamadas de execução entre serviços. (Existem ferramentas de gerenciamento (APMs) para visualizar essas chamadas)

- Agregando métricas: 

    - Entenda: Enquanto logs precisam de desenvolvimento, métricas só precisam de instrumentação.

    - Baseie as visualizações de status com dashboards para ter uma visão de alto nível. Isso facilita a tomada de decisão e visualização do ambiente e sistema como um todo.

### Microserviços: explorando os conceitos

#### 1.0 Arquitetando microsserviços

- Composição de microsserviços: APIs, Databases, Tarefas, Processadores de mensagens (cada um em um servidor).

    - Uma máquina (servidor) pode ser considerada um componente. Várias aplicações em uma mesma máquina podem ser vários componentes. Um serviço de apoio (como banco de dados ou fila de mensageria) pode ser um componente. Qualquer coisa que efetivamente componha o serviço, é um componente.

    ![Imaagem de exemplificação da composição de microsserviços](/Anexos/img/composicaoMicrosservicos.png)

- Contrato de microsserviços: Comunicação entre APIs

    - Faça modificações aditivas

        - Novos endpoints
        - Novos campos

    - Versionamento de APIs

        - Comunicação com o cliente, pra quando versionar, sinalizar o tempo de manutenção de ambas as versões e quando a versão antiga cairá.

    - Mantenha equipes separadas, donas de cada serviço

- Identificando barreiras entre microssserviços:

    - Cada serviço possui funcionalidades específicas.

    - DDD pode ajudar a entender melhor cada barreira, com a separação dos domínios (Bounded Contexts).

    - Em uma arquitetura monolítica, cada módulo pode ser um ponto de partida para entender melhor o que seria cada serviço.

    - Evite segmentar serviços apenas por cada substantivo do sistema em microsserviços. Entenda melhor o domínio. Para isso sempre é importante começar aplicações de forma monolítica.

    - "Pense antes de implementar"

    - [Arquitetura de Software](https://dias.dev/2020-04-10-o-que-e-arquitetura/)

#### 2.0 Criação de serviços

- Cuidando do host:

    - Entenda sobre SOs (Sistemas Operacionais), preferencialmente Linux.

    - Máquinas Virtuais geralmente são onde ficam os serviços. Importante de entender que o custo de processamento é alto para manter Máquinas Virtuais.

    - Outro local onde podem ficar hospedados os serviços são os sistemas em cloud. Manter um ambiente de produção em cloud é relativamente simples hoje.

    - Muito utilizado hoje é o container, para subir nos hosts. É a opção mais recomendada.

- Criação de novo serviço:

    - Precisamos configurar o repositório para versionamento. (Vários repositórios ou monorepo?)

    - Precisamos pensar no formato do CI/CD da forma mais automatizada possível. Pensar em testes e padrões a serem seguidos é de suma importância.

- Definindo um padrão:

    - Criação de logs: Formato e Destino
    - Verificação de status
    - Monitoramento de métricas
    - Busca por configuração e secrets
    - Projeto esqueleto, com tudo que qualquer microsserviço precisa
    - Scripts de build, mínimo de código necessário
    - Ter uma imagem docker base que conterão os microsserviços
    - Ter uma configuração base de um orquestrador de containers

#### 3.0 Como se comunicar

- Comunicação síncrona: Comunicação que espera uma resposta.

    - Como se comunicar de forma síncrona? HTTP, gRPC, Protocolos personalizados.

- Comunicação assíncrona: Comunicação que NÃO precisa esperar por uma resposta.

    - Como se comunicar de forma assíncrona? CQRS e Eventos

- Lidando com falhas:

    - Formas de tratar problemas na comunicação síncrona:

        - Circuit Breaker (Utilizando proxy)
        - Cache

    - Formas de tratar problemas na comunicação assíncrona:

        - Retry
        - Retry com back-off
        - Fila de mensagens mortas
        - Mensagens devem poder ser lidas fora de ordem
        - Mensagens devem poder ser recebidas repetidamente(idempotência)

- Service Discovery:

    - Como um serviço pode encontrar outro? 

        - DNS em redes privadas (kubernetes, docker compose, ngix)

#### 4.0 Segurança de serviços

- Visão geral de segurança web:

    - Segurança no transporte: HTTPS

    - Segurança no repouso: Criptografia (Em disco, BD cifrados, Em back-ups), Anonimização

    - Hashs: 

        -  Argon2 é uma função de hash de senhas ganhadora de diversos prêmios. É uma das mais recomendadas para armazenamento de senhas cifradas.

        -  Md5 é um algoritmo de hash muito utilizado para verificar integridade de arquivos transferidos na rede, por exemplo, ou após serem transferidos entre dispositivos para backup.

- Autenticação e autorização: Cada requisição deve informar quem é o cliente. E nossa aplicação define a permissão.

    - Formas de autenticação: Basic HTTP, [Tokens (JWT)](https://youtu.be/B-7e-ZpIWAs), OAuth, OpenID Connect

    - Formas de autorização: ACL(Access control list), RBAC(Role-based access control), On behalf of

- Segurança na rede:

    - Colocar os serviços em redes virtuais

    - Utilizar firewall antes de chegar na API Gateway

    - Utilizar lista de IPs que permitem conexão com determinados seviços

- Defense in Depth: Defesa em profundidade é um conceito usado em segurança da informação em que várias camadas de controles de segurança são colocadas em um sistema de tecnologia da informação.

    - Estude as ferramentas dos atacantes (hackers)

    - Tenha uma equipe de infosec e execute pentests

    - Automatize verificações de segurança. Faça requisições com certificados inválidos, usuários não autorizados (para garantir integridade)

    - Tenha ferramentas para monitorar ataques em tempo real

    - Tenha logs e audite sistemas com frequência

#### 5.0 Lidando com Deploy

- Um monolito pode ser entregeu de forma manual. Mas quando se trata de microsserviços se torna impossível, pois a complexidade é muito grande para esse processo.

    - Para isso é importante um release pipeline (uma linha de processos executaods para gerar entrega de um projeto).

- Ambientes de execução: O microsserviço pode ser implantado em vários ambientes

    - Tipos de ambientes:

        - Desenvolvimento: Local onde é criado / alterado o serviço pelos desenvolvedores

        - Staging/QA: Local onde são feitos os testes, contendo testes configuração para testes de performance e smoke testes

        - Homologação: Local onde clientes ou um PO pode testar o sistema

        - Produção: Local onde o sistema de fato está 

    - Configurações de ambientes e aplicações:

        - Ambiente: Configurar quantidade de recursos e localização

        - Aplicação: Configurar logs(por ambiente), dependências(por ambiente) e dados de acesso(por ambiente)

- Estratégias de deploy: É importante lembrar que nossa pipeline possa realizar a entrega e deploy de micorsserviços de forma isolada e não precisemos fazer o build de todos os serviços da aplicação.

    - Arquivo distribuível(.exe, .war, .phar, .zip)
    - Tag do git
    - Imagem do container

    - Estratégias de releases: Rolling upgrade, Blue-green, Feature toggle

### Microserviços na prática: entendento a tomada de decisões

#### 1.0 Boas-vindas à realidade

- [Repositório da aplicação do curso](https://github.com/CViniciusSDias/alura-ms)

Comando para clonar projeto - (vídeo)
~~~

git clone --recurse-submodules --remote-submodules git@github.com:CViniciusSDias/alura-ms

~~~

Comando para clonar projeto - (transcrição)
~~~

git clone --recursive https://github.com/CViniciusSDias/alura-ms

~~~

Comando para rodar o projeto - (transcrição)
~~~

docker-compose up --build

~~~

- Para configurar o email defina no docker-compose.yml

    - Variáveis `GMAIL_USER` e `GMAIL_PASSWORD`

#### 2.0 O início de tudo

-  Dica: Para facilitação do trabalho com microsserviços, quanto mais padronizado melhor, restringindo as escolhas (Linguagens, Nuvem, Scripts).

- [Submódulos](https://www.atlassian.com/git/tutorials/git-submodule) são ponteiros para commits.

#### 3.0 Infraestrutura

- Os [12 fatores](https://12factor.net/pt_br/) são um conjunto de princípios sobre organização de código, práticas de desenvolvimento, arquitetura e operações para construção de aplicações modernas.

#### 4.0 Build e deploy

- Build: Conceito de revisão do código para ver se o estilo de codificação está de acordo com a comunidade daquela linguagem, análise estática, erro de sintaxe.

- [Jenkins](https://www.jenkins.io/), [Travis CI](https://www.travis-ci.com/) ou [GitHub Actions](https://github.com/features/actions): Ferramentas para criar uma pipeline para builds.

- Prcessos como esse protegem a aplicação de deploys que possam quebrar o código na main.

#### 5.0 Um pouco de código

- [Screaming Architecture](https://medium.com/@danilo.arruda/o-que-%C3%A9-arquitetura-gritante-137bc45d621d)

- [RabbitMQ](https://www.rabbitmq.com/tutorials/tutorial-three-php.html): Instruções para PHP

#### 6.0 Front-end

- O front pode ser único ou trabalhado de forma independente como serviços e times específicos.

- Optimistic vs Pessimistic: Abordagem otimista (parte do princípio de que vai dar certo) e abordagem pessimista (parte do princípio que vai dar errado).

- Microfrontends: é um estilo arquitetônico que separa uma aplicação de front em várias camadas menores, cada uma sendo responsável por um módulo específico da aplicação, normalmente separadas por domínios ou contextos de uso, permitindo assim, que diferentes times cuidem dessas funcionalidades de forma independente. (Cada tela pode ser feita com uma tecnologia específica)