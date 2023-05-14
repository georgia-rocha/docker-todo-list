## OBJETIVO
Colocar em prática os assuntos de Docker abordados pela Trybe na primeira sessão de back-end com aproveitamento de 100%, foi desenvolvido uma conteinerização de uma aplicação full-stack, onde foi necessário desenvolver arquivos de configuração para cada frente específica: 'Front-end', 'Back-end' e um app de 'teste' que valida se as aplicações estão se comunicando.

<details>
<summary><strong>Para clonar e testar</strong></summary><br />

1. Clone o repositório
 
```
git clone git@github.com:georgia-rocha/docker-todo-list.git
```
 
 * Entre na pasta do repositório que você acabou de clonar:
 
 ```
 cd docker-todo-list
 ```
 
2. Instale as dependências:
 
 ```
 npm install
 ```
 
3. Verifique se os testes estão executando:
```
 npm test
 ```
</details>

# 100% dos Requisito Obrigatórios

- [x] 1. Crie um container em modo interativo, sem rodá-lo, nomeando-o como `01container` e utilizando a imagem `alpine` na versão `3.12`

- [x] 2. Inicie o container `01container`

- [x] 3. Liste os containers filtrando pelo nome `01container`

- [x] 4. Execute o comando `cat /etc/os-release` no container `01container` sem se acoplar a ele

- [x] 5. Remova o container `01container`

- [x] 6. Faça o download da imagem `nginx` com a versão `1.21.3-alpine` sem criar ou rodar um container

- [x] 7. Rode um novo container com a imagem  `nginx` com a versão `1.21.3-alpine` em segundo plano nomeando-o como `02images` e mapeando sua porta padrão de acesso para porta `3000` do sistema hospedeiro

- [x] 8. Pare o container `02images` que está em andamento

## Dockerfile

- [x] 9. Gere uma build a partir do Dockerfile do `back-end` do `todo-app` nomeando a imagem para `todobackend`

- [x] 10. Gere uma build a partir do Dockerfile do `front-end` do `todo-app` nomeando a imagem para `todofrontend`
ir desse Dockerfile, o comando `npm` deve ser rodado `sempre`;

- [x] 11. Gere uma build a partir do Dockerfile dos `testes` do `todo-app` nomeando a imagem para `todotests`

# 100% dos Requisito bônus do projeto

## Docker-compose

- [x] 12. Suba uma orquestração em segundo plano com o docker-compose de forma que `backend`, `frontend` e `tests` consigam se comunicar.
