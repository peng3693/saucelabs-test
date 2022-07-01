properties([
                    	parameters([
							[$class: 'ChoiceParameter', 
                                    choiceType: 'PT_RADIO', 
                                    filterLength: 1, 
                                    filterable: false, 
                                    name: 'Run_Tests_On_Landscapes', 
				    description: 'Run Tests On Landscapes',
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
                                                "return['All Landscape','Spesific Lanscape']"
                                        ]
                                    ]
                                ],
				string(defaultValue: 'f252ba42-4753-4090-a10b-ac1b48849913', name: 'Tenant_ID', description: 'Enter the Tenant ID of the subaccount subscribed to the UI (Required)', trim: true),
				[$class: 'CascadeChoiceParameter', 
                                    choiceType: 'PT_SINGLE_SELECT', 
                                    name: 'Landscapes', 
				    description: 'Landscapes',
                                    referencedParameters: 'Run_Tests_On_Landscapes', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                        classpath: [], 
                                        sandbox: false, 
                                        script: "return['Could not get Tests']"
                                        ],  
                                        script: [
                                            classpath: [], 
                                            sandbox: false, 
                                            script: """
					    if (Run_Tests_On_Landscapes.equals("All Landscape")) 
                                                    {
                                                        return['All 111','Spesific 1111']
                                                        
                                                    }
                                                    
					    if(Run_Tests_On_Landscapes.equals("Spesific Lanscape"))
                                                    {
                                                        return['All 222','Spesific 222']
                                                    }
                                                    """.stripIndent()
                                                ]
                                        ]
                                ],
// 				    [$class: 'DynamicReferenceParameter',
// 				      choiceType: 'ET_ORDERED_LIST', description: 'Select the  AMI based on the following information',
// 				      name: 'Image Information',referencedParameters: 'Run_Tests_On_Landscapes',
// 				      script:
// 					  [$class: 'GroovyScript',
// 					  script: 'return["Could not get AMi Information"]',
// 					  script: [
// 					      script: '''
// 						      if (Env.equals("All Landscape")){
// 							  return["ami-sd2345sd:  AMI with Java", "ami-asdf245sdf: AMI with Python", "ami-asdf3245sd: AMI with Groovy"]
// 						      }
// 						      else if(Env.equals("Spesific Lanscape")){
// 							  return["ami-sd34sdf:  AMI with Java", "ami-sdf345sdc: AMI with Python", "ami-sdf34sdf: AMI with Groovy"]
// 						      }
// 						      '''.stripIndent()
// 						  ]
// 					  ]
// 				  ]
				[
          $class: 'DynamicReferenceParameter',
          choiceType: 'ET_FORMATTED_HTML',
          name: 'Dynamic_Test',
          description: 'Dynamic Test',
          randomName: 'choice-parameter-56313144223333',
          referencedParameters: '',
          script: [
              $class: 'GroovyScript',
              fallbackScript: [
                  classpath: [],
                  sandbox: false, script:
                    """
                    html =
                        '''
                            <!DOCTYPE html>
                            <html>
                            <body>
                            <blockquote>
                              loadCss in fallback script
                            </blockquote>
                            </body>
                            </html>
                         '''
                         return html
                    """
              ],
              script: [
                  $class: 'ScriptlerScript',
                  parameters: [[$class: 'org.biouno.unochoice.model.ScriptlerScriptParameter', name: 'aaa', value: '$value']],
                  scriptlerScriptId: 'script.groovy'
              ]
          ]
      ]
                                
                        ])
	 ])

//     properties([
//         buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '10', daysToKeepStr: '5', numToKeepStr: '10')),
//         parameters([
// //             string(defaultValue: 'https://saas-shg-patientaccounting-shg.cfapps.eu10.hana.ondemand.com/cp.portal/site#Shell-home', name: 'UI_Url', description: 'UI url that want to let saucelabs test'),
// //             string(defaultValue: 'https://feature-flag-svc-pacc-shg.cfapps.eu10.hana.ondemand.com', name: 'Feature_Flag_Url', description: 'Feature Flag Service Application URL'),
// //             string(defaultValue: 'https://sap-health-dev-ui.authentication.eu10.hana.ondemand.com', name: 'Authorization_Url', description: 'The url in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
// //             string(defaultValue: 'sb-patient-accounting-shg!b87096', name: 'Client_ID', description: 'The clientid in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
// //             string(defaultValue: 'd/2Qei2+9ZrhGdn3nhR0w/hQLcs=', name: 'Client_Secret', description: 'The clientsecret in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
// //             string(defaultValue: 'f8bf2200-4254-4214-ac75-251bd2841d9a', name: 'Tenant_ID', description: 'The Tenant ID Of The Subaccount That Subscribes To The UI'),

//             choice(defaultValue: 'Validation Environment', name: 'Test_Environment', choices: ['Validation Environment', 'Production Environment'], description: 'Please select whether you are testing a Validation Environment or a Production Environment'),
//             string(defaultValue: 'https://sap-health-validation-ui-autotest-patientaccounting-prerelease.cfapps.eu10.hana.ondemand.com/cp.portal/site#Shell-home', name: 'UI_Url', description: 'Enter the UI link you want to test (Required)', trim: true),
//             string(defaultValue: 'f252ba42-4753-4090-a10b-ac1b48849913', name: 'Tenant_ID', description: 'Enter the Tenant ID of the subaccount subscribed to the UI (Required)', trim: true),
//             string(defaultValue: 'https://feature-flag-svc-pacc-prerelease.cfapps.eu10.hana.ondemand.com', name: 'Feature_Flag_Url', description: 'If Test_Environment is Validation Environment, Enter the link of the Health Feature Flag Service; If Test_Environment is Production Environment, Enter credentials.uri in the feature-flags instance "patient-accounting-feature-flags-std" (Required)', trim: true),
//             string(defaultValue: 'https://sap-health-validation-paprerel.authentication.eu10.hana.ondemand.com', name: 'Authorization_Url', description: 'Enter credentials.url in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
//             string(defaultValue: 'sb-patient-accounting-prerelease!b73122', name: 'Client_ID', description: 'Enter credentials.clientid in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
//             string(defaultValue: 'AzI0Qb9D4b92qb3uKW2tZpLWoRM=', name: 'Client_Secret', description: 'Enter credentials.clientsecret in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
//             string(defaultValue: 'sbss_xtxduclg6of2kmyl+p2u6qvbu6yfx2bquudyxu9pptyepzllt2fnejlqvvxa8+fgo+k=', name: 'Username', description: 'Enter credentials.username in the feature-flags instance "patient-accounting-feature-flags-std" (Production Environment Required)', trim: true),
//             string(defaultValue: 'aa_rPKNzxw1VxZCNYbRSOnDL6Wt17Y=', name: 'Password', description: 'Enter credentials.password in the feature-flags instance "patient-accounting-feature-flags-std" (Production Environment Required)', trim: true),
//         ])
//     ])

//     if ( Test_Environment == 'Validation Environment') {
//         if (UI_Url == '' || Tenant_ID == '' || Feature_Flag_Url == '' || Authorization_Url == '' || Client_ID == '' ||  Client_Secret == '') {
//            error("In the Validation Environment, UI_Url, Tenant_ID, Feature_Flag_Url, Authorization_Url, Client_ID and Client_Secret are mandatory fields!")
//         }
//     } else if ( Test_Environment == 'Production Environment') {
//         if (UI_Url == '' || Tenant_ID == '' || Feature_Flag_Url == '' || Username == '' ||  Password == '') {
//            error("In the Production Environment, UI_Url, Tenant_ID, Feature_Flag_Url, Username and Password are mandatory fields!")
//         }
//     }

