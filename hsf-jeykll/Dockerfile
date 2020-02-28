FROM jekyll/jekyll
LABEL maintainer="Graeme Stewart <graeme.andrew.stewart@cern.ch>"

# Install missing/fixed CA certs
# I don't know why the rucio certificate has such problems in the URL
# checked base image, but the fix is to use https://whatsmychaincert.com/
# to download the correct chain and then patch that in here.
# (https://www.sslshopper.com/ssl-checker.html is also a useful validation
# and does hint at issues with the intermediate certificates in the chain.)
COPY rucio.cern.ch.chain.crt /usr/local/share/ca-certificates/
RUN /usr/sbin/update-ca-certificates


# Bootstrap gem bundle so that jekyll can start quickly
WORKDIR /tmp
RUN gem install bundler
COPY Gemfile /tmp
RUN bundle install

# To avoid permissions issues it's best to use the --user option
# when starting this container and start as your own UID
WORKDIR /srv/jekyll
