  node{
      stage('Clone') {
          checkout scm
      }
      stage('Creation user'){

          apk add ansible sshpass
          ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa

          sshpass -p 'Anteor78!' ssh-copy-id  -o stricthostkeychecking=no root@192.168.195.129
         
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
