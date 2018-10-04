node {
    docker.image('centos').inside {
        stage('Stage1') {
            sh 'yum --version'
        }
        stage('Stage2') {
            node {
                docker.image('docker.elastic.co/elasticsearch/elasticsearch:5.2.2').withRun('-p 9200:9200 -e "http.host=0.0.0.0" -e "transport.host=127.0.0.1"') {
                }
                sh "curl 127.0.0.1:9200/_search -u elastic:changeme"
            }
        }
    }
}