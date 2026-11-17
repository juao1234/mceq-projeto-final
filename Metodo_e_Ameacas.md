# Rascunho da seção Método e Ameaças à validade

> **Estado:** alinhado à explicação da Pessoa 1. O relatório apresenta dois cálculos do efeito bisserial, com tratamentos diferentes dos empates.

## 3 Método

### Base e instrumentação

Utilizamos a versão final pública do pacote *Artifacts of a Controlled Experiment About the Impact of Microservice API Patterns on Understandability*, de Bogner, Wójcik e Zimmermann (Zenodo, DOI: [10.5281/zenodo.10814369](https://doi.org/10.5281/zenodo.10814369), versão 2, licença CC BY 4.0; acesso registrado em 29/10/2026). Os autores originais coletaram as respostas por meio de um experimento controlado on-line no LimeSurvey. A base final (`dados/brutos/results-03-final.csv`) contém 65 participantes; segundo a documentação dos autores, um participante foi removido do conjunto intermediário por apresentar tempos acima de 400 segundos. As respostas livres foram codificadas pelos autores originais como corretas (1) ou incorretas (0), com avaliação manual de algumas respostas.

O experimento cobriu seis padrões de API de microsserviços — Error Report (ER), Parameter Tree (PT), Wish List (WL), Metadata Element (ME), API Gateway (AG) e Request Bundle (RB) — em dois cenários por padrão. A sequência experimental (`randnumber`) distribuiu aleatoriamente as versões com padrão (P) e sem padrão (N) entre tarefas. Cada participante é a unidade de análise e contribui com observações das duas condições; a sequência é registrada para contextualizar possíveis efeitos de ordem.

### Variáveis, limpeza e unidade de análise

A variável independente é a condição da API (P ou N). A variável dependente confirmatória é a proporção de respostas corretas por participante em cada condição, calculada pela média das respostas binárias válidas das tarefas correspondentes. A comparação principal é feita entre as duas proporções do mesmo participante. A base contém 65 pares; 61 participantes têm as 12 respostas e quatro têm 11, por quatro campos ausentes (IDs 63 e 65 em WL1P, ID 89 em ME2P e ID 80 em AG1N). Cada média de condição usa as respostas válidas disponíveis naquela condição. Não aplicamos limpeza nova à análise principal: usamos `results-03-final.csv`, no qual os autores já removeram o participante de ID 54. Oito durações abaixo de 10 segundos foram mantidas na análise principal, conforme o protocolo, e excluí-las foi uma análise de sensibilidade.

Os tempos de resposta e a métrica derivada TAU não compõem a hipótese confirmatória. As análises por padrão, por sequência e com filtros adicionais de duração são exploratórias. A lista de variáveis chama TAU de variável principal do estudo original, mas o protocolo da equipe e a análise da Pessoa 1 definem corretude como a variável dependente desta reanálise.

### Análise estatística

O teste principal é o *t* pareado bilateral sobre as diferenças individuais (P − N), com α = 0,05. Cada participante contribui com uma proporção em cada condição, de modo que há 65 pares. A normalidade das diferenças foi examinada com gráfico e teste de Shapiro–Wilk (W = 0,893; p = 3,8 × 10⁻⁵). Embora a normalidade tenha sido rejeitada, a distribuição é discreta, com 26 diferenças nulas; a assimetria reportada é moderada (0,52), não foram identificados valores extremos, e n = 65. A equipe manteve o *t* pareado como análise principal e executou Wilcoxon dos postos sinalizados bilateral como verificação de robustez. Para o *t*, são reportados a diferença média, IC de 95%, *d*<sub>z</sub> e IC do efeito. Para Wilcoxon, a Pessoa 1 reporta a correlação bisserial calculada pela fórmula apresentada em aula para a amostra completa (n = 65), r = 0,56, com IC bootstrap. Também apresenta, como valor complementar, r = 0,71 ao excluir os 26 empates e calcular o efeito nos 39 participantes com diferenças não nulas. O bootstrap usa semente 2026 e 10.000 reamostragens, conforme o script da Pessoa 1. Os dois valores usam conjuntos diferentes e devem ser rotulados assim na tabela.

Como análise exploratória, a equipe também estimou a diferença balanceada entre sequências; comparou as diferenças por sequência; reaplicou aos tempos o filtro de 10–400 segundos; e comparou corretude por padrão com McNemar exato e correção de Holm. Essas análises não substituem nem alteram a hipótese confirmatória. A interpretação será restrita às tarefas e aos participantes da base pública, sem generalizar o resultado para todas as APIs de microsserviços.

## 5 Ameaças à validade

**Validade de conclusão.** A análise tem 65 participantes; quatro respostas de tarefa estão ausentes e, portanto, quatro médias de condição são calculadas com cinco tarefas em vez de seis. As proporções por participante assumem valores discretos e 26 das 65 diferenças são zero; Shapiro–Wilk rejeitou normalidade. A equipe manteve o *t* pareado pela robustez da média com 65 pares e executou Wilcoxon como verificação, reportando efeito e incerteza. A sensibilidade que exclui oito respostas com duração abaixo de 10 segundos levou à mesma decisão, reduzindo a preocupação de que esses tempos determinem a conclusão. Ainda assim, a amostra limita a precisão e as estimativas devem ser interpretadas com seus intervalos de confiança.

**Validade interna.** A comparação pode ser influenciada pela ordem das tarefas, aprendizagem ou fadiga. Dentro de cada sequência, a condição está confundida com a versão da tarefa que recebe o padrão; o contrabalanceamento entre as duas sequências (35 e 30 participantes) é o que compensa diferenças de dificuldade entre versões. A análise agregada não separa completamente efeitos de sequência, padrão e cenário. A equipe comparou as diferenças entre sequências como sensibilidade, mas essa comparação não elimina confundimento residual nem substitui um modelo que inclua participante e tarefa. A conclusão deve se limitar à diferença observada neste desenho contrabalanceado.

**Validade de construção.** Acertar uma tarefa é uma medida operacional de compreensão, mas não representa todos os aspectos da compreensibilidade, da facilidade de uso ou da qualidade de uma API. Além disso, respostas livres foram codificadas pelos autores originais, incluindo avaliações manuais de algumas respostas; não reavaliamos essa codificação. As conclusões serão formuladas em termos de corretude nas tarefas observadas.

**Validade externa.** Os dados vêm de um único experimento publicado, com participantes, APIs, tarefas e padrões específicos. O tamanho e a composição da amostra limitam a generalização para outros profissionais, domínios ou implementações de microsserviços. O estudo é uma reanálise de dados públicos e não uma nova replicação; os resultados devem ser apresentados como preliminares e circunscritos a esse contexto.

## Apresentação consistente do efeito de Wilcoxon

Os valores r = 0,56 e r = 0,71 não são resultados contraditórios: r = 0,56 é calculado na amostra completa (n = 65), pela função indicada no slide da disciplina; r = 0,71 é calculado apenas nos 39 participantes com diferenças não nulas, excluindo os 26 empates. Na tabela final, identificar explicitamente o segundo como “0,71 sem os zeros (n = 39)”, como previsto pela Pessoa 1. Manter o IC bootstrap associado ao cálculo de n = 65 e evitar sugerir que o IC também se refere ao cálculo sem empates, a menos que esse intervalo seja calculado separadamente.

Depois, basta transferir o método para o template ACM e conferir com a Pessoa 3 se amostra, métrica, sinal P − N, teste e números usados em Resultados são os mesmos.
