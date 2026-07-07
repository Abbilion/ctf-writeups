# LAB1 - File path traversal, simple case

![Imagem 1](img1.png)

O desafio começou com esse site de *e-commerce*. A ideia é procurar por uma vulnerabilidade específica: o *path traversal*, que nos permite ver qualquer arquivo em um *server*.

![Imagem 2](img2.png)

Olhando para o código HTML, podemos perceber que as imagens são chamadas por um *endpoint* */image* que recebe um parâmetro *filename=56.jpg*. Como foi explicado no *lab*, eu fiz uma requisição GET diferente para esse *endpoint*.

```
https://0a42009e04a5a02380f47b8900700077.web-security-academy.net/image?filename=/etc/passwd
```

O arquivo */etc/passwd* é um arquivo comum no Linux que guarda informações sobre todas as senhas.

![Imagem 3](img3.png)

Eu recebi uma mensagem de *no such file* como resposta. Nesse ponto, eu fiquei confuso e acabei resolvendo o desafio sem querer. O problema é que o *endpoint* não aceita *absolute paths*. Então, eu subi os diretórios até receber uma resposta positiva.

```
https://0a42009e04a5a02380f47b8900700077.web-security-academy.net/image?filename=../../../etc/passwd
```

![Imagem 4](img4.png)

Eu recebi a mensagem de *lab* concluído, porém eu não tinha realmente conseguido ler o arquivo, porque o *browser* esperava uma imagem e recebeu um *ASCII text*. Olhando a solução, eu percebi que é possível ler o arquivo se eu ver a requisição pelo ZAP.

![Imagem 5](img5.png)

Em cima, podemos ver uma resposta 200, que indica uma solicitação bem-sucedida, e abaixo, as informações do arquivo *passwd*.

Obs.: *endpoint* é uma URL em um site que espera uma requisição GET para fazer alguma coisa. Por exemplo:

```js
server.get('/hello', function (req, res) {
    res.send('Hello World!');
});
```

Num *web server* feito com *Express.js*, eu criei o *endpoint /hello* que, ao receber uma requisição GET, ele devolve uma página com a mensagem *'Hello World!'*.

![Imagem 6](img6.png)
