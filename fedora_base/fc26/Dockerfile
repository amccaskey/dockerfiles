from fedora:26
expose 22
RUN dnf -y update && dnf -y install curl \
    subversion gdb wget git make environment-modules \
    libtool gcc-c++ unzip cmake mpich-devel \
    boost-mpich-devel python openssh-server \
    procps mc nmap sudo passwd && dnf clean all 
run dnf -y update vim-minimal && dnf -y install vim-enhanced
RUN mkdir /var/run/sshd && \
    sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
    echo "%sudo ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' 
run echo 'root:password' | chpasswd
run sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/ssh_config
run echo "export VISIBLE=now" >> /etc/profile && mkdir /projects
WORKDIR /projects
CMD ["/usr/sbin/sshd", "-D"]
