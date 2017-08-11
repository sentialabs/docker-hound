FROM ruby:2.4.1

RUN apt-get update \
  && apt-get install -y apt-transport-https \
  && curl -sS https://deb.nodesource.com/gpgkey/nodesource.gpg.key \
    | apt-key add - \
  && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg \
    | apt-key add - \
  && echo "deb https://deb.nodesource.com/node_6.x jessie main" \
    > /etc/apt/sources.list.d/nodesource.list \
  && echo "deb https://dl.yarnpkg.com/debian/ stable main" \
    > /etc/apt/sources.list.d/yarn.list \
  && apt-get update \
  && apt-get install -y --no-install-recommends \
    locales \
    nodejs \
    yarn \
    python3 \
    python3-pip \
    dbus-1-dbg \
    libqt5webkit5-dev \
    qt5-default \
    xvfb \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN mkdir -p /usr/src/app
RUN git clone https://github.com/houndci/linters /usr/src/app \
    && cd /usr/src/app \
    && git reset --hard 5f53339d7f6bcf880a58db6820f10b0a720a7925
WORKDIR /usr/src/app

RUN bundle install
RUN yarn install --production true
RUN pip3 install -r requirements.txt

CMD bin/resque
