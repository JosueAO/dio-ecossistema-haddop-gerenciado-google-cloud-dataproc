### Projeto Big Data usando o Google Cloud Platform (GCP). Configurar o Google Cloud Dataproc, um Hadoop totalmente gerenciado, usando seus créditos gratuitos da GCP.

### Fluxo do desafio:

<p align="center"><img src="./fluxoDesadio.png" width="500"></p>

### A maoir parte do projeto(Desafio) é realizado no portal GCP, mas abaixo está em linha de comando(Cloud Shell) do gcloud para criar o ambiente(Cluster) Dataproc neste projeto:

gcloud dataproc clusters create cluster-desafio-dataproc --enable-component-gateway --region us-central1 --subnet default --zone us-central1-c --master-machine-type n1-standard-4 --master-boot-disk-size 500 --num-workers 3 --worker-machine-type n1-standard-4 --worker-boot-disk-size 500 --image-version 2.0-debian10 --optional-components JUPYTER,ZEPPELIN,ZOOKEEPER --project cosmic-tensor-324421

<h4>seu_usuario@cloudshell:~ (cosmic-tensor-324421)$ </h4> gcloud dataproc jobs submit spark \
> --cluster=cluster-desafio-dataproc \
> --region="us-central1" \
> --class=org.apache.spark.examples.SparkPi \
> --jars=file://usr/lib/spark/examples/jars/spark-examples.jar \
> -- 1000


# Abaixo uma rotina do projeto descrita pela o especialista Marcelo Marques:

<p align="center"><img src="./DIO.png" width="500"></p>

## Desafio GCP Dataproc

O desafio faz parte do curso na plataforma da Digital Innovation One:

__*Criando um ecossitema Hadoop totalmente gerenciado com Google Cloud Platform*__

O desafio consiste em efetuar um processamento de dados utilizando o produto Dataproc do GCP. Esse processamento irá efetuar a contahem das palavras de um livro e informar quantas vezes cada palavra aparece no mesmo.

---

### Etapas do Desafio

1. Criar um bucket no Cloud Storage
1. Atualizar o arquivo ```contador.py``` com o nome do Bucket criado nas linhas que contém ```{SEU_BUCKET}```.
1. Fazer o upload dos arquivos ```contador.py``` e ```livro.txt``` para o bucket criado (instruções abaixo)
    - https://cloud.google.com/storage/docs/uploading-objects

1. Utilizar o código em um cluster Dataproc, executando um Job do tipo PySpark chamando ```gs://{SEU_BUCKET}/contador.py```
1. O Job irá gerar uma pasta no bucket chamada ```resultado```. Dentro dessa pasta o arquivo ```part-00000``` irá conter a lista de palavras e quantas vezes ela é repetida em todo o livro.

### Entrega do Resultado

1. Criar um repositório no GitHub.
2. Criar um arquivo chamado ```resultado.txt```. Dentro desse arquivo, colocar as 10 palavras que mais são usadas no livro, de acordo com o resultado do Job.
3. Inserir os arquivo ```resultado.txt``` e ```part-00000``` no repositório e informar na plataforma da Digital Innovation One.

---

### Obeservação caso venha acontecer:

NOTA: Se o Job mostrar um WARN de Interrupt, basta ignorar. Existe um bug no Hadoop que é conhecido. Isso não impacta no processamento.


