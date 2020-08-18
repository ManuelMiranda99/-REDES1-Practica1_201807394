**Universidad de San Carlos de Guatemala**
**Facultad de Ingeniería**
**Escuela de Ciencias y Sistemas**
**Redes de Computadoras 1**
**Ing. Pedro Pablo Hernandez Ramirez**
**Aux. Andrés Alejandro Montufar Cordero**
**Angel Manuel Miranda Asturias**
**201807394**

# Practica 1 - Manual de Configuración

## Configuración de la topología de red en GNS3

La topología de red que se nos presento para realizar para la práctica es la siguiente (Ya agregada las IPs correspondientes):

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Topologia.PNG "Topologia de Red")

Para la configuración de la red se hizo uso de GNS3 para su simulación. Se conectaron el Router, Switches, VPCS y la máquina virtual de TinyCore Linux dentro de la interfaz de GNS3. 

Las configuraciones de los dispositivos usados para la pr[actica se detallan a continuación.

### Router

El router es un dispositivo que nos proporciona conectividad a nivel de red. Este conecta con otras redes o subredes para enviar datos a través de estas. La configuración del router se detalla a continuación:

#### Mostrar IPs

Primero se debería de observar las interfaces que trae el router por "defecto". Para esto se usa el comando:

```
sh ip int brief
```

Nos muestra el siguiente resultado:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Router/ShowIPs.PNG "Mostrar Interfaces")

#### Entrar a la Configuración

Luego de saber que configuraciones tienen las interfaces de nuestro router vamos a ingresar a una de estas para configurarla. Primero se configuro el lado izquierdo de la red. El comando para entrar a la configuración es:

```
conf t
int (Nombre De Interfaz)
```

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Router/EnterInterface.PNG "Entrar a configuracion")

Notaremos que en la línea de comandos cambia y nos agrega paréntesis con el texto _config-if_.

#### Colocar una IP a la Gateway

Para colocarle una IP a la puerta de enlace de nuestra interfaz se debe de usar el siguiente comando:

```
ip address (IP) (Máscara de Red)
```

De la siguiente manera:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Router/SetIP.PNG "Settear Gateway 1")

Luego de eso ya tenemos colocada la IP de nuestra puerta de enlace de la primera interfaz. Ya solo falta salir de la configuración de la interfaz y confirmar que se haya realizado bien la configuración. Le damos al comando _exit_ hasta que la consola únicamente tenga _R1#_ en ella. 

#### Confirmar IP de Gateway

Para confirmar la IP de nuestra puerta de enlace se debe de utilizar el comando que utilizamos antes par amostrar IPs. Ahora se mostrará un resultado distinto:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Router/ConfirmInterface.PNG "Primera puerta de enlace configurada")

#### Para interfaz 0/1

Para la siguiente interfaz se realizan los mismos pasos pero asignando una puerta de enlace distinta y al momento de entrar a la configuración se usará 0/1 en vez de 0/0.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/Router/ConfigureLastInterface.PNG "Segunda puerta de enlace configurada")

#### Guardar Cambios

Luego de realizar los cambios correspondientes se deben de guardar las configuraciones con el comando siguiente para tenerlos disponibles después cuando se vuelva a iniciar el proyecto.

```
wr
```

Luego para confirmar todas las configuraciones procederemos a usar el comando:

```
sh run
```

Este nos mostrará todas las configuraciones que tiene nuestro router. Para avanzar se le dará al espacio hasta que ya hayamos finalizado de configurar nuestro router.

### VPCS

Las configuraciones de VPCS son prácticamente idénticas en todos los VPCS. Únicamente cambian las IPs y puertas de enlace para las distintas VPCS.

#### VPCS 1 (PC1):

##### Mostrando Configuración

Para mostrar la información de nuestra VPCS se hace uso del siguiente comando:

```
show ip
```

Este nos mostrará el nombre de nuestra computadora, la IP, la máscada de red entre otros.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/FirstShowIP.PNG "Show IP VPCS1")

##### Asignar IP

Luego de verificar que nuestra VPCS no tuviera una IP asignada, se prosiguió a colocarle una IP a la computadora. Para eso se hace uso del siguiente comando:

```
ip (IP) (Máscara de red) (Puerta de Enlace del router)
```

También se puede colocar la máscara de red seguida de la IP de la siguiente manera:

```
ip (IP)/(Máscara de red en decimal) (Puerta de Enlace del router)
```

Se realizó de la siguiente manera:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/SetIPX30.PNG "Set IPX30")

##### Guardar y Verificar cambios

Para guardar los cambios de lo que acabamos de realizar se utilizan los siguientes comandos:

```
save
```

Luego de eso verificamos que los cambios se hayan realizado con _show ip_. Quedando de la siguiente manera:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/SaveAndCheck.PNG "Save and Check")

#### VPCS 2 (PC2):

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/SetIPY15.PNG "Set IPY15")

#### VPCS 3 (PC3):

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/SetIPY39.PNG "Set IPY30")

### Máquina Virtual

La configuración de la máquina virtual de TinyLinux se hizo uso del _Panel de Control_ para poder realizar los cambios. Debido a esto es un poco más sencillo, aunque no se guardan los cambios realizados después de volver a iniciar la red. 

#### Abrir Panel de Control

Hay dos maneras de abrir el Panel de Control. Ambas son muy intuitivas, la más sencilla es seleccionandolo en la barra de tareas en la parte inferior de la pantalla. Luego de abrir el Panel de Control encontramos lo siguiente:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/EnterConf.png "Panel de Control")

#### Entrar a la configuración de IP.

Para entrar a la configuración donde colocaremos nuestra IP, daremos click en _Network_ en las opciones del panel de control. Mostrará la siguiente ventana.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/setIPVM.png "Network")

En esos cuadros de texto colocamos la IP y automáticamente nos llenará lo demás. Le damos a guardar luego de eso y podemos cerrar las ventanas.

### Comunicación entre Nodos de la Red

Para la comunicación entre computadoras se hizo uso del siguiente comando:

```
ping (IP existente en la red)
```

A continuación se muestra una "galería" de los resultados al momento de realizar ping entre las distintas computadoras.

#### IP 192.168.14.30 -> 192.168.19.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1430_PC1915.PNG "Ping 1430-1915")

#### IP 192.168.14.30 -> 192.168.19.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1430_PC1930.PNG "Ping 1430-1930")

#### IP 192.168.19.15 -> 192.168.14.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1915_PC1430.PNG "Ping 1915-1430")

#### IP 192.168.19.15 -> 192.168.19.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1915_PC1930.PNG "Ping 1915-1930")

#### IP 192.168.19.30 -> 192.168.14.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1930_PC1430.PNG "Ping 1930-1430")

#### IP 192.168.19.30 -> 192.168.19.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VPCS/Pings/PC1930_PC1915.PNG "Ping 1930-1915")

#### IP 192.168.14.30 -> 192.168.14.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingPCX30_VM.png "Ping 1430-1415") 

#### IP 192.168.19.15 -> 192.168.14.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingPCY15_VM.png "Ping 1915-1415") 

#### IP 192.168.19.30 -> 192.168.14.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingPCY30_VM.png "Ping 1930-1415") 

#### IP 192.168.14.15 -> 192.168.14.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingVM_PCX30.PNG "Ping 1415-1430")

#### IP 192.168.14.15 -> 192.168.19.15

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingVM_PCY15.PNG "Ping 1415-1915")

#### IP 192.168.14.15 -> 192.168.19.30

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica1_201807394/blob/master/Imgs/VM/PingVM_PCY30.PNG "Ping 1415-1930")

## Glosario

Se preparo un glosario con términos que son importantes para la realización de la práctica y entender la red un poco mejor. 

1. **Switch:** Es un dispositivo de interconexión utilizado para conectar equipos en red formando lo que se conoce como una red LAN y cuyas especificaciones técnicas siguen el estándar conocido como Ethernet. 
2. **Router:** Este término se puede traducir como el enrutador o encaminador. Este es un dispositivo de red utilizado para unir redes y encaminar datos entre ellas. 
3. **VPCS:** Estos son ordenadores virtuales que funcionan como el punto de inicio y final de las transferencias de datos. Estos tienen una única dirección IP que se puede asignar manualmente o automáticamente.
4. **Virtual Machine:** Este es un software que permite emular una computadora dentro de otra computadora. Parecida a las VPCS pero con diferente sistema operativo. 
5. **Dirección IP:** Es un número que identifica de manera única a una interfaz en red de cualquier dispositivo conectado a ella que utilice protocolo IP, correspondiente al nivel de red del modelo TCP/IP.
6. **Topología:** Esta es una rama de las matemáticas dedicada al estudio de aquellas propiedades de los cuerpos geométricos que permanecen inalteradas por transformaciones continuas. Aplicada al curso, una topología de red es un mapa físico de una red para el intercambio de datos. 
7. **Red:** Una red de computadoras es un conjunto de equipos conectados entre sí por medio de dispositivos físicos (cables) o inalámbricos que envían y reciben impulsos eléctricos, ondas electromagnéticas o cualquier otro medio para transportar datos.
8. **Host:** También conocido como anfitrión, se usa en informática para referirse a computadoras u otros dispositivos conectados a una red que proveen y utilizan servicios de ella. 
9. **Interfaz:** Dentro de la práctica esta el término interfaz de router. Este se refiere al conector físico en el router cuyo principal objetivo es el enviar y recibir paquetes. Dígase los puertos del router.
10. **Ping:** Es una utilidad de diagnóstico en redes de computadoras que comprueba la comunicación del anfitrión local con uno o varios equipos remotos de una red que ejecuten IP. Envía paquetes de una computadora a otra, y la otra lo confirma. 
11. **Dirección de Red:** Es una manera estándar de hacer referencia a una red. También se puede utilizar como la máscara de subred o la duración de prefijo. 
12. **Simulación:** Hace referencia a la investigación de una hipótesis o un conjunto de hipótesis para representar lo que se espere que suceda en la realidad. 
13. **GNS3:** Es un simulador gráfico de red que permite diseñar topologías de red complejas y realizar una simulación a partir de estas. 