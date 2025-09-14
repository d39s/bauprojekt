@Library('d39s-jenkins-library@remove-eval') _

pipeline {
    agent none
    options {
        ansiColor('xterm')
        disableConcurrentBuilds()
    }
    stages {
        stage('Download') {
            agent {
                kubernetes {
                    inheritFrom 'rclone'
                    defaultContainer 'rclone'
                }
            }
            options {
                skipDefaultCheckout()
            }
            environment {
                NC_URL = credentials('nextcloud-url')
                NC_USERNAME = credentials('nextcloud-username')
                NC_PASSWORD = credentials('nextcloud-password')
            }
            steps {
                downloadNextcloud from: '/Anpassung Referenzen/', to: 'src/assets/referenzen/', extraArgs: [
                    '--include',
                    '/{{referenz-\\d+/[^/]+\\.(json|jpg|png)}}'
                ]
                stash includes: '**', name: 'referenzen'
            }
        }
        stage('Build') {
            agent {
                kubernetes {
                    inheritFrom 'kaniko'
                    defaultContainer 'kaniko'
                }
            }
            steps {
                unstash 'referenzen'
                kaniko()
            }
        }
    }
}
