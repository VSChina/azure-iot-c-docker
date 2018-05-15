FROM ubuntu:xenial

RUN apt-get update && apt-get install -y --no-install-recommends software-properties-common \
    cmake gcc g++ \
    gdb procps
RUN add-apt-repository -y ppa:aziotsdklinux/ppa-azureiot
RUN apt-get update && apt-get install -y azure-iot-sdk-c-dev
RUN apt-get install make

COPY . /app
RUN mkdir cmake
WORKDIR /app/cmake
RUN ls /app
RUN cmake .. 
RUN make

CMD ["./iothub_client_sample_mqtt"]
