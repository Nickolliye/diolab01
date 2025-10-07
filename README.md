# Projeto de Previsão de Preços de Carros Usados

Este projeto foi criado como parte do curso Formação Microsoft Azure AI Fundamentals (AI-900) pela DIO. Ele demonstra o processo de ponta a ponta para a criação e implantação de um modelo de machine learning usando o Azure Machine Learning.

🎯 ## Objetivo
O objetivo é utilizar um modelo de regressão para prever o preço de carros usados com base em suas características, como ano, marca, modelo e quilometragem, e implantá-lo como um serviço web acessível via API REST.

1.  **Preparação do Ambiente:** O primeiro passo foi criar uma conta no **portal.azure.com** e acessar o Azure Machine Learning através do link **https://ml.azure.com/**;
    > Foi criado um Workspace no Azure Machine Learning, que serve como um container central para todos os recursos do projeto, incluindo conjuntos de dados, recursos de computação, modelos e pontos de extremidade.
2.  **Treinamento do Modelo:** Utilizei o recurso de AutoML (Automated Machine Learning) do Azure para criar um ML automatizado. Enviei um conjunto de dados de carros usados no formato CSV e configurei o AutoML para encontrar o melhor modelo de regressão entre o RandomForest e o LightGBM para prever a coluna "preço" (selling_price) do arquivo;
3.  **Implantação do Modelo:** Após a conclusão do trabalho do AutoML, o melhor modelo foi selecionado (VotingEnsemble) com base na Normalized Root Mean Squared Error, que indicou o menor erro de previsão;
   > No menu lateral, acessei o modelo gerado e o acionei com a implementação de um ponto de extremidade em tempo real (real-time endpoint), gerando uma API REST para consumo.
4.  **Consumo do Modelo:** As informações de consumo do modelo (URL e estrutura da requisição) estão detalhadas abaixo.

## Como Usar o Ponto de Extremidade

Para fazer uma previsão, é necessário enviar uma requisição `POST` para a URL abaixo, contendo a chave de API secreta no cabeçalho e os dados do carro no corpo da requisição.

* **URL do Endpoint:** `https://precos-carros-endpoint.eastus2.inference.ml.azure.com/score`
* **Chave de API:** A chave de API é um segredo e deve ser obtida no portal do Azure. Ela não é compartilhada neste repositório por motivos de segurança.

O formato dos dados a serem enviados está no arquivo `exemplo_requisicao.json`.
