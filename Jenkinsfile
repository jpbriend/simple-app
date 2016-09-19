node('maven') {
    stage 'Checkout'
    checkout scm

    stage 'Build'
    sh 'mvn clean verify'
}
