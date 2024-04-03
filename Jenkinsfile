pipeline { 
    agent any 
     
    parameters { 
        string(name: 'LOGIN', description: 'Login del usuario') 
        string(name: 'NOMBRE_APELLIDO', description: 'Nombre y Apellido del usuario') 
        choice(name: 'DEPARTAMENTO', choices: ['contabilidad', 'finanzas', 'tecnología'], description: 'Departamento del usuario') 
    } 
     
    stages { 
        stage('Crear Usuario') { 
            steps { 
                script { 
                    def tempPassword = sh(script: "openssl rand -base64 12 | tr -d '=' | tr -d '+' | tr -d '/' | tr -d '\n'", returnStdout: true).trim() 
                    sh "sudo useradd -m -s /bin/bash -g ${params.DEPARTAMENTO} ${params.LOGIN}" 
                    sh "echo ${params.LOGIN}:${tempPassword} | sudo chpasswd" 
                } 
            } 
        } 
    } 
     
    post { 
        success { 
            script { 
                def emailBody = "Estimado ${params.NOMBRE_APELLIDO},\n\nSe ha creado una cuenta para usted en nuestro sistema.\n\nLogin: 
                ${params.LOGIN}\nPassword temporal: ${tempPassword}\n\nPor favor, recuerde cambiar su contraseña en su primer inicio de sesión.\n\nSaludos,\nEquipo de Seguridad" 
                emailext body: emailBody, subject: 'Cuenta de usuario creada', to: 'usuario@example.com' 
} 
} 
} 
}