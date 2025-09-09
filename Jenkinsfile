pipeline {
  agent none

  stages {
    stage('Build Android App and Archive APK') {
      agent {
        dockerfile {
          dir '.'
          args '-u root:root'
        }
      }

      stages {
        stage('Build APK') {
          steps {
            sh 'chmod +x gradlew'
            sh './gradlew clean assembleDebug'
          }
        }

        stage('Archive APK') {
          steps {
            archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk', followSymlinks: false
          }
        }
      }
    }
  }
}
