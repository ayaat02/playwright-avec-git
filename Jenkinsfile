pipeline{
    agent {
        docker { image 'mcr.microsoft.com/playwright:v1.60.0-noble' }
    }

    parameters {

        choice(name: 'BROWSER', choices: ['firefox', 'webkit', 'chromium'], description: 'Pick you browser')
         
        choice(name: 'TAGS', choices: ['@integration', '@hc', '@regression', '@sanity', '@invalide'], description: 'Pick your tag')
         
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
            build job:"Jenkinsfile2",
                parameters{
                    choice(name: 'BROWSER', value:'webkit')
         
                    choice(name: 'TAGS', value : '@regression')
         
                    booleanParam(name: 'CHECKBROWSER', value: true)

                    booleanParam(name: 'CHECKTAGS', value: true)

                }
            }
            
        }
    }
}