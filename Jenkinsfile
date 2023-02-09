pipeline {
  agent {
    node {
      label 'target'
    }
 
  }
  stages {
    stage('updated index.html') {
      steps {
        git(url: 'https://github.com/WesJohnson-wrk/index_test', branch: 'main')
      }
    }
 
    stage('replace index.html') {
      steps {
        sh '''whoami
pwd
ls
cat index.html
sudo cp index.html /var/www/html/index.html
ls
sudo cat /var/www/html/index.html
pwd
'''
      }
    }
 
  }
}
