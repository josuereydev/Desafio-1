pipeline { 
    agent any 
     
    parameters { 
        string(name: 'LOGIN', description: 'Ingrese el login del 
usuario') 
        string(name: 'NOMBRE_APELLIDO', description: 'Ingrese el 
nombre y apellido del usuario') 
        choice(name: 'DEPARTAMENTO', choices: ['contabilidad', 
'finanzas', 'tecnología'], description: 'Seleccione el departamento 
del usuario') 
    } 
 
    stages { 
        stage('Crear Usuario') { 
            steps { 
                script { 
                    def login = params.LOGIN 
                    def nombreApellido = params.NOMBRE_APELLIDO 
                    def departamento = params.DEPARTAMENTO 
                    def passwordTemporal = generatePassword() 
 
                    sh "sudo useradd -m -s /bin/bash -g $departamento 
$login" 
                    sh "echo $login:$passwordTemporal | sudo chpasswd" 
 
                    echo "Usuario creado: $login" 
                    echo "Password temporal: $passwordTemporal" 
                } 
            } 
        } 
    } 
} 
 
def generatePassword() { 
    def charset = 
"ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789" 
    def password = "" 
    8.times { 
        password += charset[Math.floor(Math.random() * 
charset.length())] 
    } 
    return password 
} 
 