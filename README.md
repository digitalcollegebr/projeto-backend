
# Título do Projeto

Uma breve descrição sobre o que esse projeto faz e para quem ele é


## Deploy

Para fazer o deploy desse projeto rode

```bash
  npm  start
```


## Rodando os testes

Para rodar os testes, rode o seguinte comando

```bash
  npm  test
```




## Documentação da API




## Funcionalidades

- Temas dark e light
- Preview em tempo real
- Modo tela cheia
- Multiplataforma



## Tecnologias usadas


- **Node.js** para fornecer a possibilidade de executar JS em um servidor
- **Express.js** para criar rotas de api
- **Dotenv** para criarmos configurações com mais facilidade e segurança
- **Nodemon** para termos mais produtividade em nosso ambiente de desenvolvimento
- **MySQL** para persistência de dados
- **Sequelize** para termos mais produtividade ao lidar com o banco de dados 
- **JWT** para adicionar segurança e limitar o acesso nas rotas de API
- **JEST** para nos ajudar a testar e manter a qualidade do código

## Estrutura dO Projeto
```
project-root/
├── src/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── app.js
│   └── server.js
├── tests/
├── .env
├── .gitignore
└── package.json
```





## Rotas


## - Rotas do CRUD de usuarios

<details>
 
  
- GET /v1/user/:id

**Response body**
```json
{
  "id": 1,
  "firstname": "user firstname",
  "surname": "user surname",
  "email": "user@mail.com"
}  
```
</details>


<details>
  
  
- POST /v1/user



**Payload**

```json
{
  "firstname": "user firstname",
  "surname": "user surname",
  "email": "user@mail.com",
  "password": "123@123",
  "confirmPassword": "123@123",
}  
```

</details>

<details>


  - PUT /v1/user/:id

**Headers**
- Content-type: application/json

**Payload**
```json
{
  "firstname": "user firstname",
  "surname": "user surname",
  "email": "user@mail.com",
}  
```


</details>


<details>
 

- DELETE /v1/user/:id



</details>

## Rotas CRUD de categorias

<details>
 

- GET /v1/category/search

**Query params**
  - `limit=-1`
    - Query string para definir o limit de itens por página
    - Use `-1` como valor para buscar todos os itens
    - Padrão: 12
  - `page=1`
    - Query string para definir a paginação dos dados retornados
    - Quando `limit` receber `-1` a opção de `page` não tem nenhum efeito no resultado da busca e pode ser omitida da query string
    - Padrão: 1
  - `fields=name,slug`
    - Query string para limitar quais campos serão retornados
  - `use_in_menu=true`
    - Query string para filtrar apenas as categorias que podem aparecer no menu

**Response body**
```json
{
  "data": [
    {
      "id": 1,
      "name": "Shoes",
      "slug": "shoes",
      "use_in_menu": true
    },
    {
      "id": 2,
      "name": "Offers",
      "slug": "offers",
      "use_in_menu": true
    },
    {
      "id": 3,
      "name": "Black Friday",
      "slug": "black-friday",
      "use_in_menu": false
    }
  ],
  "total": 10,
  "limit": -1,
  "page": 1
}  
```


</details>

<details>
 
- GET /v1/category/:id

**Response body**
```json
{
  "id": 1,
  "name": "Shoes",
  "slug": "shoes",
  "use_in_menu": true
}  
```

**Response Status Code**
- 200 OK - Deve ser retornado quando a requisição foi bem sucedida
- 404 Not Found - Deve ser retornado quando o recurso solicitado não existe
</details>


<details>
  <summary><strong>Requisito 03 - Criar endpoint de cadastro de categoria</strong></summary><br>

- POST /v1/category



**Payload**

```json
{
  "name": "Shoes",
  "slug": "shoes",
  "use_in_menu": true
}  
```


</details>

<details>
 

- PUT /v1/category/:id

**Headers**
- Content-type: application/json

**Payload**
```json
{
  "name": "Shoes",
  "slug": "shoes",
  "use_in_menu": true
} 
```

</details>

<details>
  

- DELETE /v1/category/:id


</details>

## Seção 04 - Implementar endpoints para o CRUD de produtos

<details>


- GET /v1/product/search

**Query params**
  - `limit=30`
    - Query string para definir o limit de itens por página
    - Use `-1` como valor para buscar todos os itens
    - Padrão: 12
  - `page=2`
    - Query string para definir a paginação dos dados retornados
    - Quando `limit` receber `-1` a opção de `page` não tem nenhum efeito no resultado da busca e pode ser omitida da query string
    - Padrão: 1
  - `fields=name,images,price`
    - Query string para limitar quais campos serão retornados
  - `match=Tênis`
    - Query string usada para filtrar o resultado de produtos por um termo que combine com o nome ou descrição do produto
  - `category_ids=15,24`
    - Query string usada para filtrar o resultado de produtos pelo ID das categorias
  - `price-range=100-200`
    - Query string para filtrar o resultado de produtos por uma determinada "janela" de preços 
  - `option[45]=GG,PP`
    - Query string para filtrar o resultado de produtos pelo valor das opções disponíveis

**Response body**
```json
{
  "data": [
    {
      "id": 1,
      "enabled": true,
      "name": "Produto 01",
      "slug": "produto-01",
      "stock": 10,
      "description": "Descrição do produto 01",
      "price": 119.90,
      "price_with_discount": 99.90,
      "category_ids": [1, 15, 24, 68],
      "images": [
        {
          "id": 1,
          "path": "https://store.com/media/product-01/image-01.png"
        },
        {
          "id": 2,
          "path": "https://store.com/media/product-01/image-02.png"
        },
        {
          "id": 3,
          "path": "https://store.com/media/product-01/image-02.jpg"
        }
      ],
      "options": [
        { 
          "id": 1
          ... 
        },
        { 
          "id": 2
          ... 
        }
      ]
    }
  ],
  "total": 120,
  "limit": 12,
  "page": 1,
}  
```

</details>

<details>
  

- GET /v1/product/:id

**Response body**
```json
{
  "id": 1,
  "enabled": true,
  "name": "Produto 01",
  "slug": "product-01",
  "stock": 10,
  "description": "Descrição do produto 01",
  "price": 119.90,
  "price_with_discount": 99.90,
  "category_ids": [1, 15, 24, 68],
  "images": [
    {
      "id": 1,
      "content": "https://store.com/media/product-01/image-01.png"
    },
    {
      "id": 2,
      "path": "https://store.com/media/product-01/image-02.png"
    },
    {
      "id": 3,
      "path": "https://store.com/media/product-01/image-02.jpg"
    }
  ],
  "options": [
    { 
      "id": 1
      ... 
    },
    { 
      "id": 2
      ... 
    }
  ]
}  
```

**Response Status Code**
- 200 OK - Deve ser retornado quando a requisição foi bem sucedida
- 404 Not Found - Deve ser retornado quando o recurso solicitado não existe
</details>

<details>
 
- POST /v1/product



**Payload**

```json
  {
    "enabled": true,
    "name": "Produto 01",
    "slug": "produto-01",
    "stock": 10,
    "description": "Descrição do produto 01",
    "price": 119.90,
    "price_with_discount": 99.90,
    "category_ids": [1, 15, 24, 68],
    "images": [ 
      {
        "type": "image/png",
        "path": "base64 da imagem 1" 
      },
      {
        "type": "image/png",
        "path": "base64 da imagem 2" 
      },
      {
        "type": "image/jpg",
        "path": "base64 da imagem 3" 
      }
    ],
    "options": [
      {
        "title": "Cor",
        "shape": "square",
        "radius": "4px",
        "type": "text",
        "value": ["PP", "GG", "M"]
      },
      {
        "title": "Tamanho",
        "shape": "circle",
        "type": "color",
        "values": ["#000", "#333"]
      }
    ]
  }
  ```


</details>

<details>
 

- PUT /v1/product/:id

**Headers**
- Content-type: application/json

**Payload**

```json
  {
    "enabled": true,
    "name": "Produto 01 atualizado",
    "slug": "produto-01-atualizado",
    "stock": 20,
    "description": "Descrição do produto 01 atualizado",
    "price": 49.9,
    "price_with_discount": 0,
    "category_ids": [1, 15, 24, 68],
    "images": [ 
      {
        "type": "image/png",
        "path": "base64 da imagem 1" 
      },
      {
        "id": 2,
        "path": true
      },
      {
        "id": 3,
        "path": "base64 da imagem 3" 
      },
      {
        "id": 1,
        "path": "https://store.com/media/product-01/image-01.jpg"
      }
    ],
    "options": [
      {
        "id": 1,
        "deleted": true,
      }
      {
        "id": 2,
        "radius": "10px",
        "value": ["42/43", "44/45"]
      },
      {
        "title": "Tipo",
        "shape": "square",
        "type": "text",
        "values": ["100% algodão", "65% algodão"]
      }
    ]
  }
  ```

</details>


<details>
  <summary><strong>Requisito 05 - Criar endpoint de atualização de produto</strong></summary><br>

- DELETE /v1/product/:id

</details>


## Rotas de  implementação e validação do token JWT
<details>

- POST /v1/user/token


**Payload**

```json
{
  "email": "user@mail.com",
  "password": "123@123",
}  
```

**Response body**
```json
{
    "message": "User logado com suceso",
    "newlongin": {
        "token": <token>
    }
} 
```


</details>


## Referência

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)



## Autores

- [@octokatherine](https://www.github.com/octokatherine)

