pipeline {
    agent any 
    
    parameters { 
        string(name: 'LOGIN', description: 'Ingresar el UserID', defaultValue: '') 
        string(name: 'NombreApellido', description: 'Ingresar Nombre y Apellido del Usuario', defaultValue: '') 
        choice(name: 'DEPARTAMENTO', choices: ['Contabilidad', 'Finanzas', 'Tecnología'], description: 'A que depto pertenece el Usuario:') 

    stages { 
        stage('Crear usuario') { 
            steps { 
                sh "sudo useradd -m -s /bin/bash -c '${NombreApellido}' ${Login}"
        }
///
        stage('Generar password temporal') { 
            steps { 
                script { 
                    def passwordTemporal = sh(script: 'sudo openssl rand -base64 10', returnStdout: true).trim()
                    echo "Su contraseña es: ${passwordTemporal}" 
                    env.PASSWORD_TEMPORAL = passwordTemporal 
                }
            }
        }

        stage('Asignar contraseña temporal') { 
            steps {
                sh "echo ${Login}: ${PASSWORD_TEMPORAL} | sudo chpasswd" 
            }
            }
            }
            }

