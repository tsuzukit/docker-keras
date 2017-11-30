FROM debian:jessie

RUN apt-get update && \
    apt-get install -y xvfb \
                       wget \
                       curl \
                       unzip \
                       python3 \
                       python3-pip \
                       libgconf-2-4 \
                       libxml2-dev \
                       libxslt1-dev \
                       lib32z1-dev \
                       python3-scipy \
                       python3-h5py \
                       libjpeg-dev \
                       zlib1g-dev \
                       libmysqlclient-dev \
                       locales && \
    rm -rf /var/lib/apt/lists/*

# Locale and language setting
RUN locale-gen ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LC_CTYPE ja_JP.UTF-8
RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8

# Setup python
WORKDIR /usr/repo
RUN pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.4.0-cp34-cp34m-linux_x86_64.whl
COPY ./docker/requirements.txt /usr/repo/requirements.txt
RUN pip3 install -r requirements.txt

# Create symlink
RUN ln /usr/bin/python3 /usr/bin/python && \
    ln /usr/bin/pip3 /usr/bin/pip

ENTRYPOINT tail -f /dev/null
