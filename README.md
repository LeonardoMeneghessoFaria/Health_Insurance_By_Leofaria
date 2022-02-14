# Insurance All

Classificação dos clientes mais prováveis para comprar seguro de veículo dentro de uma base de dados utilizando aprendizado de máquina.

![machine-learning](https://opencadd.com.br/wp-content/uploads/2021/02/machine-redimensionado.jpg)

# Problema de Negócio

A Insurance All é uma empresa que oferece seguro de saúde para seus clientes e a equipe de produto está analisando a possibilidade de oferecer um novo produto que seria o seguro de carros. Os clientes deste novo seguro de automóvel devem pagar anualmente um valor à Insurance All para obter um valor segurado pela empresa, destinado aos custos de um eventual acidente ou dano ao veículo.

Insurance All entrevistou cerca de 380.000 clientes sobre o interesse em aderir a um novo produto de seguro automóvel no ano passado. Todos os clientes demonstraram interesse ou não em adquirir o seguro de automóvel e essas respostas foram salvas em um banco de dados juntamente com outros atributos dos clientes.

A equipe de produto selecionou 127 mil novos clientes que não responderam à pesquisa para participar de uma campanha, na qual receberão uma oferta do novo produto seguro automóvel. A oferta será feita pela equipe de vendas por meio de ligações telefônicas. No entanto, a equipe de vendas tem capacidade para realizar 20.000 atendimentos no período da campanha.

# Desafio

O desafio seria construir um modelo que preveja se o cliente estaria ou não interessado em seguro de automóvel.

Como resultado da minha consultoria, preciso apresentar um modelo que mostre um ranking de clientes que comprariam um seguro de carro e responda as seguintes perguntas:

 1. Os atributos mais relevantes dos clientes interessados em adquirir um seguro automóvel.
 
 2. Qual a porcentagem de clientes interessados em adquirir um seguro de automóvel que a equipe de vendas poderá contatar fazendo 20.000 ligações?
 
 3. E se a capacidade da equipe de vendas aumentar para 40.000 ligações, qual a porcentagem de clientes interessados em adquirir um seguro de automóvel que a equipe de vendas poderá contatar?
 
 4. Quantas ligações a equipe de vendas precisa fazer para entrar em contato com 80% dos clientes interessados em adquirir um seguro auto?

# Suposições

- Os canais de venda de apólices mais utilizados foram telefone, e-mail e celular.
- Todos os clientes estavam acima da idade mínima para dirigir.

# Lista de Atributos

| Atributos                        | Descrições                                                     |
| -------------------------------- | ------------------------------------------------------------ |
| Id                               | Um id que representa um cliente|
| Gender                           | Sexo do cliente|
| Age                              | Idade do cliente|
| Driving_License                  | 0 : Cliente não possui DL, 1 : Cliente já possui DL|
| Region_Code                      | Código da região do cliente|
| Previously_Insured               | 1 : Cliente já possui Seguro de Veículo, 0 : Cliente não possui Seguro de Veículo|
| Vehicle_Age                      | Idade do Veículo|
| Vehicle_Damage                   | 1 : O cliente teve seu veículo danificado no passado. 0 : O cliente não teve seu veículo danificado no passado.|
| Annual_Premium                   | Valor que o cliente pagou à empresa pelo seguro saúde anual|
| PolicySalesChannel               | Código anônimo para o canal de contato com o cliente|
| Vintage                          | Número de dias, o cliente foi associado à empresa|
| Response                         | 1 : O cliente está interessado, 0 : O cliente não está interessado|

# Estratégia de Solução

O método que apliquei no projeto foi o CRISP-DM:
- Step 01. Descrição dos dados: O objetivo é usar métricas estatísticas para identificar outliers no escopo do negócio.

- Step 02. Feature Engineering: Derive novos atributos com base nas variáveis originais para descrever melhor o fenômeno a ser modelado.

- Step 03. Filtragem dos Dados: Filtre as linhas e selecione as colunas que não contêm informações para modelagem ou não correspondem ao escopo do negócio.

- Step 04. Análise Exploratória dos Dados: Explore os dados para encontrar insights e entender melhor o impacto das variáveis no aprendizado do modelo.

- Step 05. Preparação dos Dados: Prepare os dados para que os modelos de machine learning possam aprender um comportamento específico.

- Step 06. Seleção de Features: Seleção dos atributos mais significativos para treinar o modelo.

- Step 07. Machine Learning Modeling: Treinamento de modelo de machine learning.

- Step 08. Hyperparameter Fine Tunning: Escolha os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.

- Step 09. Converta o desempenho do modelo em valores de negócios: Converta o desempenho do modelo em um resultado de negócios.

- Step 10. Deploy do Modelo em Produção: Publique o modelo em um ambiente de nuvem para que outras pessoas ou serviços possam usar os resultados para melhorar a decisão de negócios.

- Step 11. Google Sheets: Criação de botão de planilhas do google para mostrar a pontuação do cliente.

# Três principais Insights para o time de negócio

- Hipótese 3 - O local de residência influi na decisão de contratar um seguro de carro.

TRUE: O local de residência influi

- Hipótese 6 - Pessoas com veículos mais novos tem maior tendência a contratar seguro de carro.

FALSE: Pessoas com veículos entre 1 e 2 anos tendem a contratar

- Hipótese 8 - Pessoas sem carta de motorista tendem a nao querer o seguro de carro.

TRUE: Pessoas sem carta de motorista tendem a nao querer o seguro de carro.

# Machine Learning aplicados

Os testes foram realizados usando os seguintes algoritmos:

KNN Classifier

Logistic Regression

Extra Trees Classifier

Random Forest Classifier

XGBoost Classifier

Naive Bayes Classifier

LGBM Classifier

# Machine Learning Model Performance

- Single Performance

|Model Name                    |	Precision_at_k |Recall_at_k |
| -----------------------------|----------------|------------|
|LGBM Classifier               |0.333933        |0.707671	   |
|XGBoost Classifier	           |0.333433	       |0.706612	   |
|Random Forest Classifier	     |0.306385        |0.649290	   |
|Extra Trees Classifier	       |0.302985        |0.642085    |
|Naive Bayes Classifier	       |0.296485	       |0.628311	   |
|KNN Classifier	               |0.295685	       |0.626616	   |
|Logistic Regression Classifier|0.289486	       |0.613477	   |

- Real Performance - Cross Validation

|Model Name                    |	Precision_at_k |Recall_at_k    |
| -----------------------------|----------------|---------------|
|LGBM Classifier               |0.311 +/- 0.001 |0.83 +/- 0.002	|
|XGBoost Classifier	           |0.309 +/- 0.001	|0.827 +/- 0.002|
|Random Forest Classifier	     |0.293 +/- 0.002 |0.783 +/- 0.005|
|Extra Trees Classifier	       |0.29 +/- 0.002  |0.774 +/- 0.005|
|Naive Bayes Classifier	       |0.291 +/- 0.001	|0.776 +/- 0.003|
|KNN Classifier	               |0.285 +/- 0.002	|0.762 +/- 0.005|
|Logistic Regression Classifier|0.277 +/- 0.002	|0.74 +/- 0.006	|

O LGBM Classifier tem o melhor desempenho e é mais leve que os demais classificadores então ele foi escolhido para continuar o projeto.

- Final Performance - Hyperparameter Fine Tunning Cross Validation

Depois de encontrar os melhores parâmetros para o modelo por meio do método de pesquisa aleatória, as métricas finais para o modelo foram as seguintes:

|Model Name                    |	Precision_at_k |Recall_at_k    |
| -----------------------------|----------------|---------------|
|LGBM Classifier               |0.305 +/- 0.0   |0.814 +/- 0.0 	|
|LGBM Classifier               |0.305 +/- 0.0	  |0.814 +/- 0.001|
|LGBM Classifier               |0.311 +/- 0.0   |0.832 +/- 0.002|
|LGBM Classifier               |0.305 +/- 0.0   |0.814 +/- 0.001|
|LGBM Classifier               |0.311 +/- 0.001 |0.83 +/- 0.002 |

# Desempenho do modelo em valores de receita

Com o modelo construído e utilizado, consigo responder as perguntas iniciais do desafio.

1. Os atributos mais relevantes dos clientes interessados em adquirir um seguro automóvel.
R: Os atributos mais relevantes são: "vintage", "annual_premium", "age", "region_code", "vehicle_damage", "policy_sales_channel".
 
2. Qual a porcentagem de clientes interessados em adquirir um seguro de automóvel que a equipe de vendas poderá contatar fazendo 20.000 ligações?
R: O percentual de clientes interessados realizando 20.000 ligações chegará a 69% dos clientes. 

3. E se a capacidade da equipe de vendas aumentar para 40.000 ligações, qual a porcentagem de clientes interessados em adquirir um seguro de automóvel que a equipe de vendas poderá contatar?
R: O percentual de clientes interessados realizando 40.000 ligações chegará a 90% dos clientes.

4. Quantas ligações a equipe de vendas precisa fazer para entrar em contato com 80% dos clientes interessados em adquirir um seguro auto?
R:








