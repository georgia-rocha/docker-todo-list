## OBJETIVO
Colocar em prática os assuntos de Docker abordados pela Trybe na primeira sessão de back-end com aproveitamento de 100%.

<details>
<summary><strong>Para clonar e testar</strong></summary><br />

1. Clone o repositório
* `git clone git@github.com:georgia-rocha/docker-todo-list.git`
* Entre na pasta do repositório que você acabou de clonar:

2. Instale as dependências:
* `npm install`

3. Verifique se os testes estão executando:
  * `npm test`
  
</details>

<details>
<summary><strong>👨‍💻 O que foi desenvolvido</strong></summary><br />
Foi desenvolvido uma conteinerização de uma aplicação full-stack, onde foi necessário desenvolver arquivos de configuraçãi para cada frente específica: 'Front-end', 'Back-end' e um app de 'teste' que valida se as aplicações estão se comunicando.
</details>

# 100% dos Requisito Obrigatórios

- [x] 1. Crie um container em modo interativo, sem rodá-lo, nomeando-o como `01container` e utilizando a imagem `alpine` na versão `3.12`

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command01.dc`.

#### Observações técnicas

- O container **não deve ser inicializado**, somente criado;
- O container deve estar preparado para acesso interativo.

#### Dicas
- Dê uma olhada no comando [`create`](https://docs.docker.com/engine/reference/commandline/create/). 😉
- Lembre-se que um parâmetro não é necessariamente aplicável a apenas um comando;
- Consulte sempre que possível a [Documentação Oficial](https://docs.docker.com/engine/reference/commandline/docker/) sobre comandos básicos;
- Lembre-se que a esmagadora parte dos comandos docker recebe parâmetros (opções), como [nesse exemplo](https://docs.docker.com/engine/reference/commandline/logs/#options).

#### O que será testado

- O `nome` do container deve ser `01container`;
- O container deve usar a imagem `alpine` na versão `3.12`;
- O `status` do container deve ser `created`;
- O container **não deve** estar em execução após ter sido criado.

</details>

- [x] 2. Inicie o container `01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command02.dc`.

#### Observações técnicas

- O container `01container`, que acabou de ser criado e está parado, deve ser iniciado;
- Se o container tiver sido iniciado de modo interativo, ele deve se manter ativo ao iniciá-lo.
  
#### O que será testado

- O avaliador verificará se o container está parado;
- O avaliador executará o comando criado neste requisito;
- O container **deve** estar em execução.

</details>

- [x] 3. Liste os containers filtrando pelo nome `01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command03.dc`.

#### Dicas

- Praticamente todo comando de listagem no Docker possui uma forma de filtragem.

#### O que será testado

- O comando deve retornar uma lista contendo informações **apenas** do `01container`.

</details>

- [x] 4. Execute o comando `cat /etc/os-release` no container `01container` sem se acoplar a ele

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command04.dc`.

#### Observações técnicas

- O container deve estar rodando e você deve ser capaz de **executar um comando** nesse container.

#### Dicas

- É possível fazer isso sem usar o comando `attach`.

#### O que será testado

- Que o comando retornará os dados corretos da `distro` no container:
  - `NAME="Alpine Linux"`
  - `ID=alpine`
  - `VERSION_ID=3.12`

</details>

- [x] 5. Remova o container `01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará os comandos nos arquivos `command05.dc` e `command03.dc`.

#### O que será testado

- O avaliador rodará o comando 5;
- O avaliador validará o processo com o comando 3.

</details>

- [x] 6. Faça o download da imagem `nginx` com a versão `1.21.3-alpine` sem criar ou rodar um container

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command06.dc`.

#### O que será testado

  - Que a imagem correta foi baixada;
  - Que nenhum container foi iniciado para isso.

</details>

- [x] 7. Rode um novo container com a imagem  `nginx` com a versão `1.21.3-alpine` em segundo plano nomeando-o como `02images` e mapeando sua porta padrão de acesso para porta `3000` do sistema hospedeiro

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command07.dc`.

#### O que será testado

  - Que o container foi iniciado corretamente;
  - Que é possível ter acesso ao container pelo endereço `localhost:3000`;
  - Que a página retorna o valor esperado.

</details>

- [x] 8. Pare o container `02images` que está em andamento

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command08.dc`.

#### O que será testado

  - Que não há nenhum container ativo após seu comando.

</details>

## Dockerfile

- [x] 9. Gere uma build a partir do Dockerfile do `back-end` do `todo-app` nomeando a imagem para `todobackend`
<details>
<summary>➕ Informações adicionais</summary><br />
Escreva no arquivo `command09.dc` um comando que fará o `build`([documentação do comando](https://docs.docker.com/engine/reference/commandline/build/)) de uma imagem a partir do arquivo `./docker/todo-app/back-end/Dockerfile`, esta imagem deve ter o nome `todobackend`.

No arquivo `./docker/todo-app/back-end/Dockerfile` escreva os comandos que farão com que a imagem:
- rode a partir da imagem do `node` na versão 14;
- exponha a porta 3001;
- trabalhe em um diretório denominado `app`;
- adicione o arquivo `node_modules.tar.gz` à imagem;
- copie todos os arquivos da pasta `back-end` para a imagem. (você pode usar o caminho relativo, lembrando que a `Dockerfile` está em `./docker/todo-app/back-end/Dockerfile`);
- inicie a aplicação com o comando `npm start` respeitando as seguintes restrições: 
  1. ao subir um container baseado na imagem buildada a partir desse Dockerfile, o comando `npm` deve ser rodado `sempre`;
  2. ao subir um container baseado na imagem buildada a partir desse Dockerfile, deve ser possível sobrescrever o comando `start`.
  </ details>

<details>
  <summary>➕ Informações adicionais</summary><br />

- Nesse contexto, deve-se criar um arquivo [`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format) na pasta `./docker/todo-app/back-end/`, que será utilizado com comando exigido no requisito;
- Esse arquivo deve buscar reproduzir as etapas de `back-end` contidas no [`README.md`](docker/todo-app/README.md) da *pseudo-aplicação* (também estão descritas na seção `O que será testado`, do requisito) para que ele rode corretamente;
- O avaliador executará o comando no arquivo `command09.dc`.

#### Dicas 

- O [comando `ADD`](https://docs.docker.com/engine/reference/builder/#add) do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  - Entenda a diferença entre o comando `ADD` e `COPY` [neste artigo](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).

#### O que será testado

- Se existe um arquivo `Dockerfile` em `./docker/todo-app/back-end/`:
  - O Dockerfile deve rodar uma imagem `node` utilizando a versão `14`;
    - Recomenda-se o uso da variante `-alpine`, pois ela é otimizada para desempenho;
    - Lembre-se de consultar o README do `todo-app` para validar os requisitos da aplicação.
  - Deve estar com a porta `3001` exposta;
  - Deve conter um diretório denominado `app`;
  - Os arquivos do projeto devem estar dentro do diretório `app`;
  - Deve adicionar o arquivo `node_modules.tar.gz` a imagem;
  - Deve copiar todos os arquivos da pasta `back-end` para a imagem;
  - Ao iniciar a imagem deve rodar o comando `npm start`, sendo o `npm` um comando executado `sempre` e o `start` um comando passível de sobrescrita.
- Se ao *buildar* o Dockerfile o nome da imagem gerada é igual a `todobackend`.

</details>
</details>

- [x] 10. Gere uma build a partir do Dockerfile do `front-end` do `todo-app` nomeando a imagem para `todofrontend`
<details>
<summary>➕ Informações adicionais</summary><br />
Escreva no arquivo `command10.dc` um comando que fará o `build`([documentação do comando](https://docs.docker.com/engine/reference/commandline/build/)) de uma imagem a partir do arquivo `./docker/todo-app/front-end/Dockerfile`, esta imagem deve ter o nome `todofrontend`.

No arquivo `./docker/todo-app/front-end/Dockerfile` escreva os comandos que farão com que a imagem:
- rode a partir da imagem do `node` na versão 14;
- exponha a porta 3000;
- trabalhe em um diretório denominado `app`;
- adicione o arquivo `node_modules.tar.gz` à imagem;
- copie todos os arquivos da pasta `front-end` para a imagem. (você pode usar o caminho relativo, lembrando que a `Dockerfile` está em `./docker/todo-app/front-end/Dockerfile`);
- inicie a aplicação com o comando `npm start` respeitando as seguintes restrições: 
  1. ao subir um container baseado na imagem buildada a partir desse Dockerfile, o comando `npm` deve ser rodado `sempre`;
  2. ao subir um container baseado na imagem buildada a partir desse Dockerfile, deve ser possível sobrescrever o comando `start`.


<details>
  <summary>➕ Informações adicionais</summary><br />

- Nesse contexto, deve-se criar um arquivo [`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format) na pasta `./docker/todo-app/back-end/`, que será utilizado com comando exigido no requisito;
- Esse arquivo deve buscar reproduzir as etapas de `front-end` contidas no [`README.md`](docker/todo-app/README.md) da *pseudo-aplicação* (também estão descritas na seção `O que será testado`, do requisito) para que ele rode corretamente;
- O avaliador executará o comando no arquivo `command10.dc`.

#### Dicas

- O [comando `ADD`](https://docs.docker.com/engine/reference/builder/#add) do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  - Entenda a diferença entre o comando `ADD` e `COPY` [neste artigo](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).
#### O que será testado

  - Se existe um arquivo `Dockerfile` em `./docker/todo-app/front-end/`:
    - O `Dockerfile` pode rodar uma imagem `node` utilizando a versão `14`;
      - Recomenda-se o uso da variante `-alpine`, pois ela é otimizada para desempenho;
      - Lembre-se de consultar o README do `todo-app` para validar os requisitos da aplicação.
    - Deve estar com a porta `3000` exposta;
    - Deve conter um diretório denominado `app`;
    - Os arquivos do projeto devem estar dentro do diretório `app`;
    - Deve adicionar o arquivo `node_modules.tar.gz` a imagem, de maneira que ele seja extraído dentro do `container`;
    - Deve copiar todos os arquivos da pasta `front-end` para a imagem;
    - Ao iniciar a imagem deve rodar o comando `npm start`, sendo o `npm` um comando executado `sempre` e o `start` um comando passível de sobrescrita.
  - Se ao *buildar* o `Dockerfile` o nome da imagem gerada é igual a `todofrontend`.

</details>
  </details>

- [x] 11. Gere uma build a partir do Dockerfile dos `testes` do `todo-app` nomeando a imagem para `todotests`
<details>
<summary>➕ Informações adicionais</summary><br />
Escreva no arquivo `command11.dc` um comando que fará o `build`([documentação do comando](https://docs.docker.com/engine/reference/commandline/build/)) de uma imagem a partir do arquivo `./docker/todo-app/tests/Dockerfile`, esta imagem deve ter o nome `todotests`.

No arquivo `./docker/todo-app/tests/Dockerfile` escreva os comandos que farão com que a imagem:
- rode a partir da imagem do `mjgargani/puppeteer:trybe1.0`;
- trabalhe em um diretório denominado `app`;
- adicione o arquivo `node_modules.tar.gz` à imagem;
- copie todos os arquivos da pasta `tests` para a imagem. (você pode usar o caminho relativo, lembrando que a `Dockerfile` está em `./docker/todo-app/tests/Dockerfile`);
- inicie a aplicação com o comando `npm test` respeitando as seguintes restrições: 
  1. ao subir um container baseado na imagem buildada a partir desse Dockerfile, o comando `npm` deve ser rodado `sempre`;
  2. ao subir um container baseado na imagem buildada a partir desse Dockerfile, deve ser possível sobrescrever o comando `test`.

<details>
  <summary>➕ Informações adicionais</summary><br />

- Nesse contexto, deve-se criar um arquivo [`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format) na pasta `./docker/todo-app/back-end/`, que será utilizado com comando exigido no requisito;
- Esse arquivo deve buscar reproduzir as etapas de `testes` contidas no [`README.md`](docker/todo-app/README.md) da *pseudo-aplicação* (também estão descritas na seção `O que será testado`, do requisito) para que ele rode corretamente;
- O avaliador executará o comando no arquivo `command11.dc`.

#### Dicas

- O [comando `ADD`](https://docs.docker.com/engine/reference/builder/#add) do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  - Entenda a diferença entre o comando `ADD` e `COPY` [neste artigo](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).
#### Observações técnicas

- A aplicação `todotests` só funciona corretamente se estiver dockerizada e dentro de uma rede docker configurada corretamente.

#### O que será testado

- Se existe um arquivo `Dockerfile` em `./docker/todo-app/tests/`:
  - O Dockerfile deve rodar a imagem `mjgargani/puppeteer:trybe1.0` para que os testes funcionem;
  - Deve conter um diretório denominado `app`;
  - Os arquivos do projeto devem estar dentro do diretório `app`;
  - Deve adicionar o arquivo `node_modules.tar.gz` a imagem;
  - Deve copiar todos os arquivos da pasta `tests` para a imagem;
  - Ao iniciar a imagem deve rodar o comando `npm test`, sendo o `npm` um comando executado `sempre` e o `test` um comando passível de sobrescrita.
- Se ao *buildar* o Dockerfile o nome da imagem gerada é igual a `todotests`.

</details>
  </details>

# 100% dos Requisito bônus do projeto

## Docker-compose

- [x] 12. Suba uma orquestração em segundo plano com o docker-compose de forma que `backend`, `frontend` e `tests` consigam se comunicar

<details>
  <summary>➕ Informações adicionais</summary><br />

O avaliador executará o comando no arquivo `command12.dc`. Este comando pressupõe a existência do arquivo `./docker/docker-compose.yml`.

O `docker-compose` deve rodar na versão 3 ou superior.

#### Dicas

- Use as imagens já **"buildadas"** que foram executadas nos requisitos 9, 10 e 11 para a criação do compose;
- Consulte a documentação em `./docker/todo-app/README.md`;
- É possível adicionar e extrair arquivos `.tar.gz` no `Dockerfile` com apenas um comando.

#### O que será testado

##### tests

- O container de `todotests` deve ter como dependencia os containers `frontend` e `backend`;
- O nome do _service_ deverá ser `todotests`;
- Deve ter uma variável de ambiente `FRONT_HOST` que recebe como valor o nome do container do `frontend`
  - Lembrando que, dentro de uma rede docker, o host de um container é identificado pelo seu nome.

##### front-end

- O container de `todofrontend` deve rodar na porta `3000`;
- O nome do _service_ deverá ser `todofront`;
- Deve ter como dependencia o container `backend`;
- Deve ter uma variável de ambiente `REACT_APP_API_HOST` que recebe como valor o nome do container do `backend`.
  - Lembrando que, dentro de uma rede docker, o host de um container é identificado pelo seu nome.

##### back-end

- O container de `todobackend` deve rodar na porta `3001`;
- O nome do _service_ deverá ser `todoback`;

</details>

