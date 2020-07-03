FROM archlinux:latest

ENV LANG=en_US.UTF-8
ADD http://worldclockapi.com/api/json/utc/now /opt/docker/etc/timestamp

RUN pacman -Syu --noconfirm \
   gcc-fortran \
   intel-mkl \
   meson \
&& echo -e "y\ny" | pacman -Scc --confirm

ENV LIBRARY_PATH=/opt/intel/mkl/lib/intel64

ARG USER=builder
ARG WORKDIR=/$USER
RUN useradd -m $USER && mkdir $WORKDIR && chown $USER $WORKDIR
WORKDIR $WORKDIR
USER $USER

CMD ["/bin/bash"]
