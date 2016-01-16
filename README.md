## Web Pay Button##

ClipClap te permite incorporar la acción de pagar en tu página web de forma fácil y rápida. Sólo debes realizar estos sencillos pasos y listo.

## Prerrequisitos ##

 1. ***Tener una cuenta ClipClap Datáfono:***
Para poder realizar la integración con ClipClap debes primero tener una cuenta en ClipClap Datáfono, puedes hacer el proceso de registro siguiendo este [link](https://clipclap.co/datafono/dashboard/php/views/login.php) o desde la misma aplicación ClipClap Datáfono.

 2. ***Tener el webKey de tu negocio:***
Una vez tengas tu usuario Datáfono, tendrás que tener a la mano el “webKey” de tu negocio, puedes consultar los pasos para adquirirlos en detalle [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 3. ***Guardar el nombre del dominio de tu página:***
Debes Colocar el nombre del dominio de tu página para que te permitamos usar nuestro servicio. Si no lo haz hecho hazlo aquí [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 4. ***ClipClap Billetera para tus clientes:***
Para que tus usuarios puedan acceder al evento de pago de ClipClap deben tener instalada la aplicación Billetera, esta permitirá realizar los pagos de forma rápida y segura para tus clientes.

 5. ***Entorno de Prueba y Entorno de Producción:***
Recuerda que puedes cambiar entre entorno de prueba y de producción, para llevar un mayor control de tu integración. puedes aprender cómo hacerlo en el siguiente [link](https://clipclap.co/datafono/dashboard/php/views/settings.php).

 6. ***Formas de enviar información:***
Hay dos forma de crear un cobro para que ClipClap Billetera lo gestione:

a) *Forma 'producto por producto':* Esta opción permite agregar al cobro productos de forma individual especificando su nombre, precio y cantidad del producto.
b) *Forma 'total-impuesto-propina':* Esta opción permite definir el total a cobrar de forma inmediata especificando el total a cobrar sin impuestos, el impuesto sobre el total y de forma opcional la propina.
> ***Nota:*** Estas dos formas de crear el cobro son mutuamente excluyentes. Si usted utiliza ambas formas al mismo tiempo, la *forma 'total-impuesto'* prevalece sobre la *forma 'producto-por-producto'*.

## Integración ##

Implementar el botón de pago es muy fácil. Te garantizamos que después de leer el documento te tomará 2 minutos realizar la implementación.

**Paso 1: Lo primero que debes hacer es crear una etiqueta button html y darle un identificador único, ya sea mediante el atributo id o el atributo class.
El siguiente es un ejemplo de una eqitueta button con un id que llamaremos 'botonClipClap'



        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'AQUI_TU_WEB_KEY';
            /////AQUI TU LOGICA///////
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;
            cc.src = './js/paybutton.min.js';
            //cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>

Listo!, ves que fácil. Ya estás a la mitad de implementar el botón.

**Paso 2: Configurar el cobro.**

Ahora lo que necesitas es agregar los datos para construir el cobro, tienes dos formas de hacerlo.











