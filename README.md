# Mexican-EasSame-Monitor
Recibe notificaciones a tu servidor cuando el [Sistema de Alerta Sísmica Mexicano (SASMEX)](http://www.cires.org.mx/sasmex_n.php) transmita avisos a través de las emisoras EAS-SAME en la Ciudad de México.

![EasSame](https://github.com/sassla/Mexican-EasSame-Monitor/blob/main/eas_same.png)

## General
[SASSLA](https://github.com/sassla/sassla) proveé esta herramienta de manera gratuita con fines de divulgación, concientización y educación. Este NO es un servicio de Alerta Sísmica.

> Mexican-EasSame-Monitor requiere de autorización por parte de SASSLA para su implementación.

## Funciones clave

| Función                      | Descripción                                                              |
|------------------------------|--------------------------------------------------------------------------|
| Digitalización de códigos SAME | SASSLA decodifica las transmisiones SAME y las digitaliza para transmitirlas a través de internet. |
| Decodificación rápida | SASSLA decodifica rápidamente las transmisiones SAME. Menos de 2 segundos. |
| Notificaciones en tiempo real | Recibe las transmisiones SAME en tu servidor en formato JSON en tiempo real. |

## Códigos SAME habilitados

En la Ciudad de México, la tecnología EAS-SAME se utiliza únicamente para la difusión de la Alerta Sísmica del [SASMEX](http://www.cires.org.mx/sasmex_n.php), por lo que sólo están habilitados 2 códigos SAME en esta herramienta:

- ``` RWT ```: Prueba Semanal Obligatoria. Se transmite cada 3 horas con el objetivo de verificar el correcto funcionamiento del sistema. Estos son los horarios de transmisión preestablecidos: 02:45, 05:45, 08:45, 11:45, 14:45, 17:45, 20:45 y 23:45 hrs.

- ``` EQW ```: Alerta de Terremoto. Se transmite en el momento que el [SASMEX](http://www.cires.org.mx/sasmex_n.php) activa la Alerta Sísmica para la Ciudad de México.

## Implementación
Para recibir notificaciones, tu servidor debe habilitar característias específicas detalladas a continuación:
