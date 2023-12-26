# Desafio SQL - Banco de Dados
> www.dio.me | Cassio 30/10/2023

## Agradecimentos
[Bruno Freschi](https://github.com/BrunoFreschiAgger) Nǐ hǎo👋 |
[Cassia Alvalaz](https://github.com/CassiaAlvalaz) |
[Gabriel Pimenta](https://github.com/Gabranato).

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de banco de dados, da trilha .NET da DIO.

## Contexto
Você é responsável pelo banco de dados de um site de filmes, onde são armazenados dados sobre os filmes e seus atores. Sendo assim, foi solicitado para que você realize uma consulta no banco de dados com o objetivo de trazer alguns dados para análises.

## Proposta
Você precisará realizar 12 consultas ao banco de dados, cada uma retornando um tipo de informação.<br/>
O seu banco de dados está modelado da seguinte maneira:

![Diagrama banco de dados](Imagens/diagrama.png)

## Estrutura do Banco de Dados
As tabelas sao descritas conforme a seguir:

- **Tabela Filmes**   armazena informações dos filmes.
- **Tabela Atores**   armazena informações dos atores.
- **Tabela Generos**  armazena os gêneros dos filmes.
- **Tabela ElencoFilme**   representa um relacionamento do tipo muitos para muitos entre filmes e atores, ou seja, um ator pode trabalhar em muitos filmes, e filmes podem ter muitos atores.
- **Tabela FilmesGenero**  representa um relacionamento do tipo muitos para muitos entre filmes e gêneros, ou seja, um filme pode ter mais de um gênero, e um genêro pode fazer parte de muitos filmes.

## Preparando o banco de dados
Você deverá executar o arquivo **Script Filmes.sql** em seu banco de dados SQL Server, presente na pasta Scripts deste repositório ([ou clique aqui](Script%20Filmes.sql)). <br/>Esse script irá criar um banco chamado **Filmes**, contendo as tabelas e os dados necessários para você realizar este desafio.

## Objetivo
Você deverá criar diversas consultas, com o objetivo de retornar os dados a seguir. Abaixo de cada pedido tem o retorno esperado. <br/> **O seu retorno deve ser igual ao da imagem.**

## 1 - Nome e ano dos filmes✅
```sql
SELECT Nome, Ano
FROM Filmes
```
![Exercicio 1](Imagens/1.png)

## 2 - Nome e ano dos filmes, ordenados por ordem crescente pelo ano✅
```sql
SELECT Nome, Ano, Duracao
FROM filmes ORDER BY Ano
```
![Exercicio 2](Imagens/2.png)

## 3 - Filme de volta para o futuro, trazendo o nome, ano e a duração✅
```sql
SELECT Ano, Nome, Duracao
FROM Filmes  WHERE Nome LIKE  'DE VOLTA PARA O FUTURO'
```
![Exercicio 3](Imagens/3.png)

## 4 - Filmes lançados em 1997✅
```sql
SELECT Nome, Ano, Duracao
FROM FILMES WHERE Ano = 1997
```
![Exercicio 4](Imagens/4.png)

## 5 - Filmes lançados APÓS o ano 2000✅
```sql
SELECT Nome, Ano, Duracao
FROM Filmes WHERE Ano > 2000
```
![Exercicio 5](Imagens/5.png)

## 6 - Filmes com a duracao maior que 100 e menor que 150, ordenando pela duracao em ordem crescente✅
```sql
SELECT Nome, Ano, Duracao FROM Filmes
WHERE Duracao > 100 AND Duracao < 150 ORDER BY Duracao
```
![Exercicio 6](Imagens/6.png)

## 7 - A quantidade de filmes lançadas no ano, agrupando por ano, ordenando pela duracao em ordem decrescente✅
```sql
SELECT Ano, COUNT(*) Quantidade FROM Filmes
GROUP BY Ano ORDER BY Quantidade DESC
```
![Exercicio 7](Imagens/7.png)

## 8 - Buscar os Atores do gênero masculino, retornando o PrimeiroNome, UltimoNome ✅
```sql
SELECT * FROM Atores
WHERE Genero = 'M'
```
![Exercicio 8](Imagens/8.png)

## 9 - Atores do gênero feminino, retornando o PrimeiroNome, UltimoNome, e ordenando pelo PrimeiroNome ✅
```sql
SELECT * FROM Atores
WHERE Genero = 'F'
ORDER BY PrimeiroNome
```
![Exercicio 9](Imagens/9.png)

## 10 - Buscar o nome do filme e o gênero ✅
```sql
SELECT Nome, Genero FROM Filmes
INNER JOIN FilmesGenero ON Filmes.Id = FilmesGenero.IdFilme
INNER JOIN Generos ON FilmesGenero.IdGenero = Generos.Id
```
![Exercicio 10](Imagens/10.png)

## 11 - Nome do filme e o gênero do tipo "Mistério" ✅
```sql
SELECT Nome, Genero FROM Filmes
INNER JOIN FilmesGenero ON Filmes.Id = FilmesGenero.IdFilme
INNER JOIN Generos ON FilmesGenero.IdGenero = Generos.Id
WHERE Genero = 'Mistério'
```
![Exercicio 11](Imagens/11.png)

## 12 - Nome do filme e os atores, trazendo o PrimeiroNome, UltimoNome e seu Papel ✅
```sql
SELECT Nome, PrimeiroNome, UltimoNome, Papel FROM Filmes
INNER JOIN ElencoFilme ON ElencoFilme.IdFilme = Filmes.Id
INNER JOIN Atores ON ElencoFilme.IdAtor = Atores.Id
```
![Exercicio 12](Imagens/12.png)
