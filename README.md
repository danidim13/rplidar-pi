# README

## Detectar el sensor RPLidar

Para poder usar el sensor RPLidar es necesario determinar a si el dispositivo fue detectado por el Sistema Operativo y que nombre se le asigno. El dispositivo que andamos buscando es un "CP210x UART Bridge" o similar. Para ver si el SO lo reconocio al conectarlo podemos simplemente listar los dispositivos USB

```bash
~/ $ lsusb
...
Bus 001 Device 006: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light
...
~/ $
```

Luego debemos saber el nombre del archivo con el que se monto el dispositivo, usualmente este es `/dev/ttyUSB0` pero esto puede variar. Tambien hay varias formas de determinarlo, una es buscarlo en los mensajes del sistema:

```bash
~/ $ dmesg | grep -i "CP210"
...
[ 1495.157622] usb 1-1.4: cp210x converter now attached to ttyUSB0
...
~/ $
```

Finalmente podemos accesar al dispositivo buscandolo en el directorio `/dev/` 

## Obtener y compilar el SDK

El SDK se encuentra disponible en la [pagina de SLAMTEC](http://www.slamtec.com/en/support). El mismo soporta Windows, OSX y Linux. Para compilar la libreria y los programas de ejemplo basta usar el makefile que viene includo.

La documentacion del SDK se puede obtener en la misma pagina.

### Compilar y enlazar con otros programas

El SDK del RPLidar usa C/C++, para poder usarlo en nuestros programas ocupamos incluir los headers en nuestro codigo fuente y ademas enlazar la libreria al compilar.

