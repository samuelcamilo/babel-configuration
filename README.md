# Babel

[![](https://d33wubrfki0l68.cloudfront.net/7a197cfe44548cc1a3f581152af70a3051e11671/78df8/img/babel.svg)](https://babeljs.io)

Nesse primeiro tutorial quero demonstrar como configurar o Babel na sua aplicação. Estou iniciando nesse mundo de tutoriais e a muito tempo queria escrever alguma coisa. Atualmente estou estudando javascript e a algum tempo o Babel tem ganhado bastante espaço por sua importancia nas aplicações que usam ecmascript6+. Espero poder te ajudar ao máximo, e já peço desculpas por algum possivel erro, esse é meu primeiro post, então estou aprendendo. Muito grato, e vamos lá...


O Babel é um transpiler de código, que tem a função de tranformar código ecmascript6+ em uma versão que os navegadores atuais possam suportar. Hoje ele é extremamente necessário em aplicações feitas com React, Vue e Angular.
Com demonstrações simples, quero demonstrar como a configuração pode ser feita de forma fácil e correta. Existem outras formas mais práticas para a configuração do Babel, mas caso você seja uma pessoa, que como eu, gosta de saber como as coisas funcionam por debaixo dos panos, vamos lá...

### Iniciando um projeto javascript

Inicialmente precisaremos ter instalado o [Node.js](https://nodejs.org/), como também um gerenciador de pacotes. Nesse tutorial estou utilizando o [Yarn](https://yarnpkg.com/pt-BR/). Ele nos permitirá compartilhar e usar esses códigos compartilhados por desenvolvedores do mundo todo. Existem outros gerenciadores, mas fique a vontade para escolher.
 
### Instalação

Crie uma pasta para darmos inicio ao projeto.

```sh
mkdir exemplo_babel && cd exemplo_babel
```

Com a pasta já criada, vamos dar o start inicial.

```sh
yarn init
```
O comando acima, cria o nosso arquivo `package.json`. Nele contém alguns padrões customizavéis. 

Arquivo gerado:

```json
{
  "name": "babel_configuration",
  "version": "1.0.0",
  "main": "index.js",
  "repository": "https://github.com/samuelcamilo/babel_configuration.git",
  "license": "MIT"
}
```

Agora vamos realizar a instalação de algumas dependências importantes para o funcionamendo do Babel. Usando os comandos baixo, estaremos fazendo a instalação do `@babel/cli e @babel/preset-env`. Eles nos ajudarão a identificar qual tipo de ambiente estamos rodando a nossa aplicação e assim colocar o Babel no contexto da aplicação.

```sh
yarn add @babel/cli
yarn add @babel/preset-env
```

Não vamos esquecer de instalarmos o `@babel/core`

```sh
yarn add @babel/core
```
Caso esteja tudo certo com nossas instalações, podemos seguir para o próximo passo.

### Configuração

Vamos criar o arquivo `.babelrc`. Esse arquivo tem a finalidade de iniciar o preset-env, fazendo com que o Babel possa identificar qual o tipo de ambiente estamos.

```json
{
    "presets":[
        "@babel/preset-env"
    ]
}
```

Nós iremos precisar de 3 arquivos. Esses arquivos serão de uma certa forma, gerenciados pelo Babel.

O `main.js` vai ser o local aonde vamos colocar nosso códigos ecmascript6+

```sh
touch main.js
```

O `index.html` é responsavel por renderizar a saída do código que já passou pelo transpiler

```sh
touch index.html
```
insira o código abaixo:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Ecmascript 6 - Babel</title>
    </head>
    <body>
        <script src="bundle.js"></script>
    </body>
</html>
```

Note que no `body` do código html acima, está presente o arquivo `bundle.js`. Isso ocorre por que após o código ecmascript6+ passar pelo transpiler, ele é colocado no nosso `bundle.js` como um código javascript entendido pelos navegadores atuais. Por isso não podemos esquecer de cria-lo também.

```sh
touch bundle.js
```

Calma que já vamos terminar...

Voltando no nosso arquivo `package.json`, vamos adicionar uma configuração que permitirá a transferência do código colocado no nosso `main.js` para o `bundle.js` e assim ele ser renderizado no `index.html`. Como vai ficar nosso `package.json`:

```json
{
  "name": "babel_configuration",
  "version": "1.0.0",
  "main": "index.js",
  "repository": "https://github.com/samuelcamilo/babel_configuration.git",
  "license": "MIT",
  "dependencies": {
    "@babel/cli": "^7.0.0",
    "@babel/core": "^7.0.0",
    "@babel/preset-env": "^7.0.0"
  },
  "scripts": {
    "dev":"babel main.js -o bundle.js -w"
  }
}
```

Adicionamos esse script no `package.json`:

```json
{
  "scripts": {
    "dev":"babel main.js -o bundle.js -w"
  }
}
```

Agora vamos analisar o código inserido. No atributo `"dev": "babel main.js -o bundle.js -w"` estamos passando o caminho que ficará o código já transpilado. De forma simples, estou dizendo que o que tiver no `main.js`, transpile e passe para o `bundle.js`. 

Obs: Com o uso do `{w}`, posso ver em tempo real as modificações nos arquivos e mensagens de erros. 

### Finalizando

Feito tudo isso, você pode dar o start na aplicação com o código:

```sh
yarn run dev
```

Após todas as instalações e configurações realizadas, podemos agora ver o funcionamento do Babel. Você pode verificar o transpiler sendo feito no arquivo `bundle.js`

Qualquer dúvida, estou a disposição para ajudar.
Entrar em contato: ssamuelcamilo@gmail.com
