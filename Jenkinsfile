pipeline{
    agent {
        docker { image 'mcr.microsoft.com/playwright:v1.60.0-noble' }
    }

    parameters {

        choice(name: 'BROWSER', choices: ['firefox', 'webkit', 'chromium'], description: 'Pick you browser')
         
        choice(name: 'TAGS', choices: ['@hocine', '@regression', '@sanity', '@invalide', '@integration'], description: 'Pick your tag')
         
        booleanParam(name: 'CHECKBROWSER', defaultValue: true, description: 'Would you select browser ?')

        booleanParam(name: 'CHECKTAGS', defaultValue: true, description: 'Would you select tags ?')

    }

    stages{
        stage('playwrigth install'){
            steps{
                sh'npm install'
            }
        }
        stage('verifier la version'){
            steps{
                sh'npx playwright --version'
            }
        }
        stage('script playwright'){
            steps{
                script{
                if(params.CHECKBROWSER){
                    echo'npx playwright test'
                }else{
                    if(params.CHECKTAGS){
                        echo('npx playwright test --project '+params.BROWSER+' --grep '+params.TAGS)
                    }else {
                        echo('npx playwright test --project '+params.BROWSER)
                    }
                }
            }
            }
            
        }
    }
}