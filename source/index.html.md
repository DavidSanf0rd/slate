---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introdução

A Api do sistema de rádio deve ser implementada assim como descrita nesse documento.

# Autenticação

Modo de autenticação deve ser definido pelo desenvolvedor do servidor.

<aside class="notice">
O modo de autenticação deve ser informado aos desenvolvedores do aplicativo antes do término do desenvolvimento.
</aside>

# Notícias

## Listar todas as notícias


```shell
curl "http://host.com/api/news"
  -H "Authorization: someKey"
```

> O comando acima retorna um json com a estrutura abaixo:

```json
[
  {
    "id": 1,
    "title": "VI Concurso de música jovens talentos",
    "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "image": "PD94bWwgdmVgLz48L3N2Zz4="
  },
  {
    "id": 2,
    "title": "A orquestra de câmara Vovó Dedé",
    "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "image": "PD94bWwgdmVgLz48L3N2Zz4="
  }
]
```

Esse endpoint retorna todas as notícias paginadas

### Requisição HTTP

`GET http://host.com/api/news`

### Parâmetros (query)

Parametro | Padrão | Descrição
--------- | ------- | -----------
page | 1 | o número da página requisitada
size | 5 | o número de notícias em uma página

### Observações sobre as chaves do json

Chave | Observação
--------- | -----------
text | essa chave do json deve conter o texto resumido da notícia para ser mostrada na tela de listagem.
image | essa chave do json deve retornar uma imagem de resolução 200x113 codificada em base64.

## Lista uma notícia específica

```shell
curl "http://host.com/api/news/2"
  -H "Authorization: someKey"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "title": "A orquestra de câmara Vovó Dedé",
  "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
  "image": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVA5TDksMTYuMTdMMTkuNTksNS41OUwyMSw3WiIgLz48L3N2Zz4=="
}
```

> text: essa chave do json deve conter o texto completo da notícia para ser mostrada na tela de detalhes

> image: essa chave do json deve retorar uma imagem de resulução 640x360 codificada em base64

Esse endpoint retorna uma notícia em específica

### Requisição HTTP

`GET http://host.com/api/news/<ID>`

### URL Parameters

parametro | Descrição
--------- | -----------
ID | o id da notícia requisitada

### Observações sobre as chaves do json

Chave | Observação
--------- | -----------
text | essa chave do json deve conter o texto completo da notícia para ser mostrada na tela de detalhes.
image | essa chave do json deve retornar uma imagem de resolução 750x422 codificada em base64.

# Comentários

## Listar comentários


```shell
curl "http://host.com/api/comments"
  -H "Authorization: someKey"
```

> O comando acima retorna um json com a estrutura abaixo:

```json
[
  {
    "id": 1,
    "author": "David Sanford",
    "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "timeStamp": "08/01/2017 14:30:25"
  },
  {
    "id": 2,
    "author": "Luisa macedo",
    "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "timeStamp": "07/01/2017 19:34:25"
  }
]
```

Esse endpoint retorna os ultimos comentários ordenado de acordo com o campo timeStamp

### Requisição HTTP

`GET http://host.com/api/comments`

### Parâmetros (query)

parametro | Padrão | Descrição
--------- | ------- | -----------
page | 1 | o número da página requisitada
size | 15 | o número de comentários em uma página

## Criar comentário


```shell
curl "http://host.com/api/comments"
  -H "Authorization: someKey"
```

> O comando acima recebe um json com a estrutura abaixo:

```json
  {
    "author": "David Sanford",
    "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit"
  }
```

Esse endpoint cria um novo comentário

### Requisição HTTP

`POST http://host.com/api/comments`

<aside class="notice">
O json ao lado deve ser enviado no corpo da requisição HTTP.
</aside>

# Curtir música

## Criar curtida


```shell
curl "http://host.com/api/like"
  -H "Authorization: someKey"
```

> O comando acima recebe um json com a estrutura abaixo:

```json
  {
    "program": "Ouvindo estrelas",
    "song": "The side winder - Lee Morgan"
  }
```

Esse endpoint cria uma entrada para curtida de uma música.

### Requisição HTTP

`POST http://host.com/api/like`

<aside class="notice">
O json ao lado deve ser enviado no corpo da requisição HTTP.
</aside>

# Banners

## listar banners


```shell
curl "http://host.com/api/banners"
  -H "Authorization: someKey"
```

> O comando acima retorna um json com a estrutura abaixo:

```json
[
  {
    "id": "1",
    "partner": "Example",
    "image": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVA5TDksMTYuMTdMMTkuNTksNS41OUwyMSw3WiIgLz48L3N2Zz4=="
  },
  {
    "id": "2",
    "partner": "Example2",
    "image": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVA5TDksMTYuMTdMMTkuNTksNS41OUwyMSw3WiIgLz48L3N2Zz4=="
  }
]
```

Esse endpoint cria uma entrada para curtida de uma música.

### Requisição HTTP

`GET http://host.com/api/banners`

<aside class="notice">
Os banners devem ser recebidos de acordo com o horário. Assim cabe ao administrador do sistema definir quais banners serão recebidos em determinado horário.
</aside>
