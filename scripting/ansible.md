# Ansible

## Install Ansible
AGY2F7WZ
### Create virtual env
virtualenv ansible

### Activate virtual env
cd /Users/cs/Desktop/repositories/python-virtual-env
source ansible/bin/activate

cd ansible/host-dir

ansible all -i hosts-phx -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/"

### Prerequisite configure reload_ssh in your bash profile
Reference: https://confluence.oci.oraclecorp.com/pages/viewpage.action?spaceKey=DLCBLD&title=SSH+Configuration+for+dlcbld+host
SECEDGE-SSH-Configs in above link

### configure your ssh configuration

22:23 $ cat ~/.ssh/config 
Include ssh_configs/config
Include user
Include bastioniad

22:24 $ cat ~/.ssh/bastioniad 
Host 10.*
 ProxyJump overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaaxkqy74yattueonuskbyhjiw7jjf6ljiepscrzx6hrrwrr74k3tlq-172.16.220.210


## Phase 2

ansible all -i hosts-iad -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -o ProxyJump="overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaaxkqy74yattueonuskbyhjiw7jjf6ljiepscrzx6hrrwrr74k3tlq-172.16.220.210"'
ansible all -i hosts-iad -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-extra-args='-J overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaaxkqy74yattueonuskbyhjiw7jjf6ljiepscrzx6hrrwrr74k3tlq-172.16.220.210'  --ssh-common-args='-o StrictHostKeyChecking=no' --ssh-common-args='-o UserKnownHostsFile=/dev/null'

ansible all -i hosts-phx -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-o ProxyJump="overlay-host.bastion.us-phoenix-1.oci.oracleiaas.com,ocid1.bastion.oc1.phx.amaaaaaaxkqy74yazp4rry6siudxoyj4xwkh5rbgtj4h43pfgnakcbtnn3na-172.16.236.229"'

ansible all -i hosts-london -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.uk-london-1.oci.oracleiaas.com,ocid1.bastion.oc1.uk-london-1.amaaaaaaxkqy74yaeipxkyouhepypsehpsjq6xbfg4x6hcwaaq7mvlgldhbq-192.168.203.46'

ansible all -i hosts-frankfurt -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.eu-frankfurt-1.oci.oracleiaas.com,ocid1.bastion.oc1.eu-frankfurt1.amaaaaaaxkqy74yanmznvs5nigai7pqsvcangqspcrvuyvwfudjy5bpqh7da-192.168.160.174'

--------------
ssh -J overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaaxkqy74yattueonuskbyhjiw7jjf6ljiepscrzx6hrrwrr74k3tlq-172.16.220.210 10.2.2.244

ansible all -i hosts-iad -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaaxkqy74yattueonuskbyhjiw7jjf6ljiepscrzx6hrrwrr74k3tlq-172.16.220.210'

ssh -J overlay-host.bastion.us-phoenix-1.oci.oracleiaas.com,ocid1.bastion.oc1.phx.amaaaaaaxkqy74yazp4rry6siudxoyj4xwkh5rbgtj4h43pfgnakcbtnn3na-172.16.236.229 10.2.2.116

ansible all -i hosts-phx -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.us-phoenix-1.oci.oracleiaas.com,ocid1.bastion.oc1.phx.amaaaaaaxkqy74yazp4rry6siudxoyj4xwkh5rbgtj4h43pfgnakcbtnn3na-172.16.236.229'


ssh -J overlay-host.bastion.uk-london-1.oci.oracleiaas.com,ocid1.bastion.oc1.uk-london-1.amaaaaaaxkqy74yaeipxkyouhepypsehpsjq6xbfg4x6hcwaaq7mvlgldhbq-192.168.203.46 10.2.2.218

ansible all -i hosts-london -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.uk-london-1.oci.oracleiaas.com,ocid1.bastion.oc1.uk-london-1.amaaaaaaxkqy74yaeipxkyouhepypsehpsjq6xbfg4x6hcwaaq7mvlgldhbq-192.168.203.46'

ssh -J overlay-host.bastion.eu-frankfurt-1.oci.oracleiaas.com,ocid1.bastion.oc1.eu-frankfurt1.amaaaaaaxkqy74yanmznvs5nigai7pqsvcangqspcrvuyvwfudjy5bpqh7da-192.168.160.174 10.2.2.185

ansible all -i hosts-frankfurt -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-prod/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.eu-frankfurt-1.oci.oracleiaas.com,ocid1.bastion.oc1.eu-frankfurt1.amaaaaaaxkqy74yanmznvs5nigai7pqsvcangqspcrvuyvwfudjy5bpqh7da-192.168.160.174'


#### IAD DEV
ssh -J overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaab6fywtyaax2eiye7u3dfwk3irfkfmpobxoz7rtrsidioho2626fa-172.16.226.242 10.2.2.250

ansible all -i hosts-iad-dev -a "/usr/bin/du -h /var/odo/volumes/dlc-build-service-dp-worker-dev/logs/devops-service/" --ssh-common-args='-J overlay-host.bastion.us-ashburn-1.oci.oracleiaas.com,ocid1.bastion.oc1.iad.amaaaaaab6fywtyaax2eiye7u3dfwk3irfkfmpobxoz7rtrsidioho2626fa-172.16.226.242'