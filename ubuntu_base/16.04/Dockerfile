from ubuntu:16.04
maintainer Alex McCaskey <mccaskeyaj@ornl.gov>
run apt-get -y upgrade && apt-get -y update && apt-get install -y software-properties-common python-software-properties && add-apt-repository ppa:ubuntu-toolchain-r/test \
   && apt-get update && apt-get install -y vim openssh-server curl libboost-all-dev libblas-dev liblapack-dev wget git make libtool python cmake unzip gcc-6 g++-6 mpich gdb \
   && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6 && rm -rf /var/lib/apt/lists/* \
   && mkdir /var/run/sshd && echo 'root:password' | chpasswd \
   && sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
# SSH login fix. Otherwise user is kicked off after login
   && sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd \
   && echo "export VISIBLE=now" >> /etc/profile
workdir /projects
expose 22
cmd ["/usr/sbin/sshd", "-D"]
