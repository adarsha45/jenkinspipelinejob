node{
    stage('checkout scm'){
        echo 'Checking out scm'
        checkout scm
    }
    stage('parameterized build'){
       properties([
        parameters([
            string(name: 'IMAGE_NAME', defaultValue: 'python-app', description: 'The name of the image to build'),
            string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'The tag of the image to build'),
            choice(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'The type of ENVIRONMENT to perform build', choices: ['dev', 'prod', 'uat']),
            boolean(name: 'isWorking', defaultValue: true, description: 'Is this Working'),
            string(name: 'REQ_INC', defaultValue: '1', description: 'The REQ_INC')
        ])
       ])
    }
    stage('Set build name'){
        currentBuild.description = "#${REQ_INC}"
    }
    stage('Build image'){
        echo 'Building image...'
        bat '''docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'''
    }
}