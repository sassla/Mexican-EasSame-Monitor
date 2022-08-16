# Mexican-EasSame-Monitor
Recibe notificaciones a tu servidor cuando el [Sistema de Alerta Sísmica Mexicano (SASMEX)](http://www.cires.org.mx/sasmex_n.php) transmita avisos a través de las emisoras [EAS-SAME](https://en.wikipedia.org/wiki/Specific_Area_Message_Encoding) en la Ciudad de México.

![EasSame](https://github.com/sassla/Mexican-EasSame-Monitor/blob/main/eas_same.png)

![SASMEX](https://github.com/sassla/Mexican-EasSame-Monitor/blob/main/sasmex_difusion.png)

## General
[SASSLA](https://github.com/sassla/sassla) proveé esta herramienta de manera gratuita con fines de divulgación, concientización y educación. Este NO es un servicio de Alerta Sísmica.

> Mexican-EasSame-Monitor requiere de autorización por parte de SASSLA para su implementación.

## Funciones clave

| Función                      | Descripción                                                              |
|------------------------------|--------------------------------------------------------------------------|
| Digitalización de códigos SAME | SASSLA decodifica las transmisiones SAME y las digitaliza para transmitirlas a través de internet. |
| Decodificación rápida | SASSLA decodifica rápidamente las transmisiones SAME. Menos de 2 segundos. |
| Notificaciones en tiempo real | Recibe las transmisiones SAME en formato JSON en tiempo real. |

## Códigos SAME habilitados

En la Ciudad de México, la tecnología EAS-SAME se utiliza únicamente para la difusión de la Alerta Sísmica del [SASMEX](http://www.cires.org.mx/sasmex_n.php), por lo que sólo están habilitados 2 códigos SAME en esta herramienta:

- ``` RWT ```: Prueba Semanal Obligatoria. Se transmite cada 3 horas con el objetivo de verificar el correcto funcionamiento del sistema. Estos son los horarios de transmisión preestablecidos: 02:45, 05:45, 08:45, 11:45, 14:45, 17:45, 20:45 y 23:45 hrs.

- ``` EQW ```: Alerta de Terremoto. Se transmite en el momento que el [SASMEX](http://www.cires.org.mx/sasmex_n.php) activa la Alerta Sísmica para la Ciudad de México.

## Implementación
Para recibir notificaciones, tu servidor debe habilitar característias específicas detalladas a continuación:

### Disponibilidad

Tu servidor debe permanecer activo las 24 horas del día para recibir peticiones en cualquier momento.

### Endpoint

Tu servidor debe habilitar un extremo para que SASSLA pueda establecer una conexión ``` TCP ``` y enviar peticiones. Ejemplo:

```
http://yourserver:port/eas-same
```

> El url debe incluir la ruta /eas-same

### Method

```
POST
```
Tu servidor debe permitir recibir peticiones POST desde cualquier IP. SASSLA no utiliza un IP específico, cambia constantemente.

### Password

Debes proporcionar una contraseña para validar las peticiones que reciba su servidor.

La contraseña puede ser cualquier combinación de letras, números y símbolos (solo caracteres del estándar ASCII) de máximo 100 caracteres. No se admiten acentos ni caracteres acentuados.

No puede usar una contraseña que:

- Sea poco segura. Ej.: "contrasena123".
- Empiece o termine con un espacio en blanco.

### Request

#### Headers

Tu servidor debe tener la capacidad de leer los encabezados de cada petición POST para identificar dos puntos importantes:
- Formato del cuerpo de la solicitud.
- Verificar que la contraseña que incluye la solicitud coincida con la preestablecida por el cliente. 

```json
{
   "Content-Type": "application/json",
   "Authorization": "key=PASSWD"
}
```

#### Body

```json
{
       "source": "XDIF/005",
       
        "message": {
            "code": "EQW",
            "timestamp": 1663589940,
            "date": "2022-09-19T12:19:00"
        }
}
```

### Sintaxis de la solicitud

| Parámtero | Uso | Descripción |
|-----------|-----|-------------|
| **source** | Obligatorio, string | Este parámetro especifica el identificador de la emisora EAS-SAME que transmite el mensaje. |
| **message** | Obligatorio, matriz JSON | Consultar mexican.eassame.monitor.message |

#### mexican.eassame.monitor.message

| Parámtero | Uso | Descripción |
|-----------|-----|-------------|
| **code** | Obligatorio, string | Este parámetro especifica el código SAME decodificado de la transmisión. |
| **timestamp** | Obligatorio, número | Este parámetro especifica la fecha de decodificación de la transmisión en formato UNIX. |
| **date** | Obligatorio, string | Este parámetro especifica la fecha (CST) de decodificación de la transmisión en el siguiente formato:  ```yyyy-MM-dd'T'HH:mm:ss```. |


## Solicita implementación 
Envía un email a ```app@sassla.mx``` con el asunto **"Apply for Mexican-EasSame-Monitor"**. Incluye un método de contacto donde podamos comunicarnos contigo.

## Licencia
Mexican-EasSame-Monitor is licensed under the Apache License, version 2.0.
