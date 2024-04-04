El siguiente  script esta desarrollado para automatizar la creacion de usuarios de manera correcta y evitar errores ya que se venian cometiendo desde el area de IAM.
Con lo cual el paso numero uno es la creacion de un Pipeline en Jenkins que permita el despligue de lo solicitado.

Iniciamos el Pipeline para ejecutarlo en cualquier agente (any agent)
Ingresamos los parametros   string o cadena para introducir el Login, Nombre y Apellido
Un parametro choice  para seleccionar  del departamento al cual pertenece el usuario.
Pasamos a las etapas de la creacion del usuario y la generacion de la contraseña temporal que posteriormente  el usuario deberá cambiar segun lo solicitado.
 