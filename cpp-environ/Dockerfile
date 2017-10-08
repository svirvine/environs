FROM ubuntu:16.04

RUN apt-get update
RUN apt-get -y install build-essential sudo
RUN apt-get -y install llvm-4.0 clang-4.0 clang-format-4.0 libc++-dev

RUN useradd -gecos ',,,,' sirvine
RUN mkdir -p /home/sirvine/.ssh && chmod 600 /home/sirvine/.ssh && chown sirvine:sirvine /home/sirvine/.ssh
COPY ../common/sirvine.pub /home/sirvine/.ssh/authorized_keys
RUN chown sirvine:sirvine /home/sirvine/.ssh/authorized_keys
COPY ../common/dot_emacs /home/sirvine/.emacs
RUN chown sirvine:sirvine /home/sirvine/.emacs
COPY dot_emacs_cpp /home/sirvine/dot_emacs_cpp
RUN cat /home/sirvine/dot_emacs_cpp >> /home/sirvine/.emacs && rm /home/sirvine/dot_emacs_cpp
COPY ../common/dot_gitconfig /home/sirvine/.gitconfig
RUN chown sirvine:sirvine /home/sirvine/.gitconfig
COPY ../common/dot_tmux.conf /home/sirvine/.tmux.conf
RUN chown sirvine:sirvine /home/sirvine/.tmux.conf

RUN apt-get -y install libjpeg-dev libncurses-dev libpng-dev libtiff-dev libxpm-dev libgif-dev
RUN wget http://ftp.gnu.org/gnu/emacs/emacs-25.3.tar.xz
RUN tar -xJf emacs-25.3.tar.xz && cd emacs-25.3 && ./configure --with-x-toolkit=no --prefix=/usr/local/emacs25 && make -j 4 install
