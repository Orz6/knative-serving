# Dockerfile to bootstrap build and test in openshift-ci

FROM openshift/origin-release:golang-1.10

# Add Google Cloud SDK repository
ADD openshift/ci-operator/build-image/google-cloud-sdk.repo /etc/yum.repos.d/

# Add kubernetes repository
ADD openshift/ci-operator/build-image/kubernetes.repo /etc/yum.repos.d/

ADD openshift/ci-operator/build-image/entrypoint /usr/local/bin/

RUN yum install -y google-cloud-sdk kubectl ansible && \
    go get github.com/google/go-containerregistry/cmd/ko

RUN chmod g+rw /etc/passwd

ENTRYPOINT [ "/usr/local/bin/entrypoint" ]
