# Parte 2 - Protocolo de Pesquisa

**Disciplina:** 12576 - Métodos de Computação Experimental e Quantitativa (PUC-Campinas)  
**Equipe:** Augusto Fidélis dos Santos Custódio; Lucca Schroelder Scovini; João Pedro Pires de Andrade  
**Marco:** 03/11/2026  

## Problema e pergunta de pesquisa

Padrões de projeto para APIs de microsserviços são propostos para reduzir a complexidade de uso e compreensão das APIs, mas é necessário verificar empiricamente se a presença desses padrões altera o desempenho em tarefas de compreensão. A pergunta é: **APIs que utilizam padrões de projeto para microsserviços produzem desempenho diferente em tarefas de compreensão quando comparadas a APIs sem esses padrões?**

## Hipóteses

**H0:** a média de corretude das tarefas é igual nas condições com padrão (`P`) e sem padrão (`N`), isto é, μP = μN.  
**H1 (bilateral):** a média de corretude difere entre as condições `P` e `N`, isto é, μP ≠ μN.

## Variáveis e desenho

**VI:** condição da API, com dois níveis: `P` (com padrão) e `N` (sem padrão).  
**VD principal:** proporção média de respostas corretas por participante, calculada a partir das variáveis binárias de corretude (`0` = incorreta; `1` = correta).  
**Unidade de análise:** participante. A base final contém 65 participantes (35 na sequência 1 e 30 na sequência 2); todos possuem observações nas duas condições.  
**Desenho:** experimento controlado publicado, com alocação aleatória de sequência e comparação pareada/blocada por participante. Cada participante respondeu tarefas nas condições `P` e `N`; os participantes são os blocos. Serão utilizadas as respostas válidas disponíveis por condição, registrando os valores ausentes.

**Controles/moderadoras:** sequência experimental (`randnumber`), padrão avaliado, cenário da tarefa e experiência declarada com padrões de projeto, APIs/HTTP e padrões de API para microsserviços. Esses fatores serão considerados na interpretação e em análises exploratórias, não como hipóteses confirmatórias deste protocolo.

## Base e mudança em relação à Ficha da Semana 4

Base pública: *Artifacts of a Controlled Experiment About the Impact of Microservice API Patterns on Understandability*, Bogner, Wójcik e Zimmermann; Zenodo DOI `10.5281/zenodo.10814369`; versão 2; acesso em 29/10/2026; licença CC BY 4.0. A versão final utilizada contém 65 participantes; o ID `54` foi removido na etapa final por tempos acima de 400 s.

A Ficha da Semana 4 propunha comparar as estratégias **Overlap** e **TextRank** em listas de funcionalidades geradas a partir de Java/Javadoc, usando acurácia percebida em escala Likert. Essa hipótese não pode ser testada com a base pública escolhida, que não contém essas estratégias, projetos Java ou avaliações Likert. O tema foi adaptado, antes da análise, para a comparação `P` versus `N` em APIs de microsserviços, usando a corretude objetiva disponível na base. A mudança preserva o foco em compreensão e comparação experimental de técnicas/representações de software.

## Tipo de estudo, teste e incerteza

O estudo é um **experimento publicado**, não observacional, pois os participantes foram distribuídos a sequências experimentais pelos autores originais. O teste confirmatório previsto é o **teste t pareado** sobre a diferença individual entre a corretude média em `P` e em `N`, com `α = 0,05`. Será reportado o p-valor, a diferença média, o tamanho de efeito de Cohen para dados pareados (`d_z`) e IC de 95% da diferença média. Se os pressupostos do teste t forem inadequados, será utilizado o teste de Wilcoxon para amostras pareadas, com tamanho de efeito compatível e IC por bootstrap. Análises por padrão de API, tempo ou TAU serão exploratórias e identificadas como tais.

## Ameaças iniciais à validade

**Conclusão:** amostra final moderada, valores ausentes e possível não normalidade das diferenças; serão reportados ICs, dispersão e teste alternativo. **Interna:** efeitos de ordem, padrão e cenário podem influenciar a comparação; a sequência será controlada/descritiva e a aleatorização original será informada. **Construção:** corretude é uma aproximação de compreensibilidade e não captura toda a experiência do usuário; tarefas e codificação foram definidas pelos autores originais. **Externa:** os resultados se referem ao contexto, às APIs e aos participantes do experimento original, não a todas as APIs de microsserviços.
