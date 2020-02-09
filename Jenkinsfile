pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:${env.PATH}"
    }

    dir('subDir') {
        checkout scm
    }

    stages {
        stage('Install tools') {
            steps {
                sh """
                python3 -m venv ~/molecule-libvirt
                source ~/molecule-libvirt/bin/activate
                pip3 install --upgrade pip
                pip3 install --upgrade molecule molecule[docker] ansible yamllint ansible-lint python-vagrant
                """
            }
        }
        stage('Test') {
            steps {
                sh """
                source ~/molecule-libvirt/bin/activate
                cd apache
                echo $PATH
                echo $PWD
                ls -la
                which molecule
                molecule --debug test -s kvm
                """
            }
        }
    }
}
