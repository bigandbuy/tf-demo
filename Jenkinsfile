properties([
    parameters([
        [$class: 'ChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            description: 'Select the Env Name from the Dropdown List',
            filterLength: 1,
            filterable: true,
            name: 'Env',
            randomName: 'choice-parameter-5631314439613978',
            script: [
                $class: 'GroovyScript',
                fallbackScript: [
                    classpath: [],
                    sandbox: false,
                    script:
                        'return[\'Could not get Env\']'
                ],
                script: [
                    classpath: [],
                    sandbox: false,
                    script:
                        'return["us-west-1","eu-central-1","us-east-2","ap-northeast-2","ap-southeast-1","eu-west-2"]'
                ]
            ]
        ],
        [$class: 'CascadeChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            description: 'Select the Server from the Dropdown List',
            filterLength: 1,
            filterable: true,
            name: 'Server',
            randomName: 'choice-parameter-5631314456178619',
            referencedParameters: 'Env',
            script: [
                $class: 'GroovyScript',
                fallbackScript: [
                    classpath: [],
                    sandbox: false,
                    script:
                        'return[\'Could not get Environment from Env Param\']'
                ],
                script: [
                    classpath: [],
                    sandbox: false,
                    script:
                        ''' if (Env.equals("us-west-1")){
                                return["devaaa001","devaaa002","devbbb001","devbbb002","devccc001","devccc002"]
                            }
                            else if(Env.equals("eu-central-1")){
                                return["qaaaa001","qabbb002","qaccc003"]
                            }
                            else if(Env.equals("ap-northeast-2")){
                                return["staaa001","stbbb002","stccc003"]
                            }
                            else if(Env.equals("us-east-2")){
                                return["praaa001","prbbb002","prccc003"]
                            }
                            else if(Env.equals("ap-southeast-1")){
                                return["praaa001","prbbb002","prccc003"]
                            }
                            else if(Env.equals("eu-west-2")){
                                return["praaa001","prbbb002","prccc003"]
                            }
                        '''
                ]
            ]
        ]
    ])
])

pipeline {
  parameters {
      string(defaultValue: "brazil", description: 'What environment?', name: 'name')
      choice(choices: ['t2.micro', 't2.small'], description: 'Instance Type?', name: 'instancetype')
  }
  environment {
         vari = ""
  }
  agent any
  stages {
      stage ("Example") {
        steps {
         script{
          echo 'Hello'
          echo "${params.Env}"
          echo "${params.Server}"
          if (params.Server.equals("Could not get Environment from Env Param")) {
              echo "Must be the first build after Pipeline deployment.  Aborting the build"
              currentBuild.result = 'ABORTED'
              return
          }
          echo "Crossed param validation"
        } }
      }
  }
}
