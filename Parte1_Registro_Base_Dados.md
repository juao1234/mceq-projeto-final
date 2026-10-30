# Parte 1 — Registro Oficial da Base de Dados Candidata

**Disciplina:** 12576 – Métodos de Computação Experimental e Quantitativa (PUC-Campinas)  
**Responsável:** Membro 1 (Área de Foco: Dados e Repositório)  
**Marco de Entrega:** 03/11/2026  

---

## 1. Os 5 Dados Obrigatórios da Base

1. **Nome da base e autores:**  
   * **Título:** *Artifacts of a Controlled Experiment About the Impact of Microservice API Patterns on Understandability*  
   * **Autores:** Justus Bogner (Vrije Universiteit Amsterdam), Pawel Wójcik (Independent Researcher) e Olaf Zimmermann (OST – Ostschweizer Fachhochschule).  
   * **Artigo científico associado:** Bogner, J., Wójcik, P., & Zimmermann, O. (2024). *How Do Microservice API Patterns Impact Understandability? A Controlled Experiment*. Proceedings of the IEEE/ACM International Conference on Program Comprehension (ICPC 2024).

2. **Link original ou DOI:**  
   * **DOI:** `10.5281/zenodo.10814369`  
   * **Link oficial do DOI:** https://doi.org/10.5281/zenodo.10814369  
   * **Link direto no Zenodo:** https://zenodo.org/records/10814369  

3. **Versão da base:**  
   * **Versão:** Versão 2 (publicada em 13 de março de 2024; ID do registro: `10814369`; DOI conceitual: `10.5281/zenodo.10210246`).

4. **Data de acesso / download:**  
   * **Data:** 29/10/2026.

5. **Licença:**  
   * **Licença:** Creative Commons Attribution 4.0 International (**CC BY 4.0**).  
   * **Permissões:** Permite livremente o uso acadêmico, compartilhamento, redistribuição no repositório da equipe e adaptação dos dados, exigindo apenas a devida citação dos autores originais.

---

## 2. Arquivos Baixados (Sem Edição Manual)

Os arquivos originais foram salvos intactos na pasta `dados/brutos/` do repositório:

| Arquivo | Tamanho | Descrição |
| :--- | :--- | :--- |
| `experiment-artifacts.zip` | 732 KB | Pacote original completo baixado do Zenodo (MD5: `43486d360c80146e1080a91f336e48f8`). |
| `results-01-raw.csv` | 95 KB | Dados brutos originais exportados da plataforma do experimento (LimeSurvey). |
| `results-02-cleaned.csv` | 48 KB | Dados intermediários filtrados pelo script de pré-processamento original. |
| `results-03-final.csv` | 16 KB | Base validada dos 66 participantes que concluíram o experimento, contendo acerto (`0`/`1`), tempos em segundos e dados demográficos. |
| `pattern-tasks.md` | 11 KB | Enunciados e gabaritos das 12 tarefas aplicadas no experimento controlado. |
| `LICENSE.md` | 19 KB | Licença oficial CC BY 4.0 incluída pelos autores. |

---

## 3. Verificação dos Critérios de Avaliação da Base (Seção 3.2 do Roteiro)

* **Proveniência:** Pacote de replicação oficial depositado no Zenodo pelos próprios autores do experimento controlado, com DOI fixo e artigo publicado no ICPC 2024.
* **Documentação:** Acompanha descrição completa das tarefas (`pattern-tasks.md`) e scripts comentados explicando cada coluna e cálculo das métricas.
* **Licença:** Licença aberta CC BY 4.0 declarada formalmente no Zenodo e no arquivo `LICENSE.md`.
* **Tamanho:** Contém respostas completas de **66 participantes** divididos aleatoriamente em 2 grupos/sequências (34 no Grupo 1 e 32 no Grupo 2), realizando 12 tarefas (totalizando 792 observações de tarefas), garantindo excelente poder estatístico.
* **Variáveis e Medição:** Contém claramente a Variável Independente (presença ou ausência do padrão de API de microsserviços: `P` vs. `N`) e as Variáveis Dependentes medidas automaticamente pela ferramenta LimeSurvey (tempo gasto em segundos em cada tarefa e corretude da resposta `0` ou `1`, além da métrica composta *TAU - Timed Actual Understandability*).
