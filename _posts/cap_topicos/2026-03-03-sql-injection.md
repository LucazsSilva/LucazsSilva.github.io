---
title: "SQL Injection"
date: 2026-03-03 21:37:00
hidden: true
---

### O que é o SQL Injection?

Seria quando na entrada de dados, injetamos querys sql na aplicação. Com o sucessão de injeção, podemos ler dados sensiveis da aplicação, manipulação dos dados, bypass de telas de login e a divulgação dos do dados do sistema.

### Tipos de SQL Injection

Existem variações da vulnerabilidade

- Classic SQL Injection

É o tipo mais comum, onde um invasor explora os campos de entrada de uma aplicação web.

- Error based

Técnica de reconhecimento usada para pegar a estrutura do banco de dados e causado mensagens de erro. Essas mensagens de erro retornam informações importantes do schema e seus dados.

Query break

```sql
'
"
```

Query joined

```sql
or '1'
or 1='1'
AND '1'
AND 1='1'
```

Determinando números de colunas,

```sql
order by
```

- Union-Based

Ele usa o comando UNION para juntar o resultado da consulta com uma consulta nova criada pelo atacante, mas você precisa saber o número exato de colunas da consulta original. Esse número de colunas e encontrados através do `order by`

- Second-Order SQL Injection

Um input contendo payload SQL é enviado e armazenado no banco sem causar impacto imediato.
Posteriormente, esse dado armazenado é reutilizado na construção dinâmica de uma nova query SQL vulnerável, causando a execução da injeção. A second-order SQlI é tão prejudicial quanto a first-ordem, pois permite manipular a execução das queries SQL no backend e roube dados confidenciais.

A Second-Order SQL Injection é mais sutil e mais difícil de ser detectada, pois uma vez que a entrada é enviada em uma aplicação web, ela é armazenada no banco de dados e não é executada imediatamente. Quando ocorre uma outra requisição, a entrada maliciosa é carregada, permitindo o ataque.

Essa vulnerabilidade permite que o atacante manipule consultas SQL no backend, podendo levar à visualização, extração, modificação ou exclusão de dados sensíveis.

- Time Based

É um tipo de Blind SQL Injection onde o atacante não recebe mensagens de erro e nem diferenças visíveis na resposta da aplicação. A vulnerabilidade é identificada por meio da medição do te    mpo de resposta do servidor.

O atacante realiza uma injeção com uma condição que, se for verdadeiro, faz o banco executar uma função de atraso na consulta atual (como SLEEP(tempo)). Caso a resposta demore o tempo informado, isso indica que a condição foi avaliada como uma possibilidade de exploração.


> Além desses que expliquei, existem outras variações e técnicas que dependem do contexto da aplicação e do banco de dados utilizado.
{: .prompt-tip }

### Prevenção

- Query Parameterization - É uma técnica que visa seperar consultas SQL de valores de entrada do usuário.
- Input Validation - [Entendendo Input Validation]({% post_url cap_topicos/2026-02-21-cap-input-validation %})
- Implementação de whitelist
- Usar WAF (Web Application Firewall) - O WAF vai atuar como barreira entre a aplicação e a internet. Ele vai inspecionar e bloquear request recebidas em busca de uma assinatura, sequência de caracteres ou algum padrão malicioso e usando o aprendizado de máquina. 


**Referências**: 

[https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)

[https://cheatsheetseries.owasp.org/cheatsheets/Query_Parameterization_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Query_Parameterization_Cheat_Sheet.html)

[https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection)
