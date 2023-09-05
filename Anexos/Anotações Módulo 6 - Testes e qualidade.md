# Tópicos sobre Testes e qualidade

## Conteúdo de artigos e Alura+





## Conteúdo dos módulos de treinamento

### Quality Assurance: plano de testes e gestão de bugs

#### 1.0 Testes e cenários de testes

- Reduzir o risco e falhas de um sistema.

    [Material do treinamento](/Anexos/docs/QA_Fundamentos_-_Slides.pdf)

- O documento que define os requisitos de testes se chama "Plano de Testes".

    [Modelo de Plano de Teste](/Anexos/docs/ModeloPlanoTeste.docx)

- **Cenário de teste** é o que precisa ser testado.

- **Caso de teste** é como é realizado o teste do cenário.

- BDD (Behavior driven development) - Desenvolvimento Guiado por Comportamento

    - Dado - Pré-condições devem ser verdadeiras para que eu execute o teste?

    - Quando - Qual ação será executada no sistema que fornecerá o resultado validado?

    - Então: - De acordo com a ação disparada, qual será o resultado esperado?

#### 2.0 Qualidade

- Algumas atividades do QA:

    - Testes (Plano de teste)

    - Debug e logs

    - Pequenas implementações com pair programming

    - Gestão de erros

    - Papel na metodologia ágil

- Manifesto de Teste Ágil:

    - Testar durante o desenvolvimento

    - Prevenir bugs

    - Testar o entendimento, não só funcionalidades

    - Todo o time é responsável pela qualidade

- Critérios de aceite: Valores mínimos aceitáveis para o projeto.

#### 3.0 Aprofundando nos tipos de testes

- Tipos de testes:

    - Teste de regressão é uma técnica de teste a ser aplicada quando surgem novas versões mais recentes do software e garante que não surjam novos defeitos em componentes já analisados;

    - Teste de sanidade é o subconjunto do teste de regressão e também é realizado quando não temos tempo suficiente para fazer o teste mais elaborado. Ele tem um nível superficial e verifica se as funcionalidades mais críticas do sistema estão conforme o esperado;

    - Testes de limite consistem em testar os valores mínimo e máximo (ou primeiro e último valores) de uma partição. Essa técnica é geralmente usada para testar requisitos que exigem um intervalo de números (incluindo datas e horas);

    - Teste de transição de estados é utilizado para testar a capacidade que o software tem de entrar em e sair de estados definidos através de transições válidas e inválidas;

    - Testes não-funcionais tem como objetivo testar aspectos do software que não são associados a funcionalidades. Ex: escalabilidade, desempenho, segurança;

    - Testes de performance são um conjunto de testes que visam analisar o desempenho. Entre eles, temos:

        - Teste de carga, que tem como objetivo verificar o desempenho de um sistema quando ele é submetido a cargas variáveis de usuários ou transações.

        - Teste de capacidade, parecido com o de carga, tem como objetivo identificar os limites da aplicação, ou seja, quantos usuários simultâneos ou chamadas por segundo a aplicação é capaz de suportar dentro dos parâmetros de qualidade definidos.

        - Teste de stress, verifica a performance de um sistema quando é submetido a cargas que estão no limite ou acima do limite especificado inicialmente.

    - Teste de usabilidade, tem como objetivo observar usuários reais usando o software para descobrir problemas e pontos de melhorias.

- Uma ferramenta para realização de testes de performance é o **Google Lighthouse**.

#### 4.0 Pirâmides de testes

- Teste de Caixa Branca: Sem saber como o sistema funciona, não se tem como testá-lo.

    - Teste de um sistema para fazer verificações na arquitetura. (QAs um pouco mais técnicos, que entendem como o software funciona)

        - Teste unitário
        - Teste de integração de componentes
        - Teste de serviço (API)

    - Teste de Caixa Preta: 

        - Não é necessário um conhecimento específico sobre o código do sistema.

            - Teste de aceitação
            - Teste de sistemas
            - Teste de usabilidade

- Uma ferramenta para gravar evidências de testes pode ser o **Gravador de Passos** do Windows. 

#### 5.0 Gestão de Erros

- Classificamos bugs no sistema por severidade. Então, eles se dividem em: blockers (que bloqueiam nossos testes), críticos e graves, moderados e pequenos. Especificamos a severidade no nosso plano de teste, considerando o impacto deles no sistema.

- Reporte de bugs:

    - O reporte de bugs consiste em descrever bem o bug de forma precisa a fim que todo o time consiga reproduzi-lo.

#### 6.0 Estratégia de teste

- Arquitetura, Escopo, Ambiente e Ferramentas devem ser descritos no plano de testes. [Modelo de Plano de Testes](/Anexos/docs/ModeloPlanoTeste.docx)

#### 7.0 Refinamentos e conclusões

- É importante para o cenário de testes levantar algumas métricas:

    - Estimativa de testes: Fatores para se levar em consideração são entender o tamanho do produto, complexidade do software, nível de detalhes para documentação, ferramentas a ser utilizadas, habilidades das pessoas envolvidas e entender cenários de retrabalho. (Com isso se consegue ter uma noção do esforço a ser realizado para aqueles testes)

    - Métricas de qualidade: Importante se levantar alguns indicadores como total de defeitos, total de defeitos em produção, total de defeitos removidos, tempo médio de reparo, quantidade de testes automatizados, cobertura de código (quantidade de linhas de código com testes unitários) e pesquisas de satisfação do usuário.