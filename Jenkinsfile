node {
    stage('Checkout') {
            
        echo 'Github checkout....'
        checkout scm
        sh 'pwd'
    }
    stage('GoBuild') {
        def code = pwd()
        def root = tool name: 'go1.6.2', type: 'go'
        withEnv(["GOPATH=${code}", "PATH+GO=${root}/bin"]){
        
        sh 'go build main.go'

        }
    }

    stage('DockerBuild'){
        sh 'cp goBot docker'
        dir('docker'){
            docker.build("doctornkz/gobot")
    
        }

    }   
    
    stage('Test') {
        echo 'Building....'
    }

    stage('Deploy') {
        echo 'Deploying....'
    }
}