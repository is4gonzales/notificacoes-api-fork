# Registro de Testes Unitários

Aluno: Isabele Gonzales Firmino  
Grupo: 01  
Data: 24/09/2026  

## Testes escritos

| # | Arquivo | O que o teste verifica | Tipo |
| - | ------- | ---------------------- | ---- |
| 1 |`ambiente.test.js` |(1 + 1 = 2) |sucesso|
| 2 |`validators.test.js`|`isEmail` aceita um e-mail válido retornando `null` |sucesso|
| 3 |`validators.test.js`|`isEmail` nega um e-mail inválido sem o caractere `@` |falha|
| 4 |`validators.test.js`|`minLength` aceita uma string com o tamanho exato do limite mínimo|borda|
| 5 |`parseId.test.js`|lança `ValidationError` caso receba uma string só de letras|falha|
| 6 | `parseId.test.js`|nega um ID com números e letras como `"12abc"`|borda|

## Resultado

Passaram: 4
Falharam: 2

## Defeito encontrado

Teste: `parseId.test.js` (`"12abc"`)
Esperado: Lançar um erro `ValidationError` por ser um formato inválido.
Obtido: O teste falhou 

## Cobertura

% Lines da linha "helpers": 33.33
Em uma frase, o que esse número significa: Os testes cobrem apenas 33.33 das linhas da pasta *helpers*.
