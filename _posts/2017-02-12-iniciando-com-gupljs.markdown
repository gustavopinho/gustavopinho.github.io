---
layout: post
title:  "Iniciando com Gulpjs"
date:   2017-02-12 11:50
author: gustavo
categories: blog
---

# Iniciando com Gulp

O Gulp sem dúvidas é uma ótima ferramenta para quem trabalho com front-end, nesse artigo vou mostrar como iniciar com o gulp e agilizar tarefas difíceis do nosso dia-dia.

Mostrarei como é feita a instalação e configurações básicas para iniciantes.

O que é o Gulp?
---------------

O gulp é uma ferramenta de automação, ele faz todo o trabalho braçal que precisariamos para colocar o nosso código em produção. O bom do gulp é que ele nos permite desenvolver sem dor :).


Então... Por onde começar?
--------------------------

Para funcionar o Gulp precisa que você tenha instalado em sua maquina o nosso amigo **Node.js**, para mais informações sobre o node.js acesse [nodejs.org](https://nodejs.org).

Precisaremos também do **npm** que nos ajudará com todas as nossas dependências JavaScript, mais sobre o npm acesse [NPM](https://docs.npmjs.com).

Agora que já sabemos o que vamos precisar podemos começar a instalação do Gulp.

Instalando o Gulp
-----------------

Após tudo configurado primeiro vamos instalar o **gulp-cli**, ele tem como objetivo deixar o Gulp como uma aplicação global em nosso sistema, mas sem instalar o Gulp globalmente isso poís as vezes temos projetos com versões diferentes do gulp e se trabalharmos com versões globais correremos o risco de erro ou conflitos.

- $ npm install gulp-cli -g

O comando acima irá instalar o gulp, a opção **-g** indica que será instalado globalmente.

Finalizada a instalação do **gulp-cli** podemos iniciar com a instalação do gulp em nosso projeto, é necessário que você esteja na pasta do projeto.

- $ npm install gulp -D

Esse comando instalará o gulp a opção **-D** que é uma abreviação para **--save-dev** fara com que o gulp seja instalado apenas em nosso projeto.

Instalado o gulp é necessário criarmos o nosso arquivo **gulpfile.js**, nesse arquivo vamos configurar todas as tarefas que serão executadas pelo gulp.

Editando o arquivo gulpfile.js
------------------------------

Como o nosso arquivo ainda não tem nenhuma linha, é hora de inserirmos os dados necessário para o funcionamento do gulp, e também adicionarmos as tarefas que serão executadas por ele.

No nosso exemplo vamos usar os seguintes plugins do gulp:
- **gulp-sass**: $ npm install gulp-sass --save-dev
- **gulp-uglify**: $ npm install gulp-uglify --save-dev
- **gulp-jshint**: $ npm install jshint gulp-jshint –save-dev
- **gulp-csso**: $ npm install gulp-csso --save-dev
- **browser-sync**: $ npm install browser-sync –save-dev

O **gulp-sass** é usado para converter os nossos arquivos sass para css, o **gulp-uglify** para minificar os nosssos arquivos .js, já o **gulp-jshint** fará a varedura dos nosso arquivos js e procurar possíveis erros ou problemas, o **gulp-csso** é usado para minificar os nosssos arquivos .css e por fim o **browser-sync** fará o trabalho de sincronizar todos os browser que estiverem executando a nossa aplicação e também fazer o reload em caso se alguma alteração em nossos arquivos.

Abaixo segue o arquivo de configuração usado no nosso projeto:



