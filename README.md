# Análise de Estilos de Pilotagem na Fórmula 1 - Temporada 2024

Este repositório contém o código-fonte e os dados utilizados no Trabalho de Conclusão de Curso (TCC) para o curso de Ciência da Computação na Universidade Federal de Alagoas (UFAL).

O projeto aplica técnicas de clusterização (Aprendizado de Máquina Não Supervisionado) para identificar e caracterizar padrões de pilotagem entre os 20 pilotos da temporada de 2024 da Fórmula 1.

## 🎯 Objetivo Principal

O estudo buscou responder à seguinte pergunta de pesquisa: *como a aplicação de técnicas de clusterização sobre métricas de desempenho e estratégicas pode revelar padrões distintos de pilotagem entre os pilotos da Fórmula 1?*

A análise utilizou dados de 21 corridas em pista seca, coletados via API FastF1, e focou em métricas de engenharia de atributos, como consistência de ritmo, gerenciamento de pneus, número de paradas e duração dos stints.

## 📊 Resultados e Perfis Identificados

A análise com os algoritmos K-Means e Agrupamento Hierárquico demonstrou de forma robusta a existência de **quatro perfis principais** de pilotagem na temporada de 2024:

1.  **Elite - Foco em Pneus Médios:** Pilotos rápidos e consistentes, com estratégia predominante no uso de pneus médios.
2.  **Elite - Foco em Pneus Duros:** Grupo de alta performance, com consistência elevada e estratégia focada em stints longos com pneus duros.
3.  **Perfil Agressivo:** Pilotos com desempenho intermediário que adotam estratégias agressivas, com uso predominante de pneus macios.
4.  **Performance Inferior:** Grupo caracterizado pela alta inconsistência de ritmo, maior variabilidade nos tempos de volta e desempenho geral inferior.

## 📁 Estrutura do Repositório

O projeto segue um pipeline claro de Descoberta de Conhecimento em Bases de Dados (KDD), organizado em três diretórios principais:

1.  **`/Obtendo Dados`**:
    * `ObtendoOsDados.ipynb`: Notebook Jupyter responsável por se conectar à API FastF1, coletar os dados de todas as corridas da temporada 2024 e salvá-los como arquivos `.csv`.
    * `/Todas as pistas em csv`: Contém os dados brutos de cada corrida, separados por arquivo.

2.  **`/Obtendo Features`**:
    * Este diretório contém subpastas para cada uma das 21 corridas analisadas.
    * Em cada subpasta, um notebook (ex: `01Bahrein-Features.ipynb`) realiza o pré-processamento, limpeza e engenharia de atributos (cálculo de consistência, proporção de pneus, etc.) para aquela corrida específica.
    * O resultado de cada notebook é salvo em um arquivo `.csv` (ex: `df_completoBahrein.csv`).

3.  **`/Clusterizando`**:
    * `grupos.ipynb`: O notebook principal do projeto. Ele consolida os dados de todas as corridas, aplica os algoritmos de clusterização (K-Means, Hierárquico), realiza a redução de dimensionalidade para visualização (PCA e t-SNE) e gera todos os gráficos e análises presentes no TCC.
    * `df_all_corridas_2024.csv`: O dataset final e consolidado, contendo a média das features de cada piloto ao longo da temporada. Este é o arquivo usado como entrada para o notebook `grupos.ipynb`.

## 🛠️ Ferramentas e Bibliotecas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * `fastf1`: Para coleta de dados da Fórmula 1.
    * `pandas`: Para manipulação e análise dos dados.
    * `scikit-learn`: Para aplicação dos algoritmos de K-Means, PCA e padronização dos dados.
    * `matplotlib` e `seaborn`: Para a visualização dos dados e clusters.
    * `scipy`: Para a execução do Agrupamento Hierárquico.
* **Ambiente:** Jupyter Notebook

## 🚀 Como Replicar a Análise

Para executar o projeto e replicar os resultados, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/PedroMesquitaIsidoro/Perfis-de-pilotos---F1-2024.git
    ```

2.  **Instale as dependências:**
    Recomenda-se criar um ambiente virtual. As bibliotecas necessárias estão listadas acima.

3.  **Execute os notebooks:**
    * Para ver a análise final, você pode ir diretamente para a pasta `/Clusterizando` e executar o notebook `grupos.ipynb`. Ele já utiliza o arquivo `df_all_corridas_2024.csv` que está pronto.
    * Se desejar refazer todo o processo desde o início, execute os notebooks na seguinte ordem:
        1.  `/Obtendo Dados/ObtendoOsDados.ipynb` para baixar os dados brutos.
        2.  Os notebooks na pasta `/Obtendo Features` para gerar as métricas de cada corrida.
        3.  Finalmente, o notebook `/Clusterizando/grupos.ipynb` para realizar a clusterização.

## 📄 Autor

* **Pedro Henrique Mesquita Isidoro** 
