FROM ubuntu:latest

RUN apt update

# Prep basic packages to build STM32 CMake project
RUN apt install -y \
	build-essential \
	ninja-build \
	git gnupg2 \
	stlink-tools \
	xz-utils curl 

# Get ARM Toolchain
RUN apt install -y wget \
	&& wget https://developer.arm.com/-/media/Files/downloads/gnu/13.2.rel1/binrel/arm-gnu-toolchain-13.2.rel1-x86_64-arm-none-eabi.tar.xz -O gcc-arm-none-eabi.tar.xz \
	&& mkdir /opt/gcc-arm-none-eabi-13.2.rel1 \
	&& tar xf gcc-arm-none-eabi.tar.xz \
      -C /opt/gcc-arm-none-eabi-13.2.rel1 --strip-components 1 \
	&& rm gcc-arm-none-eabi.tar.xz \
    && ln -s /opt/gcc-arm-none-eabi-13.2.rel1/bin/* /usr/local/bin


# Install cmake
RUN apt purge -y cmake \
	&& apt install -y openssl \
	&& wget https://github.com/Kitware/CMake/releases/download/v3.28.3/cmake-3.28.3-linux-x86_64.tar.gz -O cmake.tar.gz \
	&& mkdir /opt/cmake-3.28 \
	&& tar xf cmake.tar.gz -C /opt/cmake-3.28 --strip-components 1 \
	&& rm cmake.tar.gz \
	&& ln -s /opt/cmake-3.28/bin/* /usr/local/bin

# Get static analysis tools: clang-format clang-tidy, Lizard, cpplint
RUN apt-get install -y \
	clang-format clang-tidy \
	python3 python3-pip \
	&& pip install lizard cpplint \
	&& apt-get clean