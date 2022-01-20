pipeline {
  agent any
  stages {
    stage('Inicializar / Mensagem') {
      steps {
        echo 'Esta a pipeline do site do AnotaAi.'
        mail(subject: '[Jenkins] Iniciando pipeline', body: 'Estamos iniciando a pipeline.', to: 'lana.mesquita@ufc.br')
      }
    }

  }
}