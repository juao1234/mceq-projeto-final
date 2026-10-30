# Parte 3 — Levantamento de Todas as Variáveis Disponíveis e Forma de Medição

**Disciplina:** 12576 – Métodos de Computação Experimental e Quantitativa (PUC-Campinas)  
**Responsável:** Membro 1 (Área de Foco: Dados e Repositório)  
**Marco de Entrega:** 03/11/2026  
**Base de Dados:** *Artifacts of a Controlled Experiment About the Impact of Microservice API Patterns on Understandability* (`DOI: 10.5281/zenodo.10814369`)

---

## 1. Instrumentação Geral do Experimento Original

Os dados foram coletados pelos autores originais (Bogner, Wójcik e Zimmermann, 2024) por meio de um **experimento controlado online** executado na plataforma **LimeSurvey**.  
* **Participantes:** 66 participantes válidos (após remoção de questionários incompletos onde `lastpage < 29` e remoção de *outliers* de tempo `< 10 s` ou `> 400 s` por tarefa).
* **Desenho de coleta:** Cada participante foi alocado por sorteio (`randnumber` = 1 ou 2) a uma sequência contendo **12 tarefas de compreensão de APIs** (6 padrões de API de microsserviços × 2 cenários por padrão), vendo metade das tarefas **com o padrão (`P`)** e metade **sem o padrão (`N`)**.

---

## 2. Resumo das Variáveis por Papel Metodológico

| Papel no Estudo | Variáveis na Base | Escala / Tipo | Unidade |
| :--- | :--- | :--- | :--- |
| **Variável Independente (VI / Fator)** | Presença do Padrão de API nas tarefas (sufixo `P` = *Com Padrão* vs. `N` = *Sem Padrão*) distribuídas nos 6 padrões (`ER`, `PT`, `WL`, `ME`, `AG`, `RB`) | Categórica Nominal (Binária por tarefa) | Níveis: `P` (*Pattern*) e `N` (*Non-Pattern*) |
| **Variável Dependente 1 (VD1)** | Corretude da resposta nas 24 colunas de tarefa (`ER1P`, `ER1N`, ..., `RB2N`) | Categórica Binária (Dicotômica) | `0` (Incorreta) ou `1` (Correta) — ou `%` de acerto |
| **Variável Dependente 2 (VD2)** | Tempo de resposta nas 24 colunas de duração (`ER1PTime`, `ER1NTime`, ..., `RB2NTime`) | Numérica Contínua (Razão) | Segundos (`s`) |
| **Variável Dependente Composta (VD Principal)** | **TAU** (*Timed Actual Understandability*) — combina acerto e tempo normalizado | Numérica Contínua (Razão/Intervalar) | Escala adimensional de `0.0` a `1.0` |
| **Variáveis de Controle / Moderadoras (Demográficas)** | `DemYearsOE`, `DemAcInd`, `DemBackground`, `DemExperience[SQ001..SQ003]` | Numérica (Razão), Categórica Nominal e Ordinal (Likert 1–5) | Anos, Categorias de Cargo/Setor e Nível 1 a 5 |
| **Variáveis de Controle do Experimento / Metadados** | `id`, `randnumber`, `lastpage`, `startdate`, `datestamp` | Identificadores, Binária e Data/Hora | ID inteiro, Grupo `1`/`2`, Timestamp |

---

## 3. Dicionário Completo de Variáveis e Como Foram Medidas

### 3.1. Metadados e Controle do Experimento (6 colunas em `results-03-final.csv`)

| Nome da Coluna | Significado / Descrição | Tipo e Escala | Como foi medida (Instrumentação) |
| :--- | :--- | :--- | :--- |
| `id` | Identificador único e anônimo do participante. | Inteiro (Nominal / ID) | Gerado automaticamente de forma sequencial pelo sistema LimeSurvey ao iniciar o questionário. |
| `lastpage` | Última página do questionário que o participante alcançou (de 30 páginas totais). | Inteiro (Discreta) | Registrado automaticamente pelo LimeSurvey. Usado no pré-processamento para filtrar apenas participantes que concluíram o estudo (`lastpage >= 29`). |
| `startdate` | Data e hora em que o participante iniciou o experimento. | Data/Hora (`DD.MM.YYYY HH:MM`) | Marcador de tempo (*timestamp*) registrado automaticamente pelo servidor do LimeSurvey no momento de abertura do formulário. |
| `datestamp` | Data e hora em que o participante concluiu/enviou o experimento. | Data/Hora (`DD.MM.YYYY HH:MM`) | Marcador de tempo (*timestamp*) registrado automaticamente pelo servidor do LimeSurvey na submissão da última página. |
| `randnumber` | Grupo/sequência experimental atribuída ao participante (`1` ou `2`). | Categórica Binária (`1` ou `2`) | Sorteio aleatório automático realizado pelo LimeSurvey no início do questionário para balancear a ordem e qual versão (`P` ou `N`) o participante veria em cada tarefa (*crossover design*). |
| `ThanksAndComments` | Comentários livres e feedback opcional sobre o experimento. | Texto livre | Pergunta aberta opcional exibida na última página do questionário. |

*(Nota: O arquivo bruto `results-01-raw.csv` também inclui colunas técnicas auxiliares de auditoria do LimeSurvey: `submitdate`, `startlanguage`, `seed`, `interviewtime` [tempo total em segundos] e tempos de visualização das telas de instruções `groupTime385..389`, `randnumberTime`, `DemYearsOETime`, `DemAcIndTime`, `DemBackgroundTime`, `DemExperienceTime` e `ThanksAndCommentsTime`, todos medidos automaticamente em segundos pelo cronômetro de página do LimeSurvey).*

---

### 3.2. Variáveis de Corretude das Tarefas — VD1 (24 colunas)

Cada código de coluna segue o formato **`[Padrão][Cenário][Tratamento]`**, onde:
* **Padrão (6 padrões de API):**
  * `ER` = *Error Report* (Relatório de Erro estruturado)
  * `PT` = *Parameter Tree* (Árvore de Parâmetros aninhados)
  * `WL` = *Wish List* (Lista de Desejos de atributos na requisição)
  * `ME` = *Metadata Element* (Elemento de Metadados na resposta)
  * `AG` = *API Gateway* (Gateway de API entre clientes e microsserviços)
  * `RB` = *Request Bundle* (Pacote/Lote de Requisições em uma única chamada)
* **Cenário:** `1` (Primeira tarefa do padrão) ou `2` (Segunda tarefa do padrão).
* **Tratamento (Variável Independente):** `P` (*Pattern* — API usa o padrão) ou `N` (*Non-Pattern* — API não usa o padrão).

| Colunas (Com Padrão `P` / Sem Padrão `N`) | Padrão Avaliado e Tarefa | Escala / Valores (no CSV final) | Como foi medida e codificada |
| :--- | :--- | :--- | :--- |
| `ER1P`, `ER1N` | **Error Report (Tarefa 1):** Identificar a causa de um erro HTTP 401 no login da API. | Binária: `0` (erro) ou `1` (acerto); vazia (`NaN`) se o participante era do outro grupo. | Questão de **múltipla escolha** (5 alternativas, 1 correta). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `ER2P`, `ER2N` | **Error Report (Tarefa 2):** Identificar qual campo causou erro de validação usando documentação da API. | Binária: `0` (erro) ou `1` (acerto). | Questão de **múltipla escolha** (5 alternativas, 1 correta). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `PT1P`, `PT1N` | **Parameter Tree (Tarefa 1):** Contar no payload JSON quantos alunos de *Computer Science* estão matriculados. | Binária: `0` (erro) ou `1` (acerto). | Questão de **entrada numérica curta** (resposta correta = `4`). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `PT2P`, `PT2N` | **Parameter Tree (Tarefa 2):** Contar no payload JSON de uma API de cinema quantos filmes de *thriller* existem. | Binária: `0` (erro) ou `1` (acerto). | Questão de **entrada numérica curta** (resposta correta = `2`). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `WL1P`, `WL1N` | **Wish List (Tarefa 1):** Escrever a requisição HTTP/código para buscar apenas 3 atributos de um estudante (`id=20`). | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre (código)**. Respostas padrão foram codificadas via script e variações sintáticas foram avaliadas manualmente pelos autores para gerar `results-03-final.csv`. |
| `WL2P`, `WL2N` | **Wish List (Tarefa 2):** Escrever a requisição HTTP/código para buscar apenas 3 atributos de um evento de calendário (`id=167`). | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre (código)**. Avaliada por script para respostas exatas + inspeção manual pelos autores para variações equivalentes. |
| `ME1P`, `ME1N` | **Metadata Element (Tarefa 1):** Identificar o critério e ordem de classificação dos vídeos retornados pela API. | Binária: `0` (erro) ou `1` (acerto). | Questão de **múltipla escolha** (5 alternativas, 1 correta). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `ME2P`, `ME2N` | **Metadata Element (Tarefa 2):** Identificar o critério e ordem de classificação dos produtos retornados pela API. | Binária: `0` (erro) ou `1` (acerto). | Questão de **múltipla escolha** (5 alternativas, 1 correta). Codificada automaticamente em `0` ou `1` pelo script `01-data-preprocessing.ipynb`. |
| `AG1P`, `AG1N` | **API Gateway (Tarefa 1):** Indicar quais componentes do diagrama precisam mudar se o *Service 3* mudar de IP/endpoint. | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre**. Avaliada via script + revisão manual dos autores (com padrão: apenas `API Gateway`; sem padrão: `Client 1, Client 2, Client 3`). |
| `AG2P`, `AG2N` | **API Gateway (Tarefa 2):** Indicar quais componentes do diagrama precisam mudar se o *MainService* mudar de IP/endpoint. | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre**. Avaliada via script + revisão manual dos autores (com padrão: apenas `API Gateway`; sem padrão: `Web App 1, Mobile App 1, Mobile App 2`). |
| `RB1P`, `RB1N` | **Request Bundle (Tarefa 1):** Escrever a(s) chamada(s) `GET` para buscar 4 clientes (`IDs 5, 9, 13, 24`). | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre (chamada HTTP)**. Avaliada via script + revisão manual dos autores (1 chamada com vírgulas em `P` vs. 4 chamadas separadas em `N`). |
| `RB2P`, `RB2N` | **Request Bundle (Tarefa 2):** Escrever a(s) chamada(s) `DELETE` para remover 4 produtos (`IDs 12, 16, 27, 35`). | Binária: `0` (erro) ou `1` (acerto). | Questão de **texto livre (chamada HTTP)**. Avaliada via script + revisão manual dos autores (1 chamada em lote em `P` vs. 4 chamadas separadas em `N`). |

---

### 3.3. Variáveis de Tempo de Resposta por Tarefa — VD2 (24 colunas)

| Colunas de Tempo | Significado / Descrição | Tipo, Escala e Unidade | Como foi medida (Instrumentação) |
| :--- | :--- | :--- | :--- |
| `ER1PTime`, `ER1NTime`, `ER2PTime`, `ER2NTime` | Tempo gasto nas tarefas do padrão *Error Report*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (mede o tempo exato em segundos desde o carregamento da questão até a submissão da resposta). |
| `PT1PTime`, `PT1NTime`, `PT2PTime`, `PT2NTime` | Tempo gasto nas tarefas do padrão *Parameter Tree*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (em segundos). |
| `WL1PTime`, `WL1NTime`, `WL2PTime`, `WL2NTime` | Tempo gasto nas tarefas do padrão *Wish List*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (em segundos). |
| `ME1PTime`, `ME1NTime`, `ME2PTime`, `ME2NTime` | Tempo gasto nas tarefas do padrão *Metadata Element*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (em segundos). |
| `AG1PTime`, `AG1NTime`, `AG2PTime`, `AG2NTime` | Tempo gasto nas tarefas do padrão *API Gateway*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (em segundos). |
| `RB1PTime`, `RB1NTime`, `RB2PTime`, `RB2NTime` | Tempo gasto nas tarefas do padrão *Request Bundle*. | Numérica Contínua (Razão) — **Segundos (`s`)** | Cronômetro automático de página do LimeSurvey (em segundos). |

> **Regra de higienização aplicada pelos autores nos tempos:** Pontos de dados individuais cuja duração foi inferior a `10 s` (chute sem leitura) ou superior a `400 s` (distração/interrupção externa) foram invalidados na passagem de `results-02-cleaned.csv` para `results-03-final.csv`.

---

### 3.4. Variável Dependente Derivada — `TAU` (*Timed Actual Understandability*)

Embora não esteja gravada como coluna estática no CSV bruto, o notebook oficial `02-data-analysis.ipynb` deriva a variável principal do estudo para cada uma das 24 tarefas (`TAU_ER1P`, `TAU_ER1N`, ..., `TAU_RB2N`):

* **Fórmula de medição:**
  $$\text{TAU}_{i,t} = \text{Corretude}_{i,t} \times \left(1 - \frac{\text{Tempo}_{i,t}}{\max(\text{Tempo}_{t})}\right)$$
  Onde:
  * $\text{Corretude}_{i,t} \in \{0, 1\}$ é o acerto do participante $i$ na tarefa $t$;
  * $\text{Tempo}_{i,t}$ é o tempo (em segundos) gasto pelo participante $i$ na tarefa $t$;
  * $\max(\text{Tempo}_{t})$ é o maior tempo observado entre todos os participantes naquela tarefa (considerando as versões `P` e `N` do mesmo cenário).
* **Interpretação e Escala:** Escala contínua entre `0` e `1`. Se o participante erra a questão, $\text{TAU} = 0$. Se acerta, o valor é tão mais próximo de `1` quanto mais rápido ele tiver compreendido a API em relação ao tempo máximo da tarefa.

---

### 3.5. Variáveis Demográficas e de Experiência Prévia — Controle / Moderadoras (7 colunas)

| Nome da Coluna | Significado / Descrição | Tipo, Escala e Unidade | Como foi medida (Instrumentação) |
| :--- | :--- | :--- | :--- |
| `DemYearsOE` | Anos de experiência geral na área de Tecnologia da Informação (TI). | Numérica (Razão) — **Anos** | Campo numérico aberto autodeclarado pelo participante no bloco demográfico do questionário (valores de `0` a `35` anos). |
| `DemAcInd` | Setor de atuação atual do participante. | Categórica Nominal (`"Academia"`, `"Industry"`, `"Both"`) | Questão de escolha única autodeclarada pelo participante indicando se atua na Academia, na Indústria ou em ambos. |
| `DemBackground` | Cargo ou função principal atual do participante. | Categórica Nominal (`"Student"`, `"Software Engineer"`, `"Researcher"`, `"Software Architect"`, `"Consultant"`, `"Manager"`, `"DevOps Engineer"`, `"Other"`) | Questão de escolha única autodeclarada pelo participante no questionário demográfico. |
| `DemBackground[other]` | Especificação do cargo caso tenha marcado `"Other"` em `DemBackground`. | Texto livre (Nominal) | Campo de texto condicional exibido apenas quando `DemBackground == "Other"` (ex.: `"Enterprise Architect"`, `"Supporter"`). |
| `DemExperience[SQ001]` | Nível de experiência prévia com **Padrões de Projeto de Software** (*Software Design Patterns*, ex.: GoF). | Categórica **Ordinal** (Escala Likert de 1 a 5) | Autoavaliação em escala Likert de 5 níveis: `Novice (1)`, `Beginner (2)`, `Intermediate (3)`, `Advanced (4)`, `Expert (5)`. Convertida para inteiro `1..5` na análise. |
| `DemExperience[SQ002]` | Nível de experiência prévia com **APIs Web / HTTP** (*HTTP APIs*, REST). | Categórica **Ordinal** (Escala Likert de 1 a 5) | Autoavaliação na mesma escala Likert de 5 níveis (`Novice (1)` a `Expert (5)`), convertida para inteiro `1..5`. |
| `DemExperience[SQ003]` | Nível de experiência prévia específica com **Padrões de API para Microsserviços** (*Microservice API Patterns*). | Categórica **Ordinal** (Escala Likert de 1 a 5) | Autoavaliação na mesma escala Likert de 5 níveis (`Novice (1)` a `Expert (5)`), convertida para inteiro `1..5`. |
