FROM amazonlinux:2018.03

RUN yum update -y && \
  yum groupinstall -y "Development Tools" && \
  yum install -y wget

ENV NODE_ENV=production
ENV VERSION=v10.15.2
ENV DISTRO=linux-x64
ENV OUTPUT_DIR=/tmp

# node
RUN curl https://nodejs.org/dist/latest-v10.x/node-${VERSION}-${DISTRO}.tar.gz \
          --output ${OUTPUT_DIR}/node-${VERSION}-${DISTRO}.tar.gz && \
    cd ${OUTPUT_DIR} && \
    mkdir /usr/local/lib/nodejs && \
    tar -xvzf node-${VERSION}-${DISTRO}.tar.gz -C /usr/local/lib/nodejs && \
    mv /usr/local/lib/nodejs/node-${VERSION}-${DISTRO} /usr/local/lib/nodejs/node-${VERSION} && \
    rm -rf ${OUTPUT_DIR}

# yarn
RUN wget https://dl.yarnpkg.com/rpm/yarn.repo -O /etc/yum.repos.d/yarn.repo && \
    curl --silent --location https://rpm.nodesource.com/setup_8.x | bash - && \
    yum -y install yarn

ENV NODEJS_HOME=/usr/local/lib/nodejs/node-${VERSION}/bin
ENV PATH=${NODEJS_HOME}:$PATH
