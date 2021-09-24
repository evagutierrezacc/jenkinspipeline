pipeline{

    agent any
    tools {
        maven "maven-3.8.2"
    }

    parameters{
        string(name:"OPERATION", defaultValue:"package", description:"Operación maven a realizar")
        string(name:"REPO_URL", defaultValue:"https://github.com/jesuscle/junitmavenexample", description:"Url")

    }

    stages{
        stage("Verificación"){
            steps{
                bat "java -version"
                bat "mvn -version"
                echo "Operación a ejecutar: ${params.OPERATION}"
            }
        }

        stage("Descarga del código y build"){
            steps{
                git "REPO-URL"
                bat "mvn clean ${params.OPERATION}"
            }
        }
    }

    post{
        success{
            junit 'target/surefire-reports/TEST-*.xml'
        }
    }

}
