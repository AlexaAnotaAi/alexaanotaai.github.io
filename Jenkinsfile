pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Esta a pipeline do site do AnotaAi.'
        mail(subject: '[Jenkins] Iniciando pipeline', body: 'Estamos iniciando a pipeline.', to: 'lana.mesquita@ufc.br')
        git(url: 'https://github.com/AlexaAnotaAi/alexaanotaai.github.io.git', branch: 'develop', credentialsId: 'github-ssh')
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('Teste') {
      steps {
        echo 'Iniciando teste...'
        sleep(unit: 'SECONDS', time: 15)
        build(job: 'unicorn-test', propagate: true)
      }
    }

    stage('Deploy') {
      when {
        branch 'main'
      }
      steps {
        input 'Espera pela confirma��o pra deploy.'
        echo 'Iniciando o deploy.'
      }
    }

  }
}