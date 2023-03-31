pipeline {
  agent {
      label ("built-in")
  }
  stages {
    stage ("install ") {
      steps {
                sh "curl -SL https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose"
                sh "sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose"
                sh "chmod -R 777 /usr/local/bin/docker-compose /usr/bin/docker-compose"
                sh "yum install docker -y"
                sh "systemctl start docker"
      }
    }
    stage ("build_gol") {
      steps {
                sh "mvn install"    
      } 
    }    
    stage ("docker_compose") {
      steps {
                sh "docker-compose up -d"
      } 
    }
     
     stage ("deploy") {
      steps {
                sh "cp -r /root/.jenkins/workspace/database/target/gameoflife.war /mnt/wars"
      } 
    }
  } 
}
