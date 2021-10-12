---
title: Caracteres de protección en Bash
published: true
---

### [](#header-1)Caracteres de protección en Bash

![](../assets/bash-logo.png)


### [](#header-3)Comillas dobles "

La protección es simple, eliminan el significado de todos los caracteres especiales del shell excepto <mark>$</mark>, <mark>$()</mark>, <mark>\\</mark> y a sí mismas.
```
echo "Hola, estoy en $(pwd)"
Hola, estoy en /
```

### [](#header-3)Comillas simples '

Las comillas simples eliminan el significado a todos los caracteres especiales del shell.
```
echo 'Hola, estoy en $(pwd)'
Hola, estoy en $(pwd)
```

### [](#header-3)El carácter \

La contrabarra elimina el significado especial del carácter que le sigue.
```
echo "Hola, estoy en $(pwd)"
Hola, estoy en /

echo "Hola, estoy en \$(pwd)"
Hola, estoy en $(pwd)


echo '$HOME \$HOME \\\\'
$HOME \$HOME \\\\

echo "$HOME \$HOME \\\\"
/root $HOME \\
```
