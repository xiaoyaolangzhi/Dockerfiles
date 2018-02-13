FROM library/golang:latest
WORKDIR /root
RUN apt-get clean && apt-get update && apt-get install -y unzip
RUN curl -o buildpack.zip https://codeload.github.com/cloudfoundry/php-buildpack/zip/v4.3.49 && \
    unzip buildpack.zip && rm buildpack.zip
RUN cd `ls` && /bin/bash -c "source .envrc &&  cd src/go/vendor/github.com/cloudfoundry/libbuildpack/packager/buildpack-packager && go install && cd - && buildpack-packager --cached"
CMD ["/bin/bash"]
