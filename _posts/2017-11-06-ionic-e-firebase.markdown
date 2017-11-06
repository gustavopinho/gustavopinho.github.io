---
layout: post
title:  "Ionic e Firebase"
description: "Aplicativo de lista de tarefas com Ionic e Firebase"
date:   2017-11-06 17:40
author: gustavo
categories: blog
---

Nesse tutorial será apresentado como integrar de forma simples e rápida o Framework Ionic e o Firebase. Usaremos o serviço de autenticação e o serviço de banco de dados real-time.

O que é o Ionic
==============

O Ionic é um framework de desenvolvimento de aplicações hibridas. Ele fornece um kit de ferramentas para o desenvolvimento de aplicações mobile.

Preparando o Ambiente
============

Antes de começar é necessário configurar o ambiente de desenvolvimento. Para o tutorial será necessário instalar os seguintes programas e bibliotecas.

Node.js
------
[Download](https://nodejs.org/en/download/)

Git
---
[Download](https://git-scm.com/)

Sublime Text 3
------------
[Download](https://www.sublimetext.com/3)

Android Studio
-------------
[Download](https://developer.android.com/studio/index.html)

Ionic
-----
Após a instalação dos programas anteriores é necessário instalar o Ionic, para fazer a instalação podemos seguir os passos apresentados no site [aqui](https://ionicframework.com/getting-started/) ou executar os comandos abaixo.

No meu caso com estou trabalhando com sistema operacional Windows é necessário abrir o CMD para a inserção dos comandos. 

O Ionic será instalado usando o gerenciador de pacotes **npm** que foi instalado junto com o Node.js. Então com o CMD aberto vamos inserir os seguintes comando para instalação do Ionic.

**npm install -g cordova ionic**

Esse comando geralmente demora um pouco dependendo da velocidade da internet. Nele estamos especificando que será instalado de forma global o [**Cordova**](https://cordova.apache.org/) e o [**Ionic**](https://ionicframework.com/).

Após a instalação podemos finalmente iniciar a construção do nosso aplicativo.

Criando o Aplicativo
==========================

Depois que finalizamos a cofiguração do ambiente de desenvolvimento podemos de fato iniciar o desenvolvimento do nosso aplicativo, para isso vamos usar novamente o CMD.

No CMD vamos usar basicamente dois comandos, o **cd** que serve para navegar nas pastas "Ex. cd minha_pasta" e o **mkdir** que é usado para criar uma pasta "Ex. mkdir minha_pasta".

Com o CMD aberto vamos inserir o seginte comando:

**ionic start tarefasApp tabs**

Esse comando serve para criar o nosso aplicativo, para saber mais [clique aqui](https://ionicframework.com/docs/intro/installation/). A primeira parte do comando **ionic** informa que estamos usando o [ionic CLI](https://ionicframework.com/docs/cli/), a segunda **start** informa que estamos [criando um projeto](https://ionicframework.com/docs/cli/start/), a terceira **tarefasApp*** é o nome do nosso aplicativo e por fim o **tabs** informa que vamos usar um [template de projeto](https://ionicframework.com/docs/cli/starters.html).

Digitado o comando precione a tecla "Enter" para iniciar a instalação do projeto. O processo de instalação também pode demorar um pouco por isso é importante ter paciência.












