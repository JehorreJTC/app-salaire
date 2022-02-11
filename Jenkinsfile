  node{
      stage('Clone') {
          checkout scm
      }
      stage('SSH') {
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo \"192.168.195.131 app-salaire.jeremytc.form\" > /etc/hosts"
        sh "ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa"
        sh "sshpass -p 'Anteor78!' ssh-copy-id -o stricthostkeychecking=no root@192.168.195.131"
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
