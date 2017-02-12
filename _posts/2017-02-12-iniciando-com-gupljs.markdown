---
layout: post
title:  "Iniciando com Gulp"
description: "Esse artigo pretende te mostrar como iniciar com o Gulp"
date:   2017-02-12 11:50
author: gustavo
categories: blog
---

O Gulp sem dúvidas é uma ótima ferramenta para quem trabalha com front-end. Nesse artigo vou mostrar como iniciar com o gulp e como agilizar tarefas difíceis do nosso dia-dia.

Abordarei como é feita a instalação e como criar configurações básicas para iniciantes.

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

Após tudo configurado primeiro vamos instalar o **gulp-cli**, ele tem como objetivo deixar o Gulp como uma aplicação global em nosso sistema, mas sem instalar o Gulp globalmente, isso poís as vezes temos projetos com versões diferentes do gulp e se trabalharmos com versões globais correremos o risco de erro ou conflitos.

- $ npm install gulp-cli -g

O comando acima irá instalar o gulp, a opção **-g** indica que será instalado globalmente.

Finalizada a instalação do **gulp-cli** podemos iniciar com a instalação do gulp em nosso projeto, é necessário que você esteja na pasta do projeto.

- $ npm install gulp -D

Esse comando instalará o gulp, a opção **-D**, que é uma abreviação para **--save-dev**, fará com que o gulp seja instalado apenas em nosso projeto.

Instalado o gulp é necessário criarmos o nosso arquivo **gulpfile.js**, nesse arquivo vamos configurar todas as tarefas que serão executadas pelo gulp.

Editando o arquivo gulpfile.js
------------------------------

Como o nosso arquivo ainda não tem nenhuma linha é hora de inserirmos os dados necessário para o funcionamento do gulp, e também adicionarmos as tarefas que serão executadas por ele.

No nosso exemplo vamos usar os seguintes plugins do gulp:

- **gulp-sass**: $ npm install gulp-sass --save-dev
- **gulp-uglify**: $ npm install gulp-uglify --save-dev
- **gulp-jshint**: $ npm install jshint gulp-jshint –save-dev
- **gulp-csso**: $ npm install gulp-csso --save-dev
- **browser-sync**: $ npm install browser-sync –save-dev

O **gulp-sass** é usado para converter os nossos arquivos sass para css, o **gulp-uglify** para minificar os nosssos arquivos .js, já o **gulp-jshint** fará a varedura dos nosso arquivos js e procurar possíveis erros ou problemas, o **gulp-csso** é usado para minificar os nosssos arquivos .css e por fim o **browser-sync** fará o trabalho de sincronizar todos os browser que estiverem executando a nossa aplicação e também fazer o reload em caso se alguma alteração em nossos arquivos.

Abaixo segue o arquivo de configuração usado no nosso projeto:

```javascript
var gulp = require('gulp')
var sass = require('gulp-sass')
var minifyCss = require('gulp-csso')
var minifyJs = require('gulp-uglify')
var jshint = require('gulp-jshint')
var browserSync = require('browser-sync').create();

gulp.task('sass', function() {
    return gulp.src('assets/sass/*.scss') // Especifica o caminho dos nossos arquivos sass
        .pipe(sass()) // Transforma o sass em css
        .pipe(minifyCss()) // Minifica os nossos arquivos css
        .pipe(gulp.dest('dist/css')) // Especifica o caminho de destino do arquivo minificado
        .pipe(browserSync.reload({stream: true})); // Executa um reload no browser
});

gulp.task('js', function() {
    return gulp.src('assets/js/*.js') // Especifica o caminho dos nossos arquivos JavaScript
        .pipe(jshint()) // Verifica erros em nossos arquivos
        .pipe(minifyJs()) // Minifica os nossos arquivos
        .pipe(gulp.dest('dist/js')) // Especifica o caminho de destino
        .pipe(browserSync.reload({stream: true})); // Executa um reload no browser
});

// Servidor
gulp.task('browser-sync', function() {

    // Cria um servidor estático para a nossa aplicação
    browserSync.init({
        server: {
            baseDir: "./"
        }
    });

    // Verifica alterações em arquivos .js e executa a tarefa js
    gulp.watch('assets/js/*.js', ['js']);
    // Verifica alteraçõe em arquivos .scss e executa  a tarefa sass
    gulp.watch('assets/sass/*.scss', ['sass']);
    // Verifica alteraçõe em arquivos .html recarrega o browser
    gulp.watch('./*.html').on('change', browserSync.reload);
});

// Executa todas as nossas tarefas em default
// $gulp
gulp.task('default', ['sass', 'js'])

// Executa todas as nossas tarefas em ambiente de desenvolvimento
// $gulp development
gulp.task('development', ['sass', 'js', 'browser-sync'])
```

Bom agora que está tudo configurado é só executar o gulp e aproveitar o tempo economizado no processo de desenvolvimento.

- **production**: $ gulp
- **development**: $ gulp development

Em desenvolvimento use o comonado gulp seguido da opção **development**, já para produção você precisa executar apenas gupl.


Conclusão
---------

Ainda sou novato no desenvolvimento com o gulp, mas até o momento estou gostando muito de usar essa poderosa ferramenta, com ela consegui poupar muito tempo no processo de desenvolvimento.

Obrigado pela atenção, até o proximo post.


