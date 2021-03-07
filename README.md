# Modelagem de Dados CVM utilizando Dataform

## Projeto

Esse projeto tem por objetivo utilizar o Dataform para realizar a modelagem de dados brutos do [Portal de Dados Abertos CVM](http://dados.cvm.gov.br/) em uma modelagem de fatos e dimensões, a [modelagem estrela](https://en.wikipedia.org/wiki/Star_schema). Esses dados dizem respeito a dados históricos de fundos de investimento referentes a instrução da [CVM 555](http://dados.cvm.gov.br/dataset/emissores/resource/b2ef23f2-0196-48b7-af0b-40d5f3b2ff7c): dados de adminstrador, gestor do fundo, classificação dos fundos quanto a classe e rentabilidade. 

## Dataform

[Dataform](https://dataform.co/) é um aplicativo para gerenciar dados no BigQuery, Snowflake, Redshift e outros data warehouses. Ele permite que as equipes de dados criem pipelines de transformação de dados escalonáveis, testados e baseados em SQL, usando o controle de versão e as melhores práticas inspiradas na engenharia.

Para este projeto especificamente vamos explorar a integração do Dataform com o BigQuery.

## Arquitetura

![Untitled Diagram (2)](https://user-images.githubusercontent.com/52939036/110257298-06b30580-7f7c-11eb-94ef-2dab26fcf9a7.png)

## Modelagem dos dados CVM 555

Os dados foram modelados conforme a modelagem estrela, com uma tabela fato e quatro dimensões.

![Untitled Diagram (1)](https://user-images.githubusercontent.com/52939036/110255038-994da780-7f70-11eb-947f-498f6b67fbb7.png)


## Estrutura do Projeto

Com o objetivo de acelar o desenvolvimento a estrutura do projeto foi desenvolvida utilizando o [CookieCutter Template Dataform Projects](https://github.com/oliveiraJessica/cookiecutter-dataform).

```shell
├── definitions         <- Pasta principal do projeto.
    ├──00_source        <- Pasta onde declara-se os dados de entrada do sistema.
        ├──raw          <- Pasta onde estão os dados brutos da CVM
    ├──01_staging       <- Pasta onde ocorrem as transformações de dados intermediárias.
    ├──02_tests         <- Pasta de testes do projeto.
        ├──unit         <- Pasta de testes unitários: testam a lógica da modelagem.
    ├──03_reports       <- Pasta que contém os resultados da modelagem (fatos, dimensões).
        ├──refined      <- Dados modelados em fatos e dimensões.
        ├──report_views <- Views criadas com base nos dados modelados.
├──.gitignore           <- .gitignore
├── README.md           <- README de instruções do projeto.
├── dataform.json       <- Arquivo base de configuração do dataform.
├── environments.json   <- Arquivo de ambientes de desenvolvimento.
├── package-lock.json   <- Arquivo de configurações do npm.
├── package.json        <- Arquivo de instalação do dataform.
        
```
