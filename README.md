# Predição de Métricas de Rede

Este projeto implementa uma solução preditiva para métricas de qualidade de rede, utilizando dados fornecidos no contexto de um desafio de monitoramento de redes. O objetivo principal é prever métricas como *bitrate* e latência com base em medições históricas, empregando técnicas de mineração de dados e aprendizado de máquina.

## Estrutura do Código

### 1. **Carregamento e Pré-processamento de Dados**
- O código carrega arquivos JSON contendo informações de medições DASH, RTT e Traceroute para pares cliente-servidor.
- Realiza o tratamento de valores faltantes e normalização.
- Extrai *features* relevantes, como médias e desvios padrões de taxas (*bitrate*), RTT e métricas de Traceroute.

### 2. **Engenharia de Features**
- As *features* são construídas a partir das medições históricas, agregando dados temporais e estatísticos.
- Métricas adicionais, como cliente e servidor codificados, são incluídas para capturar relações contextuais.

### 3. **Treinamento e Validação**
- O modelo principal utilizado é o **Random Forest Regression**, complementado por **Linear Regression** e **Voting Regressor**.
- Utiliza-se validação cruzada (*K-Fold Cross Validation*) para garantir a robustez e generalização dos modelos.
- Hiperparâmetros são otimizados via *Grid Search*.

### 4. **Predição e Avaliação**
- As métricas de desempenho são avaliadas com o **Mean Absolute Percentage Error (MAPE)** e o *Score Kaggle*.
- As previsões incluem as métricas médias e desvios padrões de taxas para intervalos de 5 e 10 minutos futuros.

## Resultados
- O **Linear Regression** alcançou o menor *Score Kaggle* (0.0818), evidenciando sua capacidade de capturar padrões simples nos dados.
- O **Random Forest Regression** demonstrou desempenho ligeiramente inferior, sendo mais sensível à quantidade limitada e à variabilidade dos dados.
- A complexidade adicional dos modelos avançados não resultou em melhorias significativas devido ao alto nível de ruído e à pequena quantidade de dados disponíveis.

## Requisitos
- **Python 3.8+**
- Bibliotecas:
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `matplotlib`
  - `json`
