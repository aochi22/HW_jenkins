// ==> version 1 - simple
// pipeline {
//     agent any
//     environment {
//         PATH = "${env.PATH}:/usr/bin/python3"
//     }
//     stages {
//         stage('Checkout') {
//             steps {
//                git branch: 'main', url: 'https://github.com/aochi22/HW_jenkins.git'
//             }
//         }
//         stage('Build') {
//             steps {
//                 script {
//                     if (isUnix()) {
//                         sh 'echo "Running on Unix"'
//                         // Add your Unix-specific build commands here
//                     } else {
//                         bat 'echo "Running on Windows"'
//                         // Add your Windows-specific build commands here
//                     }
//                 }
//             }
//         }
//     }
// }

// ==> Versions LINUX et windows (2 en 1)
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/hrhouma/hello-python.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        withEnv([
                            "JAVA_HOME=/usr/bin",
                            "PYTHON_HOME=/usr/bin",
                            "PATH=${env.PATH}:${env.JAVA_HOME}:${env.PYTHON_HOME}"
                        ]) {
                            sh 'echo "Running on Unix"'
                            sh 'javac HelloWorld.java'
                            sh 'java HelloWorld'
                            sh 'python3 hello.py'
                        }
                    } else {
                        withEnv([
                            "JAVA_HOME=C:\\Program Files\\Java\\jdk1.8.0_202",
                            "PYTHON_HOME=C:\\Users\\rehou\\AppData\\Local\\Microsoft\\WindowsApps",
                            "PATH=${env.PATH};${env.JAVA_HOME}\\bin;${env.PYTHON_HOME}"
                        ]) {
                            bat 'echo "Running on Windows"'
                            bat 'javac HelloWorld.java'
                            bat 'java HelloWorld'
                            bat 'python hello.py'
                        }
                    }
                }
            }
        }
    }
}