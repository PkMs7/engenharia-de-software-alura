# Tópicos sobre Devops e Monitoramento

## Conteúdo de artigos e Alura+

### DevOps

- DevOps: Desenvolvimento(Desenvolvimento de código, novas funcionalidades) / Operações(Monitoramento, infraestrutura, saúde do sistema que está em disponibilizaçõa, garantia de estabilidade).

- Desenvolvedores são mais maleáveis, aceitam melhor a mudança. Operações são menos flexíveis, geralmente partindo da premissa "Não toque num sistema que está funcionando". O movimento DevOps quer derrubar essa barreira, num cenário de implementação de novas funcionalidades (desenvolvimento), sem que isso derrube o que já está funcionando (operações).

- Importância da visibilidade dos scripts de ambientes e configurações, para que todos entendam onde e o que está acontecendo.

- ![Algumas ferramentas de DevOps](/Anexos/img/ferramentasDevOps.png)

### DevSecOps

- DevSecOps é a camada de segurança do DevOps.

    ![DevSecOps](/Anexos/img/devSecOps.png)

- Segurança a qualquer custo, mesmo que diminua a velocidade. Abaixo os pilares do DevSecOps:

    - Segurança em primeiro lugar
    - Automação é fundamental
    - Velocidade
    - Entrega rápida e contínua (CI/CD)
    - Confiabilidade

- Em resumo, a camada de segurança, na prática entra diretamente na pipeline, com checks (auditorias e scanners de vírus) de arquivos maliciosos antes de subir a aplicação, por exemplo.

### SRE (Site Reliability Engineering) - Engenharia de Confiabilidade de Sites

- O embate entre Desenvolvedores e Infra acontecem no ponto de **"Confiabilidade"**. (Como você pode assegurar que seu software é confiável?)

- Nesse cenário nasce o SRE, pra que se consiga deixar esse deploy mais confiável e seguro. (Foi desenvolvida essa disciplina pelo Google)

- Ajuda a obter métricas para trazer informações de confiabilidade. Seu ponto forte é a **Observabilidade**.

- Quatro sinais de ouro do SRE: Latência, Tráfego, Erros e Saturação.

### Observabilidade

- Monitoramento de sistemas distribuídos (problema).

- Desafio: Agir proativamente ou reativamente em métricas e logs distribuídos.

- Pilares da Observabilidade:

    - Métricas
    - Traços Distribuídos
    - Logs

- Uma ferramenta para exportar algumas métricas é o **Prometheus** (base de dados para métricas).

- A ferramenta para visualizar essas métricas é o **Grafana** (importa a base de dados do Prometheus).

- Uma ferramenta para trabalhar com Instrumentação Manual é a Jaeger. Podem ser plugadas na ferramenta:

    - Service Mesh (Istio)
    - Proxy (Envoy, Traefik, Kong)

- Para trabalhar com logs pode-se usar: Sidecar, Logging agent instalado no host, Shell script. Uma ferramenta para ser utilizada é o Graylog.

### 4 Golden Signals

- Latência, Tráfego, Erros e Saturação. Esses sinais podem ser observados através do Grafana.

## Conteúdo dos módulos de treinamento

### Integração Contínua: mais qualidade e menos risco no desenvolvimento

#### 1.0 Conhecendo a arquitetura

- Qual problema a integração contínua busca resolver? Resolve o problema de edição e deploy de códigos compartilhados. É importante padronizar e criar a esteira de deploys de forma contínua, para que não se tenha demoras e atrasos para as partes posteriores a edição dos códigos. Tem se a ideia de comparilhamentos contínuos. Busca evitar deploys apenas na final das sprints. "Integração Contínua é a prática de desenvolvimento que requer a integração do código várias vezes ao dia."

- Boas práticas para se usar no sistema de controle de versão: 

    - Ferramenta não importa
    - Comita-se todo o necessário para construção do projeto 
        - Código
        - Scripts
        - Migrações
        - Schemas
        - IDE Configs

    - Não se comita o que pode ser construído (gem, jar, image, modules)
    - Cones e starts (build) devem ser fáceis

- Cada projeto que tenha o seu repositório se chama multi-repo.

- O repositório que conta com todos os projetos centralizados se chama mono-repo.

#### 2.0 Estratégias de ramificação

- Branch ou ramo é a estrutura de quebra do fluxo principal de versionamento do código, fazendo com que a edição do código não afete a estrutura principal (master / main), e só vai voltar a fazer parte da estrutura principal a partir do comando de "merge".

- Branch models são os modelos de estrutura de regras para se trabalhar com os ramos de versionamento (Git Flow, Trunk Based Development, Gitlab Flow, One Flow, Github Flow).

    ![Imagem de Branch Models](/Anexos/img/Branches.png)

- Boas práticas com branchs:

    - Commits simples e orientados a tarefas
    - Branches atrasam integração e seguram o código, então tenha branches com vida curta -> Merges mais simples
    - Estratégias de branch models devem ser bem alinhados entre o time de desenvolvimento.

- Aguns exemplos de Brandhing Models:

    - Temporários (branches locais)
    - Feature branches
    - Historical branches (Master/Main e Develop)
    - Environment branches (Staging e Production)
    - Maintenance branches (Release e Hotfix)

- Técnicas de branching

    - Trunk-based development: Branch com menor distancia da Master/Main (Muito pouco usado, pois requer um nível de confiança muito grande).
    - Feature Branch Workflow: Ramificação de acordo com as demandas de tarefas (features) para depois serem mergeadas com a Master/Main.
    - Feature Branch + Pull Request: Segue o modelo de Feature Branch Workflow, mas agora com uma camada de aprovação (pull request) antes de ser mergeada para Master/Main. (Usado para novos desenvolvedores, com uma camada extra de aprovação, mas geralmente não é usado em Integração Contínua)
    - Git Flow: O mais popular e complexo modelo de trabalhos com branches, onde passa por várias camadas até ser mergeado com a Master / Main.
        ![Modelo Git Flow](/Anexos/img/GitFlow.png)

- Dicas para evitar branches de vida longa:

    - Algumas técnicas são Feature Flags e Branch by Abstraction
    - Feature Flag: O código é inserido no master, mas ele não é visível para a equipe. O Feature flag server também para testar funcionalidades, por exemplo.
    - Branch by Abstraction: Branch by Abstraction, apesar do nome, não envolve a criação de uma nova ramificação. Temos um módulo ligado, uma parte da aplicação utiliza uma biblioteca antiga e precisa ser substituída. Esse é um processo lento, e muitos elementos precisam ser alterados.

- Dicas para sincronizar branches:

    - Vantagens e desvantagens de Merge e Rebase.
        - Merge: Comando para juntar branch com master. Cria um novo commit (Merge commit) desse evento de sincronização. 
            ![Comando Git Merge](/Anexos/img/Merge.png)
        - Rebase: Muda a base do commit, e puxa os commits da base Master. Nesse caso ele "transforma" a branch na master.
            ![Comando Git Rebase](/Anexos/img/Rebase.png)

#### 3.0 Builds e testes automatizados

- Dicas para testes automatizados:

    - Fazem parte da construção
    - Rodar antes do commit
    - TDD pode ajudar
    - Desempenho é importante
    - Código testável é um código simples
    - Devemos categorizar os testes (unidade, integração e funcionalidade)
    - Rodar primeiramente testes rápidos (use smoke tests)
    - Testes fazem parte do build
    - Feedback sempre

- Tipos de testes:

    - Testes de unidade
    - Testes de integração
    - Testes funcionais

    ![Exemplificação da pirâmide de testes](/Anexos/img/tiposDeTestes.png)

    - Uma técnica utilizada é o Smoke Test, trata-se de uma seleção de testes que garantem que as funcionalidades mais importantes do sistema estejam operando corretamente.

- Etapas do build:

    - Clean -> Compile -> Uniti tests -> Static analysis -> Package software -> Integrate database...

- Busque sempre automatizar builds

    - Build a cada commit
    - Tudo automatizado / silgle commando
    - Build sem depender da IDE
    - Tudo está no repositório (install scripts, env settings, build scripts, config files, database files, code)

- Dicas de build rápido / feedback rápido:

    - Otimize o build, métricas ajudam
        - Verifique a fase de testes e analise o código
        - Verifique a ordem dessas fases
        - Verifique a infra do build system
    - Use cache
    - Use staged build/pipeline

- Ferramentas de automação e construção, separado por linguagem/plataforma:

    - Java: Ant, Maven, Gradle
    - Front-end: Gulp, Grunt, Webpack
    - .NET: MSBuild
    - Ruby: Rake
    - Kotlin: Gradle
    - Clojure: Leiningen
    - C/C++: CMake/Make
    - PHP: Composer

- E alguns frameworks famosos da área de teste:

    - Selenium (automação do navegador)
    - Cucumber (testes de aceitação)
    - Postman e SoapUI (testes de API)
    - JMeter (stress tests)
    - JUnit, xUnit, PHPUnit (automação de testes)
    - entre muitos outros frameworks e bibliotecas
    
- Para o configuration management e provisioning podemos mencionar:

    - Ansible
    - Puppet
    - Chef
    - Salt
    - Terraform (cloud)

#### 4.0 Mais feedbacks com builds contínuas

- É importante que se tenha um local que faça testes completos, geralmente utilizado um servidor central pra isso, denominado CI Daemon.

    - Exemplos de servidores de integração:

        - Jenkins (https://jenkins.io/)
        - GoCD (https://www.gocd.org/)
        - Bamboo (https://www.atlassian.com/br/software/bamboo)
        - Travis CI (https://travis-ci.org/)
        - Team City (https://www.jetbrains.com/teamcity/)
        - Circle CI (https://circleci.com/)
        - Gitlab (https://about.gitlab.com/product/continuous-integration/)
        - AWS Code Pipeline https://aws.amazon.com/codepipeline/
        - Azure (https://azure.microsoft.com/pt-br/services/devops/server/)

- O que fazer quando o build quebra?

    - Como conceito principal da metodologia ágil, "software funcionando acima de documentação extensa", quando um build quebra, se torna uma PRIORIDADE DE TODA A EQUIPE ajustar (afinal agora nada mais pode ser commitado, e isso trava todos os commits posteriores). Corrigir bugs na hora.

    - O servidor de integração contínua monitora o repositório de código:

        - Ao detectar uma alteração, deve iniciar o build do projeto
        - O build deve acontecer a cada novo commit
        - O resultado do build deve ser publicado
        - Os desenvolvedores devem ser notificados sobre o status do build

    - Um build quebrado deve ser arrumado em no máximo 10 minutos, com prioridade máxima:
        
        - É responsabilidade de todos da equipe arrumar um build quebrado

#### 5.0 Um pouco sobre a entrega contínua

- Segundo o manifesto ágil a prioridade mais alta é deixar o cliente satisfeito, e isso é feito por meio de entrega contínua.

- RNF: Deployability (quão fácil é de realizar o deploy de sua aplicação?)

### Entrega Contínua: confiabilidade e qualidade na implantação de software

#### 1.0 O que é Entrega Contínua?

- [Artigos Alura sobre Entrega Contínua](https://cursos.alura.com.br/course/entrega-continua-confiabilidade-qualidade/task/72281)

- É importante entender que deploys demorados **aumentam** o risco de problemas de integração.

    - Uma dica para deploys é que eles precisam ser frequentes e **automatizados**.

- ![Dicas de Livros](/Anexos/img/LivrosEntregaContinua.png)

- Antipaterns (anti-padrão): Devem ser evitados

    - Gerenciamento manual de ambientes: Cada ambiente precisa ser configurado e reconfigurado, e temos vários. Deveria ser fácil destruir o pipeline e reconstruí-lo com a mesma facilidade. Se etapas que já são complexas forem executadas manualmente teremos a presença de erros e inconsistências. Há casos em que o deploy funcionou em ambiente de homologação, mas não de produção, e é importante mencionar que são ambientes muito similares. **Regra de Ouro**: Todos os ambientes são tratados como código, versionados e criados de maneira automatizada.

    - Deploy manual:Geralmente temos um manual que define as etapas de um deploy, mas geralmente a aplicação evolui e a documentação não é mais precisa e real. Há desenvolvedores que não sabem como o deploy é de fato realizado, afinal é um fazer delegado a poucas pessoas dentro da empresa em algumas configurações de equipe. Os deploys podem ser lentos e durarem horas ou dias. Nessa configuração teremos um deploy vagaroso, sujeito a erros e não confiável.
    **Regra de ouro**: apenas duas tarefas devem ser executadas manualmente: escolher a versão do release e o clique em "deploy buttom.

    - Deploy apenas no fim do ciclo: Por exemplo, ao desenvolveremos em aplicações estáveis e grandes focam em testes de criação de novas features e não interagem com a equipe de produção. Dessa maneira não sabemos se as novas features serão de fato funcionais e estáveis em produção.
    **Regra de ouro**: deployment faz parte do desenvolvimento desde a primeira interação, todos definem um delivery team.

### 2.0 Fundamentos

- Definição de **Entrega contínua**: Entregar software com alta qualidade e grande valor, de maneira eficiente, rápida e confiável

- Os princípios básicos da Entrega contínua são:

    - Automatize
    - Versione
    - Repita
    - Garanta qualidade
    - Defina "done"(feito em produção)
    - Crie um delivery team (todos os envolvidos com a entrega em produção como um todo)
    - Use melhoria contínua(feedbacks contínuos)

- Elementos da Entrega contínua:

    - Cultura DevOps:
        - feedback, colaboração, confiança, melhoria e aprendizagem contínua
    - Patterns:
        - deployment pipeline, deploy patterns (blue/gree, canary, feature toggle)
    - Arquitetura
        - Novas propriedades(testability, deployability), SOLID, Services, 12 Factor App

### 3.0 Deployment pipeline

- Estágios da Pipeline do deploy:

    **Simplificado**
    ![Estagios da Pipeline do Deploy](/Anexos/img/EstagiosPipelineDeploy.png)

    **Detalhado**
    ![Estagios da Pipeline do Deploy Detalhado](/Anexos/img/EstagiosPipelineDeployDetalhado.png)

    **Diagrama**
    ![Diagrama da Pipeline do Deploy](/Anexos/img/DiagramaPipelineDeploy.png)

- Boas práticas:

    - Pipeline deve ser a única forma de deploy
    - Manter a pipeline a mais rápida possivel
    - Bulid apenas uma vez
    - Build independente do ambiente
    - Ambientes iguais / semelhantes ao ambiente de produção
    - Deploy para ambientes de maneira igual
    - Ambientes temporários também podem ajudar em testes iniciais, pois não levam "sujeiras" de outros lugares

### 4.0 Stages de commit e testes de aceitação

- Commit Stage: É nesta etapa em que rodamos os testes de unidade (ou commit test), buildamos e disponibilizamos o artefato, e geramos relatórios de qualidade. **É ideal que esta etapa não demore mais do que 10 minutos**(Pois o desenvolvedor está aguardando os testes para poder seguir com suas demandas).

    ![Commit Stage](/Anexos/img/CommitStage.png)

- Stage de testes de aceitação: Nesta fase queremos testar a aplicação inteira e avaliar se ela preenche os **requisitos de negócio**. Esta é uma etapa essencial para chegar ao deploy contínuo e inserir a aplicação na fase de produção de maneira segura.

    ![Testes De Aceitacao](/Anexos/img/TestesDeAceitacao.png)

### 5.0 Stage de Homologação

- Nesta fase os testes são executados pelo cliente, isto é, um usuário real do produto utiliza a interface do software, por isso essa etapa também é conhecida como "teste de aceitação".

- Importante se atentar aos feedbacks. O cliente consegue usar o sistema de acordo com o esperado? Realiza as ações requisitadas? Apresenta dificuldade?

- Teste de carga: Em paralelo a homologação, podemos executar o "Capacity Testing Stage". Os testes de carga buscam descobrir qual é a real capacidade do nosso sistema, ou seja, seu baseline. Conhecendo nosso sistema, devemos estabelecer metas claras e utilizar ferramentas de monitoração para descobrir as modificações arquiteturais que são necessárias.

### 6.0 Estratégias de release

- Formas de fazer com que o deploy seja feito com a maior segurança possível. Releases são incrementais.

    ![Gold Release](/Anexos/img/GoldRelease.png)

- Blue-Green Deployment:

    - Tecnicamente, o deploy já foi realizado, mas temos duas versões: uma antiga(azul) e a nova(verde) que já está em ambiente de produção.

    - Entre as versões há um roteador, então em algum momento podemos modificar o fluxo para o novo ambiente, a nova versão. O ambiente velho (blue) fica no ar ainda um bom tempo caso algum problema surja. As conexões que existiam para o azul ficarão disponíveis até que realmente apenas a versão verde esteja totalmente funcional.

- Canary Release:

    - Neste caso, as duas versões são utilizadas ao mesmo tempo, tanto azul quanto a verde, mas a nova versão não é acessada por todos os usuários. Uma parcela dos usuários que têm acesso a nova versão serão agentes de um teste.