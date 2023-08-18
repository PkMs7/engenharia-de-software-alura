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

## Conteúdo dos módulos de treinamento

### Integração Contínua: mais qualidade e menos risco no desenvolvimento

#### 1.0 Conhecendo a arquitetura