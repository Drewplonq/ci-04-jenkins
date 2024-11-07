...
netology@netology-VirtualBox:~/cicd/jenkins/ci-04-jenkins$ ansible-playbook -i inventory/cicd/hosts.yml site.yml

PLAY [Preapre all hosts] **************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************
The authenticity of host '158.160.24.79 (158.160.24.79)' can't be established.
ED25519 key fingerprint is SHA256:nddh8900q4c/OG/5eFvkexPkIb9n2HAj4PsrjqeIOMA.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
[WARNING]: Platform linux on host jenkins-agent-01 is using the discovered Python interpreter at /usr/bin/python3.9, but future installation of another Python interpreter could
change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [jenkins-agent-01]
[WARNING]: Platform linux on host jenkins-master-01 is using the discovered Python interpreter at /usr/bin/python3.9, but future installation of another Python interpreter could
change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [jenkins-master-01]

TASK [Create group] *******************************************************************************************************************************************************************
changed: [jenkins-master-01]
changed: [jenkins-agent-01]

TASK [Create user] ********************************************************************************************************************************************************************
changed: [jenkins-master-01]
changed: [jenkins-agent-01]

TASK [Install JDK] ********************************************************************************************************************************************************************
changed: [jenkins-master-01]
changed: [jenkins-agent-01]

PLAY [Get Jenkins master installed] ***************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Get repo Jenkins] ***************************************************************************************************************************************************************
changed: [jenkins-master-01]

TASK [Add Jenkins key] ****************************************************************************************************************************************************************
changed: [jenkins-master-01]

TASK [Install epel-release] ***********************************************************************************************************************************************************
changed: [jenkins-master-01]

TASK [Install Jenkins and requirements] ***********************************************************************************************************************************************
changed: [jenkins-master-01]

TASK [Ensure jenkins agents are present in known_hosts file] **************************************************************************************************************************
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
changed: [jenkins-master-01] => (item=jenkins-agent-01)
[WARNING]: Module remote_tmp /home/jenkins/.ansible/tmp did not exist and was created with a mode of 0700, this may cause issues when running as another user. To avoid this, create
the remote_tmp dir with the correct permissions manually

TASK [Start Jenkins] ******************************************************************************************************************************************************************
fatal: [jenkins-master-01]: FAILED! => {"changed": false, "msg": "Unable to start service jenkins: Job for jenkins.service failed because the control process exited with error code.\nSee \"systemctl status jenkins.service\" and \"journalctl -xeu jenkins.service\" for details.\n"}

PLAY RECAP ****************************************************************************************************************************************************************************
jenkins-agent-01           : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
jenkins-master-01          : ok=10   changed=8    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0

netology@netology-VirtualBox:~/cicd/jenkins/ci-04-jenkins$ ansible-playbook -i inventory/cicd/hosts.yml site.yml

PLAY [Preapre all hosts] **************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************
[WARNING]: Platform linux on host jenkins-master-01 is using the discovered Python interpreter at /usr/bin/python3.9, but future installation of another Python interpreter could
change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [jenkins-master-01]
[WARNING]: Platform linux on host jenkins-agent-01 is using the discovered Python interpreter at /usr/bin/python3.9, but future installation of another Python interpreter could
change the meaning of that path. See https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [jenkins-agent-01]

TASK [Create group] *******************************************************************************************************************************************************************
ok: [jenkins-master-01]
ok: [jenkins-agent-01]

TASK [Create user] ********************************************************************************************************************************************************************
ok: [jenkins-agent-01]
ok: [jenkins-master-01]

TASK [Install JDK] ********************************************************************************************************************************************************************
ok: [jenkins-agent-01]
ok: [jenkins-master-01]

PLAY [Get Jenkins master installed] ***************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Get repo Jenkins] ***************************************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Add Jenkins key] ****************************************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Install epel-release] ***********************************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Install Jenkins and requirements] ***********************************************************************************************************************************************
ok: [jenkins-master-01]

TASK [Ensure jenkins agents are present in known_hosts file] **************************************************************************************************************************
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
# 158.160.18.124:22 SSH-2.0-OpenSSH_8.7
changed: [jenkins-master-01] => (item=jenkins-agent-01)

TASK [Start Jenkins] ******************************************************************************************************************************************************************
skipping: [jenkins-master-01]

PLAY [Prepare jenkins agent] **********************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************
[WARNING]: Module remote_tmp /home/jenkins/.ansible/tmp did not exist and was created with a mode of 0700, this may cause issues when running as another user. To avoid this, create
the remote_tmp dir with the correct permissions manually
ok: [jenkins-agent-01]

TASK [Add master publickey into authorized_key] ***************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Create agent_dir] ***************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Add docker repo] ****************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Install some required] **********************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Update pip] *********************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Install Ansible] ****************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Reinstall Selinux] **************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Add local to PATH] **************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Create docker group] ************************************************************************************************************************************************************
ok: [jenkins-agent-01]

TASK [Add jenkinsuser to dockergroup] *************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Restart docker] *****************************************************************************************************************************************************************
changed: [jenkins-agent-01]

TASK [Install agent.jar] **************************************************************************************************************************************************************
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (10 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (9 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (8 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (7 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (6 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (5 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (4 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (3 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (2 retries left).
FAILED - RETRYING: [jenkins-agent-01]: Install agent.jar (1 retries left).
fatal: [jenkins-agent-01]: FAILED! => {"attempts": 10, "changed": false, "dest": "/opt/jenkins_agent/", "elapsed": 0, "gid": 1002, "group": "jenkins", "mode": "0755", "msg": "Request failed: <urlopen error [Errno 111] Connection refused>", "owner": "jenkins", "secontext": "unconfined_u:object_r:usr_t:s0", "size": 6, "state": "directory", "uid": 1001, "url": "http://158.160.24.79:8080/jnlpJars/agent.jar"}

PLAY RECAP ****************************************************************************************************************************************************************************
jenkins-agent-01           : ok=16   changed=10   unreachable=0    failed=1    skipped=0    rescued=0    ignored=0
jenkins-master-01          : ok=10   changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
...
