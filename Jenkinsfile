def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
    containerTemplate(name: 'docker', image: 'node:carbon-jessie', command: 'cat', ttyEnabled: true),
]) {
    node(label) {
        container('docker') {
            stage('Step 1') {
                echo "Your Pipeline works!"
                sh('ls -la')

                //sh('git clone "https://github.com/frank-qi/date-display-app"')
                checkout scm

                echo "Here's what you cloned!"
                sh('ls -la')
            }

            stage('Testing') {
                echo "TESTINGGGGGG!!!!"
                //sh('cd date-display-app; npm install; npm test')
                sh('npm install')
                sh('npm test')
            }
            
            stage('Pushing Docker Image') {
                sh('docker build -t slalomdojo/team1_image .')
                sh('ls -la')
            }
        }
    }
}
