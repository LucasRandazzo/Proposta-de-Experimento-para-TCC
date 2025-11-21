# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Avaliação de um Software com Interface Gráfica para Mineração Automatizada de Repositórios GitHub e Análise de Métricas de Pull Requests utilizando Paralelismo e Checkpoints

### 1.2 ID / código
EXP-GH-METRICS-2025-01

### 1.3 Versão do documento e histórico de revisão
| Versão | Data       | Descrição                             |
|--------|------------|----------------------------------------|
| v1.0   | 2025-11-21 | Criação inicial do plano de experimento |

### 1.4 Datas (criação, última atualização)
- **Criação:** 21/11/2025  
- **Última atualização:** 21/11/2025  

### 1.5 Autores
- **Lucas Randazzo** – Engenharia de Software – lucasrandazzo2@gmail.com

### 1.6 Responsável principal (PI)
**Lucas Randazzo**

### 1.7 Projeto / iniciativa relacionada
Este experimento faz parte da proposta de desenvolvimento de um **software instalável com interface gráfica**, cujo objetivo é facilitar a mineração de repositórios GitHub e o cálculo de métricas de Pull Requests para fins de análise empírica em Engenharia de Software.

---

## 2. Contexto e problema

### 2.1 Descrição do problema / oportunidade
Pull Requests (PRs) são elementos centrais no processo de revisão de código em projetos GitHub, influenciando diretamente qualidade, colaboração e eficiência no desenvolvimento de software. No entanto, minerar PRs em larga escala para fins de pesquisa apresenta várias dificuldades:

- APIs do GitHub exigem conhecimentos técnicos avançados;
- a coleta manual é lenta e propensa a erros;
- processos longos podem ser interrompidos e precisariam ser retomados;
- pesquisadores iniciantes enfrentam barreiras para extrair e analisar métricas de PRs.

Assim, surge a oportunidade de desenvolver um **software com interface gráfica**, capaz de:

- automatizar a mineração de repositórios;
- extrair, filtrar e consolidar métricas de PRs;
- oferecer melhor observabilidade (progresso, logs, status);
- permitir retomada segura via checkpoints;
- reduzir barreiras para uso por pesquisadores e profissionais.

O problema central é:

> **Como avaliar se um software com interface gráfica melhora a acessibilidade, eficiência e confiabilidade na mineração de repositórios GitHub, mantendo a qualidade das métricas coletadas?**

---

### 2.2 Contexto organizacional e técnico
O experimento será realizado em contexto acadêmico, no âmbito de um curso de Engenharia de Software. O software a ser avaliado está em fase de concepção e deverá integrar:

- uma interface gráfica amigável ao usuário;
- um pipeline automatizado de consultas à API do GitHub;
- execução paralela para reduzir tempos de coleta;
- mecanismos de checkpoint para retomada confiável de execuções.

O foco não é apenas a implementação, mas **avaliar experimentalmente** se essa abordagem traz benefícios reais frente aos métodos tradicionais de mineração, mais técnicos e pouco acessíveis.

---

### 2.3 Trabalhos e evidências prévias

#### **Evidências internas — Laboratório 03 (Disciplina: Laboratório de Experimentação de Software)**  
O experimento se apoia no trabalho realizado no **Laboratório 03** da disciplina de *Laboratório de Experimentação de Software*, disponível em:  
🔗 **https://github.com/o-romeroo/lab-experimentacao-03**

Esse laboratório teve como objetivo analisar métricas de Pull Requests em repositórios populares do GitHub, seguindo critérios como:

- PRs com status MERGED ou CLOSED;  
- pelo menos uma revisão humana;  
- tempo mínimo de análise de 1 hora;  
- métricas de tamanho, tempo, descrição e interação.

Foram respondidas questões de pesquisa sobre como tamanho do PR, tempo de análise, interações e descrição influenciam a aceitação do PR ou o número de revisões.  
Esse estudo evidenciou a **importância de métricas de PRs** e **as dificuldades práticas de realizar essa mineração manualmente**, motivando o desenvolvimento de um software automatizado.

---

#### **Evidências externas — literatura acadêmica**

A literatura em Mineração de Repositórios de Software (MSR) e Code Review destaca:

- **Importância dos PRs como artefatos de colaboração e qualidade**  
- **Desafios de mineração manual**  
- **Fatores que influenciam a aceitação de PRs**

Principais referências:

1. **Rahman & Roy (2014)** — *An Insight into the Pull Requests of GitHub*  
   🔗 https://dl.acm.org/doi/10.1145/2597073.2597121  
   Estuda fatores que diferenciam PRs aceitos de rejeitados em dezenas de projetos open source.

2. **Kalliamvakou et al. (2014)** — *The Promises and Perils of Mining GitHub*  
   🔗 https://chisel.cs.uvic.ca/pubs/kalliamvakou-MSR2014.pdf  
   Discute limitações dos dados da plataforma e riscos ao minerar GitHub sem critérios rigorosos.

3. **Yang et al. (2024)** — *A Survey on Modern Code Review: Progresses, Challenges and Opportunities*  
   🔗 https://github.com/watreyoung/MCR-Survey  
   Apresenta o estado da arte em revisão de código moderna.

4. **Vidoni (2022)** — *A systematic process for Mining Software Repositories*  
   🔗 https://www.sciencedirect.com/science/article/pii/S0950584921002317  
   SLR sobre técnicas e desafios da mineração de repositórios.

5. **Wessel et al. (2023)** — *GitHub Actions: The Impact on the Pull Request Process*  
   🔗 https://www.ime.usp.br/~gerosa/papers/Wessel_EMSE_Actions.pdf  
   Investiga como automações afetam PRs.

Essas evidências reforçam a relevância científica do tema e a necessidade de ferramentas de mineração mais acessíveis e automatizadas.

---

### 2.4 Referencial teórico e empírico essencial

O experimento fundamenta-se em quatro eixos:

#### **(1) Mineração de Repositórios de Software (MSR)**  
Base teórica para extrair e analisar artefatos como PRs.  
Referência:  
🔗 Kalliamvakou et al. (2014) – https://chisel.cs.uvic.ca/pubs/kalliamvakou-MSR2014.pdf

#### **(2) Métricas de Pull Requests**  
Métricas como tamanho, interação e tempo de análise são amplamente utilizadas na literatura para caracterizar processos de revisão.  
Referência:  
🔗 Rahman & Roy (2014) – https://dl.acm.org/doi/10.1145/2597073.2597121

#### **(3) Paralelismo e Tolerância a Falhas**  
Conceitos herdados de sistemas distribuídos orientam o uso de paralelismo e checkpoints para lidar com execuções longas.

#### **(4) Interfaces gráficas e usabilidade**  
GUI melhora observabilidade e acessibilidade em ferramentas técnicas.  
Baseado em princípios clássicos de IHC (Norman, Nielsen).

---



