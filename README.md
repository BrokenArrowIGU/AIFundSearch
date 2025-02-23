# AIFundSearch
# Referencia: https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html

Nesse Repo, faço o uso e implementação do AI Search Azure.

São necessários vários pontos para implementação do mesmo, criação do AI Services, Storage, para então implementação do AI Search.

1° Iniciando pelo AI Search, dentro do portal da Azure, buscamos o referido e criamos o resource com os Seguintes Parâmetros:

Subscription: Deixamos a default;

Resource group: Selecionar a de preferencia (No caso de já possuir uma) ou criamos uma nova no Create new;

Service name: Nome de preferencia;

Location: Preferencialmente as regiões East US, devido ao custo reduzido da implementação;

Princing: Atentar-se para ser a BASIC, devido a custos;

Após esses passos clickar em Review + Create.

2° Para o AI Services, seguimos os seguintes passos:

Subscription: Deixamos a default;

Resource group: Selecionar a de preferencia (No caso de já possuir uma) ou criamos uma nova no Create new;

Region: a mesma do AI Search;

Name: Nome de preferencia;

Princing: Standard S0;

Não esquecer de assinalar a aceitação dos termos, após  Review + Create;

3° Por ultimo, geramos o Storage Account: 

Subscription: Deixamos a default;

Resource group: Selecionar a de preferencia (No caso de já possuir uma) ou criamos uma nova no Create new;

Storage account name: um nome único, todo em letras minusculas, para o storage;

Location: EAST US ou EAST US 2;

Performace: Standard (reduzimos o custo, sem contar que não há necessidade da premium para essa rápida aplicação);

Redundancy: LRS (baixo custo);

Após, Review e Create. Após o Deploy completar, buscar a guia de Configurations e modificar o Allow Blob anonymous access para Enable, esse passo é necessário para nossa implementação.

Com esses passos podemos seguir para o Deploy dos documentos que se encontram nas referencias.
Dentro do container, criamos um novo com nome : "coffeereviews", puclic access level: Coutainer, Advanced: sem alterações. Após isso utilizamos o Upload, para anexar os arquivos baixados. Após concluído vamos até o Overview e Import data.
No Connect to your data, dentro da Data Source selecionamos Azure Blob Storage, onde completamos da seguinte forma:

Data Source: Azure Blob Storage;

Data source name: coffeecustomerdata;

Data to extract: Contend and metadata;

Parsing mode: Default;

Connection string: Selecione a coffee-reviews;

Demais itens podem ser deixados da forma padrão;

No Add cognitive skills: 

Attach AI Services selecione o AI Services;

No Add Enrichments substitua o Skillset name para coffee-skillset;

Acione o checkbox do OCR;

Source data field: merged_content;

Enrichment granularity level para Pages( 5000 character chuncks).

Selecionar Extract location names, Extract key phases, Detect sentiment, Generate tags from images, Generate captions from images;

No Save enrichments to a knowledge store, selecione: Image projections, Documents, Pages, Key phrases, Entities, Image details Image references;

Azure blob projections Documents, selecionando uma conecxão existente;

Index name: coffee-index;

Marque o Retrievable, Filterable e Searchable;

No Create an indexer, troque o nome do Indexer para coffee-indexer;

Deixe o Schedule on Once e no Advanced Options, deixe o Base-64 Encode Keys, após Submit;

Após esses parametros serem implementados é possivel verificar os Indexers e realizar o Search explorer.













