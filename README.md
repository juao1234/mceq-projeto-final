# Projeto Final — Métodos de Computação Experimental e Quantitativa (12576)

Repositório oficial da equipe para o Projeto Final da disciplina **12576 – Métodos de Computação Experimental e Quantitativa** (PUC-Campinas, 2º semestre de 2026).

---

## 1. Proveniência e Dados Obrigatórios da Base Pública

* **Nome da base:** *Artifacts of a Controlled Experiment About the Impact of Microservice API Patterns on Understandability*
* **Autores:** Justus Bogner (Vrije Universiteit Amsterdam), Pawel Wójcik (Independent Researcher) e Olaf Zimmermann (OST – Ostschweizer Fachhochschule)
* **Link original / DOI:** https://doi.org/10.5281/zenodo.10814369 (URL direta: https://zenodo.org/records/10814369)
* **Versão da base:** Versão 2 (publicada em 13/03/2024 — registro Zenodo `10814369`, conceito `10210246`)
* **Data de acesso / download:** 29/10/2026
* **Licença:** Creative Commons Attribution 4.0 International (`CC BY 4.0`) — permite uso acadêmico, adaptação e redistribuição dos dados com atribuição aos autores originais.

---

## 2. Arquivos da Base de Dados (`dados/brutos/`)

Os arquivos originais foram baixados diretamente do Zenodo e mantidos íntegros (sem edição manual) no diretório [`dados/brutos/`](./dados/brutos/):

* `experiment-artifacts.zip`: Pacote original completo baixado do Zenodo (MD5: `43486d360c80146e1080a91f336e48f8`).
* `results-01-raw.csv`: Dados brutos exportados diretamente da ferramenta de questionário online do experimento (LimeSurvey).
* `results-02-cleaned.csv`: Dados pré-processados com respostas completas e codificação automática inicial.
* `results-03-final.csv`: Conjunto de dados final validado pelos autores (66 participantes válidos) com respostas de texto livre codificadas (`0` = incorreto, `1` = correto) e tempos de resposta em segundos.
* `pattern-tasks.md`: Documentação original das 12 tarefas do experimento controlado.
* `LICENSE.md`: Texto integral da licença CC BY 4.0.

---

## 3. Documentação do Marco de 03/11 (Membro 1 — Dados e Repositório)

* **[Parte1_Registro_Base_Dados.md](./Parte1_Registro_Base_Dados.md):** Registro formal da base escolhida, os 5 dados obrigatórios de proveniência e justificativa dos critérios da Seção 3.2 do roteiro.
* **[Parte3_Lista_Variaveis.md](./Parte3_Lista_Variaveis.md):** Dicionário completo de todas as 61 variáveis disponíveis na base (metadados do experimento, variáveis independentes dos 6 padrões `P` vs. `N`, variáveis dependentes de corretude `0`/`1`, tempos em segundos, métrica derivada `TAU` e variáveis demográficas/experiência em escala Likert), detalhando como cada uma foi medida.
