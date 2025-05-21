pipeline{
    agent any
    parametres{
        choice(name: 'ENV', choices: ["dev", "prod"], description: 'Среда деплоя:')
    }
    stages{
        stage('Message'){
            steps{
               sh 'echo "Deploying to ${ENV}"'
            }
        }
        stage('Clear Workdir'){
            steps{
                sh 'rm -rf .'
            }
        }
        stage('Send files to remote server'){
            sshPublisher(
                publishers:[
                    configName: "Ubuntu2",
                    transfers: [
                        sshTransfer(sourceFiles: ".")
                    ]
                ]
            )
        }
    }
}

