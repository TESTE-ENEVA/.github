## Hi there 👋

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

#### copia e cola de um fluxo aleatório
```mermaid
flowchart LR

    subgraph legenda
        direction LR
        tipo1 --- |Lambda| tipo2
        tipo2 --- |ECS| tipo3
        tipo3 --- |Serviço Atual| null
        end
    
        subgraph fluxo
            direction LR
                nasa([FTP CPTEC]) -.- tg-gefs-att[<font color=black>tg-gefs-att] --> DB[(DOCDB)]
                tg-gefs-att --> tg-processamento-grade
                tg-gefs-att --> S3
                tg-processamento-grade[<font color=black>tg-processamento-grade] --> tg-chuva-acumulada[<font color=black>tg-chuva-acumulada] --> tg-gefs-ons[<font color=black>tg-gefs-ons]
                tg-processamento-grade --> tg-regressao-grade[<font color=black>tg-regressao-grade]
                tg-processamento-grade --> tg-chuva-prevista[<font color=black>tg-chuva-prevista]

                end
  linkStyle 0,1,2 stroke:#0000,stroke-width:0px;

classDef lambda fill:#d66313;
classDef ecs fill:#d6c756;
classDef hide fill:#0000,stroke:#0000,stroke-width:0px,color:#0000;
classDef hide-font color:#0000;
classDef servico-atual fill:#b213d6;

class tg-processamento-grade,tg-gefs-att,tg-chuva-acumulada,tipo2 ecs
class tg-chuva-prevista,tg-gefs-ons,tg-regressao-grade,tipo1 lambda
class tg-gefs-ons,tipo3 servico-atual
class fluxo,legenda,null hide;
class tipo1,tipo2,tipo3 hide-font;

```
