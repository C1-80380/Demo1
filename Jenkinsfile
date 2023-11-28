pipeline {
     agent any

      stages {
         stage ('SCM') {
               steps {
                  git branch: 'master', url: 'https://github.com/C1-80380/Demo1.git'
               }
           }
          stage ('docker login') {
              steps {
                  sh 'echo dckr_pat_WutX3ighYn5leDCE1jYhdftLlxg | /usr/bin/docker login -u shrijeet99 --password-stdin'
              }
          }
          stage ('docker build image') {
             steps {
                 sh '/usr/bin/docker image build -t shrijeet99/exercise2 .'
              }
          }
          stage ('docker push image') {
              steps {
                  sh '/usr/bin/docker image push shrijeet99/exercise2'
              }
          }
          stage ('docker remove service') {
              steps {
                  sh '/usr/bin/docker service rm my-service'
              }
          }
          stage ('docker create service') {
              steps {
                  sh '/usr/bin/docker service create --name my-service -p 9876:80 --replicas 4 shrijeet99/exercise2'
             }
          }
      }
  }

