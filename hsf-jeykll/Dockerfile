FROM jekyll/jekyll
LABEL maintainer="Graeme Stewart <graeme.andrew.stewart@cern.ch>"

# Install missing/fixed CA certs
COPY science.energy.gov.chain.crt spack.io.chain+root.crt rucio.cern.ch.chain.crt joomla-mi.mi.infn.it.chain.crt /usr/local/share/ca-certificates/
RUN /usr/sbin/update-ca-certificates

# Bootstrap gem bundle so that jekyll can start quickly
WORKDIR /tmp
RUN gem install bundler
COPY Gemfile /tmp
RUN bundle install

# To avoid permissions issues it's best to use the --user option
# when starting this container and start as your own UID
WORKDIR /srv/jekyll
