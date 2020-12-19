FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update &&\
    apt-get install -y git \
                      swig \
                      x11-apps \
                      cmake \
                      doxygen \
                      build-essential \
                      libboost-all-dev \
                      libtool \
                      libusb-1.0-0 \
                      libusb-1.0-0-dev \
                      libudev-dev \
                      libncurses5-dev \
                      libfftw3-bin \
                      libfftw3-dev \
                      libfftw3-doc \
                      libcppunit-1.14-0 \
                      libcppunit-dev \
                      libcppunit-doc \
                      ncurses-bin \
                      cpufrequtils \
                      qt4-bin-dbg \
                      qt4-default \
                      qt4-doc \
                      qt4-dev-tools \
                      libqt4-dev \
                      libqt4-dev-bin
RUN apt-get install -y python3 \
                      python3-pip \
                      python3-mako \
                      python3-numpy \
                      python3-requests \
                      python-mako \
                      python-numpy \
                      python-numpy-doc \
                      python-numpy-dbg \
                      python-scipy \
                      python-docutils \
                      python-six \
                      python-lxml \
                      python-qt4 \
                      python-qt4-dbg \
                      python-qt4-dev \
                      python-gps \
                      python-setuptools \
                      python-opengl \
                      python-cheetah \
                      libqwtplot3d-qt5-dev \
                      libqwt-dev \
                      libqwt6abi1 \
                      libfftw3-bin \
                      libfftw3-dev \
                      libfftw3-doc 
RUN apt-get install -y ncurses-bin \
                      libncurses5 \
                      libncurses5-dev \
                      libncurses5-dbg \
                      libfontconfig1-dev \
                      libxrender-dev \
                      libpulse-dev \
                      libtool \
                      python-dev \
                      libfftw3-dev \
                      libcppunit-dev \
                      libusb-dev \
                      libusb-1.0-0-dev \
                      fort77 \
                      libsdl1.2-dev \
                      python-wxgtk3.0 \
                      libqt4-dev \
                      ccache \
                      libgsl-dev \
                      libusb-1.0-0-dev \
                      pyqt4-dev-tools \
                      python-qwt5-qt4 
RUN apt-get install -y wget \
                      libxi-dev \
                      gtk2-engines-pixbuf \
                      r-base-dev \
                      python-tk \
                      liborc-0.4-0 \
                      liborc-0.4-dev \
                      libasound2-dev \
                      python-gtk2 \
                      libzmq3-dev \
                      libzmq5 \
                      python-requests \
                      python-sphinx \
                      libcomedi-dev \
                      python-zmq \
                      python-six \
                      libgps-dev \
                      libgps23 \
                      gpsd 
RUN apt-get install -y gpsd-clients \ 
		                  dpdk \ 
                      dpdk-dev \ 
                      librte-pmd-mlx5-17.11 \
                      libogg-dev \
                      libogg0 \
                      libvorbis-dev \
                      libvorbis0a \
                      libvorbisenc2 \ 
                      libvorbisfile3 \
                      libpng++-dev \
                      libpng-dev \
                      libpng-tools \
                      libpng16-16 \
                      libnova-0.16-0 \
                      libnova-dev \
                      python3-tornado \ 
                      python3-requests \
                      python-matplotlib


RUN mkdir /sdr
WORKDIR /sdr
RUN git clone https://github.com/EttusResearch/uhd

WORKDIR /sdr/uhd
RUN git checkout UHD-3.15.LTS

WORKDIR /sdr/uhd/host/
RUN mkdir build

WORKDIR /sdr/uhd/host/build
RUN cmake ..

RUN make -j2

RUN make install

RUN ldconfig

RUN uhd_images_downloader 

WORKDIR /sdr

RUN git clone --recursive https://github.com/gnuradio/gnuradio

WORKDIR /sdr/gnuradio

RUN git checkout maint-3.7

RUN git submodule update --init --recursive

RUN mkdir build

WORKDIR /sdr/gnuradio/build

RUN cmake ..

RUN make -j2

RUN make install

RUN ldconfig

RUN gnuradio-config-info --version

WORKDIR /sdr

RUN git clone https://github.com/osmocom/gr-osmosdr

WORKDIR /sdr/gr-osmosdr

RUN git checkout gr3.7

RUN mkdir build

WORKDIR /sdr/gr-osmosdr/build

RUN cmake ..

RUN make -j2

RUN make install

RUN ldconfig

WORKDIR /sdr

RUN git clone https://github.com/devnulling/gr-satnogs

WORKDIR /sdr/gr-satnogs

RUN mkdir build

WORKDIR /sdr/gr-satnogs/build

RUN cmake ..

RUN make -j2

RUN make install

RUN ldconfig

WORKDIR /sdr

