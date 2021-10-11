---
title: Arrancar, parar y ver estado de procesos en GNU/Linux
published: true
---

### [](#header-1)Arrancar, parar y ver estado de procesos en GNU/Linux

![](https://raw.githubusercontent.com/LLamasDev/hacker-blog/master/assets/git-logo.png)


### [](#header-3)Posibles errores al ejecutar el script

Convierte los saltos de línea de formato DOS a UNIX.
**sed** es un potente editor de flujo de texto. Podemos hacer insertar, borrar, buscar y reemplazar.
**-i** para editar archivos en el lugar en lugar de mostar el resultado.
**-e** usa los comandos de edición pasados al sed.
```
sed -i -e 's/\r$//' ALGO.sh
```


### [](#header-3)Ver el estado

Ver si esta corriendo el proceso:
```
#!/bin/bash

primer_ag=$1 # Primer argumento

function funcion() {
  { # try
    proceso=$(ps -ef | grep -i $primer_ag.py | grep -v "SCREEN\|grep" | wc -l)

    if [ $proceso -eq 1 ]; then # Si el contador del proceso es 1 significa que esta corriendo
      return 'El proceso esta corriendo'
    else # El proceso no es 1 significa que no esta corriendo, ya que solo puede estar arrancado una vez
      return 'El proceso no estaba corriendo'
    fi
      return $index
  } || { # catch
    return 'El proceso esta en estado anomalo'
  }
}

funcion
```

Para tomar el primer argumento que se le pase al script usamos:
```
primer_ag=$1
```

Con el **ps** vemos los procesos corriendo:
```
ps -ef
```

Con el **grep** filtramos por la palabra pasada, lo que buscamos es un archivo python que se esta ejecutando por lo que añadimos .py:
**-i** no hace caso de si las letras son mayúsculas o minúsculas ni en el patrón ni en los ficheros de entrada.
```
grep -i $primer_ag.py
```

La idea es contar cuantos hay y si hacemos un grep aparecerán en el **ps**, ejemplo:
```
ps -ef | grep -i python
grep --color=auto -i python
```

Por lo cual en el filtro mostraremos todo menos lo que queremos, en nuestro caso no queremos ver nada de ventanas (**screen**) ni el **grep** y lo añadimos separándolos con **\|**, también se puede usar **|**, pero si se añade **-E** al **grep**:
-v filtra por todo menos por lo indicado a continuación.
```
grep -v "SCREEN\|grep"
```

Y para contarlos usaremos **wc**:
**-l** cuenta cuantas líneas aparecerán.
```
wc -l
```
