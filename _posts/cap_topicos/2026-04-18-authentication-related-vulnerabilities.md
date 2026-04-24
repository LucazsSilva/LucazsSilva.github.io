---
title: "Authentication Related Vulnerabilities"
date: 2026-04-18 15:23:00
hidden: true
---

As vulnerabilidades relacionadas à autenticação surgiram com a própria necessidade de restringir o acesso. Em ambientes corporativos, as vulnerabilidades deixam de ser um “erro técnico” e passam a ser um risco de negócio. Um exploção bem sucedida, explorando mecanismo de autenticação, como senhas fracas, credenciais padrão e erros de lógica, pode significar vazamento de dados de clientes, ataques de ransowares.

#### Falando sobre autenticação - Por que ela é importante?

É um processo que verifica a identidade de alguém, ou seja, ela confirma que você é realmente quem diz ser. Sem esse processo, sua conta poderia ser acessada. Imagina que qualquer pessoa poderia ter acesso a sua conta bancária (não sei se a pessoa ia ficar triste ou feliz). 

#### Como surgem as vulnerabilidades de autenticação

Essa vulnerabilidades surgem quando há falhas na implementação de processos, seja no software, lógico ou no gerenciamento fraco.

**Mecanismos de Defesa Fracos -** O sistema não tem barreiras suficientes para impedir o atacante. Seja uma política errada, erro em gerenciar as sessões, falta de MFA

**Engenharia Social -** O atacante pode induzir o usuário a passar suas crendenciais, por exemplo, se passando por um e-mail de algum serviço que o usuário use. Outro fator critico humano é o reuso de senhas

**Uso de Credenciais Padrão -** Muitos dispositivos já saem das fábricas com uma senha padrão.

#### Mitigação

1. Uso de senhas fortes e autenticação de dois fatores.
2. Impedir o processo de enumeração de usuários, por exemplo, não exibi uma mensagem “usuário existe” ou “usuário não existe”
3. Medidas para detecção de força bruta.
4. Nunca armazenas senhas em texto simples. Sempre utilizar algortimos de criptografia modernos e uso de salt.
5. Usar protocolo seguros. Garantir que páginas utilizam protocolos com criptografia, seja ela o https com versões do tls mais recentes.

Embora existam inúmeras técnicas e ferramentas para mitigação, implementando os pilares da autenticação, você transforma sua aplicação de um alvo fácil em um “alvo menos fácil”.


**Referências**: 

[https://www.ibm.com/br-pt/think/topics/authentication](https://www.ibm.com/br-pt/think/topics/authentication)

[https://portswigger.net/web-security/authentication](https://portswigger.net/web-security/authentication)

[https://portswigger.net/web-security/authentication/securing](https://portswigger.net/web-security/authentication/securing)

[https://www.strongdm.com/blog/authentication-vulnerabilities](https://www.strongdm.com/blog/authentication-vulnerabilities)

[https://owasp.org/Top10/2021/A07_2021-Identification_and_Authentication_Failures/](https://owasp.org/Top10/2021/A07_2021-Identification_and_Authentication_Failures/)






