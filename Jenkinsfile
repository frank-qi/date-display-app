def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
    containerTemplate(name: 'docker', image: 'node:carbon-jessie', command: 'cat', ttyEnabled: true),
]) {
    node(label) {
            stage('Step 1') {
                echo "Your Pipeline works!"
                sh('ls -la')

                sh('git clone "https://github.com/frank-qi/date-display-app"')

                echo "Here's what you cloned!"
                sh('ls -la')
            }

            stage('Testing') {
                container('docker') {
                    container('docker') {}
                    echo "TESTINGGGGGG!!!!"
                    sh('npm install')
                    sh('npm test')
                }
            }
    }
}
