pipeline{
agent any
environment {
  name = "durga rao"
  course = "Jenkins"
}
stages {


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



