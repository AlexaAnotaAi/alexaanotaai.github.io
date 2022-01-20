pipeline {
  agent any
  stages {
    stage('Inicializar') {
      steps {
        echo 'Esta a pipeline do site do AnotaAi.'
        mail(subject: '[Jenkins] Iniciando pipeline', body: 'Estamos iniciando a pipeline.', to: 'lana.mesquita@ufc.br')
        git(url: 'https://github.com/AlexaAnotaAi/alexaanotaai.github.io.git', branch: 'main', credentialsId: 'github-ssh')
      }
    }

    stage('Teste') {
      steps {
        echo 'Iniciando teste...'
      }
    }

  }
}