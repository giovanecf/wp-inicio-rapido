## WP Inicio Rápido

Repo para inicio rápido do WordPress com o Docker Compose e MySQL

## Uso

Se não tiver docker e docker-compose, utilize [este script](https://github.com/suportefafar/docker_installs).
Uma vez já instalado, execute:

```
git clone https://github.com/suportefafar/wp-inicio-rapido.git
cd wp-inicio-rapido/
docker compose up -d
```

## Troubleshooting

Caso tenha problema de premissão ao executar o comando a cima, utiliz-o com **sudo**:

```
sudo docker compose up -d
```

Ou dê premissão ao seu usuário para utilizar o docker, colocando-o no grupo _docker_:

```
sudo usermod -aG docker ${USER}
```

E então, para aplicar a mudança insira o seguinte comando:

```
su - ${USER}
```

Se não funcionar, reinicie ou faça logout.

Para verificar se foi feito com sucesso, insira no terminal:

```
groups
```

Esse comando deve retornar a lista de grupos que o usuário atual se encontra.
O grupo _docker_ deve ser um deles.
