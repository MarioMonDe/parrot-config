# parrot-config
Parrot Security Configuration

## Instalación y configuración de Bspwm y Sxhkd

En resumen, primeramente ejecutaremos el siguiente comando:

```bash
apt install build-essential git vim libxcb1-dev libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libxcb-xkb-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev
```

Posteriormente, aplicaremos una actualización del sistema con el comando `apt update`. Acto seguido, tenéis que dirigiros a la carpeta de descargas de vuestro equipo y descargar los proyectos 'bswpm' y 'sxhkd' con los siguientes comandos:

```bash
git clone https://github.com/baskerville/bspwm.git
git clone https://github.com/baskerville/sxhkd.git
```

Para instalar cada uno de estos, lo que debéis hacer es meteros en ambos directorios por separado y ejecutar los comandos `make` y `sudo make install`.

A continuación tenéis el enlace al archivo de configuración [bspwm_resize](https://hack4u.io/files/bspwm_resize.txt) que usamos al final de esta clase:

```bash
#!/usr/bin/env dash

if bspc query -N -n focused.floating > /dev/null; then
	step=20
else
	step=100
fi

case "$1" in
	west) dir=right; falldir=left; x="-$step"; y=0;;
	east) dir=right; falldir=left; x="$step"; y=0;;
	north) dir=top; falldir=bottom; x=0; y="-$step";;
	south) dir=top; falldir=bottom; x=0; y="$step";;
esac

bspc node -z "$dir" "$x" "$y" || bspc node -z "$falldir" "$x" "$y"
```