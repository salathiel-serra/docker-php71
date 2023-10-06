# DOCKER-PHP71

Este projeto define a configuração necessária para ambiente de execução de aplicações PHP71 e para iniciar, <br>
acesse o projeto que você deseja executar com docker e execute:
```
git clone https://github.com/salathiel-serra/docker-php71.git 
```

Antes de executar o container, precisamos destacar alguns pontos: <br>
1) O sucesso para execução do container dependente de uma rede chamada: ```stc_nw``` , <br> 
para verificar a existência da rede, execute: ```docker network ls``` , <br> 
caso precise criar a rede, execute: ```docker network create --driver bridge stc_nw``` <br>
OBS: você poderá nomear a rede conforme sua necesssidade, basta alterar o arquivo docker-compose.yml

2) O arquivo docker-compose.yml mapeia no host a porta: ```8060```, <br>
Ajuste a definição de porta no arquivo conforme a sua necessidade

3) O container será nomeado da seguinte forma após inicialização: ```[nome projeto]_container```

4) A pasta ```apache/logs/``` mapeia os arquivos de logs do servidor, em caso de erro acesse com maior facilidade esses dados

<br> <hr> <br> 

Após o entendimento desses pontos importantes, vamos à execução do container e para isso acesse a pasta: ```docker-php71``` <br>
à partir deste diretório, digite: ```docker-compose up -d``` ou ```docker compose up -d``` , esteja atento às suas permissões de usuário e acrescente **sudo** ao comando, caso necessário.

<br>

Se você estiver executando o comando **up** pela primeira vez, o processo poderá levar um pouco mais de tempo, aguarde.

Após a conclusão do processo e imaginando que ocorreu tudo conforme o esperado, acesse seu navegador de preferência e digite: ```http://localhost:8060``` , <br>
caso tenha alterado à porta, informe a porta mapeada.

Para visualizar os containers em execução, digite: ```docker ps```

Para acessar o container, digite: ```docker exec -it [nome projeto]_container bash```

<br> <hr> <br> 

Este projeto define apenas a configuração de ambiente, todos os demais processos para execução da aplicação que estiverem ligados à linguagem ou framework deverão ser executados manualmente <br> Para aplicações PHP 7.1 e Laravel 5.1 não esqueça:

1. ```composer install```
2. ```chmod 777 -R storage/* bootstrap/cache```
3. ```cp .env-example .env```  | realize ajustes necessários para banco
4. ```php artisan key:generate```
5. ```php artisan config:cache```
