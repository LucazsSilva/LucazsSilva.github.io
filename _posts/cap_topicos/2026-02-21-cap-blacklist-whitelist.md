---
title: "Blacklist & Whitelist"
date: 2026-02-21 19:00:00
hidden: true
---
### Sobre blacklist e whitelist

A entradas maliciosas é realizada intecionalmente para explorar vulnerabildades em uma aplicação. Podemos comprometer funcionalidades e, com isso, afetar a segurança da aplicação. Criando uma blacklist para bloquear essas entradas maliciosas, evitaremos que um atacante explorar essas vulnerabilidades. O objetivo também de uma whitelist seria justamente para tratar e permitir apenas entradas que são válidas. Mas em resumo, essa prática é importante, pois geralmente rejeita entradas de conteúdos específicos e conhecidos. Seja por caracteres, padrões, sequências e outros metódos de verificação.

- Blacklist

A blacklist envolve bloquear caracteres que possam causar uma possível exploração, ou seja, baseia-se no princípio de **exclusão**. 

Por exemplo:

```java
<script>, SELECT, '
```

Mesmo que tenhamos realizado um filtro para “bloquear” esses caracteres, o atacante pode usar, por exemplo, um encode de url

```java
<script>alert(1)</script> //Sem urlencode
%3Cscript%3Ealert%281%29%3C%2Fscript%3E //Com urlencode
```

Esse metódo não é o dos melhores para realizar validações e o metódo comum seria o uso de **regex (Expressões Regulares)**

```java
'|%|--|;|/⧹∗|⧹⧹⧹∗|_|⧹[|@|xp_
```

***Lembrando que cuidado ao usar Regex e se atente no uso dele. Expliquei sobre em [Entendendo Input Validation]({% post_url cap_topicos/2026-02-21-cap-input-validation %})***

- Whitelist

A whitelist tem o objetivo de verificar se os dados enviados correspodem ao que foi definido na regra. Por exemplo, comprimento, tipo do dado, valores esperados pela aplicação e etc. Um exemplo seria quando enviamos um CPF, ser feito a validação se tem 11 dígitos, verificar se o cpf não é inválido e passar no cálculo de validação de cpf.

- Tipo de dado: O dado é realmente o que a aplicação espera? Se ele deve ser númerico ou não, se deveria ser número positivo.
- Limite de caracteres: Um campo com limite de caractares evita entradas excessiva no campo

```html
<form action="/login.php">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" maxlength="10">
  <input type="submit" value="Submit">
</form>
```

Essa validação é 100% segura (confia)

Como já foi falado, evitar deixar que o usuario tenha controle de algo. A forma correta seria validar no backend, onde o usuário é decretado, abolido e não tem aura.

- Uso de Regex: Olha o regex sendo citado novamente. Com o regex eu consigos setar regras específicas falando o que é permitido.
- Verificação de upload de imagens: Validar entrada, tamanho, tipo do arquivo, alterar o nome quando entrar na aplicação é muito importante. Leia mais em: [https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)

