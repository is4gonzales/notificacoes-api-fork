# Registro de Testes de Endpoint
Aluno:
Grupo:
## Testes escritos
| # | Verbo e rota | Com token? | Status esperado | Verde ou vermelho? |
| --- | ------------ | ---------- | --------------- | ------------------ |
| 1 | `POST /eventos` | Sim (`Bearer <token>`) | `201` | Verde |
| 2 | `GET /eventos/:id` | Não | `404` | Verde |
| 3 | [Ex: `POST /eventos` (data passada) ou rota do desafio] | [Sim / Não] | [Ex: `400` ou `422`] | Vermelho (ou Verde) |

## Resultado

Linha "Tests:" da saída do npm run test:endpoint:
`Tests: 1 failed, 4 passed, 5 total` *(ou cole exatamente a última linha `Tests: ...` que apareceu no seu terminal)*

Teste:
Esperado:
Obtido:
Em qual aula esse mesmo defeito já tinha aparecido, e como: Aula 04. O parseId("12abc") devolvia 12 em vez de dar erro.