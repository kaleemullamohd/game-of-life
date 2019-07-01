node {
    stage ('Stage SCM'){
        git 'https://github.com/kaleemullamohd/game-of-life.git'
    }
    stage ('Stage Package') {
        sh label: 'building package', script: 'mvn package'
    }
    stage ('Archive atrifacts'){
        archive 'gameoflife-web/target/gameoflife.war'
    }
    stage ('Test reports'){
        junit 'gameoflife-web/target/surefire-reports/*.xml'
    }
}