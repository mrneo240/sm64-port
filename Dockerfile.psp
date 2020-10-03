FROM ubuntu:18.04 as build

RUN apt-get update && \
    apt-get install -y \
      binutils-mips-linux-gnu \
      bsdmainutils \
      build-essential \
      libaudiofile-dev \
      pkg-config \
      python3 \
      wget \
      zlib1g-dev

RUN wget https://github.com/pspdev/pspdev/releases/download/v20200725-2/pspdev-linux-x64.tar.gz && \
  echo '301f01970aa1c1aac7ba31cd698aaec4dd673e5e9b8acc297a953f97e3abe395 pspdev-linux-x64.tar.gz' | sha256sum pspdev-linux-x64.tar.gz && \
  tar xvzf pspdev-linux-x64.tar.gz && \
  rm pspdev-linux-x64.tar.gz

RUN mkdir /sm64
WORKDIR /sm64
ENV PATH="/pspdev/bin:${PATH}"

CMD echo 'usage: docker run --rm -v $(pwd):/sm64 sm64 make TARGET_PSP=1 VERSION=${VERSION:-us} -j4\n'
