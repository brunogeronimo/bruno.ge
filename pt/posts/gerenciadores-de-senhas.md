---
title: Por que você deveria usar um gerenciador de senhas
date: 2022-09-27T21:19:27+02:00
draft: false
authors: [Bruno Geronimo]
reviewers: []
translators: []
summary: É comum as pessoas não verem valor nessa mudança, ou acharem muito confuso ou complicado. Vamos explorar um pouco o assunto!
---

__Aviso: Este não é um post patrocinado.__

Recentemente, eu convenci uma amiga a dar uma chance a um gerenciador de senhas. Eu noto que sempre que falo disso com outras pessoas, há uma certa resistência. Algumas acham muito complicado, outras não vêem valor na mudança, e por aí vai. Meu intuito com este artigo é te convencer a pelo menos dar uma chance a esta ferramenta.

## O problema

Nós usamos diversos serviços online diariamente, seja pra trabalho ou pra entretenimento. Netflix, TikTok, Twitter, e-mail, banco, entre outros. É bem difícil não depender deles no cotidiano.

Por conta da quantidade de coisas, é bem comum as pessoas reciclarem senhas. Muita gente usa a senha da conta do Google em outros sites, como redes sociais, serviços de streaming e até mesmo bancos, e isso é um problema.

Se uma de suas senhas for vazada na internet ou descoberta, você ficará em uma situação bem vulnerável. Quando vazamentos ocorrem, é bem comum hackers tentarem essas mesmas credenciais de serviços menos seguros em sites mais críticos, como Google e Apple. Quando se reutiliza senhas entre serviços, a chance de afetarem outras contas além da que foi vazada acaba aumentando.

Além disso, mesmo serviços menos críticos também armazenam informações sensíveis. Todo site pago precisa de dados de faturamento do usuário, que incluem número de telefone e endereço. Tais informações podem acabar sendo acessadas por terceiros quando não usamos uma senha segura.

## Gerenciadores de senhas

Para explicar melhor o que eles fazem, vamos imaginar o seguinte cenário: Carla usa uma única senha criada em 2012 em todas as contas que ela cria.

{{< cdn src="images/carla_caotico_senhas.png" alt="Cenário caótico de Carla" >}}

A senha `Abacate@2012` é utilizada em tudo. Twitter, Instagram, Facebook, banco... Enfim, tudo.

Quando utilizamos um gerenciador de senhas, nós damos à Carla uma única missão: Criar uma senha forte. Neste exemplo, usaremos Carla_Senh@forte#2020!.

A idéia é que Carla delegue a tarefa de criar senhas únicas para tudo a um aplicativo, que as armazena de forma segura e criptografada. Isso muda o cenário acima para o diagrama abaixo:

{{< cdn src="images/carla_feliz_senhas.png" alt="Cenário feliz de Carla" >}}

Desta forma, resolvemos o principal problema. Caso a conta do Spotify seja hackeada, por exemplo, Carla não precisará entrar em pânico. A senha do serviço de streaming não é usada em nenhum outro lugar.

## Como isso funciona de maneira segura

O usuário precisa pensar em uma senha forte, contendo letras maiúsculas e minúsculas, números, símbolos e o número máximo de caracters que conseguir. Tenha em mente que você **não pode, sob nenhuma hipótese, esquecer essa chave. Caso isso ocorra, você provavelmente perderá o acesso ao cofre.**

O gerenciador utiliza esta senha para criptografar tudo que ele armazena. Desta forma, caso ocorra alguma invasão ou vazamento de dados, nada poderá ser lido por um terceiro, já que apenas o dono da conta tem acesso a senha utilizada.

## Opções disponíveis

Existem várias opções no mercado. Algumas gratuítas, soluções de código aberto, self-hosted, entre outros.

### Por onde começar

Aqui cito algumas sugestões de gerenciadores de senhas, sendo que os quatro primeiros oferecem armazenamento **gratuito** ilimitado de credenciais:

* Bitwarden: https://bitwarden.com/
* LastPass: https://www.lastpass.com
* NordPass: https://nordpass.com
* Apple Keychain: https://support.apple.com/en-us/HT204085 (só recomendo caso você tenha iPhone e MacBook)
* 1Password: https://1password.com/

Além disso, todos os listados acima oferecem opções para exportar os dados, caso você mude para outro serviço no futuro.

### Comece!

{{< cdn src="images/just_do_it.gif" alt="APENAS FAÇA!" >}}

Eu sugiro fortemente que você escolha um gerenciador que mais atenda suas necessidades e simplesmente comece um teste. Baixe o aplicativo, faça o setup no celular e nos navegadores que você usa e comece.

O processo inicial de cadastrar todas as senhas e alterar as que são repetidas pode ser um pouco demorado (algumas das minhas ainda não foram trocadas), mas apenas o começo é difícil. Uma vez terminado, é fácil manter tudo armazenado e atualizado.

Existem muito mais assuntos para abordar relacionados a gerenciadores, como contatos de emergência, vantagens e desvantagens, armazenamento de arquivos, compartilhamento de senhas, entre outros. Mas esses eu deixarei para outro artigo.
