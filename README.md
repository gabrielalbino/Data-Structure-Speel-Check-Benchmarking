# Spell Check benchmarking using differente data structures
Corretores Otográficos que utilizam estruturas de dados diferentes para carregar o dicionário para a memória
## Descrição geral
### Descrição do problema:
> Verificadores ortográficos são ferramentas que analisam um texto em linguagem natural e destacam
erros de ortografias. De forma simplista, um verificador ortográfico pode ser visto como uma
ferramenta que contém um dicionário contendo todas as palavras de um certo idioma. Para
encontrar se uma palavra está errada ou não, bastaria verificar se a palavra existe ou não no
dicionário. Computacionalmente, o problema de verificar ortografia pode ser custoso, uma vez que
existem milhares de palavras em um idioma e, para um texto com 100 palavras, são necessárias até
100 consultas no dicionário.

### Objetivo
> Utilização de diferentes estruturas de dados para construção de corretores ortográficos com o objetivo de entender como elas influenciam na
eficiência/desempenho do programa.
### Implementação
> 3 estruturas de dados diferentes foram utilizadas para a implentação da solução. Cada uma encontra-se na pasta de arquivos fontes identificadas como "corretorOrtograficoXXX.c", onde XXX  o tipo de estrutura de dados utilizado para a implementação.
Cada uma das implementações tem vantagens e desvantagens.
## Testes
> Os testes foram feitos utilizando um dicionário de lingua inglêsa composto de 143091 palavras utilizado para corrigir um texto de 29758 palavras.
> > Hash:

> > ![Resultados Hash](https://i.imgur.com/qHlFUVJ.png)

>> Tries:

> > ![Resultados Tries](https://i.imgur.com/ABAFzji.png)

>> AVL:

> >  Não foi possvel testar: Tempo de execução muito lento na leitura do dicionário (certa de 1 palavra a cada 5 segundos a partir de 10000 palavras. Deve-se achar uma alternativa para a leitura dos dados.

### Conclusão:
>Foram constatados alguns problemas em cada uma das implementações. no Hash o tempo de execução é o mais rápido porém a presição da comparação é afetada por dois motivos: o primeiro é que a função de hash implementada não possui tratamento de conflitos, isto é, duas palavras podem ter o mesmo hash. A segunda é que devido às limitações de memória RAM do computador, não seria possível criar um vetor grande o suficiente para armazenar o valor total do hash, sendo necessário normaliza-lo para um valor entre 0 e 300 mil, aumentando as chances de conflito.
A segunda implementação é dada atraves de Trie, que resolve o problema da precisão porem as desvantagens são: o tempo de execução é 5x mais lento do que a implementação do Hash e é utilizado muito mais memória do que os outros métodos (podendo chegar a 26^45 alocações de memória).
A terceira implementação é utilizando AVL, que resolve o problema da memória da Trie e da imprecisão do Hash, porém a custo de tempo de execução, que torna inviável sua utilização.

### Como utilizar:

Em linhas gerais, o corretor ortográfico (corretorOrtografico.c) recupera as palavras de um
arquivo-texto e as submete ao processo de conferência no dicionário. Ao final, o programa mostra
cada erro de ortografia no arquivo-texto junto com estatísticas de execução do processo.
De um modo geral, o programa corretorOrtografico.c só aceita dois parâmetros: um arquivo com
um dicionário e um arquivo-texto para correção. Após compilado, a forma de chamar o programa é
algo como está descrito abaixo:

> ./corretorOrtografico [dicionario] arquivo-texto <enter>

Onde:

> corretorOrtografico – é o nome do binário compilado à partir do código fonte fornecido

> dicionario – deve ser um arquivo contendo uma lista de palavras, em letras minúsculas, uma por
linha. Na pasta principal está o arquivo dicioPadrao que contempla o dicionário que deve ser
usado nos experimentos do projeto


> arquivo-texto – é um arquivo a ser corrigido ortograficamente. Os arquivos de teste estão
disponíveis na pasta textos


Como sugerem os colchetes, o uso do dicionário é opcional (se esse parâmetro for omitido, o
corretor usará o arquivo dicioPadrao como dicionário). Dentro desse arquivo estão as palavras a
serem carregadas na memória.
