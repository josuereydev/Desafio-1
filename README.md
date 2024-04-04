El siguiente  script esta desarrollado para automatizar la creacion de usuarios de manera correcta y evitar errores ya que se venian cometiendo desde el area de IAM.
Con lo cual el paso numero uno es la creacion de un Pipeline en Jenkins que permita el despligue de lo solicitado.


Paso-1
Desarrollamos un  Pipeline  utilizando el editor de texto  Visual estudio Code para ejecutarlo en cualquier agente (any agent)

Paso-2
Ingresamos los parametros   string o cadena para introducir el Login, Nombre y Apellido

Un parametro choice  para seleccionar  del departamento al cual pertenece el usuario.

Paso-3
Pasamos a las etapas de la creacion del usuario y la generacion de la contraseña temporal que posteriormente  el usuario deberá cambiar segun lo solicitado.

Paso-4
Una vez completado el codigo  vinculamos nuestra cuenta GitHub para poder subir el codigo desarrollados a nuestro repositorio y que Jenkins pueda tomarlo y para automatizar la tarea.

Paso-5  Una vez en Jenkins le damos click en Buil o Construir  Imgresamos los datos  Solicitados  y Ejecutamos.
 