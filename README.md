# PHP + VAGRANT + HOMESTEAD + LARAVEL

Primero, para obtener la estructura de **Laravel** utilizaremos [composer](https://getcomposer.org/) 

```sh
$ composer create-project laravel/laravel APIRestful 5.4.* --prefer-source
```
Donde :
  - *Composer:* manejador de dependencias de PHP
  - *create-project:* comando paera crear un nuevo proyecto
  - *laravel/laravel:* instala Laravel
  - *APIRestful:* 5.4.* nombre de la carpeta y la versión que queremos descargar

Los ficheros descargados estarán en la ruta de nuestro disco duro. Ej:
```sh
$ cd ./APIRestful
```
Para comprobar que la instalación ha ido bien arrancaremos un servidor *php artisan*
```sh
$ php artisan serve
```
Desde el navegador, escribimos la siguiente ruta. Podemos ver la página de bienvenida de Laravel
```sh
127.0.0.1.8000
```
Para instalar [homestead](https://laravel.com/docs/5.4/homestead) desde composer
```sh
$ composer require laravel/homestead
```
Una vez instalado Homestead como dependencia del proyecto, tenemos que configurar la IP, memoria, cpus, sites, ect etc. Para crear el fichero de configuracion homestead.yaml  utilizaremos el siguiente comando (Windows)
```sh
$ vendor\\bin\\homestead make
```
Ahora sólo tenemos que cambiar los parámetros según el uso que le vayamos a dar
```sh
ip: 192.168.10.10
memory: 1024
cpus: 1
provider: virtualbox
authorize: ~/.ssh/id_rsa.pub
keys:
    - ~/.ssh/id_rsa
folders:
    -
        map: 'C:\APIRestful'
        to: /home/vagrant/apirestful
sites:
    -
        map: apirestful.dev
        to: /home/vagrant/apirestful/public
databases:
    - homestead
name: apirestful
hostname: apirestful
```
Por último, sólo nos falta configurar eL host de Windows con la dirección IP de host virtual. Para ello tenemos que buscar el fichero en la siguiente ruta y agregar esta última línea al final
```sh
$ C:\Windows\System32\drivers\etc\hosts
192.168.10.10         apirestful.dev
```
Para iniciar la máquina virtual por primera vez
```sh
$ vagrant up
```
Para comprobar que todo haya ido bien
```sh
$ vagrant status
```

para establecer una conexión con la máquina virtual
```sh
$ vagrant ssh
```

*...to be continued...*
