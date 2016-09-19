node('maven') {
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
    def mavenHome = tool name: 'maven-3.3.9', type: 'hudson.tasks.Maven$MavenInstallation'

    withEnv(["PATH+MAVEN=${mavenHome}/bin"]) {
        body.call()
    }
}
