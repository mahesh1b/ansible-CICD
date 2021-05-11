pipeline{
    agent any
    
    stages{
        
        stage('creating a role'){
            steps{
                sh 'ansible-galaxy init httpd-role'
            }
        }
        
        stage('getting code from git'){
            steps{
                sh 'git clone https://github.com/mahesh1b/ansible-CICD' 
            }
        }
        
             stage('adding content to role'){
            steps{
                sh 'cp ansible-CICD/main.yml httpd-role/tasks/' 
                sh 'cp ansible-CICD/index.html.j2 httpd-role/templates/' 
            }
        }
        
               stage('creating playbook'){
            steps{
                sh 'cp ansible-CICD/apache.yml httpd.yml' 
                sh 'cp ansible-CICD/server.inv server.inv'
            }
        }
        
         stage('executing a playbook'){
            steps{
                ansiblePlaybook credentialsId: 'server', disableHostKeyChecking: true, installation: 'ansible', inventory: 'server.inv', playbook: 'httpd.yml'  
                }
        }
    }
}
