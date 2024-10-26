
# Analise de dados do Oscar

 Atividade referente ao Banco do Oscar

* 1- Quantas vezes Natalie Portman foi indicada ao Oscar?

   R: 3

```js
db["Registros"].countDocuments({nome_do_indicado:"Natalie Portman"})
```

* 2- Quantos Oscars Natalie Portman ganhou?

   R: 1

```js
db["Registros"].countDocuments({nome_do_indicado:"Natalie Portman", vencedor:'1'})
```

* 3- Amy Adams já ganhou algum Oscar?

   R: Não

```js
 db["Registros"].countDocuments({nome_do_indicado:" Amy Adams", vencedor:'0'})
```

* 4- A série de filmes Toy Story ganhou um Oscar em quais anos?

   R: O filme Toy Story ganhou três vezes, sendo duas vezes em 2011 e uma em 2020.

   ano_cerimonia: 2011

   ano_cerimonia: 2011

   ano_cerimonia: 2020

```js
 db["Registros"].find({nome_do_filme:/Toy Story/,vencedor:'1'},{ano_cerimonia:1,_id:0})
 ```

* 5- A partir de que ano que a categoria "Actress" deixa de existir?
 
   R: No ano de 1976

  ano_cerimonia: 1976

```js
 db["Registros"].find({categoria:"ACTRESS",vencedor:'1'},{ano_cerimonia:1,_id:0}).sort({ano_cerimonia:-1}).limit(1)
```

* 6- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?

   R: A primeira da categoria foi Janet Gaynor, no ano de 1928.

   ano_cerimonia: 1928
  
   nome_do_indicado: 'Janet Gaynor'

```js
db["Registros"].find({categoria:"ACTRESS",vencedor:'true'},{ano_cerimonia:1,nome_do_indicado:1,_id:0}).sort({ano_cerimonia:1}).limi(1)
```

* 7- Na campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.

```js
db["Registros"].updateMany({vencedor:'true'},{$set:{vencedor:'1'}})
db["Registros"].updateMany({vencedor:'false'},{$set:{vencedor:'0'}})
```


* 8- Em qual edição do Oscar "Crash" concorreu ao Oscar?

   R: A edição do filme "Crash" foi concorrida no ano de 2006.

   ano_cerimonia: 2006

```js
db["Registros"].find({nome_do_filme:/Crash/},{ano_cerimonia:1,_id:0}).sort({ano_cerimonia:-1}).limit(1)
```
 9- Bom... dê um Oscar para um filme que merece muito, mas não ganhou.

  R: O filme "Emma".
  ```js
  db["Registro"].updateOne({nome_do_filme:"Emma"},{$set:{vencedo:"1"}});
  ```

* 10- O filme Central do Brasil aparece no Oscar?

  R: Sim, o filme "Central Station" concorreu duas vezes em 1999, mas nunca ganhou.
  ```js
  db["Registros"].find({nome_do_filme:"Central Station"},{ano_cerimonia:1,_id:0}).sort({ano_cerimonia:-1}).pretty()
```
* 11- Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser.
  R: Os filmes "Divergente","Jonh Wick","Crepúsculo".
```js
db["Registros"].insertMany([
{nome_do_filme:"Jonh Wick", ano_filmagem:2014,vencedor:"1"},
{nome_do_filme:"Divergente",ano_filmagem:2014,vancedor:"1"},
{nome_do_filme:"Crepúsculo",ano_filmagem:2008,vancedor:"1"}
]) 
```
* 12 - Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?
 R: No ano de 2005 o melhor filme foi "
```js
db["Registos"].find({nome_do_filme:"1",ano_cerimonia:2005,nome_do_indicado:"1",categoria:"1",_id:0})



