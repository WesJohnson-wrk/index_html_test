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

    stage('metadata') {
      steps {
        sh '''ID=$(curl http://169.254.169.254/latest/meta-data/instance-id)
sudo sed -i "s/_ID/$ID/" /var/www/html/index.html
AZ=$(curl http://169.254.169.254/latest/meta-data/placement/availability-zone)
sudo sed -i "s/_AZ/$AZ/" /var/www/html/index.html
'''
      }
    }

  }
}