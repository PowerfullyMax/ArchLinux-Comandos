# ArchLinux-Comandos
Comandos que utilizo frecuentemente en Arch Linux

El primero y creo que el mas importante para mantener el sistema actualizado es:
```
sudo pacman -Syu
```


# ¿Que hace exactamente?

La idea es que `sudo` se usa para obtener permisos de administrador sin necesidad de estar logueado como administrador o root (de hecho, muchas veces en los comandos veras que no aparece un `sudo` sino un `#`. Esto quiere decir que el comando se tiene que ejecutar con privilegios de administrador para que funcione). Esto sirve porque se considera mala practica usar el usuario root, ya que tiene la capacidad de dañar el sistema si se usa de manera incorrecta, por eso es mejor usar `sudo`sobre el usuario root salvo unas pocas excepciones.

Despues, `pacman` se refiere al gestor de paquetes (o "package manager" en inglés), el cual es un conjunto de herramientas que automatizan los procesos de instalación, actualización, configuración y eliminación de los programas que usamos (tambien llamados "paquetes de software). `pacman` tiene un monton de parametros pero por ahora nos quedamos con que es el metodo de instalar, actualizar, configurar y/o eliminar software.


# Parametros
```
-Syu
```

Y por ultimo estarian los "parametros", los cuales sirven (de forma muy simplificada) para darle instrucciones al gestor de paquetes (en este caso `pacman`) de lo que exactamente debe hacer. Casi siempre empiezan poniendo un "-" y luego las letras ligadas a cada instruccion.

`-S` se utiliza para que `pacman` sincronize la lista de paquetes con la base de datos del propio `pacman`. Tambien se puede utilizar para instalar paquetes, por ejemplo:
```
sudo pacman -S nombre-del-paquete
```

`-Sy` es para que refresque la cache local del sistema. Tecnicamente con esto ya podrias actualizar el sistema, pero se considera una muy mala practica porque puede haber problemas con las dependencias de los paquetes, las cuales pueden estar en una version mas buena que el propio paquete instalado en el sistema, por eso siempre se usa con la `u` al final.

`-Syu` y llegamos a la parte final. Con los tres parametros, `pacman` sincroniza la base de datos, refresca la cache local y con la `u` termina de actualizar todo el sistema excepto los paquetes instalados de forma local.

# Consejos generales

Arch es una distribución de Liberación Continua ("Rolling Release" en inglés), esto quiere decir que los paquetes reciben actualizaciones mas seguido que en otras distribuciones como Debian por ejemplo. Teniendo esto en cuenta, se recomienda actualizar Arch alrededor de una vez por semana, asi no lo actualizaras tan pronto como para tener un nuevo software con bugs pero tampoco tener paquetes no actualizados que puedan romper el sistema si lo estuvieron por mucho tiempo.

Vuelvo a reiterar que usar `-Sy` sobre `-Syu` no es recomendable. Aunque lo uses una vez y no pase nada, en algun momento un paquete va a causar problemas por no estar actualizado del todo.

Cancelar actualizaciones del sistema mientras se actualiza el kernel puede romper el sistema. No es irreparable el daño, pero dejara tu compututadora inutilizable a no ser que de algun modo puedas bootear a una ISO de Arch Linux.
