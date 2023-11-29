---
title: "Failed Dependency! Instabilidade e TTL no Codeberg Pages"
description: "Nesse post comentamos duas possíveis razões para o erros do tipo `Failed Dependency!` ao tentar acessar uma página estática hospedada no Codeberg Pages."
tags: 'error, codeberg, DNS, TTL'
cover_image: 'https://i.imgur.com/OBT8D9x.png'
series: 'Quick Tips'
canonical_url: null
published: true
---

# Introdução

[Codeberg](https://codeberg.org) é uma alternativa gratuita e open-source ao Github/Gitlab, a qual oferece uma plataforma para gerenciamento de repositórios `git` (veja [esse](https://dev.to/yxm/codeberg-uma-alternativa-open-source-e-gratuita-ao-github-e-gitlab-b80) post). Lá você também pode hospedar um site estático de forma bastante simples no que é chamado de [Codeberg Pages](https://docs.codeberg.org/codeberg-pages/), serviço análogo ao Github/Gitlab Pages, conforme discutido [nesse](https://dev.to/yxm/como-utilizar-um-css-hospedado-no-github-ou-codeberg-em-um-projeto-html-3158) post.

# Erro 1

Suponhamos que você utiliza o Codeberg Pages e, na maioria dos casos, sua página carrega normalmente (com domínio personalizado ou não). No entanto, em algumas raras situações, ao tentar acessar sua página, você se depara com o erro 

* *Failed Dependency! (...) could not find target for custom domain*. 

Nesse caso, não se desespere! O servidor que mantém o Codeberg Pages passa, vez ou outra, por instabilidades. Lembremos que é um serviço gratuito, com foco total em projetos open-source, e mantido por doações (veja [aqui](https://docs.codeberg.org/getting-started/faq/#is-codeberg-well-funded%3F)), algo que não pode ser comparado com o GitHub (o qual é mantido pela Microsoft) nem com o Gitlab (que é uma empresa privada, com fins lucrativos).

![Failed Dependency! (...) could not find target for custom domain](https://i.imgur.com/zCjKLj0.png).

# Erro 2

Por outro lado, se você criou sua página e está tentando ativar/alterar um domínio personalizado, talvez você encontre um outro erro do tipo "Failed Depencency!" um pouco diferente:

* *Failed Dependency! (...) could not obtain repo owner from custom domain*.

Essa situação também não é motivo de desespero. Primeiramente, verifique se você:

* configurou o arquivo `.domains` na raiz de seu repositório de modo a conter uma linha única com o seu domínio customizado (digamos `my-domain.com`), conforme descrito na [documentação](https://docs.codeberg.org/codeberg-pages/); 
* adicionou registros DNS da forma correta, a saber (o erro normalmente aparece por equívoco no registro `TXT`):
    * `A`, apontando para o IPv4 `217.197.91.145`
    * `AAA`, apontando para o IPv6 `2001:67c:1401:20f0::1`
    * `TXT`, apontando para `branch.repo.user.codeberg.page`.

Se ainda assim o erro persistir, saiba que o  TTL (time to live) do cache no servidor do Codeberg Pages é de 3h (veja [aqui](https://codeberg.org/Codeberg/Community/issues/1013)). Nesse caso, é só esperar um tempo até que cache seja limpo. 

# Fim

Codeberg pode apresentar instabilidades, mas para hospedagem de sites estáticos, ainda assim é a minha opção predileta.

Até mais,

Yuri.

* [yxm.me](https://yxm.me)
* [github.com/yxm-dev](https://github.com/yxm.dev)
* [codeberg.com/yxm](https://codeberg.com/yxm) 
