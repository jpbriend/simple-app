node {
    stage 'Checkout'
    checkout scm

    stage 'Build'
    withMaven {
        sh 'mvn clean verify'
    }

    stash name: 'binary', includes: "target/*.war"
}


// Custom step
def withMaven(def body) {
    def javaHome = tool name: 'oracle-8u77', type: 'hudson.model.JDK'
    def mavenHome = tool name: 'maven-3.3.9', type: 'hudson.tasks.Maven$MavenInstallation'

    withEnv(["JAVA_HOME=${javaHome}", "PATH+MAVEN=${mavenHome}/bin"]) {
        body.call()
    }
}
