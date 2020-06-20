FROM golang:alpine

# maybe use --no-cache to update apk

# needed for go get
RUN apk add git

# python 3 is used for json beautifing
RUN apk add python3 

# openssl is used to download cert
RUN apk add openssl

RUN go get github.com/zmap/zlint/v2/cmd/zlint

# The following is just an example
RUN echo -n | openssl s_client -connect example.com:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > test1.cert
RUN zlint test1.cert | python3 -m json.tool
