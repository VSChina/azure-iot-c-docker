FROM ubuntu

RUN apt-get update && apt-get install -y software-properties-common python-software-properties \
    cmake gcc g++ \
    gdb procps
RUN add-apt-repository ppa:aziotsdklinux/ppa-azureiot
RUN apt-get update && apt-get install -y azure-iot-sdk-c-dev

COPY . /app
RUN mkdir cmake
WORKDIR /app/cmake
RUN cmake -DCMAKE_BUILD_TYPE=Debug .. 
RUN make

CMD ["./iothub_client_sample_mqtt"]
