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
                                    description: 'Select the Testing Environment from the Dropdown List',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'TestingEnvironment',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['Could not get The Testing Environment']"
                                        ],
                                        script: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['QA','DEV','STG','UAT','Production']"
                                        ]
                                    ]
                                ],
                        [$class: 'ChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the test suit using the corresponding Cucumber Tag from the Dropdown List',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'CucumberTag',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['Could not get The Cucumber Tag']"
                                        ],
                                        script: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['@amazon','@youtube','@google','@regression','@sanity','@smoke','@loadTesting']"
                                        ]
                                    ]
                                ],
                                [$class: 'ChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the Operating System from the Dropdown List',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'Os',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['Could not get The Operating System']"
                                        ],
                                        script: [
                                      
                                            classpath: [],
                                            sandbox: false,
                                            script:
                                                "return['Mac','Windows','Linux']"
                                        ]
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the Operating System Version from the Dropdown List',
                                    name: 'Os_Version',
                                    referencedParameters: 'Os',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: false,
                                                script: "return['Could not get Operating System Version']"
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: false,
                                                script: '''
                                                if (Os.equals("Mac")){
                                                    return["macOS 12(Monterey)", "macOS 11(Big Sur)", "macOS 10.15(Catalina)","macOS 10.14(Mojave)","macOS 10.13(High Sierra)","macOS 10.12(Sierra)","OS X 10.11(El Capitan)"]
                                                }
                                                else if(Os.equals("Windows")){
                                                    return["Windows 11", "Windows 10", "Windows 7","Windows 8","Windows XP","Windows Vista","Windows 2000","Windows ME","Windows 98"]
                                                }
                                                else if(Os.equals("Linux")){
                                                    return["Debian Linux", "Gentoo Linux", "Ubuntu Linux","Linux Mint Desktop","RHEL Linux Distribution","CentOS Linux Distribution","Fedora Linux Distribution","Kali Linux Distribution"]
                                                }
                                                '''
                                            ]
                                    ]
                              
                                ],
                                [$class: 'CascadeChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the Browser Name from the Dropdown List',
                                    name: 'BrowserName',
                                    referencedParameters: 'Os',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: false,
                                                script: "return['Could not get the Browser Name']"
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: false,
                                                script: '''
                                                if (Os.equals("Mac")){
                                                    return['Chrome','Edge','Safari','Opera','Firefox']
                                                }
                                                else if(Os.equals("Windows")){
                                                    return['Chrome','Internet Explorer','Edge','Safari','Opera','Firefox']
                                                }
                                                else if(Os.equals("Linux")){
                                                    return['Chrome','Edge','Safari','Opera','Firefox']
                                                }
                                                '''
                                            ]
                                    ]
                                 
                              
 //                               ],
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
                                 ]
                            ])
                        ])
                    }
                }
            }
        }
}

