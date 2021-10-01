# fazendo build do dockerfile
docker build -t wallacemachado/nginx-com-vim:latest .

# -t =  nome da tag (nome do meu github / nome do container : versão)
# . = pq o dockerfile está na pasta que estpu rodando o comando

# iniciar o bash
docker run -it wallacemachado/nginx-com-vim bash

# NOME DA IMAGEM A SER BAIXADA : VERSÃO
FROM nginx:latest

# Diretório que será criado no container
WORKDIR /app

# comando que serão rodados no container
RUN apt-get update &&\
    apt-get install vim -y

# copiando o conteudo da pasta local html para a pasta dentro do container
COPY html/ /usr/share/nginx/html

## build
docker build -t wallacemachado/nginx-com-vim:latest .
## run bash
docker run -it wallacemachado/nginx-com-vim bash
## verificar se o arquivo html foi copiado
root@2ece86e0636c:/app# cd /usr/share/nginx/html/
root@2ece86e0636c:/usr/share/nginx/html# ls
50x.html  index.html
root@2ece86e0636c:/usr/share/nginx/html# cat index.html
<h1>Wallace Machado</h1>root@527808e1df7b:/usr/share/nginx/html#
