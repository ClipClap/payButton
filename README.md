## Web Pay Button##

ClipClap te permite incorporar la acción de pagar en tu página web de forma fácil y rápida. Sólo debes realizar estos sencillos pasos y listo.

## Prerrequisitos ##

 1. ***Tener una cuenta ClipClap Datáfono:***
Para poder realizar la integración con ClipClap debes primero tener una cuenta en ClipClap Datáfono, puedes hacer el proceso de registro siguiendo este [link](https://clipclap.co/) o desde la misma aplicación ClipClap Datáfono.

 2. ***Tener el webKey de tu negocio:***
Una vez tengas tu usuario Datáfono, tendrás que tener a la mano el “webKey” de tu negocio, puedes consultar los pasos para adquirirlos en detalle [aquí](https://clipclap.co/).

 3. ***Guardar el nombre del dominio de tu página:***
Debes Colocar el nombre del dominio de tu página para que te permitamos usar nuestro servicio. Si no lo haz hecho hazlo aquí [aquí](https://clipclap.co/).

 4. **ClipClap Billetera para tus clientes:**
Para que tus usuarios puedan acceder al evento de pago de ClipClap deben tener instalada la aplicación Billetera, esta permitirá realizar los pagos de forma rápida y segura para tus clientes.

 5. ***Entorno de Prueba y Entorno de Producción:***
Recuerda que puedes cambiar entre entorno de prueba y de producción, para llevar un mayor control de tu integración. puedes aprender cómo hacerlo en el siguiente [link](https://clipclap.co/).


## Integración ##

Implementar el botón de pago es muy fácil. Te garantizamos que después de leer el documento te tomará 2 minutos realizar la implementación.

**Paso 1: Lo primero que debes hacer es copiar y pegar este código en la página donde quieres que aparezaca el/los botones de pago.

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

Ahora lo que necesitas es agregar los datos para construir el cobro

Hay dos forma de crear un cobro para que ClipClap Billetera lo gestione:

 1) *Forma 'producto por producto':* Esta opción permite agregar al cobro productos de forma individual especificando su nombre, precio, cantidad y el impuesto que se le aplica al producto. Así:



2) *Forma 'total-impuesto-propina':* Esta opción permite definir el total a cobrar de forma inmediata especificando el total a cobrar sin impuestos, el impuesto sobre el total y de forma opcional la propina. Así:



> ***Nota:*** Estas dos formas de crear el cobro son mutuamente excluyentes. Si usted utiliza ambas formas al mismo tiempo, la *forma 'total-impuesto-tip'* prevalece sobre la *forma 'producto-por-producto'*.

**Paso 3: Decirle a ClipClap Billetera que realice el cobro**

  //Implementa este código para de obtener de ClipClap un token único para este cobro. Hasta este momento todavía el cobro no se ha hecho efectivo.

  paymentButton.setSaveTokenListener(new SaveTokenListener() {

      @Override
        public void saveToken(String token) {

               //Antes de llamar a ClipClap Billetera guarda el 'token' retornado aquí en tu sistema de información.

                //LLamando a ClipClap Billetera para que gestione el cobro.
               try {
                    Uri uri = Uri.parse(button.getUrl());
                    Intent intent = new Intent(Intent.ACTION_VIEW, uri);
                    startActivity(intent);
                }catch (Exception e){
                 //LLama a la PlayStore si no está instalada
                    Uri uri = Uri.parse(PayAndGo.PLAYSTORE);
                    Intent intent = new Intent(Intent.ACTION_VIEW, uri);
                    startActivity(intent);
                }
            }
        });






