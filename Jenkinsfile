node() {
    docker.image('node:carbon-jessie').inside {
        stage('Step 1') {
            echo "Your Pipeline works!"
            sh('ls -la')

            sh('git clone "https://github.com/frank-qi/date-display-app"')

            echo "Here's what you cloned!"
            sh('ls -la')
        }

        stage('Testing') {
            echo "TESTINGGGGGG!!!!"
            sh('npm install')
            sh('npm test')
        }
    }
}
