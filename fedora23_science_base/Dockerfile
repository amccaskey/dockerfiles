from fedora:latest
maintainer Alex McCaskey <mccaskeyaj@ornl.gov>
run cd / && dnf -y install wget git make environment-modules libtool gcc-c++ unzip \ 
	cmake mpich-devel boost-mpich-devel file which python 
run cd / && git clone https://bitbucket.org/petsc/petsc petsc_src && cd petsc_src && git fetch && git checkout v3.6.1
run echo 'module load mpi/mpich-x86_64' >> /root/.bashrc 
run ln -s /usr/lib64/mpich/bin/* /usr/bin/
run cd /petsc_src && ./configure \
    --prefix=/petsc/mpich_petsc-3.6.1/gcc \
    --download-hypre=1 \
    --with-ssl=0 \
    --with-debugging=no \
    --with-pic=1 \
    --with-shared-libraries=1 \
    --with-cc=mpicc \
    --with-cxx=mpicxx \
    --with-fc=mpif90 \
    --download-fblaslapack=1 \
    --download-metis=1 \
    --download-parmetis=1 \
    --download-superlu_dist=1 \
    --download-scalapack=1 \
    --download-mumps=1 \
    CC=mpicc CXX=mpicxx FC=mpif90 F77=mpif77 F90=mpif90 \
    CFLAGS='-fPIC -fopenmp' \
    CXXFLAGS='-fPIC -fopenmp' \
    FFLAGS='-fPIC -fopenmp' \
    FCFLAGS='-fPIC -fopenmp' \
    F90FLAGS='-fPIC -fopenmp' \
    F77FLAGS='-fPIC -fopenmp' \
    PETSC_DIR=`pwd` && make PETSC_DIR=/petsc_src PETSC_ARCH=arch-linux2-c-opt all \ 
    && make PETSC_DIR=/petsc_src PETSC_ARCH=arch-linux2-c-opt install
run echo "PETSC_DIR=/petsc/mpich_petsc-3.6.1/gcc" >> /root/.bashrc
run rm -rf /petsc_src
