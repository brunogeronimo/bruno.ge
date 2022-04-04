---
title: "Trezor - Análise de e-mail falso"
date: 2022-04-02T11:30:00+02:00
draft: false
authors: [Bruno Geronimo]
reviewers: [Giullia Cristiny]
summary: "Recebeu um e-mail dizendo que você foi vítima de um vazamento? O e-mail é falso, e 
aqui eu explico por quê."
---
Pra quem não sabe, eu invisto em algumas criptomoedas, e decidi comprar uma hard wallet da
[Trezor](https://trezor.io). Hoje eu acordei com um e-mail inusitado que aparentemente foi 
enviado por eles:

{{< cdn src="trezor/email.jpg" alt="E-mail falso" >}}

Eu costumo sempre deletar e-mails com conteúdo muito "alarmista", mas alguns pontos me levaram a 
me assustar e a acreditar nesse e-mail quando o li.

Eu criei o hábito de cadastrar e-mails com aliases em sites. Um alias nada mais é do que um apelido
que podemos usar no e-mail. Ao invés de utilizar oi@bruno.ge em todos os sites, eu uso
oi+americanas@bruno.ge, por exemplo. Isso é bem útil pra segurança, mas entrarei em mais detalhes
sobre o motivo em outro artigo.

O que me fez levar esse e-mail a sério foi ter recebido o e-mail da Trezor **com** o 
alias, e nesse caso específico um alias que eu só utilizo neste serviço.

Quando eu abri o link, fui redirecionado para a seguinte página:

{{< cdn src="trezor/fake_trezor_page.png" alt="Trezor - Página falsa" >}}

Foi quando eu tentei ir para a página principal, trezor.com, e percebi algo estranho. Eu fui 
parar num site russo que vende belíssimos cofres:

{{< cdn src="trezor/trezor.com.png" alt="Site russo com belíssimos cofres" >}}

Repararam algo de estranho na URL? O link que eu fui redirecionado é, na verdade, suite.trẹzor.
com, com *ẹ*, não *e*. O domínio fica um pouquinho diferente neste caso:

{{< cdn src="trezor/converted-domain.png" alt="Domínio comvertido" >}}

Esse golpe é conhecido como [IDN homograph attack](https://en.wikipedia.org/wiki/IDN_homograph_attack).
Tratam-se de domínios que são muito semelhantes ao original, porém usando caracteres de 
alfabetos não latinos, como cirílico ou acentuados, como ã, ou ẹ, nesse caso.

Olhando para a página, eu decidi clicar em `Trezor suite for web` pra ver para onde eu seria 
redirecionado, e o link aponta para web.trezorwallet.org, que é diferente do link oficial 
https://suite.trezor.io/web/.

Com essas suspeitas em mente, eu decidi checar a data de registro desses domínios, o que também 
é estranho:

| Domínio                                              | Data de criação             |
|------------------------------------------------------| --------------------------- |
| xn--trzor-o51b.com (trẹzor.com) - Página principal   | 27/03/2022 - 11:09:17 (UTC) |
| trezorwallet.org - Página do webclient               | 27/03/2022 - 07:03:32 (UTC) |
| trezor.us - Domínio do remetente do golpe            | 09/07/2021 - 00:01:19 (UTC) |

A Trezor é uma empresa que existe desde 2013, então ter domínios tão recém criados também é um 
indicativo de golpe.

Um outro detalhe é que a maioria dos aplicativos criados pela Trezor são 
[open-source](https://github.com/trezor), 
incluindo [Trezor Suite](https://github.com/trezor/trezor-suite), 
a [página inicial](https://github.com/trezor/trezor-suite/tree/develop/packages/suite-web-landing) 
do Trezor Suite e o próprio [site](https://github.com/trezor/trezor-suite/tree/develop/packages/suite-web).
Qualquer pessoa pode baixar o código-fonte, editar os aplicativos e criar clients adulterados ou 
páginas extremamente convincentes por conta disso.

Depois de analizar todos esses fatores, apesar do e-mail ter me convencido a princípio por conta 
do alias, tudo indica que a lista foi vazada de alguma forma e os e-mails foram uma tentativa de 
golpe.

A Trezor também anunciou em seu [Reddit](https://www.reddit.com/r/TREZOR/comments/tv5yn9/we_are_investigating_a_potential_data_breach_of/) 
sobre o possível vazamento de dados no MailChimp.

Eu reportei o incidente para todas as empresas envolvidas no registro dos domínios checando o 
WHOIS, para o 
[Internet Crime Complaint Center](https://www.ic3.gov/) e para o 
[Internet Beschwerdestelle](https://www.internet-beschwerdestelle.de/en/index.html).

# Atualizações

* Trezor confirmou em seu [Twitter](https://twitter.com/Trezor/status/1510558771944333312) que 
  houve um vazamento de dados por parte de MailChimp.
* Os domínios trezor.us e xn--trzor-o51b.com (trẹzor.com) foram derrubados 
  ([fonte](https://twitter.com/Trezor/status/1510602645572050949)).
* Após receber feedback, alguns parágrafos foram reescritos para melhorar a leitura.