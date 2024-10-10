pipeline {
    agent any
    
    tools {
        maven 'maven'
    }
    
    stages {
        stage ("Start CI & git checkout"){
            steps {
                echo "CI Start"
                echo "GIT CHECKOUT"
                git branch: "main", url: "https://github.com/nbhovare/simple-app-java"
            }
        }
        stage ("Maven Install || Maven clean test package"){
            steps {
                sh "pwd"
               sh "mvn clean test package"
            }
        }
        
        stage ("Publish Over SSH") {
            steps {
                
                sshPublisher(publishers: [sshPublisherDesc(configName: 'dockeradmin', 
                transfers: [
                sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'target/*.war'), 
                sshTransfer(cleanRemote: false, excludes: '', 
                execCommand: '''
                    touch file.txt 
                    sudo docker build -t tomcat:v1 .
                    sudo docker run -d --name tomcat -p 8086:8080 tomcat:v1
                ''', 
                execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'Dockerfile')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
        
        stage ("End CI"){
            steps {
                echo "CI END"
                
            }
        }
    }
}
