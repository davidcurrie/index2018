podTemplate(
    label: 'mypod', 
    inheritFrom: 'default',
    containers: [
        containerTemplate(
            name: 'golang', 
            image: 'golang',
            ttyEnabled: true,
            command: 'cat'
        )
    ]
) {
    node('mypod') {
        stage ('Build') {
            container ('golang') {
                sh 'CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o hello .'
            }
        }
    }
}