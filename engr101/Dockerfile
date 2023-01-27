FROM mathworks/matlab:r2021b
COPY license.dat /license.dat

ENV MLM_LICENSE_FILE=/license.dat

CMD ["/bin/bash"]
ENTRYPOINT []

USER root

# See https://github.com/mathworks-ref-arch/matlab-dockerfile/blob/main/MPM.md
RUN wget -P /usr/bin https://www.mathworks.com/mpm/glnxa64/mpm
RUN chmod 744 /usr/bin/mpm
RUN mpm install --release=r2021b --destination=/home/autograder/matlab --products MATLAB Image_Processing_Toolbox Statistics_and_Machine_Learning_Toolbox

RUN apt-get update --fix-missing && apt-get install -y python3

RUN mkdir -p /home/autograder/working_dir

RUN useradd autograder && \
   mkdir -p /home/autograder/working_dir && \
   chown -R autograder:autograder /home/autograder

WORKDIR /home/autograder/working_dir
