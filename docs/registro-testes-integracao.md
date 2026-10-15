```markdown
# Registro de Testes de Integração


Aluno: Isabele Gonzales Firmino
Grupo: 02
Data: 15/10/2026


## Banco de teste


Nome do banco de teste: notificacoes_test
Por que ele é separado do banco da API (uma frase): Ele garante que os dados criados, alterados ou apagados durante os testes automatizados não poluam ou corrompam os dados reais de desenvolvimento e produção da API


## Testes escritos


| #   | Arquivo | O que o teste verifica | Verde ou vermelho? |
| --- | ------- | ---------------------- | ------------------ |
| 1   | `evento.integration.test.js` | Se o evento é gravado com o nome correto no banco de dados. | Verde |
| 2   | `participante.integration.test.js` | Se a gravação de participante com e-mail inválido (sem @) é recusada. | Verde |
| 3   | `participante.integration.test.js` | Se a rota/método de atualização realmente salva o nome novo no banco. | Vermelho (Desafio) |


## Resultado


Linha "Tests:" da saída do npm run test:integration:
- Tests: 2 failed, 3 passed, 5 total 


## Defeito encontrado


Teste: ParticipanteService.atualizar (integração) > grava o nome novo do banco
Esperado: "Ana Maria"
Obtido: "Ana"
O que o usuário da API veria (a rota responde 200, mas...): O usuário faz uma requisição para atualizar o seu nome, a API responde com o status de sucesso '200 OK', mas a alteração não é persistida de verdade no banco de dados (o nome atigido continua lá)

```
# Ticket de saída — individual

**1. Por que os testes de integração usam um banco separado do banco da API?**
Porque os testes limpam e reiniciam tabelas constantemente (`beforeEach`/`afterEach`). Usar um banco separado evita que dados reais de uso ou de desenvolvimento sejam apagados acidentalmente.

**2. No Assert, por que buscamos o registro de novo no banco, em vez de conferir o objeto que o service devolveu?**
Porque o objetivo do teste de integração é validar a persistência real. O service pode retornar um objeto alterado em memória com sucesso, mas falhar na hora de salvar definitivamente no banco de dados por um erro de query ou configuração.

**3. A rota PUT /participantes/:id responde 200. O que o seu teste do desafio mostrou sobre ela?**
O teste mostrou que a rota possui um defeito de consistência (falso positivo). Ela devolve o código de sucesso '200', mas a lógica interna não está executando a query de UPDATE corretamente no MySQL, mantendo o registro original intacto.