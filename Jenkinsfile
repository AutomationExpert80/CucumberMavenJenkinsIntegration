// pipeline {
//     agent any
//         stages {
//             stage('Parameters'){
//                 steps {
//                     script {
//                     properties([
//                             parameters([
//                                 [$class: 'ChoiceParameter',
//                                     choiceType: 'PT_SINGLE_SELECT',
//                                     description: 'Select the OS from the Dropdown List',
//                                     filterLength: 1,
//                                     filterable: false,
//                                     name: 'Os',
//                                     script: [
//                                         $class: 'GroovyScript',
//                                         fallbackScript: [
//                                             classpath: [],
//                                             sandbox: false,
//                                             script:
//                                                 "return['Could not get The OS']"
//                                         ],
//                                         script: [
//                                             classpath: [],
//                                             sandbox: false,
//                                             script:
//                                                 "return['Mac','Windows','Linux']"
//                                         ]
//                                     ]
//                                 ],
//                                 [$class: 'CascadeChoiceParameter',
//                                     choiceType: 'PT_SINGLE_SELECT',
//                                     description: 'Select the AMI from the Dropdown List',
//                                     name: 'AMI List',
//                                     referencedParameters: 'Os',
//                                     script:
//                                         [$class: 'GroovyScript',
//                                         fallbackScript: [
//                                                 classpath: [],
//                                                 sandbox: false,
//                                                 script: "return['Could not get Os from Os Param']"
//                                                 ],
//                                         script: [
//                                                 classpath: [],
//                                                 sandbox: false,
//                                                 script: '''
//                                                 if (Os.equals("Mac")){
//                                                     return["Big Sur", "Catalina", "MyMac"]
//                                                 }
//                                                 else if(Os.equals("Windows")){
//                                                     return["Windows_11", "Windows_10", "Windows_7"]
//                                                 }
//                                                 else if(Os.equals("Linux")){
//                                                     return["Obunto", "MylUNIX", "MYuNIX"]
//                                                 }
//                                                 '''
//                                             ]
//                                     ]
//                                 ],
//                                 [$class: 'DynamicReferenceParameter',
//                                     choiceType: 'ET_ORDERED_LIST',
//                                     description: 'Select the  AMI based on the following infomration',
//                                     name: 'Image Information',
//                                     referencedParameters: 'Os',
//                                     script:
//                                         [$class: 'GroovyScript',
//                                         script: 'return["Could not get Os Information"]',
//                                         script: [
//                                             script: '''
//                                                     if (Env.equals("dev")){
//                                                         return["ami-sd2345sd:  AMI with Java", "ami-asdf245sdf: AMI with Python", "ami-asdf3245sd: AMI with Groovy"]
//                                                     }
//                                                     else if(Env.equals("stage")){
//                                                         return["ami-sd34sdf:  AMI with Java", "ami-sdf345sdc: AMI with Python", "ami-sdf34sdf: AMI with Groovy"]
//                                                     }
//                                                     else if(Env.equals("prod")){
//                                                         return["ami-sdf34sdf:  AMI with Java", "ami-sdf34ds: AMI with Python", "ami-sdf3sf3: AMI with Groovy"]
//                                                     }
//                                                     '''
//                                                 ]
//                                         ]
//                                 ]
//                             ])
//                         ])
//                     }
//                 }
//             }
//         }
// }

pipeline {
    agent any
        stages {
            stage('Parameters'){
                steps {
                    script {
                    properties([
                            parameters([
                                [$class: 'ChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the Environemnt from the Dropdown List',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'Env',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['Could not get The environemnts']"
                                        ],
                                        script: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['dev','stage','prod']"
                                        ]
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the AMI from the Dropdown List',
                                    name: 'AMI List',
                                    referencedParameters: 'Env',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: false,
                                                script: "return['Could not get Environment from Env Param']"
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: false,
                                                script: '''
                                                if (Env.equals("dev")){
                                                    return["ami-sd2345sd", "ami-asdf245sdf", "ami-asdf3245sd"]
                                                }
                                                else if(Env.equals("stage")){
                                                    return["ami-sd34sdf", "ami-sdf345sdc", "ami-sdf34sdf"]
                                                }
                                                else if(Env.equals("prod")){
                                                    return["ami-sdf34sdf", "ami-sdf34ds", "ami-sdf3sf3"]
                                                }
                                                '''
                                            ]
                                    ]
                                ],
                                [$class: 'DynamicReferenceParameter',
                                    choiceType: 'ET_ORDERED_LIST',
                                    description: 'Select the  AMI based on the following infomration',
                                    name: 'Image Information',
                                    referencedParameters: 'Env',
                                    script:
                                        [$class: 'GroovyScript',
                                        script: 'return["Could not get AMi Information"]',
                                        script: [
                                            script: '''
                                                    if (Env.equals("dev")){
                                                        return["ami-sd2345sd:  AMI with Java", "ami-asdf245sdf: AMI with Python", "ami-asdf3245sd: AMI with Groovy"]
                                                    }
                                                    else if(Env.equals("stage")){
                                                        return["ami-sd34sdf:  AMI with Java", "ami-sdf345sdc: AMI with Python", "ami-sdf34sdf: AMI with Groovy"]
                                                    }
                                                    else if(Env.equals("prod")){
                                                        return["ami-sdf34sdf:  AMI with Java", "ami-sdf34ds: AMI with Python", "ami-sdf3sf3: AMI with Groovy"]
                                                    }
                                                    '''
                                                ]
                                        ]
                                ]
                            ])
                        ])
                    }
                }
            }
        }
}
