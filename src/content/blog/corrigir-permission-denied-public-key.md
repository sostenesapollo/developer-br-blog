---
title: 'Como Corrigir "Permission denied (publickey)" ao Realizar Push para o GitHub'
description: 'Soluções para resolver problemas de permissão ao tentar fazer push para um repositório no GitHub'
pubDate: 'Jun 23 2024'
heroImage: '/blog-placeholder-2.jpg'
author: 'Sóstenes Apollo'
---

Se você já tentou fazer push para um repositório no GitHub e encontrou o erro "Permission denied (publickey)", saiba que isso é comum e pode ser corrigido com alguns passos simples. Este guia mostrará como resolver esse problema.

#### Passo 1: Crie uma nova chave ssh
Execute o comando em seu terminal
```sh
ssh-keygen
```


#### Você deve ver uma tela semelhante a essa:
> `Pressione enter em todas as perguntas`
```sh
➜  ~ ssh-keygen                                                                  
Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/sostenes/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/sostenes/.ssh/id_ed25519
Your public key has been saved in /Users/sostenes/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:P6rzeICeS1HTObkeW8wxXfhX/6Q3KFDmtjkQhPbvPmg sostenes@192.168.1.4
The key's randomart image is:
+--[ED25519 256]--+
|        o.   ..  |
|       + + +..  .|
|      + * B ..  o|
|     . . O =  . +|
|    ..  S O o .+.|
|    .... = * ...o|
|   ... .o = o  ..|
|   .o ...E +     |
|    ..o=+ ...    |
+----[SHA256]-----+

```

#### Passo 2: Localize a chave criada e copie

##### Após criar a sua chave ela estará no diretório `~/.ssh/`
> Execute o comando para ver os arquivos dentro do diretório
```sh
➜ ls ~/.ssh/
id_rsa           id_rsa.pub
```

Note que agora temos dois arquivos `id_rsa` e `id_rsa.pub`

> O arquivo `id_rsa` é a sua chave privada

> O arquivo `id_rsa.pub` é a sua chave publica (que deve ser copiado para o github)

Abra o conteudo do arquivo de sua chave publica:
```sh
➜ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB36XkR2FJnclw7OavqyE= sostenes@Sosteness-MacBook-Pro.local
```

> Você deve ver um longo texto (que é a sua chave), selecione todo esse texto e copie, que vai desde `ssh-rsa` até o `nome do seu pc` (no meu caso `sostenes@Sosteness-MacBook-Pro.local`)

> Se certifique de copiar toda o conteúdo da chave, caso contrário não funcionará. 

##### No seu Github clique em configurações (settings)
<img src="/permission-denied-1.png"/>


##### Clique em SSH and GPG keys
<img src="/permission-denied-2.png"/>

##### Clique em new SSH key
<img src="/permission-denied-3.png"/>

##### Digite um nome qualquer no campo de cima e cole a chave que você copiou no campo de baixo
<img src="/permission-denied-4.png"/>

##### Pronto, você resolveu seu problema e já deve conseguir fazer `push`, `pull` e usar seu github normalmente

### Não conseguindo fazer pull
> Se certifique que você está usando o link `ssh` e não o `https` ao realizar o pull do seu github.

