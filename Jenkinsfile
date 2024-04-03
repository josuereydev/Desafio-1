pipeline {
    agent any //Define que este pipeline puede ejecutarse en cualquier agente disponible en jenkins
    
    parameters { //define los parametros que se solicitaran al usuario al iniciar el trabajo en jenkins
        string(name: 'LOGIN', description: 'Ingresa el usuario', defaultValue: '') //parametro para el nombre de usuario
        string(name: 'NOMBRE y APELLIDO', description: 'Ingresa el Nombre y Apellido del Usuario', defaultValue: '') // parametro para el nombre y apellido
        choice(name: 'DEPARTAMENTO', choices: ['Contabilidad', 'Finanzas', 'Tecnología'], description: 'Seleccione el Departamento del Usuario') //parametro para seleccionar departamento
    }

    stages { //define las etapas del pipeline
        stage('Crear usuario') { //primera etapa: crear el usuario en el sistema
            steps { //define los pasos dentro de esta etapa
                sh "sudo useradd -m -s /bin/bash -c '${Nombre y Apellido}' ${Login}" //crea un nuevo usuario en el sistema con los parametros proporcionados
            }
        }
///
        stage('Generar password temporal') { //Segunda Etapa: generar una contraseña temporal para el usuario creado
            steps { //define los pasos dentro de esta etapa
                script { //inicia un bloque de script groovy
                    def passwordTemporal = sh(script: 'sudo openssl rand -base64 10', returnStdout: true).trim() //genera una nueva contraseña temporal aleatoria
                    echo "Su contraseña es: ${passwordTemporal}" //muestra la contraseña temporal al usuario
                    env.PASSWORD_TEMPORAL = passwordTemporal //Almacena la contraseña temporal en una variable de entorno para usarla mas tarde
                }
            }
        }

        stage('Asignar contraseña temporal') { //Tercera etapa: asignar la contraseña temporal al usuario creado
            steps {//define los pasos dentro de esta etapa
                sh "echo ${Login}: ${PASSWORD_TEMPORAL} | sudo chpasswd" //Asigna la contraseña temporal al usuario creado
            }
            }
            }
            }
 