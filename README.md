


# Balancio-Kit

[![license_MIT](https://img.shields.io/github/license/udesa-ai/balancio-kit)](https://github.com/udesa-ai/balancio-kit/blob/main/LICENSE)
&nbsp;
[![stars](https://img.shields.io/github/stars/udesa-ai/balancio-kit)](https://github.com/udesa-ai/balancio-kit/stargazers)
&nbsp;
[![language_en](https://img.shields.io/badge/language-english-a0b0ba)](README_EN.md)
[![language_sp](https://img.shields.io/badge/spanish-1081c2)](README.md)

#### [README in English](README_EN.md)
----
Proyecto educativo de un robot :robot: de autobalanceo de ultra bajo costo, capaz de correr una red neuronal para mantener el equilibrio y de ser controlado de manera inalámbrica  :trackball:.

Desarrollado con fines didácticos para enseñar conceptos de RL, ML, AI y control.

<p align="center">
    <img src="resources/Balancio_0.6.jpg" height="200">
    <img src="resources/0.7a.jpeg" height="200">
    <img src="resources/balanciov3.jpg" height="200">
    <img src="resources/balancio_gif.gif" height="200">
    <img src="resources/Balancio_walle.jpg" height="200">
    <img src="resources/ensamble.jpg" height="200">
</p>



## Versiones
|                     | Estabilidad          | Facilidad de Armado  | Requiere I3D | Tiempo de [I3D](#configuración-de-impresión)|   de Impresión 3D| Foto de la versión                                 |
|:-------------------:|:--------------------:|:--------------------:|--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------:|
| V 0.7 (Recomendado) | :star: :star: :star: | :star: :star: :star: | SI           | <ul style="list-style-type:none;"> <li>  Baterias 47m </li> <li> Cuerpo 2:36 h </li> </ul>                                                                                                       | <A HREF="https://github.com/AaronLoz/balancio-kit/tree/RL_1/Planos%20de%20Impresi%C3%B3n%203D/Version%200.7"> Versión 0.7 I3D</A>      | <img src="resources/Balancio_0.71.jpg" width="70"> |
| V 0.6 AKA:Wall-e    | :star: :star: :star: | :star:               | SI           | <ul style="list-style-type:none;"> <li> C_Inferior 5:25h </li> <li> C_Superior 5:11h </li> <li>P_inferior 58m</li> <li>P_superior 55m</li> <li> Cabeza 3:19 h </li> </ul> | <A HREF="https://github.com/AaronLoz/balancio-kit/tree/RL_1/Planos%20de%20Impresi%C3%B3n%203D/Versi%C3%B3n%200.6"> Versión 0.6 I3D</A> | <img src="resources/Balancio_0.5.jpg" width="60">  |
| V 0.5               | :star:               | :star: :star: :star: | SI           |<ul> <li>Aro 49m </li> <li> Cuerpo 4:42h </li>                                                                                                                                                                            | <A HREF="https://github.com/AaronLoz/balancio-kit/tree/RL_1/Planos%20de%20Impresi%C3%B3n%203D/versi%C3%B3n%200.5"> Versión 0.5 I3D</A> | <img src="resources/balanciov3.jpg" width="60">    |
    
### Configuración de Impresión 
- Espesor de boquilla: 0.4 mm
- Altura de Capa: 0.3 mm 
- Perimetros: 3 
- Capas Solidas Top y Bottom:  3 
- Infill: 20%

## Ensamblaje :wrench:

El balancio-kit consta de los siguientes componentes:
- Placa base (impresa en 3D o hecha con algún otro material) 
- Microcontrolador NodeMCU ESP32
- IMU MPU 6050
- 2 motorreductores de 6v
- Puente-H L298N
- 2 baterías 18650 con su correspondiente porta-pilas
- BMS FCD-2S-2
- Switch 

<p align="center">
    <img src="resources/Balancio_plano.png" width="650">
</p>

## Plano Electrico 
<p align="center">
    <img src="resources/Plano_1.2.png" width="730">
</p>    
    
## Ensamblaje Mecánico 
1. Imprimir en 3D alguna de las [versiones](#versiones).
1. Encastrar piezas en su posición final.
1. Sostener los motores con precintos y/o pegamento. 
1. Conectar los componentes siguiendo el [plano electrico](#plano-electrico).  
     
## Instalación :floppy_disk:

En primer lugar, se debe clonar el repositorio. Esto se puede realizar tanto descargando el mismo
como un .ZIP, o ejecutando `git clone https://github.com/UDESA-AI/balancio-kit.git` en consola.

La instalación consta de 3 módulos principales: Microcontrolador, simulación y aplicación.
Éstos son fundamentales para el funcionamiento completo del proyecto, pero la instalación
de cada uno de ellos se puede realizar en distinto orden.
  
  
### Microcontrolador

<details open>
<summary>Instalación de la IDE</summary> 
Para programar y compilar el NodeMCU ESP32 usaremos la IDE 2 de Arduino. Para esto se
debe instalar la misma siguiendo los pasos que se especifican en el siguiente 
[link](https://www.arduino.cc/en/software) .
</details> 
<details open>
<summary>Configuración del Microcrontolador</summary> 
Una vez instalada la IDE, se debe habilitar el microcontrolador que vamos a usar.
Para esto se deben seguir los siguientes pasos:
    
1. En la IDE, ir a 'File' (Archivos) → 'Preferences' (Preferencias)
    
2. En el campo "Additional Boards Manager URLs", agregar lo siguiente: https://dl.espressif.com/dl/package_esp32_index.json. (Luego clickear 'OK').
3. Ir a 'Tools' → 'Board: ' → 'Boards Manager…' 
    
4. Buscar "esp32", e instalar "esp32 by Espressif Systems" presionando el botón 'Install'.
    
5. Indicarle a la IDE que vamos a utilizar un esp32. Ir a 'Tools' → 'Board:' → 'ESP32 Arduino' → 'NodeMCU-32S'
    
6. En 'Tools' → 'Port', seleccionar el puerto correspondiente a donde está conectado el microcontrolador.

</details> 

<details open>
<summary>Librerias de Arduino</summary> 
Luego procederemos a instalar las librerías de arduino que vamos a utilizar:
    
   
- Para eso ir a 'Sketch' → 'Include Library' → 'Manage Libraries…'
    
    
- Buscar e instalar las siguientes librerias, especificando la versión correspondiente:
    - MPU6050 by Electronic Cats (version 0.5.0)
    - PS3 Controller Host by Jeffrey van Pernis (version 1.1.0)
    - EloquentTinyML by Simone Salerno (version 0.0.7)
    
    
</details> 
<details open>
<summary>Ejecución inicial</summary> 
Para comprobar la instalación, ejecutaremos un ejemplo de prueba:
- ir a 'File' → 'Examples' → 'WiFi' → 'WiFiScan'
- En el sketch generado, presionar el botón de carga ('Upload')  :calling:
- Si todo funcionó correctamente, debe aparecer un mensaje 'Done uploading' en la consola.

Posibles errores:
- Si no se puede cargar el programa al microcontrolador, intentar mantener presionado el botón "boot" presente en la placa, mientras se realiza la carga. Esto se debería realizar solo la primera vez.
</details> 

### Simulación
<details open>
 
La simulación corre en Python :snake:, y utiliza diversos paquetes. Para facilitar la instalación de los mismos, utilizaremos [Conda](https://docs.conda.io/en/latest/).

Se debe seguir con los siguientes pasos:

1. Para el uso e instalación de conda, descargaremos miniconda (también se puede instalar [Anaconda](https://docs.anaconda.com/anaconda/install/index.html)), siguiendo con los pasos que se especifican en el siguiente [link](https://docs.conda.io/en/latest/miniconda.html#installing).
2. Crearemos un 'Environment' de conda, donde alojaremos nuestros paquetes. 
   Esto se puede realizar tanto desde la consola (en el caso de haber descargado Miniconda) o desde una GUI (en caso de haber descargado Anaconda). Respectivamente:
    - Miniconda: Ejecutar el siguiente comando en la consola: `conda env create -f requirements.yml`. Donde `requierments.yml` es el [archivo](https://github.com/UDESA-AI/balancio-kit/blob/RL_1/requirements.yml) que se encuentra dentro del repositorio y ya fue descargado.
    - Anaconda: En la GUI de Anaconda: En la pestaña environments, hacer clik en import y especificar [archivo](https://github.com/UDESA-AI/balancio-kit/blob/RL_1/requirements.yml) en file

<p align="center">
    <img src="resources/env_anaconda.png" width="500">
</p>

3. Activar el environment creado, llamado **balancio**:
    - Miniconda: Ejecutar en terminal `conda activate balancio`
    - Anaconda: En la pestaña environments, hacer clik en el ambiente que se quiere activar
4. Dentro del environment activado, ejecutar el archivo [setup.py](https://github.com/UDESA-AI/balancio-kit/blob/RL_1/simulation/balancio_lib/setup.py):
    `python setup.py`
5. Probar la instalación, corriendo el siguiente [script](https://github.com/UDESA-AI/balancio-kit/blob/RL_1/simulation/pid.py):
    `python pid.py`
    </details> 
    

### Variables Físicas de la versión 0.7
#### Cuerpo
Masa sin ruedas: 0.244 kg



Posición del centro de masa con respecto al eje de los motores y el centro simétrico del cuerpo: 


- x = 1.55 
- y ~= 0 mm
- z = 31 mm

Inercia sin ruedas desde el centro de masa (kg.m2): 

- Ixx = 0.0006945
- Ixy ~= 0
- Iyy = 0.0006536
- Ixz = -0.000013447 
- Iyz ~= 0
- Izz = 0.0001937

#### Rueda
Masa de una rueda: 0.029 kg


Posición del centro de masa con respecto al eje de los motores y el borde del agarre: 
- x = 0 mm   
- y = 15.6 mm 
- z = 0 mm


Inercia de la rueda desde el centro de masa (kg.m2):  

- Ixx = 0.000011729 
- Ixy ~= 0  
- Iyy = 0.000021531 
- Ixz ~= 0 
- Iyz ~= 0 
- Izz = 0.000011729


### Aplicación 

 La aplicación está creada en <A HREF="https://appinventor.mit.edu/"> MIT App Inventor </A>.

Simplemente entrar al website e importar el .aia en <A HREF="Balancio-kit/app/app.aia"> App Balancio  </A>. Luego de esto, se puede usar la aplicación mediante bluethooth desde un celular.


## Calibración


Estas instrucciones asumen conocimiento del uso de la IDE arduino

<details open>
<summary>Calibración del IMU</summary>
1. Abrir `Balancio-kit/Mcu/Src/imu_calibration/imu_calibration.ino` con el IDE Arduino
    
2. Colocar el robot con la IMU paralela al piso y mantenerlo firme

3. Subir el programa a la placa y usar el monitor serial para obtener las compensaciones de la IMU

4. Modificar las compensaciones de giróscopo en el archivo `balancio-kit/mcu/src/main/config.h` en:
```c++
// IMU calibration parameters
#define X_ACCEL_OFFSET -1775
#define Y_ACCEL_OFFSET  756
#define Z_ACCEL_OFFSET  2706
#define X_GYRO_OFFSET   181
#define Y_GYRO_OFFSET   77
#define Z_GYRO_OFFSET   60
```
5. Para las compensaciones de Acelerómetro debe ser tenido en cuenta la gravedad, solo midiendo las compensaciones con la gravedad perpendicualar a esa direcci 
</details>  

<details open>
<summary>Calibración del angulo de equilibrio</summary>
1. Abrir `balancio-kit/mcu/src/main/main.ino`

2. Sostener el robot en la posición de equilibrio

3. Subir el programa a la placa y usar el monitor serial para obtener las compensaciones de angulo

4. Modificar en angulo de equilibrio en el archivo `balancio-kit/mcu/src/main/config.h` en la línea:
```c++
// Angle of (approximate) static equilibrium
#define STATIC_ANGLE -0.04 // Calibrated point
```
 </details>   
 
<details open>
<summary>Calibración de las constantes PID</summary>
    
1. Sacar el jumper de 12v en el driver 

2. Elegir parámetros PID
    
3. modificar las constantes del PID en el archivo `balancio-kit/mcu/src/main/config.h` en las líneas:
```c++
// PID Constants for pitch control
#define KP 2000
#define KI 22000
#define KD 20.0
```   

4. Probar las constantes, si se sacó el jumper se puede probar incluso con el cable conectado. **Cuidado al hacer esto!**


---
</details> 
     
Una vez configurado correctamente el robot, se pueden seleccionar distintos parametros de configuracion en el archivo correspondiente (`config.h`). 

Entre ellos, se puede seleccionar el tipo de controlador deseado para estabilizar el Balancio.

Por ejemplo, en caso de querer utilizar un controlador PID:
```c++
// Control algorithm type
#define CONTROL_ALGO "PID"
```

En caso de querer utilzar un agente de aprendizaje por refuerzo:
```c++
// Control algorithm type
#define CONTROL_ALGO "RL"
```
</details> 

---

    
## How To / Armado 

<details open>
<summary>Pasos</summary>


### Paso 1 - Soldar cables a los servomotores

Soldamos los cables a los servomotores para luego encajarlos y conectarlos. 

**¿Cuál es el largo de los cables?**  \
Para determinar esto vamos a insertar los servomotores en el cuerpo del Balancio y el Puente H como se ve en la imágen. Luego determinaremos experimentalmente donde hay que cortar para que llegue del borne del servomotor al puerto correspondiente del Puente H. Una vez que ya tengas los 4 cables con las medidas correctas retira los servomotores y el Puente H del cuerpo para trabajar cómodo.

**¿Cómo me doy cuenta para que lado tiene que mirar?**  \
Como se ve en la primera foto, hacemos que las patitas miren hacia arriba y conectamos a izquierda el     
positivo (rojo) y a derecha el negativo (negro). 

Cuando lo insertamos en el cuerpo, del lado izquierdo el cable rojo tiene que estar por arriba del negro y del lado derecho al revés.

<!-- Foto -->
<p align="center">
    <img src="how_to_photos/servos.jpg" width="400">
</p>


### Paso 2 - Insertar IMU

En este paso insertamos la IMU en su ranura correspondiente, la cual se encuentra en la parte inferior del cuerpo del Balancio. Marcamos esto en la imágen a continuación. Hay que insertarla deslizándola lateralmente, lo que puede resultar difícil en un principio, por lo que si no desliza recomendamos lijar la zona. 
<p align="center">
    <img src="how_to_photos/IMU.png" height="600" >
</p>

### Paso 3 - Cableado de portabaterias

Como se encuentra indicado en el diagrama de conexiones, es requerido realizar un empalme entre el borne positivo de una de las pilas y el negativo de la otra, el cual luego se colocará en la terminal EM del componente (paso que se realizará más adelante). Para realizar este conexionado de forma efectiva, se requiere que ambos portapilas sean colocados dentro de la estructura del balancio para luego realizar el empalme descrito anteriormente, teniendo cuidado de no disponer los cables de tal manera que los mismos se enreden con las ruedas cuando el dispositivo se encuentre en funcionamiento. Una vez realizado este paso, todos los cables referentes al conexionado de las baterías deben ser pasados por un orificio en la base de la estructura para poder continuar con el armado. 

**Recomendación:** A la hora de cortar los cables necesarios para este paso, recomendamos colocar los servomotores en el cuerpo como se ve en las imágenes para poder medir de forma más precisa las distancias. 
<p align="center">
    <img src="how_to_photos/imagen-Paso3.jpg" width="500">
</p>

<p align="center">
    <img src="how_to_photos/imagen2-Paso3.jpg" width="500">
</p>

<p align="center">
    <img src="how_to_photos/diagrama-Paso 3.png" width="500">
</p>

### Paso 4 - Cableado del switch

En este paso se considera recomendable tanto el enrollar los cables en las terminales correspondientes del switch, como también estañar estas conexiones para darles firmeza. A su vez, es importante medir aproximadamente las distancias del switch colocado en la estructura del balancio al Puente H y al BMS FCD-2S-2 con la finalidad de optimizar el uso de cables y espacio. Notemos que un cable va a ser muy corto para ser conectado al BMS y el otro tendrá que llegar hasta el puente H.

<p align="center">
    <img src="how_to_photos/imagen-Paso4.jpg" height="400">
</p>

### Paso 5 - Colocación del  módulo BMS FCD-2S-2

Colocamos el módulo de carga y protección BMS en su lugar correspondiente dentro del cuerpo del balancio. La inserción se debe realizar inclinando hacia atras el módulo BMS, apoyarlo sobre el soporte inferior y luego inclinarlo hacia adelante para que quede encastrado donde se puede ver en la imágen. 

https://github.com/AlexBodner/balancio-kit-HowTo/assets/61150961/538d2bf4-75f0-46c5-89c6-0aa253f4f102

<video src="https://github.com/AlexBodner/balancio-kit-HowTo/tree/main/how_to_photos/Insercion_BMS.mp4"></video>
### Paso 6 - Colocación de switch y conexiones con BMS

Primero procedemos a insertar el switch en la ranura correspondiente del la estructura del balancio, para luego realizar las conexiones indicadas. \
**Recomendación:** Antes de tratar de unir el cable que une al switch con la terminal P+ del BMS FCD-2S-2, se recomienda precalentar la terminal P+ con el soldador de estaño y estañar el cable antes de realizar la conexión. 

<p align="center">
    <img src="how_to_photos/imagen-Paso6.jpg"  width="400">
    <img src="how_to_photos/diagrama-Paso 7.png" width="400">
</p>

### Paso 7 - Conexiones entre BMS y portapilas

Antes de tratar de unir el cable correspondiente de los portabaterías con las terminales B+ y B- del BMS FCD-2S-2, se recomienda precalentar ambas terminales con el soldador de estaño y estañar los cables antes de realizar las conexiones.

***Observaciones:***
- En violeta marcamos el cable que extendimos en el paso 3.
- Recomendamos usar los cables Dupont para las conexiones al ESP e IMU. En este paso es la marcada en amarillo en la imágen a continuación.

<p align="center">
    <img src="how_to_photos/imagen-Paso7.jpg" width="500">
</p>


<p align="center">
    <img src="how_to_photos/diagrama-Paso 8.png" width="600">
</p>


### Paso 8 - Conexión BMS y Switch a Puente H

Insertamos el puente H como se ve en la foto (con la parte negra hacia arriba) y vamos a conectar donde corresponden los cables que quedaron sueltos de los pasos anteriores. Estos son el P- del BMS y la conexión entre el Switch y el Puente H (12V).
**Falta imágen**

### Paso 9 - Conexión de servomotores al Puente H

Una vez insertados los servomotores y el puente H en sus lugares correspondientes dentro del cuerpo del balancio, procedemos a colocar los cables que colocamos anteriormente en los servomotores en las borneras correspondientes del puente H. 

***Observación:*** En la foto el Puente H se encuentra al revés. La parte negra tiene que mirar para arriba. (Esto es a cambiar) 
<p align="center">
    <img src="how_to_photos/imagen2-Paso1.jpg" width="500">
</p>

<p align="center">
    <img src="how_to_photos/diagrama-Paso 2.png" width="600">
</p>

### Paso 10 - Conexiones ESP32 a Puente
 En este paso realizaremos las conexiones del ESP32 al Puente H. Esta son indicadas en el plano a continuación. \
 **Observaciones:**
 - La conexión indicada en verde (puerto GND del Puente H) se trata de una con 2 cables que van hacia el GND del Puente H, uno de estos es un cable dupont, al cual tendremos que sacarle la punta y pelarlo. El otro proviene del BMS. Para poder conectar ambos al GND recomendamos soldarlos entre si y luego si conectarlos al GND.
 - Se recomienda usar cables Dupont tanto para este paso como para el siguiente. Exceptuando la señalada en rojo que para tener una mayor firmeza se puede realizar soldando a lo largo del pin del ESP.
 - 




<p align="center">
    <img src="how_to_photos/Paso10_ESP_Puente.png" width="700">
</p>

### Paso 11 - Conexiones ESP32 e IMU 
En este paso realizaremos las últimas conexiones, estas conectan la IMU con el ESP32 y las realizaremos con cables Dupont. En el siguiente plano indicamos cuáles son los pines a conectar.
<p align="center">
    <img src="how_to_photos/Paso10_IMU_ESP.png" width="700">
</p>

</details>  

## TODO

- [x] initial commit
- [x] Desarrollar aplicación bluetooth
- [x] Crear agente RL
- [x] Diseño mecánico
- [X] Publicar STL del diseño mecánico
- [ ] Publicar STEP del diseño mecánico
- [X] Crear diagrama electrónico
- [ ] Aclarar que datos levantar del imu calibration.



    
## Bugs conocidos
- [x] Wheel spins on startup



    
## Contribuciones
 
Las *pull requests* son bienvenidas, para cambios mayores, por favor abrir un *issue* para discutir los cambios deseados

## Licencia
[MIT](https://choosealicense.com/licenses/mit/)
