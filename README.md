# 🕵️‍♀️ Detector de Fake News - NLP

Bem-vindo ao repositório do projeto **Detector de Fake News** focado em Processamento de Linguagem Natural (NLP). Este projeto tem como objetivo principal treinar, avaliar e interpretar modelos avançados de NLP (como DistilBERT e DistilRoBERTa) para a classificação de notícias, identificando se são verdadeiras ou falsas (Fake News).

## 📌 Resumo e Principais Funcionalidades

Este projeto cobre um ciclo completo (pipeline) de Ciência de Dados e Machine Learning para NLP:

1. **Análise Exploratória de Dados (EDA)**: Limpeza, processamento e visualização das distribuições de texto no conjunto de dados.
2. **Treinamento de Modelos**: Fine-tuning dos modelos pré-treinados [DistilBERT](https://huggingface.co/distilbert-base-uncased) e [DistilRoBERTa](https://huggingface.co/distilroberta-base) usando `PyTorch` e a biblioteca `transformers` da Hugging Face.
3. **Inferência**: Geração de previsões usando os modelos treinados para criar o arquivo de submissão (e testar em novos dados).
4. **Interpretabilidade**: Análise de como o modelo toma suas decisões (importância de tokens/palavras) para garantir a transparência do modelo de Fake News.

## 📂 Estrutura do Repositório

```text
📦 fakenews_detector_nlp
 ┣ 📂 datasets/              # Conjunto de dados (treino, teste e dados processados)
 ┃ ┣ 📜 ligia_dataset_processado.csv
 ┃ ┣ 📜 test.csv
 ┃ ┗ 📜 train.csv
 ┣ 📂 notebooks_colab/       # Notebooks principais focados no Google Colab
 ┃ ┣ 📓 EDA_Ligia_NLP.ipynb                     # Análise exploratória e limpeza
 ┃ ┣ 📓 Treinamento_DistilBERT_Ligia_NLP.ipynb  # Treinamento usando DistilBERT
 ┃ ┣ 📓 Treinamento_DistilRoBERTa_Ligia_NLP.ipynb # Treinamento usando DistilRoBERTa
 ┃ ┣ 📓 Inferencia_Ligia_NLP.ipynb              # Realiza as predições e cria a submissão
 ┃ ┗ 📓 Interpretabilidade_Ligia_NLP.ipynb      # Interpretação dos resultados (SHAP)
 ┣ 📂 results/               # Modelos salvos pós-treinamento
 ┃ ┣ 📦 best_distilbert_model.zip
 ┃ ┗ 📦 best_distilroberta_model.zip
 ┣ 📜 submission.csv         # Resultado final de predições
 ┗ 📜 README.md              # Documentação do projeto
```

## 📦 Dependências Principais

Os notebooks foram estruturados para rodar **exclusivamente no Google Colab** (Recomendado pois é necessário GPU para rodar os modelos), mas caso deseje rodar localmente, o projeto depende das seguintes bibliotecas em Python:

- `pandas` e `numpy`: Manipulação de dados.
- `matplotlib` e `seaborn`: Visualização de dados.
- `torch` (PyTorch): Framework principal de Deep Learning.
- `transformers` (Hugging Face): Modelos de linguagem, Tokenizers e classes para fine-tuning.
- `scikit-learn`: Métricas e divisões de treino/teste.
- `gdown`: Download automatizado de arquivos via links do Google Drive.

## 🚀 Como Usar (Instruções de Uso)

Você pode executar este projeto diretamente usando o **Google Colab** de maneira independente, devido às melhorias implementadas na forma de ingestão de dados. Siga os passos na ordem adequada do pipeline:

1. **Análise dos Dados**: Abra o notebook `EDA_Ligia_NLP.ipynb` para visualizar e entender o processamento de texto.
2. **Treinamento**: Escolha um dos notebooks de treinamento (`Treinamento_DistilBERT_Ligia_NLP.ipynb` ou `Treinamento_DistilRoBERTa_Ligia_NLP.ipynb`). O treinamento deve preferencialmente ser executado em ambiente com **GPU** ativada (no Colab: `Ambiente de execução -> Alterar o tipo de ambiente de execução -> GPU`).
3. **Inferência**: Após ter os modelos gerados/baixados, utilize o `Inferencia_Ligia_NLP.ipynb` para prever no conjunto `test.csv` e gerar seu arquivo `submission.csv`.
4. **Compreendendo o Modelo**: Para maior transparência, utilize o `Interpretabilidade_Ligia_NLP.ipynb` para ler as atribuições e pesos que a IA deu a determinadas partes da notícia.

---

## ✨ Feature de Destaque: Carregamento Online Direto (Sem Google Drive local)

Uma das maiores facilidades incluídas nesta versão do projeto é a **Feature de carregamento online**.

- **Como funciona antes:** Os notebooks foram estruturados de forma que exigem que o utilizador monte seu disco (Google Drive Pessoal, `drive.mount('/content/drive')`), para fazer o salvamento e uploud dos arquivos de CSV e Modelos.


- **O que foi adicionado:** A dependência de montagem de drive pessoal foi substituída pelo uso da biblioteca `gdown`, dando a opção de baixar os arquivos automaticamente através de links públicos integrados diretamente ao código. (do próprio autor do projeto)


**Benefícios:**

- **Zero Configuração:** Reduz muito o trabalho manual. Basta apertar _"Run All"_ no Colab e o notebook puxará o Dataset inteiro da nuvem diretamente para a instância temporária do Google Colab.
- **Não gasta armazenamento pessoal:** O dataset não precisa ocupar espaço no seu Google Drive.
- **Portabilidade perfeita:** Outros cientistas de dados e avaliadores podem reproduzir seus testes e resultados com 1 clique.


> **Nota:** Nos notebooks de **EDA** e **Treinamento**, a montagem do Google Drive permanece obrigatória para o salvamento dos modelos e dataset processado.

