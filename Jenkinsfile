pipeline{
    agent any
    parameters{
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
                sh 'rm -rf *'
            }
        }
        stage('Send files to remote server'){
            steps{
                sshPublisher(
                publishers: [
                    sshPublisherDesc(
                        configName: "Ubuntu2",
                            transfers: [
                                sshTransfer(sourceFiles: "*")
                            ]
                        )
                    ]
                )
            }
        }
    }
}

