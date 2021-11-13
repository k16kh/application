pipeline {
    agent any
      
   
    stages {

        stage("Pull") {
            steps {
                script {
                     checkout([$class: 'GitSCM' , branches: [[name: '*/master']],
		userRemoteConfigs: [[
		    credentialsId: 'github',
		    url:'https://github.com/k16kh/application.git']]])
                   
                }
            }
        }
        
        stage ("build")
        {		
        		steps {
        			script{
        			sh " sudo ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
        			}
        			}
        }
        
              stage ("docker")
        {		
        		steps {
        			script{
        			sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
        			}
        			}
        }
        
          
    }
    
     
}
