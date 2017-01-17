FROM ubuntu:16.04
run apt-get -y update && apt-get install -y software-properties-common python-software-properties && add-apt-repository ppa:ubuntu-toolchain-r/test
RUN apt-get update && apt-get install -y vim openssh-server curl libboost-all-dev libblas-dev liblapack-dev wget git make libtool python cmake unzip gcc-6 g++-6 mpich
run update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6
RUN mkdir /var/run/sshd 
RUN echo 'root:password' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN echo "export VISIBLE=now" >> /etc/profile
WORKDIR /projects

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
