  node{
      stage('Clone') {
          checkout scm
      }
      stage('SSH') {
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo \"192.168.195.128 app-salaire.jeremytc.form\" > /etc/hosts"
        sh "ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa"
        sh "sshpass -p 'jarjar' ssh-copy-id -o stricthostkeychecking=no root@192.168.195.128"
      }
      stage('Ansible') {       
        ansiblePlaybook (
            inventory: 'hosts.yml',          
            playbook: 'playbook.yml',
            colorized: true,
            become: true,         
        )
      }
  }
