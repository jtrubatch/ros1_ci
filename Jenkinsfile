pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                script {
                    properties([pipelineTriggers([pollSCM('* * * * *')])])
                }
                git branch: 'main', url: 'https://github.com/jtrubatch/ros1_ci.git'
            }
        }
        stage('BUILD') {
            steps {
                sh 'cd ~/catkin_ws/src'
                sh '''
                    #!/bin/bash
                    if [ ! -d "ros1_ci" ]; then
                        git clone https://github.com/jtrubatch/ros1_ci.git
                    else
                        cd ros1_ci
                        git pull origin main
                    fi
                    '''
                sh 'cd ~/catkin_ws/src/ros1_ci && sudo docker build -f ros1.dockerfile -t ros1_ci .'
            }
        }
        stage('TEST') {
            steps {
                sh 'sudo docker run --rm ros1_ci:latest bash -c "rostest tortoisebot_waypoints test_package.launch"'
            }
        }
    }
}
// TEST CHANGE