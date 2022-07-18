# nginx-on-docker
Cria um proxy para um dominio unico expondo duas aplicações separadas ou para dois subdominios

obs: as apps estão rodando em portas separadas
- na portal 8080 uma app X com tecnologia diferente da segunda app
- na portal 3000 uma app Y com React

As duas apps serão expostas por padrao:<br>
```http://meusubdominio.meudominio.local```
Onde a segunda app está disponivel em<br>
```http://meusubdominio.meudominio.local/v2```

## Pré requisito

- Docker
- docker-compose

## como funciona

adicionar no host da maquina o apontamento para o dominio/subdominio

```
127.0.0.1   meusubdominio.meudominio.local
127.0.0.1   meusubdominio1.meudominio.local \\ necessario apenas em caso de 2 subdmonios
```

No mac:
/etc/hosts

No linux:
/etc/hosts

No windows:
c:\Windows\System32\drivers\etc\hosts

Rodar

```
docker-compose up
```

isso irá baixar a imagem do nginx e inserir nginx.conf

Esse arquivo expoe um unico subdominio na porta 80 onde temos duas apps
onde a segunda está disponivel no V2

Obs: caso seja react a app é necessario substituir o BrowserRoute por Hasroute uma vez que o roteado sobre problemas para identificar o root no BrowserRoute


Caso queria dois subdominios diferentes basta usar o nginx.multisubdomain.conf

então o resultado será

As duas apps serão expostas por padrao:<br>
```http://meusubdominio.meudominio.local```
Onde a segunda app está disponivel em<br>
```http://meusubdominio1.meudominio.local```