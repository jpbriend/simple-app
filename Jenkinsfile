node('jpb') {

    stage 'Checkout'
    checkout scm


    def mavenHome = tool name: 'maven-3.3', type: 'hudson.tasks.Maven$MavenInstallation'
    withEnv(["PATH+MAVEN=${mavenHome}/bin"]) {
        stage 'Build'
        sh 'mvn clean compile'

        stage 'Tests'
        sh 'mvn test'

        stage 'Package'
        sh 'mvn package'
    }
}
