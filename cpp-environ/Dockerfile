FROM ubuntu:16.04
RUN apt-get update
RUN apt-get -y install build-essential sudo git wget
RUN apt-get -y install llvm-4.0 clang-4.0 clang-format-4.0 libc++-dev
RUN adduser --disabled-login -gecos 'Sam Irvine' sirvine
RUN mkdir -p /home/sirvine/.ssh && chmod 700 /home/sirvine/.ssh && chown sirvine:sirvine /home/sirvine/.ssh

RUN sudo -u sirvine ssh-keyscan -H github.com >/home/sirvine/.ssh/known_hosts && chmod 600 /home/sirvine/.ssh/known_hosts
RUN sudo -u sirvine git clone https://github.com/svirvine/environs.git /home/sirvine/.environ.git
RUN sudo -u sirvine ln -s /home/sirvine/.environ.git/common/.gitconfig /home/sirvine/.gitconfig
RUN sudo -u sirvine ln -s /home/sirvine/.environ.git/common/.emacs_cpp /home/sirvine/.emacs
RUN sudo -u sirvine ln -s /home/sirvine/.environ.git/common/id_rsa.pub /home/sirvine/.ssh/authorized_keys
RUN sudo -u sirvine ln -s /home/sirvine/.environ.git/common/.tmux.conf /home/sirvine/.tmux.conf

RUN apt-get -y install libjpeg-dev libncurses-dev libpng-dev libtiff-dev libxpm-dev libgif-dev
RUN wget http://ftp.gnu.org/gnu/emacs/emacs-25.3.tar.xz
RUN tar -xJf emacs-25.3.tar.xz && cd emacs-25.3 && ./configure --with-x-toolkit=no --prefix=/usr/local/emacs25 && make -j 4 install
