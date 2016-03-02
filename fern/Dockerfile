from mccaskey/fedora_ssh:latest
maintainer Alex McCaskey <mccaskeyaj@ornl.gov>
run mkdir /fern && cd /fern && mkdir build
run dnf -y install git cmake make libtool gcc-c++ boost-devel; \
	cd /fern && git clone --recursive https://github.com/jayjaybillings/fern; \
        cd /fern/build && cmake -DCMAKE_BUILD_TYPE=Release ../fern; \
        make 
run rm -rf /fern/fern && ln -s /fern/build/fern-exec /usr/bin/
