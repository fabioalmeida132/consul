
# Inicializar novo consul server

Criar os consul.d
```
mkdir /etc/consul.d
```
Criar o diretório consul

```
mkdir /var/lib/consul
```

Colocar o ip da maquina no bind e alterar o node.
```
consul agent -server -bootstrap-expect=3 -node=consulserver01 -bind=172.21.0.3 -data-dir=/var/lib/consul -config-dir=/etc/consul.d
```

Rodar o comando consul join, passando o ip do outro consul
```
consul join 172.21.0.3
```

# Inicializar novo consul client
Criar o diretório consul
```
mkdir /var/lib/consul
```

Colocar o ip da maquina no bind, alterar o node e passar um ip de um consul.
```
consul agent -bind=172.21.0.5 -data-dir=/var/lib/consul -config-dir=/etc/consul.d -retry-join=172.21.0.3
```

Subir usando o config dos server
```
consul agent -config-dir=/etc/consul.d
```

# Criando nginx no client

Criar default directory
```
mkdir /usr/share/nginx/html -p
```
