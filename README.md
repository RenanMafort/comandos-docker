```yaml
 
 ▀█▀ █▀▄▀█ █▀▀█ █▀▀▀ █▀▀ █▀▀▄ █▀▀   █▀▀   █▀▀█ █▀▀█ █▀▀▄ ▀▀█▀▀ █▀▀█ ░▀░ █▀▀▄ █▀▀ █▀▀█ █▀▀
 ░█░ █░▀░█ █▄▄█ █░▀█ █▀▀ █░░█ ▀▀█   █▀▀   █░░░ █░░█ █░░█ ░░█░░ █▄▄█ ▀█▀ █░░█ █▀▀ █▄▄▀ ▀▀█
 ▄█▄ ▀░░░▀ ▀░░▀ ▀▀▀▀ ▀▀▀ ▀░░▀ ▀▀▀   ▀▀▀   █▄▄█ ▀▀▀▀ ▀░░▀ ░░▀░░ ▀░░▀ ▀▀▀ ▀░░▀ ▀▀▀ ▀░▀▀ ▀▀▀

# - EXIBE QUAIS CONTAINERS ESTÃO SENDO EXECUTADOS NO MOMENTO, UTILIZANDO A FLAG -A, TEMOS TAMBÉM TODOS OS CONTAINERS JÁ EXECUTADOS NA MÁQUINA
docker ps OU docker container ls

# - RODAR UM CONTAINER E DEIXÁ-LO EXECUTANDO NO TERMINAL
# - DESTA MANEIRA PODEMOS EXECUTAR COMANDOS DENTRO DO CONTAINER
docker run -it <IMAGE>

# - EXECUTA O CONTAINER E A FLAG -D SERVE PARA EXECUTAR EM BACKGROUND
docker run -d <IMAGE>   

# - PARAR O CONTAINER
docker stop <NOME_CONTAINER> || <ID_CONTAINER>

# - FLAG -P INDICA QUE É PRA EXPOR A PORTA 3000 DA MINHA MÁQUINA NA PORTA 80 DO CONTAINER "-d para executar em BackGround"
# - O CONTAINER É ISOLADO, PRECISAMOS EXPOR ELE EM ALGUMA PORTA PARA ACESSARMOS
docker run -p 3000:80 OU docker run -d -p 3000:80

# - REINICIA O CONTAINER
docker start <ID_CONTAINER> OU <NOME_CONTAINER>

# - EXECUTA UM CONTAINER E SETA O SEU NOME
docker run --name <NOME_CONTAINER> <IMAGEM>

# - DELETA O CONTAINER E UTILIZANDO A FLAG -F PARA FORÇAR CASO O CONTEINER ESTIVER EM EXECUÇÃO
docker -rm <ID_CONTAINER> OU <NOME_CONTAINER>

# - FAZ O DOWNLOAD DE UMA IMAGEM
docker pull <IMAGEM>

# - VERIFICA OS LOGS DO CONTAINER
docker logs <ID_CONTAINER> OU <NOME_CONTAINER>

# - QUALQUER COMANDO UTILIZANDO O --HELP PARA TER MAIS INFORMAÇÕES
docker run --help

# - USADO PARA GERAR UMA IMAGEM A PARTIR DO DOCKERFILE, O "." MOSTRA ONDE ESTÁ O CAMINHO DO DOCKERFILE
docker build -t <NOME_DA_IMAGEM_QUE_DESEJAR> .

# - NOMEAR UMA IMAGEM
docker tag <ID_IMAGE> <NOME>:<TAG>

# - RENOMEAR UMA IMAGEM
docker tag <NAME_IMAGE> <NEW_NAME>:<TAG>

# - INICIA O CONTAINER NO MODO INTERATIVO
docker start -it

# - REMOVE UMA IMAGEM, COM A FLAG -F FORÇA A REMOÇÃO
docker rmi <NAME_IMAGE>

# - FAZ A LIMPA DE IMAGENS, CONTAINERS OU CACHES SEM USOS
docker system prune

# - REMOVE O CONTAINER APÓS UTILIZÁ-LO
docker run --rm <IMAGE>

# - COPIA ARQUIVOS DO CONTAINER RODANDO PARA ALGUMA PASTA NA NOSSA MAQUINA
# - UTIL PARA PEGAR ARQUIVOS DE LOGS DA APLICAÇÃO, ETC..
docker cp <NAME_CONTAINER>:/<CAMINHO_DECLARADO_NO_WORKDIR>/<ARQUIVO_QUE_DESEJA_PEGAR> ./<CAMINHO_DE_DESTINO>

# - VERIFICA A EXECUCAÇÃO DO CONTAINER
docker top <CONTAINER>

# - MOSTRA TODAS AS INFORMACOES DO CONTAINER
docker inspect <CONTAINER>

# - MOSTRA O CONSUMO DOS CONTAINER NA NOSSA MAQUINA
docker starts 

# - UTILIZADOS PARA FAZER LOGIN NO DOCKER HUB
docker login
docker login -u="${DOCKER_USERNAME}" -p="${DOCKER_PASSWORD}"

# - UTILIZADO PARA FAZER LOGOUT DO DOCKER HUB
docker logout

# - ENVIA UMA IMAGEM PRO DOCKERHUB
# - OBS: CRIAR A IMAGEM COM O NOME "USER/REPO" PARA FACILITAR O PUSH 
docker push <IMAGE>

# - CASO QUERIA REMOVER TODOS DE UMA VEZ SE NÃO QUISER USAR O PRUNE, 
docker rm -f $(docker ps -aq)
docker rmi -f $(docker images -aq)
docker network rm $(docker network ls -q)
docker volume rm $(docker volume ls -q)



█░░▒█ █▀▀▀█ █░░░ █░▒█ █▀▄▀█ █▀▀▀ █▀▀▀█
▒█▒█░ █░░▒█ █░░░ █░▒█ █▒█▒█ █▀▀▀ ▀▀▀▄▄
░▀▄▀░ █▄▄▄█ █▄▄█ ▀▄▄▀ █░░▒█ █▄▄▄ █▄▄▄█

# - CRIA UM VOLUME DO TIPO ANONYMOUS ONDE O DIRETORIO DE DESTINO TEM QUE COINCIDIR COM O "WORKDIR"
docker run -v /<DIRETORIO_DESTINO>

# - CRIA O CONTAINER E O DIRETORIO ONDE FICARA OS VOLUMES /DATA - ESSE É DO TIPO ANONIMOUS
docker run -d -p 80:80 --name phpmessages_container -v /<DIRETORIO_DESTINO> phpmessages

# - LISTANDO TODOS OS VOLUMES
docker volume ls

# - VOLUME NOMEADO
docker run -v <nome_volume>:/<DIRETORIO_DESTINO>

# - CRIAR VOLUME BIND MOUNT - USADO PARA CRIAR O VOLUME NA NOSSA MÁQUINA
docker run -v <NOME_VOLUME>:/<DIRETORIO_DESTINO>
Ex: docker run -d -p 80:80 --name phpmessages_container -v nossodiretorio:<WORKDIR> <IMAGE>
# - BIND MOUNT TAMBÉM SERVE PARA ATUALIZAR O PROJETO EM TEMPO REAL EM CASO DE COLOCARMOS O PATH PAI DO PROJETO NO PATH PAI DO CONTAINER

# - CRIANDO VOLUME MANUALMENTE
docker volume create <NOME_VOLUME>
# - docker run -d -p 8080:80 --name phpmessages_container --rm -v <NOME_VOLUME_CREADO>:/var/www/html/ phpmessages

# - INSPECIONA O VOLUME
dcoker volume inspect <NAME_VOLUME>

# - REMOVE O VOLUME
docker volume rm <NOME_VOLUME>

# - REMOVE TODOS OS VOLUMES QUE NÃO ESTÃO SENDO UTILIZADOS
docker volume prune

# - VOLUME APENAS DE LEITURA :RO SIGNIFICA READ ONLY
docker run -v volume:/data:RO

# ==============NETWORKS=============
# - LISTA TODAS AS REDES
docker network ls

# - CRIANDO UMA REDE
docker network create <NOME_DA_REDE>

# - CRIA UMA REDE COM UM DRIVER ESPECIFICO
DOCKER NETWORK CREATE -D MACVLAN MEUMACVLAN

# - REMOVE TODAS AS REDES
DOCKER NETWORK PRUNE

# - CONECTAR CONTAINER
DOCKER NETWORK CONNECT <REDE> <CONTAINER>

# - DESCONECTAR CONTAINER
DOCKER NETWORK CONNECT <REDE> <CONTAINER>

# - INSPECIONAR CONTAINER
DOCKER NETWORK INSPECT <NOME>

 █▄░▒█ █▀▀ ▀▀█▀▀ █░░░█ █▀▀█ █▀▀█ █░█ █▀▀
 █▒█▒█ █▀▀ ░░█░░ █▄█▄█ █░░█ █▄▄▀ █▀▄ ▀▀█
 █░░▀█ ▀▀▀ ░░▀░░ ░▀░▀░ ▀▀▀▀ ▀░▀▀ ▀░▀ ▀▀▀

TIPOS DE CONEXÃO
# - EXTERNA: conexão com uma API de um servidor remoto
# - COM O HOST: comunicação com a máquina que está executando o Docker
# - ENTRE CONTAINERS: comunicação que utiliza o driver bridge e permite a comunicação entre dois ou mais containers

TIPOS DE REDES (DRIVERS)
# - BRIDGE: o mais comum e default do Docker, utilizado quando containers precisam se conectar (na maioria das vezes optamos por este driver);
# - HOST: permite a conexão entre um container a máquina que está hosteando o Docker;
# - MACVLAN: permite a conexão a um container por um MAC address;
# - NONE: remove todas conexões de rede de um container;
# - PLUGINS: permite extensões de terceiros para criar outras redes

# - USADO PARA LISTAR AS REDES
docker network ls

# - USADO PARA CRIAR UMA REDE
docker network create <NOME_DA_REDE> # - POR PADRÃO

# - REMOVENDO UMA REDE
docker network rm <NOME_DA_REDE>





 █▀▀▄ █▀▀▀█ █▀▀█ █░▄▀ █▀▀▀ █▀▀█ ░░ █▀▀█ █▀▀▀█ █▀▄▀█ █▀▀█ █▀▀▀█ █▀▀▀█ █▀▀▀
 █░▒█ █░░▒█ █░░░ █▀▄░ █▀▀▀ █▄▄▀ ▀▀ █░░░ █░░▒█ █▒█▒█ █▄▄█ █░░▒█ ▀▀▀▄▄ █▀▀▀
 █▄▄▀ █▄▄▄█ █▄▄█ █░▒█ █▄▄▄ █░▒█ ░░ █▄▄█ █▄▄▄█ █░░▒█ █░░░ █▄▄▄█ █▄▄▄█ █▄▄▄
# - DOCKER-COMPOSE UP

# - COMPOSE EM BACKGROUND
DOCKER-COMPOSE UP -D

# - PARANDO O COMPOSE
DOCKER-COMPOSE DOWN

# - VERIFICA O QUE TEM NO COMPOSE
DOCKER-COMPOSE PS


 █░▄▀ █░░█ █▀▀▄ █▀▀ █▀▀█ █▀▀▄ █▀▀ ▀▀█▀▀ █▀▀ █▀▀
 █▀▄░ █░░█ █▀▀▄ █▀▀ █▄▄▀ █░░█ █▀▀ ░░█░░ █▀▀ ▀▀█
 █░▒█ ░▀▀▀ ▀▀▀░ ▀▀▀ ▀░▀▀ ▀░░▀ ▀▀▀ ░░▀░░ ▀▀▀ ▀▀▀
MINIKUBE START --DRIVER=<DRIVER>
MINIKUBE STOP
MINIKUBE DASHBOARD
MINIKUBE DASHBOAR --URL

# - CRIANDO UM DEPLOYMENT
KUBECTL CREATE  DEPLOYMENT FLASK-DEPLOYMENT --IMAGE=RENANSEREIA/FLAS-KUBERNETES-PROJETO
KUBECTL GET DEPLOYMENTS
KUBECTL DESCRIBE DEPLOYMENTS
KUBECTL GET PODS
KUBECTL DESCRIBE PODS
KUBECTL CONFIG VIEW
KUBECTL EXPOSE DEPLOYMENT <NOME> --TYPE=<TIPO> --PORT=<PORTA>

```
# Exemplos de Dockerfile
#### Exemplo utilizando o tomcat, java 8 e a pasta dist do angular
```yaml
FROM openjdk:8-jre-alpine

# Criação do diretório para o Tomcat
RUN mkdir /opt/tomcat/

WORKDIR /opt/tomcat/

# Copie o arquivo apache-tomcat-8.5.98.tar.gz baixado localmente para o diretório atual no contêiner
COPY apache-tomcat-8.5.98.tar.gz .

# Descompacte o arquivo e exclui o arquivo compactado para economizar memoria
RUN tar xvfz apache-tomcat-8.5.98.tar.gz --strip-components=1 \
    && rm apache-tomcat-8.5.98.tar.gz

# Copie o arquivo .WAR ou a pasta /out/artifacts do intellij para o diretório  webapps do Tomcat onde é startado os aplicativos
# Apos o webapps/ é colocado o path configurado no web.xml da aplicação, assim conseguimos chamar localhost:8080/path da aplicação
COPY /out/artifacts/pccf_agencia_web /opt/tomcat/webapps/pccf_agencia_web/

COPY /dist /opt/tomcat/webapps/static/pccf_agencia_web/

# Exposição da porta 8080
EXPOSE 8080

# Comando para iniciar o Tomcat
CMD ["/opt/tomcat/bin/catalina.sh", "run"]
```
