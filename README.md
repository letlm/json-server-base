# json-server-base

Esta api tem como objetivo cadastrar os sabores preferidos de sorvetes e suas bebidas favoritas!

## Endpoints - 
A API tem um total de 7 endpoints, sendo que desses 7, 3 endpoints que ser utilizados para cadastro, 2 endpoints para login, 1 para o cadastro de sorvetes e 1 para o de bebidas. 

### Criação do cadastro :red_haired_woman:

`POST /register -  FORMATO DA REQUISIÇÃO` </br>
`POST /signup -  FORMATO DA REQUISIÇÃO` </br>
`POST /users -  FORMATO DA REQUISIÇÃO`

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password. Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.
```json
{
  "email": "testinho@gmail.com",
  "password": "123456",
  "name": "Testinho",
  "age": 23
 }
```

<h3>Possíveis erros:</h3>

- E-mail já cadastrado: 
`POST /users -  FORMATO DA RESPOSTA - STATUS 400`
```json
{
  "status": "error",
  "message": "Email already exists",
 }
```

- Senha pequena: 
A senha precisa ter no mínimo 4 caracteres.
`POST /users -  FORMATO DA RESPOSTA - STATUS 400`
```json
{
  "status": "error",
  "message": "Password is too short",
 }
```


### Login :red_haired_woman:

`POST /login -  FORMATO DA REQUISIÇÃO` </br>
`POST /signin -  FORMATO DA REQUISIÇÃO`

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"
```json
{
  "email": "testinho@gmail.com",
  "password": "123456",
 }
```

<h3>Possíveis erros:</h3>

- E-mail não encontrado: </br>
`POST /users -  FORMATO DA RESPOSTA - STATUS 400`
```json
{
  "status": "error",
  "message": "Cannot find user",
 }
```

- Senha inválida: </br>
A senha digitada está incorreta </br>
`POST /users -  FORMATO DA RESPOSTA - STATUS 400`
```json
{
  "status": "error",
  "message": "Incorrect password",
 }
```

### Listar os IceCreams :ice_cream: :icecream: :shaved_ice: - NÃO É NECESSÁRIO A AUTENTICAÇÃO

`GET /icecream -  FORMATO DA REQUISIÇÃO`


<h1>Rotas que precisam de autenticação</h1>

### Adicionar o Icecream preferido :ice_cream:

`POST /icecream -  FORMATO DA REQUISIÇÃO`

Os campos obrigatórios para adicionar o seu icecream favoritos são: icecream, syrup, userId, além do Token

```json
{
	"flavor": "Flakes",
	"syrup": "Strawberry",
	"userId": 2
}
```
<h3>Possíveis erros:</h3>

- Não adicionar o token: </br>
`POST /icecream -  FORMATO DA RESPOSTA - STATUS 401`
```json
"Missing token"
"Missing authorization header"
```

### Adicionar seus Drinks preferidos :coffee: 

`POST /drinks -  FORMATO DA REQUISIÇÃO`

```json
{
"name": "Mocaccino",
"alcoholic": "No"
}
```
Os campos obrigatórios para adicionar o seu drink favorito são: name, alcoholic, além do Token.

<h3>Possíveis erros:</h3>

- Não adicionar o token: </br>
`POST /icecream -  FORMATO DA RESPOSTA - STATUS 401`
```json
"Missing token"
"Missing authorization header"
```

- Não adicionar alguns dos campos obrigatórios:

### Listar seus Drinks preferidos :coffee: :tea: :wine_glass: :tropical_drink:

`GET /drinks -  FORMATO DA REQUISIÇÃO`

- Não adicionar o token: </br>
`POST /drinks -  FORMATO DA RESPOSTA - STATUS 401`
```json
"Missing token"
"Missing authorization header"
```
