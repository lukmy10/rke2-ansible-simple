Two simple separated playbooks to build RKE2 server node and second for agent.
inventory.ini must be adopted with server and agent IPs.
Before build stop and disbale firewalld for both nodes. 
config_server.yaml and config_agent.yaml must be adopted with server IP address - this is working for me.
this is executed by 'ansible-playbook -i inventory.ini rke2_server_install.yml --ask-pass -K' and 'ansible-playbook -i inventory.ini rke2_agent_install.yml --ask-pass -K'.
rke2_server_install.yml will create user to be used by kubectl and configure.
Build server first - test with 'kubectl get nodes' with user you have created during server build , then build agent node - test with 'kubectl get nodes' on server node .
Issue I had - I have cloned agent node from server node in vmware and this is not working then - please use fresh installations of nodes.
tested with ansible [core 2.16.5]
Tested on Fedora42 and OpenSUSE Leap 15.6 so far.
This is for lab purpose only don't use on prod.
