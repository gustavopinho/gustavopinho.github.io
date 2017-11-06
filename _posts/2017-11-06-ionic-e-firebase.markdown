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

Se tudo ocorrer bem o comando apresentará o resultado como na imagem abaixo.

![alt text](https://lh5.googleusercontent.com/KUwnfNvREylR961y_gq8jKt6IuGJQE45YM8Q5yromqJlDTCoad_XEkFLwa1L8eFNY4y2BZ3THr3WiLpAA6B3=w1440-h779 "Iniciando Projeto")

Depois de criado o projeto usaremos o comando:

**cd tarefasApp**

Caso tenha criado o projeto com outro nome use o comando cd com o nome do projeto que criou.

Agora para testar o aplicativo use o comando:

**ionic serve**

O comando deve apresentar uma saída como na imagem abaixo.

![alt text](https://lh4.googleusercontent.com/HrRyaS-9DoUniY3y-XvIaAGvgz7CGbF25z9oDdygnvkQM07nGinrN3vNjC8jf99XgAduxlBjMYsJDsFo45-z=w1440-h779 "Testando o projeto")

Logo após o comando se tudo ocorrer bem será aberto uma janela do navegador com o aplicativo já em execusão.

![alt text](https://lh5.googleusercontent.com/Rnl0RqJ3xEDi1SzEkm_Fpr3R2ouRzxoFqTGDJGq9mjO-671B1xknr_r0eyteZlcIjvrRoX6DvHfSHwMtIQaX=w1440-h779 "Aplicativo em execusão")

O aplicativo já está funcionando!

Feitos os passos anteriores agora vamos abrir o nosso aplicativo no editor de texto que foi instalado, nesse caso o [Sublime Text 3](https://www.sublimetext.com/3), lembrando que o editor não faz muita diferênça você pode usar o que mais te agradar.

Aberto o editor navegaremos até a pasta onde foi criado o projeto e vamos selecinar a pasta e clicar em "Selecionar Pasta". Selecionada a pasta vamos conseguir ver o que foi criado com os passos anteriores.

![alt text](https://lh5.googleusercontent.com/yziKIfVwd1YuNQ_ngrhACQI20AHgizl5UtIBPZVHpnmCpjV_RhoW63d6eTfh87ZdKl7AQdO0PsYXyslsvmy2=w1440-h779-rw "Primeira vista do editor")

Como apresentado na imagem exitem diversas subpastas dentro do nosso projeto, mas para esse tutorial vamos nos atentar apenas à pasta **src**. Nela é onde vamos fazer todo o nosso trabalho.

A pasta **src** é composta de diversas outras subpastas e cada uma delas tem sua função para a construção do aplicativo, durante o desenvolvimento vamos falar sobre a função de cada uma delas e vamos também criar algumas que não exitem no nosso projeto.


Criando Página de Login
=======================

Quando foi criado o projeto optamos por usar um template que foi o **tabs**, esse templete já vem com algumas páginas prontas mas iremos usar somente a página **home** as outras páginas do aplicativo serão criadas do zero.

A primeira página que vamos cria e a de login. Ela será usada para o **cadastro** e **autenticação** dos usuários do aplicativo, para criar a página vá para o CMD e insira o seguinte comando.

**ionig g page login**

O **g** informa que vamos gerar alguma coisa, pode ser **g** ou **generate**. O **page** indica que coisa que vamos gerar nesse caso uma página, já o **login** informa o nome da coisa que vamos gerar.

Após o comando voltaremos ao editor e podemos verificar a página que foi gerada.

![alt text](https://lh6.googleusercontent.com/3EkbgL5HNhwjeNRKRobbMin9hm0LmN_lTc0Cp-XkUN8LYAv49wJ5zDc4OL38WAMggQkpklpCpkNA1pJzNk-8=w1440-h779-rw "Página de login")

Na imagem podemos ver destacado em vermelho as pastas e os arquivos que foram criados com o comando para gerar as páginas. A página foi criado dentro da pasta **pages** e possuí quatro arquivos, no tutorial vamos alterar apenas os arquivos **login.html** e **login.ts**.

Criada a página de login precisaremos de um serviço para fazer a autenticação dos usuários.


Autenticação e Dados do Usuário
==============================

Para fornecer autenticação e amarmazenamendo de dados no nosso aplicativo será usada a ferramenta Firebase. O Firebase é composto de varios serviços.











