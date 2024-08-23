# Atividade 1

*"We see three critical differences between programming and software engineering: time, scale, and the trade-offs at play. On a software engineering project, engineers need to be more concerned with the passage of time and the eventual need for change. In a software engineering organization, we need to be more concerned about scale and efficiency, both for the software we produce as well as for the organization that is producing it. Finally, as software engineers, we are asked to make more complex decisions with higher-stakes outcomes, often based on imprecise estimates of time and growth."*
<br>
<br>
## Comentário:
Engenharia de Software está relacionado a uma demanda de atividade mais "dificeis" as quais devem se atentar a eficiência, escala e mais adaptações quanto a mudanças, dentro de periodos indeterminados
<br>
<br>
<br>
**Tempo:** Planejar desde o inicio com o desempenho e adaptação do software no futuro
<br>
**Escala:** Crescimmento conforme a demanda, eficiencia do processo é capaz de acompanhar o aumento de demandas
<br>
**Trade-offs:** São decisões e compensações que os engenheiros de software precisam fazer durante um projeto

---

*"Within Google, we sometimes say, “Software engineering is programming integrated over time.” Programming is certainly a significant part of software engineering: after all, programming is how you generate new software in the first place. If you accept this distinction, it also becomes clear that we might need to delineate between programming tasks (development) and software engineering tasks (development, modification, maintenance). The addition of time adds an important new dimension to programming. Cubes aren’t squares, distance isn’t velocity. Software engineering isn’t programming."5*
<br>
<br>
## Comentário: 

O texto aborda uma distinção importante entre programação e engenharia de software, destacando que, enquanto a programação se foca na criação inicial de software, a engenharia de software envolve um espectro mais amplo de atividades que se estendem ao longo do tempo, como desenvolvimento, modificação e manutenção.

# Atividade 2

## Exemplos de trade-offs com requesitos não funcionais

### 1. Manutenibilidade vs. Desempenho

- **Trade-off:** Um código que é altamente manutenível, com boa modularidade, documentação e uso de padrões de design, pode ser menos otimizado para desempenho. Otimizações de desempenho muitas vezes envolvem técnicas que tornam o código mais complexo e difícil de manter.

- **Exemplo:** Em um sistema de análise de dados, escrever código altamente otimizado para processar grandes volumes de dados rapidamente pode resultar em um código difícil de entender e modificar. Alternativamente, um código bem estruturado e fácil de manter pode não ser o mais rápido.

### 2. Confibialidade vs. Custo 

- **Trade-off:** Garantir alta confiabilidade em um sistema, como redundância em servidores ou hardware de alta qualidade, pode aumentar significativamente os custos do projeto.

- **Exemplo:** Em um sistema de controle industrial, pode-se optar por usar componentes de hardware mais caros e ter redundância em todos os sistemas para garantir que o sistema nunca falhe. No entanto, isso aumenta os custos significativamente, o que pode ser inaceitável para um projeto com um orçamento limitado.

### 3. Tempo de Desenvolvimento vs. Segurança

- **Trade-off:** Aumentar a segurança de um sistema pode exigir mais tempo para desenvolvimento, pois envolve a implementação de protocolos seguros, testes rigorosos e auditorias de código.

- **Exemplo:**  Durante o desenvolvimento de uma aplicação móvel, acelerar o lançamento para atender a uma janela de oportunidade no mercado pode significar sacrificar parte das medidas de segurança, como revisões detalhadas de código e testes de penetração, o que pode resultar em uma aplicação menos segura.

# Atividade 3

## Análise das trade-offs na arquitetura do Uber
![Uber-System-Design-High-Level-Architecture](https://github.com/user-attachments/assets/72989376-50a8-4175-903f-3e5553c88646)

### 1. Eficiência vs. Disponibilidade
-  O uso de um Load Balancer (LB) garante que as requisições de motoristas (supply) e passageiros (demand) sejam distribuídas de forma eficiente entre os servidores. No entanto, o LB pode se tornar um ponto único de falha (SPOF) se não for bem implementado.

### 2. Velocidade vs. Precisão
- Componentes como Kafka, Spark, e Storm são utilizados para processamento em tempo real de dados, como roteamento, detecção de fraudes e cálculo de ETAs (tempo estimado de chegada). O trade-off aqui está entre a velocidade de processamento e a precisão dos dados processados.

### 3. Consistência vs. Disponibilidade
- A arquitetura utiliza RDBMS para armazenamento de dados estruturados e bases de dados distribuídas para diferentes regiões (Node Region 1, 2, 3, etc.). A decisão de usar múltiplas bases de dados distribuídas implica um trade-off entre consistência dos dados e disponibilidade.

### 4. Latência vs. Complexidade
- O sistema é dividido em várias regiões (Region 1, 2, 3, etc.), com células (Cell 57, Cell 2089, etc.) dentro de cada região para gerenciar a correspondência de supply e demand. Esse particionamento reduz a latência ao processar dados localmente, mas aumenta a complexidade do sistema.

### 5. Observabilidade vs. Performance
- O uso de ELK Stack (Elasticsearch, Logstash, Kibana) para análise de logs oferece alta visibilidade e monitoramento, mas pode impactar a performance do sistema devido à sobrecarga de coleta e processamento de logs.

# Atividade 4

## Diagrama de classes UML















