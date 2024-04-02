pipeline {
  agent { label 'linux' }
  parameters {
    string(name 'Server_Name', defaultValue'',
           description: 'Enter the FQDN name of the Admin Server for the new cluster')
    
    string(name 'Admin_User_Name', defaultValue'',
           description: 'Enter weblogic admin user for the cluster')

    password(name 'Admin_User_Password', defaultValue'',
           description: 'Enter weblogic admin password for the cluster')

    string(name 'Weblogic_Domain', defaultValue'',
           description: 'Enter the domain name')
  }
  stages {
    stage{'Remote SSH'){
      steps {
        script{
          withCredentials([usernamePassword(credentialsID: 'sshOCCAS',
                                            passwordVariable: 'PASSWORD',
                                            usernameVariable: 'Username')]) {
            /* Groovylint-disable-next-line noDef, VariableTypeRequired*/
            def remote = [:]
            remote.name = params.Server_Name
            remote.host = params.Server_Name
            remote.user = params.USERNAME
            remote.password = params.PASSWORD
            remote.allowAnyHost = true

            sshCommand remote: remote, command: 'pwd'
            sshCommand remote: remote, command: 'ls -ltr'
