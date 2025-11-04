# **Lambda** en AWS

Las funciones **Lambda** son una de las herramientas dentro de **Serverless (Sin servidores)**, normalmente este tipo de servicios son ofrecidos por grandes proveedores como **Lambda functions** en Amazon, **Cloud Functions** en Google y **Azure functions** en Azure.

## Características

Las funciones **Lambda** no requieren de un servidor administrado por el propio desarrollador o empresa, básicamente no hay que montar ningún tipo de servidor desde cero con todas las implicaciones para que este tipo de cosas funcionen. Dado esto, empresas como Amazon proveen contenedores con todo lo necesario para que el código sea funcional.

Por consiguiente, los desarrolladores únicamente tienen que escribir el código, subirlo a Lambda y realizar unas pocas configuraciones.

Los recursos, la administración y la escalabilidad de estos son controlados automáticamente por **Amazon**.

### Costo
Normalmente, **Amazon** cobra por el uso de memoria durante el tiempo de ejecución, más un valor adicional por la cantidad de veces que la función lambda fue ejecutada.

Si se quiere revisar más a fondo cuánto puede costar, Amazon proporciona la siguiente calculadora para calcular los costos de la función.

[Calculadora de costos](https://aws.amazon.com/es/lambda/pricing/)

## ¿Cuándo deberían los desarrolladores o las empresas pensar en utilizar funciones Lambda?
* Cuando es necesario realizar integraciones, por ejemplo, servicios de API, correo electrónico, etc.
* Procesamiento de archivos, por ejemplo, compresión de imágenes, transcodificación de contenido, etc.
* Streaming de datos, por ejemplo, procesamiento de transacciones, datos telemáticos, etc.

Una función **Lambda** es una unidad que ejecuta una acción muy específica de la lógica de negocio o de la lógica funcional y debe estar restringida a una única tarea específica. Esto es útil para tareas que suelen tener el mismo tiempo de ejecución en cada implicación. Sin embargo,  una función **Lambda** no puede ejecutarse por siempre (actualmente las funciones lambda tienen un tiempo máximo de ejecución de hasta 15 minutos)

## Qué son y cómo funcionan?

Actualmente, se tienen disponibles los siguientes ambientes de ejecución:
* Java
* Node.js
* Python
* .Net
* Ruby
* Go

Sin embargo, en el caso de necesitar un lenguaje diferente a estos, es necesario utilizar la API de AWS para crear ambientes personalizados de ejecución. Esto nos permite poder ejecutar funciones lambdas escritas en cualquier lenguaje de programación.

### Ciclo de vida de una función Lambda

Una vez se haya escrito el códigofunción, este se sube a AWS y se define el evento de activacióncódigo para la funcionactivaciónfunción Lambda. Una vez que la funcionfunciónfunción recibe el evento, Amazonfunción crea un contenedor con el ambiente configurado y el codigo, Amazoncódigo de la funcion. códigofunción. Posteriormente función. Posteriormente,se ejecuta el código;Posteriormente,código; en este punto se puede reutilizar el container o no,, dependiendo deliempo que haya pasado desde la última ejecución. Si el tiempo es corto,, se reutiliza el contenedor; en caso de que sea muy largo, el contenedor es desechado.


En caso de haber muchas peticiones, se crean nuevos contenedores y, si no es posible utilizar uno disponible, se creará un nuevo contenedor que ya haya finalizado con la tarea.

Nota: Los eventos de activación pueden entregar datos de entrada para las funciones Lambda.


### Consideración

Se recomienda que las funciones lambda sean idempotentes (básicamente, que si hay más de una ejecución, no se vea afectada la lógica); esto debe ser así, puesto que Amazon cumple con el criterio de ejecutar la función al menos una vez, por lo cual podemos tener más de una ejecución.

Esto es aún más recomendable si se requiere manejar transacciones bancarias u otro tipo de transacciones que no deberían duplicarse.