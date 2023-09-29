pipeline{
agent any
environment {
  name = "durga rao"
  course = "Jenkins"
}
stages {
  stage('checkout') {
    steps {
     git 'https://github.com/jenkins-docs/simple-java-maven-app.git'
     echo "code checkout is complete in stage ${stageVariable} by user ${name}"
    }

    environment {
      stageVariable = "checkout"
    }
  }

  stage('compile and package') {
    steps {
     sh 'mvn -B -DskipTests clean package'
    }
  }

  stage('test') {
    steps {
    sh 'mvn test'
    }
    post {
  success {
junit '**/target/surefire-reports/*.xml'
  }
}
  }

  stage('archive') {
    steps {
    archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
    }
  }

}


}



