  node{
      stage('Clone') {
          checkout scm
      }
      stage('Creation user'){
	apk add ansible sshpass
	rm -rf /root/.ssh
	echo "192.168.195.128  app-salaire.jeremytc.form" > /etc/hosts
	ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa
	sshpass -p 'Anteor78!' ssh-copy-id -o stricthostkeychecking=no root@192.168.195.128       
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
