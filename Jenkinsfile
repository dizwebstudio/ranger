node('linux') {   // если у твоего агента другая метка — замени 'linux' на свою (или просто node {})
  stage('Checkout') {
    // Если джоб настроена как "Pipeline script from SCM", то достаточно:
    checkout scm
  }

  stage('Env') {
    sh 'java -version'
    sh 'mvn -version'
  }

  stage('Build') {
    // первая сборка без тестов (потом можно включить)
    sh 'mvn -B -V -Pall -DskipTests clean package'
  }

  stage('Archive') {
    archiveArtifacts artifacts: '**/target/*.jar,**/target/*.war,**/target/*.tar.gz,**/target/*.zip',
                     fingerprint: true,
                     onlyIfSuccessful: true
  }
}
