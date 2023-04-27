# Código HTML


1) Fazer a criação da página HTML. Pode ser um código básico, esse é o exemplo de corpo do HTML que deve estar contido na página:

```
<!DOCTYPE html>
<html lang="pt-br">
  <head>
    <title>Título da página</title>
    <meta charset="utf-8">
  </head>
  <body>
    "hello World"
  </body>
</html>

```



2) Realizar commit e push da página para o github e alocar ela dentro de um repositório específico.



# Login no Docker

1) Abra o prompt de comando da sua máquina e digite "  ssh usuario@200.17.141-82 -p 3333  "

2) Insira a senha (será enviada por email, por questões de confidencialidade)



## Inserindo a página HTML no Docker

1) Copie o link do repositório especificado do gitHub, onde a página está alocada. Exemplo:

```
https://github.com/arielabade/Network-Labs.git

```


2) Clone o link do repositório para dentro do docker com o comando

```
git clone https://github.com/arielabade/Network-Labs.git

```

A partir desse momento, você possui um diretório criado dentro do Docker para manipular os arquivos contidos neles, e consequentementes, hospedá-los no servidor do docker.

Para acessar o diretório no qual o arquivo está localizado, basta usar o comando:

```
cd Network-Labs

```


3) Crie uma imagem no Dockerfile

Por mais que o arquivo já esteja armazenado no contêiner do Docker, ele não está acessível ao usuário.

Para que ele fique acessível ao usuário, é necessário que você crie um _Dockerfile_

_Dockerfile_ é um arquivo de imagem do Docker que permite pegar as informações do servidor, a partir do path do diretório, definir as portas de acesso na sua máquina local, e definir a porta de destino no Docker através de alguns comandos.

Primeiro, você deve executar, no prompt do Docker, o comando:

```
nano Dockerfile

```

Depois disso, você deve implementar o seguinte código

```
FROM node:latest
WORKDIR /app
COPY .  .
EXPOSE 3000
CMD ["npm", "start"]

```


A partir desse momento, você possui uma forma de acesso as informações necessárias.



4) Acessando a imagem no dockerfile

Para acessar o servidor, e consequentemente, deixar a imagem online, o comanndo a ser executado é:

```
 docker run -p 6000:3000 -d my-imagem .

```

Onde 6000 é a porta externa, 3000 é a porta externa e "my-imagem ." é o arquivo de imagem a ser executado.

Caso você obtenha uma mensagem como 

```
arielzz@cedro:~/Network-Labs$  docker run -p 6000:3000 -d my-imagem .
83b164108ceaab58e618f478ba7228a4c0d3299428ebb550ab4a419c609b51ab

```

Sígnifica que o conteiner está online

5) Acessando o localhost

Para acessar o localhost e mostrar a página, basta abrir o navegador e digitar

```

http://localhost:6000

```

Caso tudo tenha sido feito da forma correta, a página deverá ser exibida normalmente, em formato do escopo HTML


