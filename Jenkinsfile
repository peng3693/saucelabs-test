

    properties([
        buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '10', daysToKeepStr: '5', numToKeepStr: '10')),
        parameters([
//             string(defaultValue: 'https://saas-shg-patientaccounting-shg.cfapps.eu10.hana.ondemand.com/cp.portal/site#Shell-home', name: 'UI_Url', description: 'UI url that want to let saucelabs test'),
//             string(defaultValue: 'https://feature-flag-svc-pacc-shg.cfapps.eu10.hana.ondemand.com', name: 'Feature_Flag_Url', description: 'Feature Flag Service Application URL'),
//             string(defaultValue: 'https://sap-health-dev-ui.authentication.eu10.hana.ondemand.com', name: 'Authorization_Url', description: 'The url in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
//             string(defaultValue: 'sb-patient-accounting-shg!b87096', name: 'Client_ID', description: 'The clientid in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
//             string(defaultValue: 'd/2Qei2+9ZrhGdn3nhR0w/hQLcs=', name: 'Client_Secret', description: 'The clientsecret in patient-accounting-uaa of the uaa instance bound by the Feature Flag service'),
//             string(defaultValue: 'f8bf2200-4254-4214-ac75-251bd2841d9a', name: 'Tenant_ID', description: 'The Tenant ID Of The Subaccount That Subscribes To The UI'),

            choice(defaultValue: 'Validation Environment', name: 'Test_Environment', choices: ['Validation Environment', 'Production Environment'], description: 'Please select whether you are testing a Validation Environment or a Production Environment'),
            string(defaultValue: 'https://sap-health-validation-ui-autotest-patientaccounting-prerelease.cfapps.eu10.hana.ondemand.com/cp.portal/site#Shell-home', name: 'UI_Url', description: 'Enter the UI link you want to test (Required)', trim: true),
            string(defaultValue: 'f252ba42-4753-4090-a10b-ac1b48849913', name: 'Tenant_ID', description: 'Enter the Tenant ID of the subaccount subscribed to the UI (Required)', trim: true),
            string(defaultValue: 'https://feature-flag-svc-pacc-prerelease.cfapps.eu10.hana.ondemand.com', name: 'Feature_Flag_Url', description: 'If Test_Environment is Validation Environment, Enter the link of the Health Feature Flag Service; If Test_Environment is Production Environment, Enter credentials.uri in the feature-flags instance "patient-accounting-feature-flags-std" (Required)', trim: true),
            string(defaultValue: 'https://sap-health-validation-paprerel.authentication.eu10.hana.ondemand.com', name: 'Authorization_Url', description: 'Enter credentials.url in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
            string(defaultValue: 'sb-patient-accounting-prerelease!b73122', name: 'Client_ID', description: 'Enter credentials.clientid in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
            string(defaultValue: 'AzI0Qb9D4b92qb3uKW2tZpLWoRM=', name: 'Client_Secret', description: 'Enter credentials.clientsecret in the xsuaa instance "patient-accounting-uaa" (Validation Environment Required)', trim: true),
            string(defaultValue: 'sbss_xtxduclg6of2kmyl+p2u6qvbu6yfx2bquudyxu9pptyepzllt2fnejlqvvxa8+fgo+k=', name: 'Username', description: 'Enter credentials.username in the feature-flags instance "patient-accounting-feature-flags-std" (Production Environment Required)', trim: true),
            string(defaultValue: 'aa_rPKNzxw1VxZCNYbRSOnDL6Wt17Y=', name: 'Password', description: 'Enter credentials.password in the feature-flags instance "patient-accounting-feature-flags-std" (Production Environment Required)', trim: true),

//               [$class: 'CascadeChoiceParameter',
//                   choiceType: 'PT_RADIO',
//                   description: 'Test Environment',
//                   filterLength: 1,
//                   filterable: false,
//                   name: 'Test_Environment',
//                   script: [
//                       $class: 'GroovyScript',
//                       fallbackScript: [
//                           classpath: [],
//                           sandbox: false,
//                           script: 'return ["Could not get The environemnts"]'
//                       ],
//                       script: [
//                           classpath: [],
//                           sandbox: false,
//                           script:
//                                   "return[Validation Environment','Production Environment']"
//                       ]
//                   ]
//               ],
//             [$class: 'CascadeChoiceParameter',
//             choiceType: 'PT_SINGLE_SELECT',
//             description: 'Select the required Landscape',
//             filterLength: 1,
//             filterable: false,
//             name: 'Landscape',
//             referencedParameters: 'Test_Environment',
//             script: [$class: 'GroovyScript',
//                 fallbackScript: [
//                     classpath: [],
//                     sandbox: true,
//                     script: 'return ["No Landscapes available"]'
//                 ],
//                 script: [
//                     classpath: [],
//                     sandbox: true,
//                     script: """
//                         if (Test_Environment == 'Validation') {
//                         'return
//                               """
//                             <input name="value" id="Landscape"  value="Landscape">
//                              <img src="error/image/url" style="display: none;" onerror='document.getElementById("Landscape").closest(".form-group").style.display=""'>
//
//                         }
//                         else if (Test_Environment == 'Product') {
//                             return
//                             """
//                             <input name="value" id="Landscape"  value="Landscape">
//                              <img src="error/image/url" style="display: none;" onerror='document.getElementById("Landscape").closest(".form-group").style.display="none"'>
//                              """
//                         }
//                     """.stripIndent()
//                 ]
//             ]
//         ]
//             [$class: 'CascadeChoiceParameter',choiceType: 'PT_SINGLE_SELECT',description: 'Select the AMI from the Dropdown List',
//                  name: 'AMI List',referencedParameters: 'Env',
//                 script:
//                     [$class: 'GroovyScript',
//                     fallbackScript: [
//                             classpath: [],
//                             sandbox: false,
//                             script: "return['Could not get Environment from Env Param']"
//                             ],
//                     script: [
//                             classpath: [],
//                             sandbox: false,
//                             script: '''
//                             if (Env.equals("dev")){
//                                 return["ami-sd2345sd", "ami-asdf245sdf", "ami-asdf3245sd"]
//                             }
//                             else if(Env.equals("stage")){
//                                 return["ami-sd34sdf", "ami-sdf345sdc", "ami-sdf34sdf"]
//                             }
//                             else if(Env.equals("prod")){
//                                 return["ami-sdf34sdf", "ami-sdf34ds", "ami-sdf3sf3"]
//                             }
//                             '''
//                         ]
//                 ]
//             ],
//             [$class: 'DynamicReferenceParameter',
//               choiceType: 'ET_ORDERED_LIST', description: 'Select the  AMI based on the following information',
//               name: 'Image Information',referencedParameters: 'Env',
//               script:
//                   [$class: 'GroovyScript',
//                   script: 'return["Could not get AMi Information"]',
//                   script: [
//                       script: '''
//                               if (Env.equals("dev")){
//                                   return["ami-sd2345sd:  AMI with Java", "ami-asdf245sdf: AMI with Python", "ami-asdf3245sd: AMI with Groovy"]
//                               }
//                               else if(Env.equals("stage")){
//                                   return["ami-sd34sdf:  AMI with Java", "ami-sdf345sdc: AMI with Python", "ami-sdf34sdf: AMI with Groovy"]
//                               }
//                               else if(Env.equals("prod")){
//                                   return["ami-sdf34sdf:  AMI with Java", "ami-sdf34ds: AMI with Python", "ami-sdf3sf3: AMI with Groovy"]
//                               }
//                               '''
//                           ]
//                   ]
//           ]

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


def status = ''
node {
    dir("${env.BUILD_NUMBER}") {
        stage("Saucelabs Tests") {
            try {
                checkout scm
                karmaExecuteTests script: this,
                  dockerImage: 'buildkite/puppeteer:latest',
                  sidecarPullImage: false,
                  dockerWorkspace: '/home/piper',
                  installCommand: 'npm install',
                  runCommand: 'npm run test.saucelabs'

                status = 'SUCCESS'
            }catch (exc) {
                status = 'FAILURE'
                throw error
            }
        }
    }
}
