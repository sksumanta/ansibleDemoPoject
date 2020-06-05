

- import_playbook: books/source_control.yaml
- import_playbook: books/loadvars.yaml
- import_playbook: books/downloadBuild.yaml
- import_playbook: books/tomcat_setup.yaml
- import_playbook: books/kickoff.yaml
- import_playbook: books/deployBuild.yaml


# how to pull the data from GitHub.
# ansible-playbook -i ../inventories/uat/hosts.yaml  source_control.yaml  -e "theEnv=uat" -e "myDomain=island"


ansible-playbook -i ../inventories/uat/hosts.yaml source_control.yaml -e "theEnv=uat" -e "mydomain=island"
ansible-playbook -i ../inventories/uat/hosts.yaml loadVars.yaml -e "theEnv=uat" -e "mydomain=island"
ansible-playbook -i ../inventories/uat/hosts.yaml downloadBuild.yaml -e "theEnv=uat" -e "mydomain=island" -e "buildNo=5"
ansible-playbook -i ../inventories/uat/hosts.yaml tomcat_setup.yaml -e "theEnv=uat" -e "mydomain=island"
ansible-playbook -i ../inventories/uat/hosts.yaml kickoff.yaml -e "theEnv=uat" -e "mydomain=island"  --skip-tags starttomcat
ansible-playbook -i ../inventories/uat/hosts.yaml deployBuild.yaml -e "theEnv=uat" -e "mydomain=island"  -e "buildNo=5"
ansible-playbook -i ../inventories/uat/hosts.yaml kickoff.yaml -e "theEnv=uat" -e "mydomain=island"  --skip-tags stoptomcat

 
