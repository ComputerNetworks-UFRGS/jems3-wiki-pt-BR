# Relatórios

Os chairs podem acessar diferentes relatórios em _Events I'm Chairing > Administrate Event > Submissions_:

* **Show all submissions**: Lista de todas as submissões. Pode ser exportada em HTML;
* **Export BibTeX list**: Gera um arquivo BibTeX do evento com todas as informações registradas nas submissões;
* **Download files**: Permite baixar todos os arquivos de todas as submissões em um arquivo .zip, filtrados por track e trackfile.

# Sugestões de Atribuição para Revisores

### Notação

* _p_: número de artigos
* _t_: número de membros do TPC
* _r_: número de revisões requeridas para cada artigo
* _PT(x)_: lista de palavras-chave do x-ésimo artigo
* _TT(y)_: lista de tópicos de interesse do y-ésimo membro do TPC
* _nTT(y)_: lista de tópicos de não interesse do y-ésimo membro do TPC
* _W(x,y)_: peso do y-ésimo membro do TPC relacionado ao x-ésimo artigo

### Funções

A função W(x,y) é dada por:

TT'(x,y) - nTT'(x,y)

onde TT'(x,y) é o número de tópicos que pertencem tanto a PT(x) quanto a TT(y), e nTT'(x,y) é o número de tópicos que pertencem tanto a PT(x) quanto a nTT(y).

Por exemplo, se PT(x) = {'a', 'k', 't', 'z'}, TT(y) = {'a', 't'}, e nTT(y) = {'k'}, então:

### Algoritmo

1. Primeiro, o algoritmo cria uma matriz cujas colunas são compostas pelos membros do TPC, e as linhas são compostas pelos artigos. Cada célula é preenchida com o valor da função W calculando o peso para cada membro do TPC em relação a cada artigo.

2. Em seguida, o processo de atribuição começa baseado em dois valores: mMin e mMax

* mMin = (int) p * r / t

* mMax = (mMin != p * r / t) ? (mMin + 1) : mMin

3. O primeiro passo da atribuição buscará artigos/revisores com o maior peso, considerando que:  
   (a) o revisor (membro do TPC) tenha indicado/interessado no artigo,  
   (b) o artigo ainda não tenha sido atribuído ao revisor,  
   (c) o revisor não seja um dos autores do artigo,  
   (d) o revisor não esteja na lista de conflitos de nenhum dos autores do artigo,  
   (e) o revisor não esteja revisando mais que mMin artigos.

4. O segundo passo é idêntico ao primeiro, exceto que a condição (e) verifica se o revisor não está revisando mais que mMax artigos, ao invés de mMin.

5. O terceiro passo é idêntico ao primeiro, exceto que não considera a condição (a), ou seja, baseia-se apenas nos tópicos de interesse do revisor, sem considerar as indicações/interesses do revisor.

6. O quarto e último passo é idêntico ao terceiro, exceto que a condição (e) verifica se o revisor não está revisando mais que mMax artigos, ao invés de mMin.

