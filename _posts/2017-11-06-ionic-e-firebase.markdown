---
layout: post
title:  "Ionic e Firebase"
description: "Aplicativo de lista de tarefas com Ionic e Firebase"
date:   2017-11-06 17:40
author: gustavo
categories: blog
---

Post não está finalizado e não foi corrigido
============

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


Cadastro e Autenticação
============

Para criar o serviço de cadastro e autenticação vamos usar o Firebase, é necessário ter uma conta do GMAIL para fazer o cadasto, se ainda não tem uma conta do [clique aqui](https://accounts.google.com/SignUp?service=mail&continue=https://mail.google.com/mail/?pc=topnav-about-en).

Se já possuí a conta então vamos direto para o cadastro no Firebase, [clique aqui para acessar](https://firebase.google.com/?hl=pt-br).

![alt text](https://lh5.googleusercontent.com/Ev8WXaWnRIRcnRgm334eHqjkjjQgFS6cA6zEQmfVEUkRhixzV9iPpNR9sb0aqiyaZMVaUt2MRx50lx8LrGxh=w1440-h804-rw "Página inicial do firebase")

No canto superior da tela na imagem acima exite dois links um é o **GO TO CONSOLE** e o outro é o **FAZER LOGIN**, ambos vão nos direcionar para a página de login do Firebase mas vamos clicar no primerio **GO TO CONSOLE**, ele irá direcionar para a página onde vamos inserir os dados do email que criamos ou para quem já tinha um email do GMAIL inserir as credencias do email.

Após o login vamos ser direcionados para a página de projetos.

![alt text](https://lh5.googleusercontent.com/bI-7AUY2xRNq1ybjZXunSWipiIwQTmVfpoEj1oIWNOngBvJ6eaelnqB1ENWIiMHPqhtI3b9KEaXrWRyAOJHe=w1440-h804-rw "Tela para criar projeto")

Se não existir nenhum projeto criado teremos então duas opções **Adicionar projeto** e **Explorar projeto de demonstração**, no tutorial vamos na opção **Adicionar projeto** e vamos dar o nome de **Tarefas App**.

![alt text](https://lh6.googleusercontent.com/zrE5RjJsqiOEjXZITPuiEIYRRwIaw4uT82nZoXzyRwe5GX_jaVRSch4UZKmesNVsNhrmXFiQZ6DKkRZ25b8O=w1440-h804 "Criando projeto")

Na tela acima você irá informar o nome do projeto e o local do projeto que no nosso caso é Brasil. Após isso clique em **CRIAR PROJETO**.

![alt text](https://lh4.googleusercontent.com/HimxjRtbfbsvKrh7-qo_5StDf9aYAuivU04Aw6maolrTL0VAm_z7RK5CVRZo3RnFQJ5PaUOPNOasBYhwZU1U=w1440-h804-rw "Firebase Dasbhoard")


No menu esquerdo temos a opção **Authentication** conforme a imagem abaixo.


Clicando em **Authentication** vamos ser direcionados para a página de configurações de autenticação conforme a imagem que segue.

Clicando em **CONFIGURAR MÉTODO DE LOGIN** aparecerá uma página com diversas opçoes de configuração, para o nosso exemplo vamos escolher a primeira que **E-mail/Senha**. Clicando em cima dessa opção aparecerá uma tela para **Ativar** e **SALVAR**, primeiro vamos ativar e depois salvar comforme imagem abaixo:


Após ativarmos e salvarmos então na tela aparecerá que a opção **E-mail/Senha** está Ativa.


Depois de ativada podemos copiar as configurações que vamos usar em nosso projeto clicando no botão **CONFIGURAÇÕES DA WEB** no canto superior direito da página.


Após clicar aparecerá um caixa de dialogo com as configurações que vamos precisar no nosso projeto.


Configurando o Firebase no Aplicativo
-------------------------------------

Como já fizemos o cadastro e já ativamos a opção de login podemos voltar para o nosso aplicativo para inserir as configurações.

Para conseguir usar o Firebase no nosso aplicativo Ionic vamos precisar usar uma biblioteca chamada [AngularFire](https://github.com/angular/angularfire2). Com ela que teremos acesso à todas as funcionalidades do Firebase, para adicionar voltamos para o CMD e vamos inserir o seguinte comando:

**npm install firebase angularfire2 --save**

O comando irá fazer o download do angularFire e apresentará uma saída parecida com a imagem abaixo:

![alt text]( "Saída do comando de instalação do angularfire2")

Terminado a instalação da biblioteca teremos que inserir as configurações necessária para que ela funcione corretamente. As configurações devem ser adicionadas no arquivo **src/app/app.module.ts**, e devem como o arquivo apresentado abaixo:

<script src="https://gist.github.com/gustavopinho/50ff79ca9e521b79734d39cdf06edd63.js"></script>

Nesse arquivo foi adicionado as seguites conficurações:

- Importações dos módulos que vamos usar do FIREBASE

**import { AngularFireModule } from 'angularfire2';**

**import { AngularFireAuthModule } from 'angularfire2/auth';**

- Adição das configurações que foram copiadas do console do firebase

**let config = {**

   **apiKey: "",**

   **authDomain: "",**

   **databaseURL: "",**
  
   **projectId: "",**

   **storageBucket: "",**

   **messagingSenderId: ""**

**};**

- Adicionar dentro do array **imports\[]**

**AngularFireModule.initializeApp(config)***

**AngularFireAuthModule***


Após adicionadas as configurações podemos testar se está tudo funcionando com o comando:

**ionic serve**

Se tudo estiver correto o aplicativo será aberto no navegador.


Criando Serviço de Autenticação
==============================

Depois que configuramos o Firebase vamos então criar o nosso serviço de autenticação que será usado na página de login do nosso aplicativo.

Primeiro vamos criar uma pasta chamada **models** dentro da pasta **src** do nosso aplicativo, dentro da pasta models vamos criar um arquivo com o nome **user.ts** e vamos inserir o conteúdo abaixo:

<script src="https://gist.github.com/gustavopinho/7969e115d839aa13ea23a8a973d98539.js"></script>

Após criar o arquivo **user.ts** vamos então criar de fato o nosso serviço de autenticação usando o seguinte comando:

**ionic g provider auth**

Após criar o nosso serviço de autenticação vamos editar o arquivo que foi criado na pasta **src/providers/auth/auth.ts** e deixa-ló como o arquivo abaixo:

<script src="https://gist.github.com/gustavopinho/53ebc44cf731b67cd9069e28b7d8586a.js"></script>


Adicionando o Serviço de Autenticação na Página de Login
========================================================

Depois de criado o serviço de autenticação podemos voltar para a página de **login** do nosso aplicativo para adicionar a autenticação e o cadastro de usuários.

O primeiro passo é editar o nosso arquivo **src/app/app.modules.ts** para registrar a nossa página de **login** (Todas as páginas criadas no nosso aplicativo devem ser registradas no arquivo app.modules.ts para que possam ser acessadas em qualquer parte do aplicativo).

Com a edição nosso arquivo ficará da seguite forma:

<script src="https://gist.github.com/gustavopinho/eab389241381e8c09ea46f8484a53ff2.js"></script>

O próximo arquivo que vamos editar é o **src/app/app.componet.ts**, vamos editar esse arquivo para ficar da seguite forma:

<script src="https://gist.github.com/gustavopinho/f1a298b7152b007dda665576fbd5b5c5.js"></script>

No arquivo acima foi feita a remoção da linha:

**import { TabsPage } from '../pages/tabs/tabs';**

E a inclusão da linha:

**import { LoginPage } from '../pages/login/login';**

E por fim a substituição do do:

**rootPage:any = TabsPage;**

Para:

**rootPage:any = LoginPage;**

Essa substituição torna a nossa página de login como a página principal do nosso aplicativo.










