FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common
# RUN add-apt-repository ppa:octave/stable
# RUN apt-get update
# RUN apt-get install -y octave

RUN apt-get install -y gcc g++ gfortran make libblas-dev liblapack-dev libpcre3-dev libarpack2-dev libcurl4-gnutls-dev epstool libfftw3-dev transfig libfltk1.3-dev libfontconfig1-dev libfreetype6-dev libgl2ps-dev libglpk-dev libreadline-dev gnuplot-x11 libgraphicsmagick++1-dev libhdf5-serial-dev openjdk-8-jdk libsndfile1-dev llvm-dev lpr texinfo libgl1-mesa-dev libosmesa6-dev pstoedit portaudio19-dev libqhull-dev libqrupdate-dev libqscintilla2-dev libqt4-dev libqtcore4 libqtwebkit4 libqt4-network libqtgui4 libqt4-opengl-dev libsuitesparse-dev texlive libxft-dev zlib1g-dev autoconf automake bison flex gperf gzip icoutils librsvg2-bin libtool perl rsync tar

COPY octave-4.4.1.tar.gz .
RUN tar -xf octave-4.4.1.tar.gz

RUN cd octave-4.4.1 && ./configure --without-qt && make && make install

#RUN ./configure --with-blas=-L/home/linuxbrew/.linuxbrew/opt/openblas/lib -lopenblas --prefix=/home/linuxbrew/.linuxbrew/Cellar/octave/4.4.1_5 --disable-silent-rules --enable-link-all-dependencies --enable-shared --disable-static --disable-docs --with-hdf5-includedir=/home/linuxbrew/.linuxbrew/opt/hdf5/include --with-hdf5-libdir=/home/linuxbrew/.linuxbrew/opt/hdf5/lib --with-x=no --with-portaudio --with-sndfile --without-qt

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

RUN octave --eval "pkg install -forge image"

RUN rm octave-4.4.1.tar.gz
RUN rm -rf octave-4.4.1
