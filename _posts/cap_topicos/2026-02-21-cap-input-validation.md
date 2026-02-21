---
title: "Input Validation Mechanisms"
date: 2026-02-21 19:00:00
hidden: true
---

### O que é o Input Validation?

A validação de entrada é um processo que tem que ser feito para garantir que os dados enviados estejam de acordo com o tipo especificado (como formato, tipo do dado e etc). Caso essa validação seja inadequada, o invasor pode injetar dados maliciosos na aplicação vulnerável. A validação de dados deve ser feita o mais cedo possível, idealmente quando os dados forem recebidos de fontes externas. 

A validação de entrada não deve só feita para previnir SQL Injection, XSS, XML e outros ataques. Por motivo de informação, a validação de entrada pode ser explorada em: XSS (Armazenado e Refletido), HTTP Parameter Pollution, SQLi, XML Injection, XML Injection, Mass Assignment e outros ataques.

- Devemos realizar a validação tanto no nível síntatico como no nível semântico

***Validação Semântica:*** É quando garantimos que a sintaxe, dentro dos valores exegidos, está correta. Por exemplo, datas, limite em transações, sinais negativos: temos um carrinho de compra e é possível informar um valor negativo, podendo causar algum estorno ou até “credito” dentro da aplicação.

***Validação Sintática:*** Deve garantir a sinaxe correta dos campos estruturados, ou seja, é focado expecificamente na estrutura do dado. É a primeira barreira que vai impedir o envio de caracteres maliciosos para quebrar a aplicação. Realizamos a validação em moedas, data: na data devemos seguir um padrão (ex: → ISO 8601 **AAAA-MM-DD).**

Algumas maneiras de realizar as validações na aplicação.

- Uso de expressões regulares (Regex)

A OWASP **(Open Worldwide Application Security Project)** faz um alerta sobre o uso de regex. Ao usar regex na sua validação, fique ciente de aplicar em toda a string. Usando o “^” para podermos percorrer do início ao fim e “$” para a selecionarmos a string inteira.

```java
/[0-9]+/ -> forma errada
/^[0-9]+$/ -> forma correta
```

Um adendo seria que cuidado ao usar regex, pois pode ser causado um ReDoS (Ataque de negação de serviço por expressão regular). Um exemplo desse ataque seria quando é enviado uma string projetada especifamente para o regex implementado e fazer com que ele fique carregando infinitamente, causando um travamento no servidor.

- Realizar a conversão de tipos

Juntamente com a conversão de tipos (Integer.parseInt(), Int(), parseInt()), usar também um tratamento rigoroso de exceções.

- Sanatização

Utilizada quando precisamos aceitar caracteres perigosos por exemplo, como em um campo de comentário que aceita pontuação. A sanitização remove ou modifica partes perigosas do input.

- Exemplo

Remover `javascript:` de uma URL.

- O caminho do arquivo precisa ser informado no backend da aplicação
- Verificação da extensão de arquivos, juntamente com seu tamanho.

Por exemplo, criar uma “whitelist” de extensões

```java
allowed_extensions = ('jpg', 'png')
```

**Referências**: 

[https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)

[https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/07-Input_Validation_Testing/README](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/07-Input_Validation_Testing/README)