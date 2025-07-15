# Classificação Fuzzy de Gêneros Musicais: Um Estudo Comparativo

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![Libraries](https://img.shields.io/badge/Bibliotecas-simpful,_librosa,_sklearn-orange.svg)
![License](https://img.shields.io/badge/Licença-MIT-green.svg)

Este repositório contém o código e os artefatos do projeto de classificação de gêneros musicais, que foca na aplicação e análise de um Sistema de Inferência Fuzzy (FIS) para distinguir gêneros musicais com diferentes níveis de similaridade acústica.

## 1. Visão Geral do Projeto

O projeto realiza um estudo comparativo para avaliar a eficácia de um classificador fuzzy em duas tarefas distintas:

1.  **Classificação de Grão Grosso (Problema de Controle):** Distinguir os gêneros **Rock** e **Clássica**, que são acusticamente muito diferentes.
2.  **Classificação de Grão Fino (Problema de Desafio):** Distinguir os gêneros **Rock** e **Metal**, que compartilham muitas características sonoras, tornando a classificação mais ambígua e desafiadora.

O objetivo principal não é apenas medir a acurácia, mas principalmente explorar a **interpretabilidade** do modelo fuzzy, utilizando suas regras linguísticas para compreender as características que definem as fronteiras entre os gêneros.

## 2. Metodologia

O pipeline do projeto foi estruturado da seguinte forma:

#### a. Extração de Características
Utilizando a biblioteca `librosa` em Python, um conjunto de 30 características de áudio (incluindo MFCCs, centroide espectral, rolloff espectral, etc.) foi extraído de cada faixa de 30 segundos do dataset GTZAN. As estatísticas de média e desvio padrão foram calculadas para gerar um único vetor de características por música.

#### b. Seleção de Características
Devido à "maldição da dimensionalidade" em sistemas fuzzy manuais, um modelo **Random Forest** foi treinado para cada uma das duas tarefas, a fim de ranquear a importância das 30 características. As **duas características mais relevantes** de cada tarefa foram selecionadas como entradas para o respectivo sistema fuzzy.

#### c. Classificador Fuzzy
Para cada experimento, um Sistema de Inferência Fuzzy (FIS) foi projetado utilizando a biblioteca `simpful`. O design incluiu:
- **Funções de Pertinência Gaussianas:** Escolhidas por sua capacidade de modelar suavemente a sobreposição e a incerteza nos dados.
- **Base de Regras com Graus de Certeza:** Um conjunto de regras `SE-ENTÃO` foi elaborado com base na análise visual da distribuição dos dados. A cada regra foi atribuído um peso (grau de certeza) para refletir a confiança em sua validade, tornando o sistema mais robusto.
## 3. Como Executar o Projeto

#### a. Pré-requisitos
-   Python 3.9 ou superior.
-   Acesso ao dataset GTZAN. Você pode baixá-lo [aqui](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification).

#### b. Instalação
Clone este repositório e instale as dependências necessárias:
```bash
git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
cd seu-repositorio
pip install pandas numpy scikit-learn librosa simpful matplotlib seaborn
```


