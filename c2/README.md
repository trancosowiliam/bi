# Apache hop
### Pipeline
![pipeline](/c2/pipeline-description.png)

* Generate rows
  * Cria 500 linhas
* Fake Data
  * Preenche as linhas geradas com dados fakes
  * Os dados com sufixo ´temp´ são dados auxiliares para gerar novos campos
* Transform Avaliacao
  * Cria o campo TIPO_AVALIACAO a partir do TIPO_AVALIACAO_TEMP
  * TIPO_AVALIACAO_TEMP é um numero de 0 a 9
  * TIPO_AVALIACAO é um enumerated com os possíveis valores: Professor, Disciplina, Curso
* Transform Status
  * Cria o campo STATUS a partir do STATUS_TEMP
  * STATUS_TEMP é um numero de 0 a 9
  * STATUS é um enumerated com os possíveis valores: Finalizada, Criada, Progresso
* Table output
  * Conecta ao banco de dados e insere os valores criados
  * Os campos com sufixo ´temp´ são ignorados
 
# Database
### Modelagem
| Campo          | Tipo    | Descrição                                                                         |
|----------------|---------|-----------------------------------------------------------------------------------|
| aluno          | varchar | hash do aluno usado no sistema para dar continuidade a uma avaliação em progresso |
| tipo_avaliacao | varchar | [Disciplina, Curso, Professor]                                                    |
| status         | varchar | [Criada, Progresso, Finalizada]                                                   |
| id_avaliacao   | number  | chave estrangeira de avaliação                                                    |
| nota_final     | integer | Média das notas das perguntas objetivas                                           |

### Connection
![connection](/c2/connection_database.png)

### Saída
![output](/c2/database-view.png)

  

