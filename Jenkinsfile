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
        stage ('Extract') {
            checkout scm 
        }
        stage ('Build') {
            container ('maven') {
                mvn version
            }
        }
    }
}