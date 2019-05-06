pipeline {
    agent any

parameters {
  string defaultValue: 'newUser', description: '', name: 'Username', trim: false
  choice choices: ['Grant', 'Deny'], description: '', name: 'Action'
}
stages{
    stage('Grant Or Deny'){
    when{
    	expression { params.choice == 'Grant' }
    }
        steps{
      for server in $(cat ./serverlist.txt){
      sshagent(['sshkey']) {
      sh 'ssh -o StrictHostKeyChecking=no server'
      sh 'vi /etc/ssh/sshd_config
      sh 'sed -i "$ a AllowUsers ${Username}"'
      sh 'systemctl restart sshd'
     }

      }
      
        }

      when{
      		expression { params.choice == 'Deny' }
      }

      steps{
      for server in $(cat ./serverlist.txt){
      sshagent(['sshkey']) {
      sh 'ssh -o StrictHostKeyChecking=no server'
      sh 'vi /etc/ssh/sshd_config
      sh 'sed -i "$ a DenyUsers ${Username}"'
      sh 'systemctl restart sshd'
     }

      }
      
        }
  }
}

}