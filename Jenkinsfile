def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
    containerTemplate(name: 'npm', image: 'node:carbon-jessie', command: 'cat', ttyEnabled: true),
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)
],
volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
]) {
    node(label) {
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

            container('npm') {
                sh('npm install')
                sh('npm test')
            }
        }

        stage('Pushing Docker Image') {
            container('docker') {
                sh('docker build -t qfrank76/dojo_node_jenkins .')
                sh('docker push qfrank76/dojo_node_jenkins')
                sh('docker images')
            }
        }
    }
}
