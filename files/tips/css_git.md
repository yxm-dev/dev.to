---
title: "Como utilizar um `.css` hospedado no GitHub ou Codeberg em um projeto HTML?" 
description: "Nesse post apresentamos duas abordagens para se utilizar  arquivos .css que estão hospedados no
Github ou no Codeberg diretamente em projetos HTML"
tags: 'css, html, github, codeberg'
cover_image: 'https://i.imgur.com/iy1igb0.png'
series: Quick Tips
canonical_url: null
published: true
---

# Introdução

Considere a seguinte situação: você possui um arquivo `.css` (digamos `style.css`) e gostaria de utilizá-lo em vários projetos de desenvolvimento web. Como fazer isso de forma simples?

Naturalmente, a ideia é utilizar um import

```html
<link rel="stylesheet" type="text/css" href="path/to/style.css">
```

Por comodidade, seria interessante se o arquivo `style.css` estivesse hospedado em algum servidor externo para que não haja a necessidade de se mantê-lo na mesma máquina onde os projetos estão sendo desenvolvidos.

Algo baste útil seria manter um repositório no GitHub, ou em outra plataforma de manejo de repositórios `git`, como Codeberg ou Gitlab, contendo todos os arquivos `.css` a serem utilizados. Neste caso, poderíamos manter os arquivos organizados por versões e, quando necessitássemos de um deles, bastaria fazer um import como acima para sua correspondente url.

A questão é: *qual url utilizar?*.

A tentativa mais óbvia seria a url

```
https://github.com/user/repo/path/to/style.css`
```

onde `path/to/style.css` é o caminho relativo ao repositório `repo`. No entanto, esta não é uma url válida. 

Ao visitar o repositório pela plataforma (digamos o GitHub) e clicar  no arquivo `style.css`, observa-se que a url indicada está no formato

```
https://github.com/user/repo/blob/branch/path/to/style.css
```

Contudo, essa url não expõe o arquivo. Poderíamos, então, pensar na url que apresenta a versão `raw` de `style.css`, a qual é da forma

```
https://raw.githubusercontent.com/user/repo/branch/path/to/style.css
```

Mas essa url expõe o *conteúdo* do arquivo `style.css`, e não o arquivo em si.

* *Poxa vida, como proceder?*

# Abordagem 1

Uma abordagem seria pegar o conteúdo exposto na url `raw` e incorporá-lo dentro da tag `<style>` do projeto no qual se deseja utilizar `style.css`.

Isso pode ser feito, por exemplo, adicionando o seguinte trecho dentro da tag `<head>` no `index.html` do projeto (veja [aqui](https://stackoverflow.com/a/63621260)):

```html
<script>
var xhttp = new XMLHttpRequest();
xhttp.open("GET", "https://raw.githubusercontent.com/user/repo/branch/path/to/style.css", true);
xhttp.onreadystatechange = function() {
    if (xhttp.readyState === 4) {
        if (xhttp.status === 200) {
            var link = document.createElement('style');
            link.innerHTML=xhttp.responseText;
            document.getElementsByTagName('head')[0].appendChild(link);
        }
    }
}
xhttp.send(null);
</script>
```

* *Caramba, mas não há uma forma mais direta de expor os arquivos `.css`?*

# Abordagem 2

Se a sua plataforma admite a criação de páginas estáticas ([GitHub Pages](https://docs.github.com/pt/pages), [Codeberg Pages](https://docs.codeberg.org/codeberg-pages/) ou [Gitlab Pages](https://docs.gitlab.com/ee/user/project/pages/), por exemplo), então há uma forma imediata de expor arquivos em repositórios. A saber, *transformando os repositórios em uma página estática*.

Eu gosto muito do Codeberg para a hospedagem de sites estáticos. De fato, lá é muito simples: *todos os repositórios podem ser vistos, por padrão, como sites estáticos*. Com efeito, ao invés de utilizar a url

``` 
https://codeberg.org/user/repo
```

basta utilizar a url

```
https://user.codeberg.page/repo/@branch
```

Nesse caso, o arquivo `style.css` ficaria automaticamente exposto na url

```
https://user.codeberg.page/repo/@branch/path/to/style.css
```

e bastaria importá-la no projeto desejado em uma tag `<link>`, como comentado no início do post.

# Fim

A depender da plataforma, algumas configurações são necessárias para transformar um repositório em um site estático. Além disso, a url para acessar as páginas do site podem variar. No entanto, no fundo o processo é o mesmo.

Outra alternativa seria colocar seus arquivos `.css` num S3 Bucket na AWS ou em algum serviço similar em outros serviços de nuvem, que fornecem uma cota gratuita. Contudo, nessa abordagem perde-se a praticidade de se trabalhar com um repositório versionado.

Até mais,
Yuri.
