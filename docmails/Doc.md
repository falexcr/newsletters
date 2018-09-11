# Css para mails

Condicionales de Outlook

Proporcionar una Hoja de estilos especificos de Outlook, similar a lo que se hace para correos electronicos moviles.
utilizando comentarios condicionales de Microsoft, y puede ser colocado despues de la CSS principal.

```
<!--[if gte mso 9]>
    <style type="text/css">
    /* Your Outlook-specific CSS goes here. */
    </style>
<![endif]-->
```
se agrega el ´gte´ en comentario para solo aplicarse en versiones Microsoft mayor o igual a 9. tambien se puede hacer objetivo menor, o versiones anteriores, mediante el uso de 'lt'. Usando ´gt´ y 'lte' se centrara en versiones de mayores o menor que o igual a, respectivamente

#Numeros de versiones de Outlook

Utilizando version numeros le permite a clientes especificos de Outlook, eje 'mso 9' es Office 2000, lo que significa que esta dirigido a Outlook 2000, otros numeros de version:

Outlook 2000 - versión 9
Outlook 2002 - versión 10
Outlook 2003 - versión 11
Outlook 2007 - Version 12
Outlook 2010 - versión 14
Outlook 2013 - versión 15

#Outlook 2007-2010

Outlook tiene un limite de longitud de 22 pulgadas o alrededor de 1800px. Cuando un correo electronico, pasa esa longitus, Outlook inserta un salto de pagina para impresion de documentos.

###Estilos CSS especificos del clientes

#Outlook.com / Hotmail

.ExternalClass clase anulacion

Cuando se tira un correo electronico en Outlook/Hotmail, cualquier regla de estilo presente en el correo electronico se adjunta con .ExternalClass. ejem

```
estos puede ayudar a crear una base de trabajo de.
.ExternalClass{
    width:100%;
}

.ExternalClass,
.ExternalClass p,
.ExternalClass span,
.ExternalClass font,
.ExternalClass td,
.ExternalClass div{
    line-height: 100%;
}
```

Outlook establece su propio color (Verde bruto) en los elementos de partida baja en nivel que el elemento <h1>, se puede cambiar al aplicar un !important en la propiedad color.
ejem

```
declaración de propiedad de color de la partida:
h2{
    color:#0066CC !important;
}
```

Propiedad para enlaces

```
#outlook a{
    padding:0;
}
```
Deshacerse se espacios creados por outlook a la izquierda y derecha de un elemento <table> Utilizando las propiedades CSS de mso-table-lspace y mso-table-rspace
```
table{
    mso-table-lspace:0pt;
    mso-table-rspace:0pt;
}
```
###OSX / IOS

Ajustes de tamaño de texto de WebKit


```
body{
    -webkit-text-size-adjust:100%;
}
```

Cuando IOS detecta un numero de telefono, direccion o fecha del calendario, establece esos elementos como enlaces para facilitar la llamada a la accion inmediatamente, El problema es que los colores de enlace son por defecto #0000ff (Azul oscuro).

En primer lugar, el numero de telefono. En el <head>

```
<meta name="format-detection" content="telephone=no">
```

Para detectar automaticamente se le coloca la propiedad de llamar al atributo href con un valor tel.

```
<a href="tel:1-800-555-5555">1-808-555-5555</a>
```

### Responsive

La estructura de los Media Queries es bastante simple. Para fines de correo electronico y estan anidados dentro de la etiqueta <style>

```
<style type="text/css">
    .standardCSS{
        color:#505050;
        font-size:15px;
    }

    @media only screen and (max-width:480px){
        .mediaQueryCSS{
            color:#CCCCCC;
            font-size:20px;
        }
    }
</style>
```

mas informacion de estilos

https://templates.mailchimp.com/development/responsive-email/

#CSS soportados

https://templates.mailchimp.com/resources/email-client-css-support/
