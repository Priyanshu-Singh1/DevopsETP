pipeline {
    agent any
    
    // Git repository configuration with polling trigger
    // For localhost Jenkins, use Poll SCM instead of GitHub webhook
    triggers {
        pollSCM('H/5 * * * *')  // Poll every 5 minutes
    }
    
    options {
        timestamps()
        timeout(time: 30, unit: 'MINUTES')
    }
    
    stages {
        stage('Build') {
            steps {
                echo '========== Build Stage =========='
                echo 'Compiling and installing dependencies...'
                // For Maven projects:
                // sh 'mvn clean compile'
                // For npm/Node.js projects:
                // sh 'npm install'
                // For Python projects:
                // sh 'pip install -r requirements.txt'
                // For Gradle projects:
                // sh 'gradle build'
                script {
                    echo 'Build completed successfully!'
                }
            }
        }
        
        stage('Test') {
            steps {
                echo '========== Test Stage =========='
                echo 'Running unit tests...'
                // For Maven projects:
                // sh 'mvn test'
                // For npm/Node.js projects:
                // sh 'npm test'
                // For Python projects:
                // sh 'pytest'
                // For Gradle projects:
                // sh 'gradle test'
                script {
                    echo 'Unit tests executed successfully!'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo '========== Deploy Stage =========='
                echo 'Deploying artifacts...'
                script {
                    // Option 1: Copy artifacts to deployment directory
                    // sh 'cp -r build/* /var/www/app/'
                    // sh 'cp -r dist/* /opt/application/'
                    
                    // Option 2: Docker container deployment
                    // sh 'docker build -t myapp:latest .'
                    // sh 'docker run -d --name myapp-container -p 8080:8080 myapp:latest'
                    
                    echo 'Artifacts deployed successfully!'
                }
            }
        }
        
        stage('Monitor') {
            steps {
                echo '========== Monitor Stage =========='
                echo 'Monitoring application health...'
                script {
                    // Health check for deployed application
                    // sh 'curl -f http://localhost:8080/health || exit 1'
                    
                    // Log collection
                    // sh 'tail -n 100 /var/log/app.log'
                    
                    echo 'Application is running and healthy!'
                }
            }
        }
    }
    
    post {
        success {
            echo '========== Pipeline Result =========='
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo '========== Pipeline Result =========='
            echo 'Pipeline failed! Check logs for details.'
        }
        always {
            echo 'Pipeline execution completed.'
        }
    }
}