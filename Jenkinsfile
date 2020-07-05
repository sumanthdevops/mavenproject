pipeline { 
    agent any  
    stages { 
        stage('git clone') { 
                git url: "https://github.com/sumanthdevops/mavenproject/edit/master"
                  }
        stage('Maven build') {  
               goals: 'clean package'
             
            }
        }   
}
