# NATAS3

![Imagem 1](img1.png)

A tela inicial exibe a mesma mensagem do NATAS2. Porém, o código-fonte anterior tinha uma imagem localizada no diretório *files*. Agora, o código-fonte não dá pista nenhuma sobre os diretórios do servidor. Eu comecei a pesquisar sobre como achar diretórios ocultos usando as ferramentes que o OverTheWire colocou na página inicial. Foi assim que eu descobri como usar uma *spider* com o ZAP.

![Imagem 2](img2.png)

Falarei mais sobre a *spider* depois, mas ela me permitiu conhecer o arquivo *robots.txt*. Esse arquivo está presente na *root* dos servidores e serve para indicar aos *search engines*, como o Google, quais diretórios eles tem permissão para entrar. Então, sabendo que *robots.txt* fica na *root*, eu poderia ter tentado acessar o arquivo diretamente, sem o uso da *spider*.

```
http://natas3.natas.labs.overthewire.org/robots.txt
```
![Imagem 3](img3.png)

Podemos ver que o diretório *s3cr3t* está oculto para todos os mecanismos de busca, mas isso não impede dele ser acessado. 

```
http://natas3.natas.labs.overthewire.org/s3cr3t/
```

![Imagem 4](img4.png)

Chegamos ao arquivo escondido.

![Imagem 5](img5.png)

```
JDrPnuZAKyl6MkiqQGFIddrqpvgOASth
```
