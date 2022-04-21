FROM python:3.8.7-slim-buster

# Updating
RUN apt-get update

# Install build-essential
RUN echo "Install build-essential" && \
	apt-get install -y build-essential wget lsb-release software-properties-common netcat nasm curl

# Install cmake
RUN echo "install cmake" && \
	yes | apt-get install cmake

# Install LLVM 14 version
RUN curl -O https://apt.llvm.org/llvm.sh && \
	chmod +x llvm.sh && \
	./llvm.sh 14

ENV PATH="/usr/lib/llvm-14/bin:${PATH}"

# Install libc++ and create symbolic link to .so file
RUN echo "install libc++" && \
	yes |apt-get install libc++-14-dev && \
	ln -s libc++abi.so.1 /usr/lib/llvm-14/lib/libc++abi.so

# Install Ninja
RUN echo "install Ninja" && \
	apt-get install -y ninja-build

# Install Rust
RUN echo "install Rust" && \
	curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

ENV PATH="/root/.cargo/bin:${PATH}"

# Install cargo
RUN echo "Install cargo" && \
	yes | apt-get install cargo

# Install Go
RUN echo "install Go" && \
	curl -O https://dl.google.com/go/go1.18.1.linux-amd64.tar.gz && \
	rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.1.linux-amd64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

# Install conan
RUN pip install conan

# Add Rust target for Android platforms
RUN rustup target add aarch64-linux-android && \
	rustup target add i686-linux-android && \
	rustup target add x86_64-linux-android && \
	rustup target add armv7-linux-androideabi

# Update Rust
RUN rustup update