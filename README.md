## - exibe quais containers estão sendo executados no momento, utilizando a flag -a, temos também todos os containers já executados na máquina;
docker ps ou docker container ls;

## - rodar um container e deixá-lo executando no terminal;
docker run -it mysql

## - para o container
docker stop <nome_container> || <id_container>

## - executa o container e a flag -d serve para executar em background
docker run -d <nome_coitaner>    

## - flag -p indica que é pra expor a porta 3000 da minha máquina na porta 80 do container
docker -p 3000:80

## - reinicia o container
docker start <id_container> ou <nome_container>

## - executa um container e seta o seu nome
docker run --name <nome_container> <imagem>

## - remove o container e utilizando a flag -f para forçar caso o conteiner estiver sendo usado
docker -rm <id_container> || <nome_container>

## - faz o download da imagem
docker pull <name_image>

## - qualquer comando utilizando o --help para ter mais informações
docker run --help

## - muda o nome da imagem e a tag
docker tag <id_image> <nome>:<tag>

## - inicia o container no modo iterativo
docker start -i

## - emove uma imagem
docker rmi

## - az a limpa de imagens,containers ou caches sem usos
docker system prune

## - opia do container para a imagem ou path especifico
docker cp

## - verifica a execucação do container
docker top <container>

#mostra todas as informaçoes do container
docker inspect <container>

## - docker login

## - docker logout

## - nvia uma imagem pro dockerhub
docker push

# ==============VOLUMES=============
## - Cria o container e o diretorio onde ficara os volumes /data - esse é do tipo anonimous
Ex: docker run -d -p 80:80 --name phpmessages_container  -v /data phpmessages

## - criar volume Bind mount
docker run -v nomedovolume:/data
Ex: docker run -d -p 80:80 --name phpmessages_container  -v nossoDiretorio:<WORKDIR> phpmessages

## - Criando volume manualmente
docker volume create <volumeteste>

## - Listando todos os volumes
docker volume ls

## - inspeciona o volume
docker volume inspect <name_volume>

## - emove o volume
docker volume rm <nome>

## - remove todos os volumes que não estão sendo utilizado
docker volume prune

## - volume apenas de leitura :ro significa read only
docker run -v volume:/data:ro

# ==============NETWORKS=============
## - LISTA TODAS AS REDES
docker network ls

## - CRIANDO UMA REDE
docker network create <nome_da_rede>

## - cria uma rede com um driver especifico
docker network create -d macvlan meumacvlan

## - REMOVE TODAS AS REDES
docker network prune

## - CONECTAR CONTAINER
docker network connect <rede> <container>

## - DESCONECTAR CONTAINER
docker network connect <rede> <container>

## - INSPECIONAR CONTAINER
docker network inspect <nome>

# =======================DOCKER-COMPOSE==========================
## - docker-compose up

## - COMPOSE EM BACKGROUND
docker-compose up -d

## - PARANDO O COMPOSE
docker-compose down

## - VERIFICA O QUE TEM NO COMPOSE
docker-compose ps

# =================KUBERNETES=================
minikube start --driver=<DRIVER>
minikube stop
minikube dashboard
minikube dashboar --url

## - criando um deployment
kubectl create  deployment flask-deployment --image=renansereia/flas-kubernetes-projeto
kubectl get deployments
kubectl describe deployments
kubectl get pods
kubectl describe pods
kubectl config view
kubectl expose deployment <NOME> --type=<TIPO> --port=<PORTA>
