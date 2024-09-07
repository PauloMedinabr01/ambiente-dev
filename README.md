# Ambiente de desenvolvimento PHP, Laravel, MySQL e Nginx.

<img src="	https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white">
<img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white">
<img src="	https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white">

## Requisitos

### Para rodar o projeto é necessário ter instalado:

Docker e Docker Compose para rodar o ambiente de desenvolvimento.

Git para clonar o repositório do projeto.

## Instalação do ambiente de desenvolvimento

Clone o repositório do projeto:

```bash
git clone git@github.com:PauloMedinabr01/app-laravel-docker.git
```

Aqui você encontrara um projeto Laravel usando a versão 11.9 e PHP 8.3, com Starter Kit Blade, MySQL e Nginx, um
Dockerfile para o ambiente de
desenvolvimento, um docker-compose.yml para subir o ambiente de desenvolvimento e um arquivo nginx.conf para configurar
o servidor Nginx.
Configure o arquivo .env com seus dados de conexão com o banco de dados.

Entre na pasta do projeto:

```bash
cd app
```

Criar o container da aplicação. Também pode ser usado para reconstruir o container.

```bash
docker compose up -d --build
```

Os containers criados são:

- application: container com o Laravel e Starter Kit Blade/Alpine.
- mysql: container com o MySQL.
- nginx: container com o Nginx.

Para parar o ambiente de desenvolvimento, execute o comando:

```bash
docker compose down
```

Para acessar o container application, execute o comando:

```bash
docker exec -it application bash
```

No terminal do container application, execute o comando abaixo para rodar as migrations:

```bash
php artisan migrate
```

Popule a tabela users com 50 registros de usuarios teste:

```bash
php artisan db:seed
```

Ainda no terminal do container, rode o comando para garantir as permissões de arquivos nas pastas storage e
bootstrap/cache:

```bash
chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache && \
chmod -R 775 /var/www/storage /var/www/bootstrap/cache
```

Para sair do container application, digite:

```bash
exit
```

Se precisar acessar o container mysql, execute o comando:

```bash
docker exec -it mysql bash
```

Digite o comando abaixo para acessar o MySQL:

```bash
mysql -u root -p
```

Verifique se o banco de dados foi criado:

```bash
show databases;
```

Para sair do MySQL, digite:

```bash
exit
```

Para sair do container mysql, digite:

```bash
exit
```

## Acesso à aplicação

Acesse a aplicação em http://localhost:8084

Teste a rota users pelo navegador ou postman e confira se a aplicação está funcionando.
Existem duas rotas disponíveis:

Rota de teste de ping:

```bash
http://localhost:8084/api/v1/ping
```

Rota de teste de usuários:

```bash
http://localhost:8084/api/v1/users
```

## Teste o projeto em seu novo ambiente de desenvolvimento. Crie algo incrível!

### Autor: Paulo Coelho

- [Dev Paulo Coelho](https://devpaulocoelho.com/)
- [Credly](https://www.credly.com/users/paulo-henrique-medina-coelho)
- [Microsoft Learn](https://learn.microsoft.com/pt-br/users/paulohenriquemedinacoelho/transcript/d9w2s0gyqmz2z87?tab=credentials-tab)

### Contato:

[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:paulomedinabr01@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/paulohcoelho/)

## Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE para mais detalhes.
