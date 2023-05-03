node{
     
    stage('SCM Checkout'){
        git url: 'https://gitlab.com/devopswebelight/webelight_practical_test.git',branch: 'master'
    }
  
    
    stage('Build Docker Image'){
        sh 'docker build -t karthikeyinid/webelight_practical_test .'
    }
    
    stage('Push Docker Image'){
        withCredentials([string(credentialsId: 'Docker_Hub_Pwd', variable: 'Docker_Hub_Pwd')]) {
          sh "docker login -u karthikeyinid -p ${Docker_Hub_Pwd}"
        }
        sh 'docker push karthikeyinid/webelight_practical_test'
     }
     
      stage('Run Docker Image '){
        
        def dockerRun = ' docker run  -d -p 5050:5050 --name webelight_practical_test karthikeyinid/webelight_practical_test'
        
       }
       
    }
     
     
}
