---
title: "Instalar Node.js en Ubuntu"
date: 2022-04-25
description: 'Una guía de como instalar Node.js en Ubuntu y derivadas mediante NVM'
---
![image](https://user-images.githubusercontent.com/94416443/165021726-35cc16e5-77ca-40cd-be61-dbb72df08449.png)

## Introducción 
En este post hablaré sobre como instalar node.js en Ubuntu y sus distribuciones derivadas (Linux Mint, PopOS, Kubuntu, ZorinOS, etc) mediante nvm, que es la mejor opción que yo considero que es para instalar node.

Node.js es un tiempo de ejecución de JavaScript para programar del lado del servidor. Permite a los desarrolladores crear funcionalidades de backend escalables usando JavaScript, un lenguaje que muchos ya conocen del desarrollo web basado en navegadores.

`NVM` (node version manager) es un gestor de versiones para node.js, esta diseñado para ser invocado por consola. nvm funciona en cualquier shell compatible con POSIX (`sh`, `dash`, `ksh`, `zsh`, `bash`), en estas plataformas: `unix`, `macOS`, y `windows WSL`. 

## Requisitos previos
Para hacer una instalación limpia de node en nuestro sistema operativo, vamos a verificar que no tengamos instalado node, si es que anteriormente no has instalado node, esto se hace como verificación. ya que, a veces, nuestro sistema operativo puede incluir una version de node, pero, estas versiones suelen ser atrasadas a las que actualmente están en activo, iremos a nuestra shell y ejecutaremos los siguientes comandos, por separado:

```
which node
which npm
```

Si alguno de los dos comandos arroja una ruta, similar a `/home/user/.nvm/versions/node/v16.14.2/bin/node` quiere decir que tenemos instalada una version de node, para desinstalarla, ejecutaremos los siguientes comandos:

```
sudo apt remove nodejs 
```

Con el siguiente comando se eliminarán el paquete y los archivos de configuración:

```
sudo apt purge nodejs 
```

Como paso final, puede eliminar cualquier paquete no utilizado que se haya instalado de forma automática con el paquete eliminado:

``` 
sudo apt autoremove 
```

## Instalación de Node.js mediante NVM
Una de la ventajas y por lo cual considero que nvm es la mejor opción para instalar node, es que no funciona a nivel del sistema operativo, nvm funciona a nivel de un directorio independiente dentro de su directorio de usuario. Quiere decir que se pueden instalar varias versiones de node sin que afecte a todo el sistema operativo.

Para instalar nvm, tenemos que ejecutar el script de instalación, usando el comando `curl` o `wget`, ten en cuenta que el numero de versión `v0.39.1` que se viene en los comandos puede diferir dependiendo de cuando estés leyendo este post:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Cualquiera de los dos comandos descarga y ejecuta el script, este clona el repositorio de nvm en `~/.nvm`.

Para verificar que ya tengamos instalado `nvm`, escribimos el comando:

```sh
nvm -v
```

Este comando nos debería regresar la versión de `nvm` que tenemos instalada, por ejemplo `0.39.1`.

Ahora, con el siguiente comando, obtendremos información sobre las versiones de node disponibles para instalar.

```sh
nvm ls-remote
```

¡Es una lista muy larga! Para instalar una versión específica de node, ejecutamos el comando:

```sh
nvm install version
```
Sustituimos `version` por la versión a instalar, por ejemplo `16.14.2`, `14.19.1`, etc.

Para instalar la última versión de node, ejecutamos el comando:

```sh
nvm install node
```

Para ver las distintas versiones de node instaladas, ejecutamos el comando:

```sh
nvm list
```

Nos regresara una lista similar a esta:

```sh
->     v16.14.2
default -> v16.14.2
iojs -> N/A (default)
unstable -> N/A (default)
node -> stable (-> v16.14.2) (default)
stable -> 16.14 (-> v16.14.2) (default)
. . .
```

La primera linea, representa la version de node que tenemos activa en este momento, seguida de algunos alias asignados y las versiones a las que apuntan, cuando una alias apunta a `N/A` quiere decir que no hay una version de node asignada a ese alias.

Para cambiar entre versiones instaladas de node, ejecutamos el comando: 

```sh
nvm use version
```

Sustituimos `version` por la versión a usar, por ejemplo `16.14.2`, `14.19.1`, etc.

Una forma de verificar que cambiamos de version de node, es mediante:

```
node -v
```
Este comando nos debería regresar la versión de `node` que tenemos instalada, por ejemplo `14.19.1`

## Solución a posibles problemas de instalación

Si al ejecutar `nvm -v` obtienes `nvm: command not found`, cierra tu terminal actual, vuelve a abrirla e intenta ejecutar el comando otra vez.

Otra opción sería ejecutar alguno de los siguiente comandos, dependiendo del tipo de shell que estés usando:

*bash*: 
```
source ~/.bashrc
```

*zsh*:

```
source ~/.zshrc
```

Como ultima alternativa, ingresa a la configuración de tu shell mediante alguno de los siguientes comandos:

*bash*: 
```
nano ~/.bashrc
```

*zsh*:

```
nano ~/.zshrc
```

Al final de tu archivo copia y pega las siguientes lineas de código

```sh
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

## 📕 Referencias
1. [Repositorio oficial de NVM](https://github.com/nvm-sh/nvm)

