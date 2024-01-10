pipeline {
    agent any
    parameters {
        choice(name: 'NUMBER',
            choices: [10,20,30,40,50,60,70,80,90],
            description: 'Select the value for F(n) for the Fibonnai sequence.')
    }
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    triggers {
        cron '@midnight'
    }
    stages {
        stage('Make executable') {
            steps {
                bat 'echo make exec step'
            }
        }
        stage('Relative path') {
            steps {
                bat ".\\scripts\\fibonacci.sh %NUMBER%"
            }
        }
        stage('Full path') {
            steps {
                bat "%WORKSPACE%\\scripts\\fibonacci.sh %NUMBER%"
            }
        }
        stage('Change directory') {
            steps {
                bat "cd %WORKSPACE%\\scripts && .\\fibonacci.sh %NUMBER%"
            }
        }
    }
}
