pipeline {
  agent any

  stages {

    stage('Commit') {
      steps {
        sh('''
          git clone --depth 1 https://github.com/folkehelseinstituttet/drat.git --brach gh-pages
          pwd
          ls
        ''')
      }
    }
  
    stage('Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'Github', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]){    
          sh('''
              echo 1
              #git config --local credential.helper "!f() { echo username=\\$GIT_USERNAME; echo password=\\$GIT_PASSWORD; }; f"
              #git push origin HEAD:release
          ''')
        }
      }
    }
  }
}
