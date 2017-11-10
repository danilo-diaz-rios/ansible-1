# Cofiguración de Ansible

## Despliegue de plataforma Moodle

Se instalaran  y configuraran estos  3 servicios : 
<ul>
  <li>Apache</li>
  <li>MySQL</li>
  <li>Redis</li>
</ul>

<h3>Primer paso, instalación de los servidores web y de archivos.</h3>

### -Intalamos Munin en los 3 servidores

Usamos el siguiente comando: 

ansible-playbook -i ../hosts inicial.yml

### -luego instalamos el servidor web en el server01

Usamos el siguiente comando: 

ansible-playbook -i ../hosts webserver.yml

<h3>Segundo paso, instalación del servidor Mysql.</h3>

### -Intalamos el servidor mysql en el server02

Usamos el siguiente comando: 

ansible-playbook -i ../hosts sqlserver.yml

Para verificar si la instalacion fue correcta entramos al servidor : 

Usamos el siguiente comando: 

ssh root@server02 -p 2222 -i ../key.private

y ejecutamos : 

mysql -h localhost -u root -p

y deberia salir esto :

      mysql> <aqui iria los comandos>

<h3>Tercer paso, instalación de Redis.</h3>

### -Intalamos Redis en el server03

Usamos el siguiente comando: 

ansible-playbook -i ../hosts redis.yml

Para verificar si la instalacion fue correcta una opcion seria esta: 

Entrar a nuestro servidor y ejecutar el comando redis-server y tendremos un output asi :

1) ssh root@server03 -p 2223 -i ../key.private
2) redis-server

       $ redis-server
       [28550] 01 Aug 19:29:28 # Warning: no config file specified, using the default config. In order to specify a config file use            'redis-server /path/to/redis.conf'
       [28550] 01 Aug 19:29:28 * Server started, Redis version 2.2.12
       [28550] 01 Aug 19:29:28 * The server is now ready to accept connections on port 6379
       ... more logs ...

<h2>Instalacion de Moodle</h2>

### -Intalamos Moodle en el server02

Usamos el siguiente comando: 

ansible-playbook -i ../hosts moodle.yml










