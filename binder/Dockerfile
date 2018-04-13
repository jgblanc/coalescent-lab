FROM rocker/binder:3.4.2

RUN apt-get -y install pkg-config libgsl0-dev hdf5-tools libhdf5-serial-dev libreadline-dev

RUN python3 -m venv ${VENV_DIR} && \
    pip3 install --no-cache-dir \
	numpy \
 	scipy \
	matplotlib \
	seaborn \
	rpy2 \
	msprime

# Copy repo into ${HOME}, make user own $HOME
USER root
COPY . ${HOME}
RUN chown -R ${NB_USER} ${HOME}
USER ${NB_USER}

## run any install.R script we find
RUN if [ -f install.R ]; then R --quiet -f install.R; fi
