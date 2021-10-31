Site: https://alanhelfer.github.io/pandas/
Estilo: https://docs.pipz.com/central-de-ajuda/learning-center/guia-basico-de-markdown#open

### CARREGAR UM ARQUIVO .XLSX OU .CSV E OBTER INFORMAÇÕES GERAIS

| Expressão | Ação | 
| --- | --- |
| var_df = pd.read_csv(‘arquivo.csv’) | Carregar arquivo .csv |
| var_df = pd.read_excel(‘arquivo.xlsx’) | Carregar arquivo .xlsx |
| var_df.head() | Mostrar n linhas do arquivo (padrão n = 5) |
| var_df.tail() | Mostrar n últimas linhas do arquivo (padrão n = 5) |
| var_df.shape | Quantidade de linhas e colunas (tupla) |
| var_df.info() | Informações gerais como quantidade de dados não-nulos, tipos dos dados e memória ocupada |

Observação:
* read_csv: parâmetro index_col=0 exclui a coluna criada para index dos elementos.

### Extração de dados estatísticos das colunas com valores numéricos:

| Expressão | Ação | 
| --- | --- |
|var_df.describe() | Média, desvio padrão, mínimo, máximo e percentis por coluna numérica em Data Frame | 
|var_df.isna().sum() | Quantidade de elementos nulos (missing) por coluna |
|var_df.isna().mean() | Média de elementos nulos (missing) por coluna | 
|var_df[‘nome_col’].value_counts() | Quantidade de vezes que cada dado aparece na coluna |

### Acessar elementos específicos:
| Expressão | Ação | 
| --- | --- |
|var_df.describe() | Média, desvio padrão, mínimo, máximo e percentis por coluna numérica em Data Frame | 
|var_df.isna().sum() | Quantidade de elementos nulos (missing) por coluna |
|var_df.isna().mean() | Média de elementos nulos (missing) por coluna | 
|var_df[‘nome_col’].value_counts() | Quantidade de vezes que cada dado aparece na coluna |


|var_df[linha_n:linha_p] | Elementos das linhas linha_n até a linha_p - 1 no formato Data Frame |
|var_df[‘key’] | Elementos da coluna key no formato Series |
|var_df[[‘key’]] | Elementos no formato Data Frame |
|var_df[[‘key_1’, ‘key_2’]] |Elementos das colunas key_1 e key_2 no formato Data Frame |

Observação:

* É possível usar estrutura condicional em determinada coluna: 

var_df[var_df[‘Salario’] == var_df[‘Salario’].max()]

### Acessar elementos específicos pelo index (índice numérico) com iloc[]:

| Expressão | Ação |
| --- | --- | 
|var_df.iloc[linha_n] | Elementos da linha n em formato Series do Pandas |
|var_df.iloc[[linha_n]] | Elementos da linha n em formato Data Frame |
|var_df.iloc[linha_n, coluna_p] | Elemento da linha n e coluna p |
|var_df.iloc[lin_in:lin_fim, col_in:col_fim] | Forma completa da funcionalidade iloc[]. O retorno tem o formato Data Frame. Espaço vazio até inicio ou fim. |

### Acessar elementos específicos pelo label do index (da linha) com loc[]:

| Expressão | Ação | 
| --- | --- |
|var_df.loc[‘label_linha_n’] | Elementos da linha label_linha_n em formato Serie do Pandas. Pode ser passado valor numérico. |
|var_df.loc[[‘label_linha_n’]] | Formato Data Frame em vez de Series |
|var_df.loc[label_1:label_n, ‘key’] | Elementos da coluna key das linhas de label_1 a label_n no formato Series |
|var_df.loc[label_1:label_n, [‘key_1’]] |Formato Data Frame em vez de  Series |
|var_df.loc[label_1:label_n, [‘key_1’, ‘key_2’, ‘key_n’]] | Elementos das colunas key_1, key_2 e key_n das linhas de label_1 a label_n no formato Data Frame |

Observação: 
* É possível usar estrutura condicional em determinada coluna: 

var_df.loc[var_df[‘Nome’] == ‘Alan’]


### Alteração/exclusão de valores/informações no Data Frame

| Expressão | Ação |
| --- | --- |
|var_df.rename(coluns={‘nome_1_ant’:’nome_1_novo’, ‘nome_2_ant’: …}) | Renomeia a coluna especificada para o termo depois dois dois pontos ( : ) |
|var_df.drop(‘nome’, axis = 0_ou_1) | Remover a coluna especificada, se axis = 1, ou a linha, se axis = 0 | 
|var_df.dropna() | Excluir linha que contenha qualquer valor nulo | 
|var_df.fillna(‘termo_incluso’) | Substituir dados faltantes por termo_incluso |

Observações:

* É possível especificar as colunas para análise utilizando var_df.[‘nome_coluna’]. Por exemplo: 

var_df[‘nome_col’].fillna(‘novo_dado’) 

dados[‘Age’].fillna(dados[‘Age’].mean())

### Sobrescrita de valores/informações no Data Frame ocorre com o parâmetro inplace = True. Se nesta condição, nada é retornado e os dados são modificados. Caso seja falso, é retornada uma cópia do objeto.

var_df.X(…, inplace = True) 

Substituir dados faltantes da coluna por novo_dado

Alguns dos métodos em que o parâmetro é aplicado: drop() dropna() fillna() query() rename() reset_index() sort_index() sort_values()
