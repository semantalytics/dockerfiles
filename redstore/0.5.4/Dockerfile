FROM alpine:3.9.3

RUN apk add redland curl tar build-base pkgconfig libxml2-dev perl

RUN curl http://download.librdf.org/source/raptor2-2.0.15.tar.gz | tar xvz
RUN cd raptor2-2.0.15 && ./configure && make && make install

RUN curl http://download.librdf.org/source/rasqal-0.9.33.tar.gz | tar xvz
RUN cd rasqal-0.9.33 && ./configure && make && make install

RUN curl http://download.librdf.org/source/redland-1.0.17.tar.gz | tar xvz
RUN cd redland-1.0.17 && ./configure && make && make install

RUN curl https://www.aelius.com/njh/redstore/redstore-0.5.4.tar.gz | tar xvz
RUN cd redstore-0.5.4 && ./configure && make && make install

RUN addgroup -S redstore && adduser -S -G redstore redstore
USER redstore

EXPOSE 8080

ENTRYPOINT ["/usr/local/bin/redstore"]

CMD["-p 8080"]
