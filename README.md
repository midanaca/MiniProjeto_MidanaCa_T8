# Mini Projeto – Análise e Tratamento de Dados de Varejo

**Autor:** Midana Cá  
**Turma:** T8  
**Data:** 26/10/2026  
**Linguagem:** Python  
**Ambiente de desenvolvimento:** Google Colab  
**Biblioteca principal:** Pandas

---

## 1. Sobre o projeto

Este projeto tem como objetivo realizar a leitura, o diagnóstico, a limpeza, a organização e a análise exploratória de uma base de dados de varejo, utilizando a linguagem Python e a biblioteca Pandas.

O trabalho foi desenvolvido em cinco Sprints, contemplando desde a importação dos dados até a geração de indicadores e a exportação da base tratada.

A proposta é desenvolver conhecimentos práticos sobre manipulação de dados, identificação de inconsistências, aplicação de funções, filtros, agrupamentos e interpretação de resultados.

## 2. Origem dos dados

A base de dados utilizada neste projeto foi obtida na plataforma Kaggle, em 25 de outubro de 2026.

**Fonte:** Base Varejo – Kaggle.

Link: https://www.kaggle.com/datasets/namespaiva/base-varejo

**Arquivo utilizado:** `base_varejo.csv`

## 3. Tecnologias e ferramentas utilizadas

As principais ferramentas e bibliotecas utilizadas foram:

| Tecnologia | Finalidade |
|---|---|
| Python | Linguagem de programação utilizada no projeto. |
| Google Colab | Ambiente de desenvolvimento e execução dos códigos. |
| Pandas | Leitura, manipulação, limpeza e análise dos dados. |
| CSV | Formato de armazenamento e exportação dos dados. |
| GitHub | Compartilhamento e versionamento do projeto. |

## 4. Estrutura e descrição da base de dados

Inicialmente, a base apresentou 830.000 registros e 14 colunas. Após a identificação e exclusão de quatro colunas completamente vazias, permaneceram 830.000 registros e 10 colunas.

As variáveis foram traduzidas para facilitar a compreensão e a interpretação das informações.

| Variável | Descrição |
|---|---|
| `Data` | Data da compra. |
| `Compra_id` | Identificador da compra. |
| `Cliente_id` | Identificador do cliente. |
| `Genero_cliente` | Gênero do cliente. |
| `Estado_civil_cliente` | Código do estado civil do cliente. |
| `Filho_cliente` | Número de filhos do cliente. |
| `Segmento_cliente` | Segmento do cliente. |
| `Produto_id` | Identificador do produto. |
| `Categoria_produto` | Categoria do produto. |
| `Nome_produto` | Nome do produto. |

**Observação:** os códigos numéricos da variável `Estado_civil_cliente` não foram traduzidos, pois a documentação da base não apresenta o significado de cada código.

## 5. Etapas de desenvolvimento

O projeto foi organizado em cinco Sprints.

### Sprint 1 – Leitura e diagnóstico

Nesta etapa, foram realizadas as seguintes atividades:

- Importação da base de dados utilizando Pandas.
- Identificação da quantidade de linhas e colunas.
- Verificação da estrutura inicial do arquivo.
- Correção da leitura do CSV utilizando o separador `;`.
- Tradução dos nomes das colunas para facilitar a interpretação.
- Identificação das colunas completamente vazias.
- Verificação dos tipos de dados e da quantidade de valores preenchidos.

### Sprint 2 – Qualidade, limpeza e padronização

Nesta etapa, foram investigadas as principais características relacionadas à qualidade dos dados:

- Identificação de valores ausentes utilizando `isna()`.
- Verificação de linhas integralmente duplicadas.
- Identificação de textos preenchidos apenas com espaços vazios.
- Investigação de possíveis diferenças de escrita.
- Análise da distribuição das categorias, segmentos, gêneros e nomes dos produtos.
- Exclusão das quatro colunas completamente vazias.

**Decisão sobre as linhas repetidas:** foram identificadas 96.553 repetições completas além da primeira ocorrência. Entretanto, optou-se por mantê-las, pois não existe um identificador único de item ou uma coluna de quantidade que permita confirmar se representam erros de duplicação ou unidades adicionais de produtos adquiridos.

Também foram mantidos os registros identificados como `#N/D`, pois a ausência de identificação da categoria ou do nome do produto não justifica a exclusão automática das respectivas compras.

### Sprint 3 – Criação de funções

Foi desenvolvida uma função denominada `resumo_numerico()`, destinada a calcular estatísticas descritivas de variáveis numéricas.

A função retorna:

- Quantidade de valores válidos;
- Média;
- Valor mínimo;
- Valor máximo.

A função foi aplicada à variável `Filho_cliente`, permitindo identificar características relacionadas ao número de filhos dos clientes.

### Sprint 4 – Análise exploratória dos dados

Nesta etapa, foram realizados filtros e agrupamentos para extrair informações relevantes da base.

As principais análises foram:

**1. Filtro de clientes com quatro filhos**

Identificação dos registros em que a variável `Filho_cliente` apresenta o valor igual a 4.

**2. Cálculo percentual**

Cálculo da participação dos registros de clientes com quatro filhos em relação ao total de valores válidos da variável.

**3. Agrupamento por categoria de produtos**

Contagem dos registros por categoria, permitindo identificar aquelas com maior frequência.

**4. Agrupamento por gênero**

Análise da quantidade de registros, dos valores válidos e da soma do número de filhos conhecidos para cada gênero.

### Sprint 5 – Exportação e conclusões

Na última etapa, foi realizada a exportação da base tratada para um novo arquivo CSV.

**Arquivo gerado:** `varejo_limpo.csv`

A exportação foi realizada utilizando o método `to_csv()`, com o parâmetro `index=False`, evitando a criação de uma coluna adicional com o índice do DataFrame.

Posteriormente, o arquivo exportado foi novamente importado para verificar suas dimensões e os nomes das colunas.

## 6. Principais resultados encontrados

A análise exploratória apresentou os seguintes resultados:

| Indicador | Resultado |
|---|---:|
| Registros originais | 830.000 |
| Colunas originais | 14 |
| Colunas após limpeza | 10 |
| Pedidos distintos | 18.471 |
| Clientes distintos | 1.000 |
| Produtos distintos por código | 229 |
| Nomes distintos de produtos | 118 |
| Repetições completas além da primeira ocorrência | 96.553 |
| Registros com quatro filhos | 80.379 |
| Média de filhos por registro | 1,15 |
| Categoria com maior frequência | ALIMENTOS |
| Registros da categoria ALIMENTOS | 434.767 |

### 6.1. Distribuição por categoria

A categoria ALIMENTOS apresentou a maior frequência, com 434.767 registros, seguida por HIGIENE, com 155.574, e LIMPEZA, com 145.754.

### 6.2. Perfil por gênero

A base apresentou a seguinte distribuição:

| Gênero | Registros | Soma do número de filhos |
|---|---:|---:|
| Feminino | 432.576 | 471.793 |
| Masculino | 397.424 | 479.835 |

A soma apresentada corresponde à variável `Filho_cliente`, e não ao valor monetário das compras.

### 6.3. Registros de clientes com quatro filhos

Foram identificados 80.379 registros em que o número de filhos do cliente é igual a quatro, correspondendo a aproximadamente 9,68% dos registros válidos dessa variável.

## 7. Limitações identificadas

Durante o desenvolvimento do projeto, foram identificadas algumas limitações:

- Ausência de informações sobre preços e valores monetários dos produtos.
- Ausência de uma coluna específica para quantidade de unidades compradas.
- Existência de 3.650 registros com identificação `#N/D` na categoria e no nome do produto.
- Ausência de documentação sobre os códigos da variável `Estado_civil_cliente`.
- Impossibilidade de confirmar se as linhas integralmente repetidas representam erros ou compras legítimas de unidades adicionais.

Essas limitações restringem algumas interpretações, especialmente aquelas relacionadas ao faturamento, à rentabilidade e ao comportamento financeiro dos clientes.

## 8. Recomendações

Recomenda-se que futuras versões da base incorporem informações sobre o preço unitário, a quantidade adquirida, os descontos e os custos dos produtos.

Essas informações permitiriam ampliar a análise para indicadores como:

- Faturamento total;
- Ticket médio;
- Receita por categoria;
- Receita por gênero;
- Receita por segmento de cliente;
- Margem de lucro;
- Rentabilidade dos produtos.

Também seria importante disponibilizar um identificador único para cada item de compra, permitindo distinguir duplicações indevidas de compras legítimas de produtos iguais.



