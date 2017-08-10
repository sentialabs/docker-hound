FROM ruby:2.4.1

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - \
  && apt-get install -y --no-install-recommends \
  locales \
  nodejs \
  libqt4-dev \
  libqtwebkit-dev \
  git \
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
RUN npm install

CMD bundle exec rake jobs:work
