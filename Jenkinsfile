podTemplate(
    label: 'mypod', 
    inheritFrom: 'default',
    containers: [
        containerTemplate(
            name: 'maven', 
            image: 'maven',
            ttyEnabled: true,
            command: 'cat'
        )
    ]
) {
    node('mypod') {
        stage ('Build') {
            container ('maven') {
                sh 'mvn -version'
            }
        }
    }
}