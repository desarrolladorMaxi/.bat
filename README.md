
# Agenda

Este es un script de Batch (.bat) que permite crear y gestionar una agenda de contactos.

## Características

- Inicio de sesión con usuario "maxi" y contraseña "123". Lo puedes cambiar a tu gusto.
- Menú principal con las siguientes opciones:
  - Crear Contacto
  - Ver Agenda
  - Salir
- Crear y agregar contactos a un archivo de texto oculto llamado "agenda.txt".
- Leer y mostrar los contactos guardados en "agenda.txt".
- Manejo de errores para opciones inválidas.

## Requisitos

- Windows con soporte para archivos .bat

## Instrucciones de uso

1. Guarda el siguiente código en un archivo con extensión `.bat` (por ejemplo, "agenda.bat").

```batch
@echo off
title agenda
color 03
chcp 65001 >nul 2>&1
:inicio
cls
set /p user="usuario: "
if %user%==maxi (goto pass) else (goto error)
:pass
set /p password="contraseña: "
if %password%==123 (goto agenda) else (goto error)
:error
cls
echo.
echo Escribiste mal algo
echo.
goto inicio
:agenda
cls
echo 1- Crear Contacto
echo.
echo 2- Ver Agenda
echo.
echo 3- Salir
echo.
set /p opcion="Opcion de  menu: "
if %opcion%==1 (goto opcion1) 
if %opcion%==2 (goto opcion2)
if %opcion%==3 (goto exit) else (goto error2)
:opcion1
if exist agenda.txt (goto agregar) else (goto crear)
:agregar
cls
echo.
set /p nombre="Nombre: "
set /p dir="Direccion: "
set /p tel="Telefono: "
echo %nombre%    %dir%        %tel%    >> agenda.txt
attrib +h agenda.txt 
goto menu2
:crear
cls
echo.
set /p nombre="Nombre: "
set /p dir="Direccion: "
set /p tel="Telefono: "
echo %nombre%    %dir%        %tel%    >> agenda.txt
attrib +h agenda.txt 
pause>nul
goto menu2
:error2
cls
echo.
echo.
echo ERROR
echo el numero no existe en las opciones
echo.
pause>nul
goto agenda
:opcion2
if exist agenda.txt (goto leer) else (goto noexiste)
:leer
cls
echo.
for /f "tokens=1,2* delims=." %%i in (agenda.txt) do (echo %%i)
pause>nul
set /p opcion3="Volve? y/n: "
if %opcion3%==y (goto agenda) else (goto exit)
:noexiste
cls
echo.
echo El documento no existe
echo.
echo que le va a hacer
pause>nul
goto agenda
:menu2
set /p opcion2="salir y/n: "
if %opcion2%==y (goto agenda)
if %opcion2%==n (goto opcion1) else ( goto exit)
:exit
cls
exit
```

2. Guarda el archivo en un directorio de tu elección.
3. Ejecuta el archivo .bat haciendo doble clic o desde la línea de comandos.
4. Inicia sesión con el usuario "maxi" y la contraseña "123".
5. Navega por las opciones del menú para crear, agregar y ver los contactos.

## Consideraciones

- El archivo "agenda.txt" se crea en el mismo directorio que el script .bat y se oculta automáticamente.
- Asegúrate de tener permisos de escritura en el directorio donde se ejecuta el script.
- Este script es una solución sencilla y no utiliza una base de datos real. 

¡Disfruta de tu nueva agenda simple por consola!
