FROM --platform=linux/amd64 ubuntu:20.04 as builder

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y gcc g++ make cmake

ADD . /UEFITool
WORKDIR /UEFITool/UEFIExtract
RUN cmake .
RUN make

FROM ubuntu:20.04 as package

COPY --from=builder /UEFITool/UEFIExtract /