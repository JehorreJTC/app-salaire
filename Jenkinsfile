  node{
      stage('Clone') {
          checkout scm
      }
      stage('Creation user'){
          
          "apk add sshpass"
          "rm -fr /root/.ssh/"
          "ssh-keygen -q -t rsa -N '' -f /root/ssh/id_rsa"
          "sshpass -p 'Anteor78!' ssh-copy-id  -o stricthostkeychecking=no root@app-salaire.jeremytc.form"
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
