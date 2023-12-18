# Oracle Linux
- oracle linux is compiled from redhat linux.

even amazon linux seems to be based on redhat.

# Oracle linux install commands
# OL7
# maven
 sudo curl -fsSL https://downloads.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz | sudo tar xzf - -C /usr/share
 sudo mv /usr/share/apache-maven-3.8.6 /usr/share/maven
 sudo ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

 # OL8
Reference: https://linuxhint.com/install_docker_on_oracle_linux_8/

sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

sudo dnf install docker-ce-<version> -y
sudo systemctl enable docker.service
systemctl start docker.service
