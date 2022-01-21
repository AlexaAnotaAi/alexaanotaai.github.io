pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Esta a pipeline do site do AnotaAi.'
        mail(subject: '[Jenkins] Iniciando pipeline', body: 'Estamos iniciando a pipeline.', to: 'lana.mesquita@ufc.br')
        git(url: 'https://github.com/AlexaAnotaAi/alexaanotaai.github.io.git', branch: 'main', credentialsId: 'github-ssh')
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('Test') {
      parallel {
        stage('Teste') {
          steps {
            echo 'Iniciando teste...'
            sleep(unit: 'SECONDS', time: 15)
            junit '*.html'
          }
        }

        stage('Teste W3C') {
          steps {
            build 'unicorn-test'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Iniciando o deploy.'
      }
    }

  }
}