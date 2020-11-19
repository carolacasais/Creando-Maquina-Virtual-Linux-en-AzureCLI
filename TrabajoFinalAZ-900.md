# Trabajo Final AZ_900 

## 1 - Conectarse desde Azure Cli A Azure
    az login
Esto nos abirá una pestaña en la que verificaremos nuestra cuenta

![imagen](img1.png)

![imagen](img2.png)

## 2 - Crear un grupo de recursos
    az group create -l EastUS -n myRGCLI 
Y el grupo creada se mostrará así

![imagen](img3.png)

## 3 - Crear una máquina virtual Linux
    az vm create ^
    --name myVMCLI ^
    --resource-group myRGCLI ^
    --image UbuntuLTS ^
    --location EastUS ^
    --admin-username azureuser ^
    --admin-password Pa$$w0rd1234 ^
    --no-wait

A continuación vemos como se ha creado:

![imagen](img4.png)

## 4 - Averiguar la dirección IP

Podemos averiguar la dirección IP de la máquina virtual recién creada o bien través del siguiente comando:

    az vm list-ip-addresses --resource-group myRGCLI --name myVMCLI

![imagen](img5.png)

O en el portal de Azure:

![imagen](img6.png)

## 5 - Conectarse a la máquina Virtual de Linux

    ssh azureuser@23.96.31.14

Seleccionamos "yes" en la creación del certificado SSH y escribimos la contraseña.

![imagen](img8.png)

## 6 - Actualizar en Linux

    sudo apt-get update

![imagen](img9.png)

## 7 - Hacer el upgrade

    sudo apt upgrade

Y le damos a "Y"

![imagen](img10.png)

## 8 - Instalar un servidor web

    sudo apt install -y apache2 apache2-utils

![imagen](img11.png)

## 9 - Vemos el estatus de Apache

    systemctl status apache2

![imagen](img12.png)

## 10 - Ponemos un mensaje en nuestra página de Apache

    cd /var/www/html

![imagen](img13.png)

## 11 - Poner una nota en la página inde.html

    sudo vi index.html <ENTER>
    <ESC> : 198 <ENTER> // irme a la linea 198 que es donde esta el mensaje de index.html
    <i> PONER EL MENSAJE <ESC>
    : x <ENTER>

![imagen](img14.png)

![imagen](img15.png)

## 12 - Salir del SSH

    exit <ENTER>

![imagen](img16.png)

## 13 - Abrimos el puerto 80

Lo creamos en el portal de Azure

![imagen](img17.png)

![imagen](img18.png)



## Comprobamos que ha funcionado y lo cambios se han realizado



![imagen](img19.png)

## 14 - Parar y "deallocate" la máquina virtual

    az vm stop --resource-group myRGCLI --name myVMCLI --no-wait
    
    az vm deallocate -g myRGCLI -n myVMCLI --no-wait

![imagen](img20.png)

![imagen](img21.png)

## 15 - Borrar la máquina virtual

    az vm delete -g myRGCLI -n myVMCLI --yes --no-wait

## 16 - Borrar el grupo de recursos

    az group delete -n myRGCLI  --yes --no-wait

## 17 - Desconectamos de Azure

    az logout

![imagen](img22.png)

![imagen](img23.png)

![imagen](img24.png)