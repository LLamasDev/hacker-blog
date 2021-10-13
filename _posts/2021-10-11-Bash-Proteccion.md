---
title: Caracteres de protección en Bash
published: true
---

![](../assets/bash-logo.png)

### [](#header-1)Comillas dobles "

La protección es simple, eliminan el significado de todos los caracteres especiales del shell excepto <mark>$</mark>, <mark>$()</mark>, <mark>\\</mark> y a sí mismas.
```
echo "Hola, estoy en $(pwd)"
Hola, estoy en /
```

### [](#header-1)Comillas simples '

Las comillas simples eliminan el significado a todos los caracteres especiales del shell.
```
echo 'Hola, estoy en $(pwd)'
Hola, estoy en $(pwd)
```

### [](#header-1)El carácter \

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
