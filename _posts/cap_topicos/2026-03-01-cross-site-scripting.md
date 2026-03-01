---
title: "Cross Site Scripting"
date: 2026-03-01 19:44:00
hidden: true
---

### O que é o Cross Site Scripting?

É um tipo de vulnerabilidade, onde é injetado scripts maliciosos que são executados no navegador da vitima. O problema está centralizado na falta de tratamento dos dados, pois aceitam e armazenam dados sem a devida sanitização

<aside>
🧠

Sanitização - Técnica utilizada para filtrar e remover caracteres especiais em scripts maliciosos.

</aside>

Essa vulnerabilidade permite explorar cookies de sessão, reescrever o conteúdo HTML, redirecionamento de páginas e várias outras técnicas.

Entenda mais sobre os tipos de XSS: 

### Reflected XSS

Esse XSS ocorre quando é injetado payload e a aplicação web já retorna o resultado dessa payload. Por exemplo, temos um campo com “código promocional” e nele iremos colocar o seguinte script

```jsx
<img src=x onerror="alert(1)">
```

Ou outro exemplo, seria um de busca, onde teriamos a seguinte url:

```jsx
https://javalicansado.com/procurar?item=<script>alert(1)</script>
```

Iremos ter uma reposta assim na aplicação

![image.png](attachment:58377324-bb05-4aef-bfc6-93d346cba29d:image.png)

### Stored XSS

O Stored XSS surge quando é enviado um script e é armazenado no servidor, como em um banco de dados. Imagine um fórum e nele há um campo de comentários. O invasor pode simplesmente carregar um xss armazenado e deixar nesse campo. Sempre que um usuário acessar a página que exibe esses dados, o script será executado no navegador dele.

Como seria o fluxo de ataque:

1. Injeção - Temos o envio do script no campo de comentários
2. Armazenamento da payload - O servidor recebe esse script e salva no seu banco de dados.
3. Execução do script no navegador da vítima - Qualquer usuário que entrar na sessão de comentários, o script que está no banco é executado.
4. Atacante Feliz

### DOM Based XSS

Vulnerabilidade que ocorre inteiramente no lado do client, onde a   script malicioso modifica o Document Objetct Model (DOM). A resposta  http não muda, mas o código rodado na página roda de uma forma   diferente, devido as modificações realizadas. Ele escreve de forma   indevida em pontos de execução, como **innerHTML** ou **eval()**. 

### Prevenção

- Escaping / Encoding / Sanitização - Garantir que tudo enviado seja passado por uma validação, higienizadas
- Content Security Policy (CSP) - São instruções que instruem o navegador a realizar restrições às ações que o código do site pode executar. Fazendo que o nevagador execute apenas fontes específicas.
- HttpOnly - Impedindo que o Javascript tenha acesso aos cookies de sessão, anulando ataques, por exemplo, o roubo de sessões.



**Referências**: 

[https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)


[https://owasp.org/www-community/attacks/DOM_Based_XSS](https://owasp.org/www-community/attacks/DOM_Based_XSS)


[https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html)


[https://owasp.org/www-community/attacks/xss/#stored-and-reflected-xss-attacks](https://owasp.org/www-community/attacks/xss/#stored-and-reflected-xss-attacks)


[https://learn.snyk.io/lesson/dom-based-xss/?ecosystem=javascript](https://learn.snyk.io/lesson/dom-based-xss/?ecosystem=javascript)
