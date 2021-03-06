## link de pago ##

ClipClap te permite generar link para que te puedan pagar desde un email o documento o factura electronica de forma fácil y rápida. Sólo debes realizar estos sencillos pasos y listo.

### Prerrequisitos ###

 1. ***Tener una cuenta ClipClap Datáfono:***
Si no tienes una cuenta en ClipClap Datáfono, puedes hacer el proceso de registro siguiendo este [link](https://clipclap.co/datafono/dashboard/php/views/login.php) o desde la misma aplicación ClipClap Datáfono.

 2. ***Tener el webKey de tu negocio:***
Una vez tengas tu usuario Datáfono, tendrás que tener a la mano el “webKey” de tu negocio, puedes consultar los pasos para adquirirlos en detalle [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 3. ***Tener el secretKey de tu negocio:***
Una vez tengas tu usuario Datáfono, tendrás que tener a la mano el “secretKey” de tu negocio, puedes consultar los pasos para adquirirlos en detalle [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 4. ***ClipClap Billetera para tus clientes:***
Para que tus usuarios puedan acceder al evento de pago de ClipClap deben tener instalada la aplicación Billetera, esta permitirá realizar los pagos de forma rápida y segura para tus clientes.

 5. ***Entorno de Prueba y Entorno de Producción:***
Recuerda que puedes cambiar entre entorno de prueba y de producción, para llevar un mayor control de tu integración. puedes aprender cómo hacerlo en el siguiente [link](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 6. ***Forma de enviar información:***
La forma de crear un link de pago para que ClipClap Billetera lo gestione es la siguiente:  *Forma 'total-impuesto-propina':* Esta opción permite definir el total a cobrar de forma inmediata especificando el total a cobrar, el impuesto a cobrar y de forma opcional la propina.

### Generar enlace de pago ###
Para generar un enlace de pago, ClipClap provee un servicio al que se accede a través de una peticion POST y este le devuelbe el enlace de pago que se desea implementar en un email o documento electronico (Factura Electronica); la peticion es: 

```curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{"netValue":"100000","taxValue":"0","tipValue":"0","description":"Zapatos","secretKey":"ltOrrdHyvQ0DHXgxRp0G","webKey":"JsUpghDncew5USqVIGFw"}' "https://payment.clipclap.co/tools/generatelink"```

Donde: 
**key**: Es el secretkey del comercio
**webKey**: Es el webkey del comercio
**netValue**: Es el valor neto en pesos que el comercio va ha cobrar
**taxValue**: Valor en pesos del impuesto que el comercio va ha aplicar
**tipValue**: Valor en peso de la propina que el comercio va ha aplicar
**description**: Descripción del valor que el comercio va ha cobrar
**paymentRef**: Referencia de pago generada por el comercio.

Esta petición dos devolera un JSON de la siguiente forma:

```{"url": "https://payment.clipclap.co/pay/?webKey=JsUpghDncew5USqVIGFw&netValue=100000&taxValue=0&tipValue=0&description=Zapatos&socialNetwork=1472744864512&hash=53b81739c178bb4478a47d52f084a467b6b60006cb82a4ef7438c9db96bb4dfa"}```

Donde:
El valor de `url`es el enlace a incorporar en los email o documentos digitales (Facturas Electronicas) 

```
https://payment.clipclap.co/pay/?webKey=JsUpghDncew5USqVIGFw&netValue=100000&taxValue=0&tipValue=0&description=Zapatos&socialNetwork=1472744864512&hash=53b81739c178bb4478a47d52f084a467b6b60006cb82a4ef7438c9db96bb4dfa
```

