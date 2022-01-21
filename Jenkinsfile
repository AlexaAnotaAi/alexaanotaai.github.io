pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Esta a pipeline do site do AnotaAi.'
        mail(subject: '[Jenkins] Iniciando pipeline', body: 'Estamos iniciando a pipeline.', to: 'lana.mesquita@ufc.br')
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('Teste') {
      post {
        success {
          mail(subject: '[Jenkins] Deu certo!! ', body: 'Código testado e em produção.', to: 'lana.mesquita@ufc.br')
        }

        failure {
          mail(subject: '[Jenkins] Deu ruim!! ', body: 'Veja o Jenkins para identificar o problema.', to: 'lana.mesquita@ufc.br')
        }

      }
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
        input 'Espera pela confirmacao pra deploy.'
        echo 'Iniciando o deploy.'
      }
    }

  }
  triggers {
    pollSCM('30 15 * * *')
  }
}