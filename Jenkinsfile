pipeline{
    agent {
        docker { image 'jacoblincool/playwright:latest' }
    }
    stages{
        stage('verifier la version'){
            steps{
                sh'npx playwright --version'
            }
        }
        stage('playwrigth install'){
            steps{
                sh'npm install'
            }
        }
        stage('tester'){
            steps{
                sh'npx playwright test'
            }
        }
    }
}