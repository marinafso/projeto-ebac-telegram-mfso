# projeto-ebac-telegram-mfso


INTRODUÇÃO

O objetivo deste relatório é realizar a análise de mensagens enviadas em um grupo do Telegram. Para isso foi criado um bot com o objetivo de armazenar as mensagens. Os dados coletados foram acessados por meio da API de bots do Telegram e posteriormente analisados através de consultas SQL por meio do sistema AWS Athena.

BIBLIOTECAS

getpass
json
requests
datetime
pandas
matplotlib.pyplot
seaborn

ESTRUTURA

INGESTÃO DE DADOS: Neste processo, os dados transacionais são ingeridos no ambiente analítico. Assim, os dados obtidos pela API do Telegram são enviados para uma API Web da AWS através de um webhook. Nesta etapa eles ainda se encontram no formato original, sem nenhuma modificação de sua estrutura. No sistema AWS, foi criada uma função Lambda para redirecionar os dados, em formato JSON para armazenamento em buckets do AWS S3.

ETL: Nesta etapa foi feita a manipulação (extraction, transformation and loading) dos dados ingeridos na etapa anterior. Foi criada outra função Lambda que realiza o processo contínuo de data wrangling, onde será feita a limpeza, alteração de formato e particionamento dos dados. Em seguida, os dados enriquecidos são enviados para outro bucket do AWS S3 onde podem ser consultados. A criação de uma função do AWS Event Bridge permite essa função lambda seja executada rotineiramente.

ANALYTICS: Visualização dos dados obtidos através de consultas por SQL e gráficos.
     
