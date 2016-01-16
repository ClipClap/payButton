## Web Pay Button##

ClipClap te permite incorporar la acción de pagar en tu página web de forma fácil y rápida. Sólo debes realizar estos sencillos pasos y listo.

## Prerrequisitos ##

 1. ***Tener una cuenta ClipClap Datáfono:***
Si no tienes una cuenta en ClipClap Datáfono, puedes hacer el proceso de registro siguiendo este [link](https://clipclap.co/datafono/dashboard/php/views/login.php){:target="_blank"} o desde la misma aplicación ClipClap Datáfono.

 2. ***Tener el webKey de tu negocio:***
Una vez tengas tu usuario Datáfono, tendrás que tener a la mano el “webKey” de tu negocio, puedes consultar los pasos para adquirirlos en detalle [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php){:target="_blank"}.

 3. ***Guardar el nombre del dominio de tu página:***
Debes Colocar el nombre del dominio de tu página para que te permitamos usar nuestro servicio. Si no lo haz hecho hazlo [aquí](https://clipclap.co/datafono/dashboard/php/views/settings.php){:target="_blank"}.

 4. ***ClipClap Billetera para tus clientes:***
Para que tus usuarios puedan acceder al evento de pago de ClipClap deben tener instalada la aplicación Billetera, esta permitirá realizar los pagos de forma rápida y segura para tus clientes.

 5. ***Entorno de Prueba y Entorno de Producción:***
Recuerda que puedes cambiar entre entorno de prueba y de producción, para llevar un mayor control de tu integración. puedes aprender cómo hacerlo en el siguiente [link](https://clipclap.co/datafono/dashboard/php/views/settings.php){:target="_blank"}.

 6. ***Formas de enviar información:***
Hay dos forma de crear un cobro para que ClipClap Billetera lo gestione:

a) *Forma 'producto por producto':* Esta opción permite agregar al cobro productos de forma individual especificando su nombre, precio , cantidad y el impuesto que debe llevar el producto.

b) *Forma 'total-impuesto-propina':* Esta opción permite definir el total a cobrar de forma inmediata especificando el total a cobrar, el impuesto a cobrar y de forma opcional la propina.
> ***Nota:*** Estas dos formas de crear el cobro son mutuamente excluyentes. Si usted utiliza ambas formas al mismo tiempo, la *forma 'total-impuesto-propina'* prevalece sobre la *forma 'producto-por-producto'*.

## Integración ##

Implementar el botón de pago es muy fácil. Te garantizamos que después de leer el documento te tomará 2 minutos realizar la implementación.

**Paso 1: Lo primero que debes hacer es crear una etiqueta button html y darle un identificador único, ya sea mediante el atributo id o el atributo class.
El siguiente es un ejemplo de una eqitueta button con un id que llamaremos 'botonClipClap'

``` html
    <button id="botonClipClap"></button>
```


Listo!, ves que fácil. Ya estás a la mitad de implementar el botón.

**Paso 2: Configurar el cobro.**

Ahora lo que necesitas es agregar los datos para construir el cobro. Supongamos que tu negocio vende productos de alimentos y quieres cobrar una hamburguesa por el costo de $8000, un perro caliente por el costo de $4000 y dos gaseosas por el costo de $2000 cada una. Agregarías los datos así:

*Forma 'producto por producto':*

        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'YOUR WEB KEY';
          _$clipclap._themeButton = "YOUR THEME";
          _$clipclap._Buttons = {
            "#botonClipClap":{
              'details': [{
                'itemCount': '1',
                'itemName': 'Hamburguesa',
                'itemValue': '8000',
                'taxId': '4'
              }, {
                'itemCount': '1',
                'itemName': 'Perro Caliente',
                'itemValue': '4000',
                'taxId': '4'
              }, {
                'itemCount': '2',
                'itemName': 'Gaseosa',
                'itemValue': '2000',
                'taxId': '4'
              }]
            }
          };
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;
            cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>

  Listo!!! ya tu negocio está listo para recibir dinero desde tu página web.

  Recuerda que debes reemplazar tu WEB Key en "YOUR WEB KEY" y puedes elegir el color del botón de pago entre blanco, azul y negro reemplazando white, blue o black donde dice "YOUR THEME" (por defecto es azul).
  Observa que hemos utilizado el id "botonClipClap", tu puedes colocar el que gustes, siempre y cuando el atributo id de la etiqueta `<button>` tenga el mismo nombre.

  > ***Nota:*** Es importante que mantengas la estructura donde dice _$clipclap._Buttons, es un formato muy específico llamado JSON *.

  La lista de impuestos, taxId es la siguiente:


    1 => IVA Regular del 16%
    2 => IVA Reducido del 5%
    3 => IVA Excento del 0%
    4 => IVA Excluído del 0%
    5 => Consumo Regular 8%
    6 => Consumo Reducido 4%
    7 => IVA Ampliado 20%

  También puedes enviar sólo el total, por ejemplo, tu negocio quiere vender un combo de Hamburguesa, perro y dos gaseosas por el costo de $13000, impuesto de $1000 y propina de $500. Puedes hacerlo así:

*Forma 'total-impuesto-propina':*

        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'YOUR WEB KEY';
          _$clipclap._themeButton = "YOUR THEME";
          _$clipclap._Buttons = {
            "#botonClipClap":{
              'netValue': '13000',
              'taxValue': '1000',
              'tipValue': '500',
              'description': 'Combo 1. Hambuerguesa, Perro y Gaseosa'
            }
          };
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;
            cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>

Existe una segunda forma de implementar el botón, y es la siguiente. Utiliza la que más te guste:

*Forma 'producto por producto':*

Establece los datos como atributo html

``` html
        <button id="test" data-clipclap="{
              'details': [{
                'itemCount': '1',
                'itemName': 'Hamburguesa',
                'itemValue': '8000',
                'taxId': '4'
              }, {
                'itemCount': '1',
                'itemName': 'Perro Caliente',
                'itemValue': '4000',
                'taxId': '4'
              }, {
                'itemCount': '2',
                'itemName': 'Gaseosa',
                'itemValue': '2000',
                'taxId': '4'
              }]
            }" ></button>
```
Coloca esto al final, reemplazando "YOUR WEB KEY" y "YOUR THEME"

        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'YOUR WEB KEY';
          _$clipclap._setButtons = "#test";
          _$clipclap._themeButton = "YOUR THEME";
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>
    </body>


*Forma 'total-impuesto-propina':*

Establece los datos como atributo html

``` html
        <button id="test" data-clipclap="{
              'netValue': '13000',
              'taxValue': '1000',
              'tipValue': '500',
              'description': 'Combo 1. Hambuerguesa, Perro y Gaseosa'
            }" ></button>
```

Coloca esto al final, reemplazando "YOUR WEB KEY" y "YOUR THEME"

        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'YOUR WEB KEY';
          _$clipclap._setButtons = "#test";
          _$clipclap._themeButton = "YOUR THEME";
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>
    </body>


Observa que esta vez, hemos llamado al botón por el id test

## Avanzado ##

Puedes implementar cuántas veces quieras el botón de pago en tu página web. Por ejemplo si quieres que tu pagína web tenga dos botones. Uno para enviar producto por producto, y uno para cobrar el combo completo, lo puedes hacer así:

``` html
        <button class="productos"></button>
        <button id="total"></button>
        <script type="text/javascript">
          var _$clipclap = _$clipclap || {};
          _$clipclap._setKey = 'YOUR WEB KEY';
          _$clipclap._setButtons = "#total";
          _$clipclap._themeButton = "YOUR THEME";
          _$clipclap._Buttons = {
            ".productos":{
              'details': [{
                'itemCount': '1',
                'itemName': 'Hamburguesa',
                'itemValue': '8000',
                'taxId': '4'
              }, {
                'itemCount': '1',
                'itemName': 'Perro Caliente',
                'itemValue': '4000',
                'taxId': '4'
              }, {
                'itemCount': '2',
                'itemName': 'Gaseosa',
                'itemValue': '2000',
                'taxId': '4'
              }]
            },
            "#total":{
              'netValue': '13000',
              'taxValue': '1000',
              'tipValue': '500',
              'description': 'Combo 1. Hambuerguesa, Perro y Gaseosa'
          }
          };
          (function() {
            var cc = document.createElement('script'); cc.type = 'text/javascript'; cc.async = true;cc.src = 'https://clipclap.co/paybutton/js/paybutton.min.js';
            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(cc, s);
          })();
        </script>
```

  > ***Nota:*** Utiliza sólo una forma de implementación, la primera enviando datos desde el script o la segunda enviando datos como atributos html.


Listo, ya tienes dos botones en la misma página para cobrar producto por producto y cobrar el total del combo.



