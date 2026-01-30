# Previsão de Abertura de OS (Ordem de Serviço) em Redes de Telecomunicações

Este repositório contém  modelos de aprendizado de máquina desenvolvidos para prever a necessidade de abertura de uma OS (Ordem de Serviço) com base em diversas métricas de qualidade de serviço em redes de telecomunicações. 

As mértricas utilizadas são:
- Latência
- Jitter
- Perda de Pacote
- Reboots
- Qualidade de Canal 2GHz
- Qualidade de Canal 5GHz
- Número de Dispositivos Distantes

## 1. `Arvore.py`

Este script implementa um modelo de Árvore de Decisão para previsão binária com base em um conjunto de dados de entrada. A árvore de decisão divide os dados em nós que representam decisões baseadas em valores de atributos específicos, com o objetivo de prever se uma determinada ação (neste caso, "Abrir OS") deve ser tomada ou não.

**Tecnologias utilizadas:**
- `pandas`: Para manipulação e análise de dados.
- `numpy`: Para cálculos numéricos.
- `sklearn.tree.DecisionTreeClassifier`: Para implementar a Árvore de Decisão.
- `sklearn.model_selection.train_test_split`: Para dividir o conjunto de dados em treinamento e teste.

**Processo:**
1. Os dados são carregados de um arquivo Excel.
2. Colunas específicas são selecionadas como variáveis de entrada (`X`) e saída (`y`).
3. Os dados são preenchidos com valores padrão em caso de valores nulos.
4. A árvore de decisão é treinada com 70% dos dados, e a precisão é avaliada nos 30% restantes.
5. O resultado final é salvo em um arquivo Excel.

## 2. `Arvore+Sequencial.py`

Este script combina uma Árvore de Decisão com um modelo de Rede Neural Sequencial para previsão binária. A rede neural é composta por várias camadas densas, proporcionando uma abordagem mais robusta ao aprendizado de padrões complexos nos dados.

**Tecnologias utilizadas:**
- `pandas`: Para manipulação e análise de dados.
- `numpy`: Para cálculos numéricos.
- `sklearn.tree.DecisionTreeClassifier`: Para a parte de Árvore de Decisão.
- `sklearn.model_selection.train_test_split`: Para dividir o conjunto de dados em treinamento e teste.
- `sklearn.preprocessing.StandardScaler`: Para padronização dos dados.
- `keras.models.Sequential` e `keras.layers.Dense`: Para construção e treinamento do modelo de rede neural.

**Processo:**
1. Os dados são carregados de um arquivo Excel.
2. As variáveis de entrada e saída são selecionadas e preparadas.
3. Os dados são padronizados usando `StandardScaler`.
4. A rede neural é definida com camadas densas e função de ativação `relu` para as camadas intermediárias, e `sigmoid` para a camada de saída.
5. O modelo é treinado por 1000 épocas com um tamanho de lote de 32.
6. A precisão é avaliada e os resultados são salvos em um arquivo Excel.

## 3. Gradient Boosting

**Descrição:**
Gradient Boosting é uma técnica de aprendizado de máquina que combina várias árvores de decisão fracas para formar um modelo preditivo mais robusto. O modelo ajusta gradativamente as previsões, reduzindo os erros dos modelos anteriores.

**Dependências:**
- `pandas`
- `numpy`
- `scikit-learn`

  ## 4. Long Short-Term Memory (LSTM)

**Descrição:**
LSTM é um tipo de rede neural recorrente (RNN) que pode aprender dependências de longo prazo em dados sequenciais. As células de memória em LSTM ajudam a capturar padrões ao longo de longos períodos de tempo.

**Dependências:**
- `pandas`
- `numpy`
- `scikit-learn`
- `keras`

## 5. MLP (Multilayer Perceptron)

### Descrição
Este modelo utiliza o `MLPClassifier` da biblioteca `sklearn` para criar uma rede neural com duas camadas ocultas de 100 neurônios cada. O modelo prevê a necessidade de abrir uma OS com base em sete diferentes métricas.

### Processamento
- Substituição de valores nulos por 0.
- Ajuste do número de linhas para que todos os conjuntos de dados tenham o mesmo tamanho, preenchendo com zeros se necessário.
- Concatenar os conjuntos de dados para criar a matriz final de entradas (`X`).
- Dividir os dados em 70% para treinamento e 30% para teste.

### Resultados
O classificador é treinado e testado, e a precisão do modelo é calculada e exibida ao final da execução. O modelo também gera um arquivo Excel (`resultadoMLP.xlsx`) contendo as predições feitas no conjunto de teste.

## 6. Perceptron

### Descrição
Este modelo utiliza o `Perceptron`, uma versão mais simples de rede neural, para realizar a previsão de abertura de OS.

### Processamento
- Substituição de valores nulos por 0.
- Binarização dos valores das métricas com base em limiares definidos (por exemplo, latência < 17 é convertida para 0, caso contrário, para 1).
- Ajuste do número de linhas para que todos os conjuntos de dados tenham o mesmo tamanho.
- Criação da matriz final de entradas (`X`) e divisão dos dados em 70% para treinamento e 30% para teste.

### Resultados
O classificador é treinado e testado, com a precisão do modelo sendo exibida ao final da execução.

## Comparação e Considerações

- **MLP (Multilayer Perceptron)**:
  - Utiliza mais métricas e uma arquitetura de rede neural mais complexa.
  - Pode capturar padrões mais complexos nos dados, resultando potencialmente em uma melhor precisão.

- **Perceptron**:
  - Modelo mais simples e rápido de treinar.
  - Binariza as métricas, o que pode simplificar o modelo, mas também levar à perda de informações detalhadas.

Ambos os modelos são úteis para diferentes casos de uso, e a escolha entre eles pode depender dos recursos computacionais disponíveis e da complexidade dos dados.

## Requisitos

- Python 3.x
- Pandas
- NumPy
- scikit-learn

## Como Executar

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu_usuario/nome_repositorio.git

2. Navegue até o diretório do projeto:
   ```bash
    cd nome_repositorio
   
3. Instale as dependências:
   ```bash
    pip install -r requirements.txt


### Contribuições
- Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests para melhorias ou correções.

### Instruções Adicionais:
- Substitua `"seu_usuario"` e `"nome_repositorio"` pelo nome do seu usuário e repositório no GitHub.
- Adapte as seções conforme necessário para refletir o conteúdo específico do seu projeto.

Esse `README.md` fornece uma visão geral clara do que o projeto faz, como ele funciona e como outras pessoas podem contribuir e usá-lo.

