pipeline {
  agent any

  stages {

    stage('Update') {
      steps {
        sh('''
          git -C C:/Users/raw996/Documents/GitHub/drat pull
          dir
        ''')
      }
    }

    stage('Build') {
      steps {
        sh('''
          C:/Program Files/R/R-4.0.2/bin/Rscript.exe -e 'install.packages("devtools")'
          C:/Program Files/R/R-4.0.2/bin/Rscript.exe -e 'devtools::install_github("folkehelseinstituttet/drathelper")'
          C:/Program Files/R/R-4.0.2/bin/Rscript.exe 'drathelper::source_to_binary(packages_to_build = "fhi", drat_repo = "C:/Users/raw996/Documents/GitHub/drat")
        ''')
      }
    }
  
    stage('Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'Github', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]){    
          sh('''
              echo 1
              #git config --local credential.helper "!f() { echo username=//$GIT_USERNAME; echo password=//$GIT_PASSWORD; }; f"
              #git push origin HEAD:release
          ''')
        }
      }
    }
  }
}
