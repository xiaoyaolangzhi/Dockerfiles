FROM library/golang:latest
WORKDIR /root
RUN apt-get clean && apt-get update && apt-get install -y unzip
RUN curl -o buildpack.zip https://codeload.github.com/cloudfoundry/python-buildpack/zip/v1.6.8 && \
    unzip buildpack.zip && rm buildpack.zip
RUN cd `ls` && /bin/bash -c "source .envrc &&  cd src/python/vendor/github.com/cloudfoundry/libbuildpack/packager/buildpack-packager && go install && cd - && buildpack-packager --cached"
CMD ["/bin/bash"]
