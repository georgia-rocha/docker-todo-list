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
<details>
<summary>2. Escolha se vai rodar o projeto localmente ou pelo Docker e faça o npm install:</summary>
 
 <details>
  <summary><strong>🐋 Rodando no Docker vs Localmente</strong></summary><br />

  ## Com Docker

  **:warning: Antes de começar, seu docker-compose precisa estar na versão 1.29 ou superior. [Veja aqui](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04-pt) ou [na documentação](https://docs.docker.com/compose/install/) como instalá-lo. No primeiro artigo, você pode substituir onde está com `1.26.0` por `1.29.2`.**

  > :information_source: Rode os serviços `node` e `db` com o comando `docker-compose up -d`.
  - Lembre-se de parar o `mysql` se estiver usando localmente na porta padrão (`3306`), ou adapte, caso queria fazer uso da aplicação em containers
  - Esses serviços irão inicializar um container chamado `all_for_one` e outro chamado `all_for_one_db`.
  - A partir daqui você pode rodar o container `all_for_one` via CLI ou abri-lo no VS Code.

  > :information_source: Use o comando `docker exec -it all_for_one bash`.
  - Ele te dará acesso ao terminal interativo do container criado pelo compose, que está rodando em segundo plano.
  - As credencias de acesso ao banco de dados estão definidas no arquivo `docker-compose.yml`, e são acessíveis no container através das variáveis de ambiente `MYSQL_USER` e `MYSQL_PASSWORD`. 💡

  > :information_source: Instale as dependências [**Caso existam**] com `npm install`. (Instale dentro do container)

  - **:warning: Atenção:** Caso opte por utilizar o Docker, **TODOS** os comandos disponíveis no `package.json` (npm start, npm test, npm run dev, ...) devem ser executados **DENTRO** do container, ou seja, no terminal que aparece após a execução do comando `docker exec` citado acima.

  - **:warning: Atenção:** O **git** dentro do container não vem configurado com suas credenciais. Ou faça os commits fora do container, ou configure as suas credenciais do git dentro do container.

  - **:warning: Atenção:** Não rode o comando npm audit fix! Ele atualiza várias dependências do projeto, e essa atualização gera conflitos com o avaliador.

  - ✨ **Dica:** A extensão `Remote - Containers` (que estará na seção de extensões recomendadas do VS Code) é indicada para que você possa desenvolver sua aplicação no container Docker direto no VS Code, como você faz com seus arquivos locais.

   <br />

  ## Sem Docker

  > :information_source: Instale as dependências [**Caso existam**] com `npm install`

  - **:warning: Atenção:** Não rode o comando npm audit fix! Ele atualiza várias dependências do projeto, e essa atualização gera conflitos com o avaliador.

  - **✨ Dica:** Para rodar o projeto desta forma, obrigatoriamente você deve ter o `node` instalado em seu computador.
  - **✨ Dica:** O avaliador espera que a versão do `node` utilizada seja a 16.

  <br/>
</details>

<details>
  <summary><strong>📑 Instruções para testar as queries</strong></summary><br />

  #### Para executar os testes locais com Docker 🐋

  - Após ter seguido os passos anteriores do `docker-compose up -d` e `docker exec -it all_for_one bash`, dentro do terminal interativo do container, rode:
  ```sh
  npm test
  ```

  #### Para executar os testes locais usando a instalação do MySQL feita na sua máquina 💻

  - Para executar localmente os testes é preciso escrever o seguinte no seu terminal:
  ```sh
  MYSQL_USER=<SEU_NOME_DE_PESSOA_USUARIA> MYSQL_PASSWORD=<SUA SENHA> HOSTNAME=<NOME_DO_HOST> PORT=<PORTA> npm test
  ```

  - Não esqueça de substituir os locais indicados com `< >` por suas credenciais:
  ```sh
  MYSQL_USER=root MYSQL_PASSWORD=password HOSTNAME=localhost PORT=3306 npm test
  ```

  #### Dicas e pontos de atenção

  - ✨ **Dica:** variáveis de ambiente definidas na mesma linha do comando valem apenas para aquele comando. Se preferir, você pode exportar as variáveis de ambiente para toda a _sessão_ (todos os comandos até você fechar aquele terminal). Por exemplo:
  ```sh
  export MYSQL_USER=root MYSQL_PASSWORD=password HOSTNAME=localhost PORT=3306
  ```
  > E depois disso você só precisa rodar `npm test` quando for testar os projetos.

  - ✨ **Dica:** Caso queira utilizar _Docker_ para rodar os testes localmente, basta executar o comando:
  ```sh
  docker run -p 3306:3306 --name mysql_57 -e MYSQL_ROOT_PASSWORD=1234 -d mysql:5.7 mysqld --default-authentication-plugin=mysql_native_password
  ```
  - Depois de usar o comando acima, agora basta executar os testes digitando no terminal:
  ```sh
  MYSQL_USER=root MYSQL_PASSWORD=1234 HOSTNAME=localhost npm test
  ```

  <details close>
    <summary>O que está sendo feito na dica acima</summary>
    <br>

    - :point_right: flag --name:
    > Define um nome para o nosso _container_: "meu-mysql-5_7".

    - :point_right: flag -e:
    > Define a variável de ambiente "MYSQL_ROOT_PASSWORD" com o valor "1234".

    - :point_right: flag -d:
    > Define que o container rode em segundo plano.

    - :point_right: flag -p:
    > Mapeia uma porta local a uma porta do _container_.

    - :point_right: mysql:5.7:
    > Define qual versão da imagem  mySQL queremos, no caso, a 5.7, que é a esperada pelo avaliador.
  </details>

  - **:warning: Atenção:** O avaliador espera que a versão do  MySQL seja a 5.7. Em caso de erro nos testes, verifique se essa é a versão que está sendo usada por você.

  - **:warning: Atenção:** Não é necessário colocar `USE northwind` ou `SET SQL_SAFE_UPDATES = 0;` no início dos seus arquivos

  - **:warning: Atenção:** Após a execução dos teste locais, o banco de dados `northwind` é recriado :warning:
</details>
</details>

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
