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
    def javaHome = tool name: 'oracle-8u77', type: 'hudson.model.JDK'

    withEnv(["PATH+MAVEN=${mavenHome}/bin"]) {
        body.call()
    }
}
