## Introdução
- Download Stata: https://mega.nz/folder/XipnmARC#atpQBsIsuvkres-BGC_pVQ
- Comunidade: https://www.statalist.org/
  
> O Stata é um software de estatística criado pela empresa StataCorp, sediada em College Station, Texas, EUA. Ele foi desenvolvido inicialmente em 1985 por William Gould, o fundador da empresa, como uma ferramenta para a análise de dados estatísticos.

### Arquivos .do
> No Stata é possível criar arquivos com a extensão .do, esses arquivos são script que podem armazenar comandos digitados no Stata em formato de texto, ou seja, um bloco de notas. Eles ajudam a automatizar análises de dados, permitindo que os usuários executem uma série de comandos de forma sequencial e replicável.

- Comandos Básicos -> https://github.com/HenrySchall/Basic_Stata/blob/main/Introdu%C3%A7%C3%A3o.do

#### Tipos de Dados

Qualitativos (atributos não numéricos).
- Nominais: Denominações (cores, gênero, raça, títulos…)
- Ordinais: atributos que podem ser classificados (Ex: classificação de filmes mais assistidos, grau de escolaridade, nível de satisfação…).

Quantitativos (atributos numéricas).
- Discreto: valores finitos ou enumeráveis (quantidade de pessoas numa sala, número de carros em um estacionamento…)
- Contínuo: infinitos valores possíveis num intervalo (renda, tempo, altura…).

### Demonstraçâo Prática 
> O exemplo e a base de dados são retirados do livro: "*Econometric Analysis of Cross Section and Panel Data, Second Edition, de Jeffrey M. Wooldridge*"

Carregar Base -> health.dta

```r
sum
```
![1](https://github.com/user-attachments/assets/6a0e0bb3-380f-484e-8d34-abcdbac26e37)

```r
tab age
```
![2](https://github.com/user-attachments/assets/be67fa1b-0776-40ad-8d9a-1d28ca7c24f3)

> Podemos observar que a base de dados apresenta idades que vão de 65 anos até 90 anos

```r
sum age if female==1
```
![3](https://github.com/user-attachments/assets/1f93dd99-31f0-4dcb-9bc3-649b2d38803f)

> Obtendo o resumo da variável age, condicionado ao fator de ser mulher

```r
sum age if female==0
```
![4](https://github.com/user-attachments/assets/acc6c15e-877e-4133-b4aa-b80cc7e502cb)

> Obtendo o resumo da variável age, condicionado ao fator de não ser mulher
 
```r
sort female
by female:sum age
```
![5](https://github.com/user-attachments/assets/bc362efb-010d-4667-85c0-be9e96431a4c)
> Obtendo o resumo da variável female, condicionado ao fator idade (age)

```r
generate log_age = log(age)
gen ln_age = ln(age)
```
> Gerando os logs da variável age

```r
pwcorr age famsze, star(.1)
```
![7](https://github.com/user-attachments/assets/3f2dd87e-5de6-416e-b975-f2cfdcc75f83)
> Gerando matriz de Correlação.
  - O comando star(.1) adiciona asteriscos à matriz de correlação para indicar a significância estatística com um nível de significância de 0.1 (10%)

```r
reg totexp age famsze
```
![8](https://github.com/user-attachments/assets/53122f77-059c-4324-9bad-a2da4bd94bd9)

* a ordem é variavel dependente e depois as variaveis explicativas
* estimação de todos os elementos é sempre usando MQO
* std. err = erros padrões
* se o meu modelo passa no teste global eu não preciso fazer os testes individuais
* leitura coeficiente -> controlado pela variavel idade quando vc aumenta o tamanho da familia em 1 unidade os dados em media os gastos de saude caem 482 dolares
* R-Squared * 100 = significa que 24% da idade e o do tamanho da familia explicam os gastos totais
* analisando coeficientes -> age é positivo então o aumento da idade aumenta os gastos da família, já o tamanho da família é negativo, isso significa que familias maiores gastam menos


correlcao e o grau de associacao eentre duas variavies





