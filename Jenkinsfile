


properties([
    parameters([
// 				[$class: 'ChoiceParameter',
//             choiceType: 'PT_RADIO',
//             filterLength: 1,
//             filterable: false,
//             name: 'Test_Environment',
// 				    description: 'Test Environment',
//             script: [
//                 $class: 'GroovyScript',
//                 fallbackScript: [
//                     classpath: [],
//                     sandbox: false,
//                     script:
//                         "return['Could not get The environemnts']"
//                 ],
//                 script: [
//                     classpath: [],
//                     sandbox: false,
//                     script:
//                         "return['Validation Environment', 'Production Environment']"
//                 ]
//             ]
//         ],
        extendedChoice(defaultValue: 'Validation Environment', description: '', multiSelectDelimiter: ',', name: 'Test_Environment', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_RADIO', value: 'Validation Environment,Production Environment', visibleItemCount: 2),
		string(defaultValue: 'https://sap-health-validation-ui-autotest-patientaccounting-prerelease.cfapps.eu10.hana.ondemand.com/cp.portal/site#Shell-home', name: 'UI_Url', description: 'Enter the UI link you want to test (Required)', trim: true),	
	    string(defaultValue: 'f252ba42-4753-4090-a10b-ac1b48849913', name: 'Tenant_ID', description: 'Enter the Tenant ID of the subaccount subscribed to the UI', trim: true),
 				string(defaultValue: 'https://feature-flag-svc-pacc-prerelease.cfapps.eu10.hana.ondemand.com', name: 'Feature_Flag_Url', description: 'If Test_Environment is Validation Environment, Enter the link of the Health Feature Flag Service; If Test_Environment is Production Environment, Enter credentials.uri in the feature-flags instance "patient-accounting-feature-flags-std"', trim: true),
				[$class: 'DynamicReferenceParameter',
            choiceType: 'ET_FORMATTED_HTML',
            description: 'Enter credentials.url in the xsuaa instance "patient-accounting-uaa"',
            name: 'Authorization_Url',
            referencedParameters: 'Test_Environment',
            script:
                [$class: 'GroovyScript',
                fallbackScript: [
                        classpath: [],
                        sandbox: false,
                        script: "return['This is the Validation Environment input field']"
                        ],
                script: [
                        classpath: [],
                        sandbox: false,
                        script: '''
                        if (Test_Environment.contains('Validation Environment')){
                            return """<input name="value" placeholder="" type="text" class="jenkins-input   " value="https://sap-health-validation-paprerel.authentication.eu10.hana.ondemand.com">"""
                        }
                        '''
                    ]
            ],
        omitValueField: true
        ] ,
				[$class: 'DynamicReferenceParameter',
            choiceType: 'ET_FORMATTED_HTML',
            description: 'Enter credentials.clientsecret in the xsuaa instance "patient-accounting-uaa"',
            name: 'Client_ID',
            referencedParameters: 'Test_Environment',
            script:
                [$class: 'GroovyScript',
                fallbackScript: [
                        classpath: [],
                        sandbox: false,
                        script: "return['This is the Validation Environment input field']"
                        ],
                script: [
                        classpath: [],
                        sandbox: false,
                        script: '''
                        if (Test_Environment.contains('Validation Environment')){
                            return """<input name="value" placeholder="" type="text" class="jenkins-input   " value="sb-patient-accounting-prerelease!b73122">"""
                        }
                        '''
                    ]
            ],
        omitValueField: true
        ] ,
				[$class: 'DynamicReferenceParameter',
            choiceType: 'ET_FORMATTED_HTML',
            description: 'Enter credentials.clientsecret in the xsuaa instance "patient-accounting-uaa"',
            name: 'Client_Secret',
            referencedParameters: 'Test_Environment',
            script:
                [$class: 'GroovyScript',
                fallbackScript: [
                        classpath: [],
                        sandbox: false,
                        script: "return['This is the Validation Environment input field']"
                        ],
                script: [
                        classpath: [],
                        sandbox: false,
                        script: '''
                        if (Test_Environment.contains('Validation Environment')){
                            return """<input name="value" placeholder="" type="text" class="jenkins-input   " value="AzI0Qb9D4b92qb3uKW2tZpLWoRM=">"""
                        }
                        '''
                    ]
            ],
        omitValueField: true
        ],
				[$class: 'DynamicReferenceParameter',
            choiceType: 'ET_FORMATTED_HTML',
            description: 'Enter credentials.username in the feature-flags instance "patient-accounting-feature-flags-std"',
            name: 'Username',
            referencedParameters: 'Test_Environment',
            script:
                [$class: 'GroovyScript',
                fallbackScript: [
                        classpath: [],
                        sandbox: false,
                        script: "return['This is the Production Environment input field']"
                        ],
                script: [
                        classpath: [],
                        sandbox: false,
                        script: '''
                        if (Test_Environment.contains('Production Environment')){
                            return """<input name="value" placeholder="" type="text" class="jenkins-input   " value="11111">"""
                        }
                        '''
                    ]
            ],
        omitValueField: true
        ] ,
				[$class: 'DynamicReferenceParameter',
            choiceType: 'ET_FORMATTED_HTML',
            description: 'Enter credentials.password in the feature-flags instance "patient-accounting-feature-flags-std"',
            name: 'Password',
            referencedParameters: 'Test_Environment',
            script:
                [$class: 'GroovyScript',
                fallbackScript: [
                        classpath: [],
                        sandbox: false,
                        script: "return['This is the Production Environment input field']"
                        ],
                script: [
                        classpath: [],
                        sandbox: false,
                        script: '''
                        if (Test_Environment.contains('Production Environment')){
                            return """<input name="value" placeholder="" type="text" class="jenkins-input   " value="2222">"""
                        }
                        '''
                    ]
            ],
        omitValueField: true
        ]

    ])
])

    if ( Test_Environment == 'Validation Environment') {
        if (UI_Url == '' || Tenant_ID == '' || Feature_Flag_Url == '' || Authorization_Url == '' || Client_ID == '' ||  Client_Secret == '') {
           error("In the Validation Environment, UI_Url, Tenant_ID, Feature_Flag_Url, Authorization_Url, Client_ID and Client_Secret are mandatory fields!")
        }
    } else if ( Test_Environment == 'Production Environment') {
        if (UI_Url == '' || Tenant_ID == '' || Feature_Flag_Url == '' || Username == '' ||  Password == '') {
           error("In the Production Environment, UI_Url, Tenant_ID, Feature_Flag_Url, Username and Password are mandatory fields!")
        }
    }

