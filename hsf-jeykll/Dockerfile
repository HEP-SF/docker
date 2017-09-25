FROM jekyll/jekyll
LABEL maintainer="Graeme Stewart <graeme.andrew.stewart@cern.ch>"

# Bootstrap gem bundle so that jekyll can start quickly
WORKDIR /tmp
RUN gem install bundler
COPY Gemfile /tmp
RUN bundle install

# Install missing CA certificate for science.energy.gov
WORKDIR /srv/jekyll
COPY science.energy.gov.chain.crt /usr/local/share/ca-certificates
RUN /usr/sbin/update-ca-certificates
