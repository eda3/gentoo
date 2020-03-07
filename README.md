### Change to root user
sudo su

### Make ssh key
sh-keygen -t rsa

useradd user -m -G users,wheel,tty -s /bin/bash
passwd user

### ssh

vi /etc/ssh/sshd_config
# Port 22
# Protocol 2

/etc/init.d/sshd start

### brew

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"


#sudo apt-get install build-essential
#sudo yum groupinstall 'Development Tools'
quickpkg sys-devel


echo 'eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)' >> /home/user/.bash_profile
eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
brew install gcc


### Docker
sudo emerge -av app-emulation/docker

groupadd docker

sudo usermod -a -G docker user
/etc/init.d/docker start
rc-update add docker default
systemctl start docker
systemctl enable docker
