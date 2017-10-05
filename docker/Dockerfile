#
# twilio-contact-center web server
#
FROM node:8.6.0
LABEL vendor="KDDI Web Communications inc." \
    maintainer="yuto.yamada@kddi-web.com"

# yarn
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    --no-install-recommends \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
    && apt-get update && apt-get install -y \
    yarn \
    --no-install-recommends && rm -rf /var/lib/apt/lists/*

# set workdir
WORKDIR /www/twilio-contact-center

# exec after container run
COPY ./docker-entrypoint.sh /usr/local/bin/
RUN chmod 755 /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["yarn", "run", "start"]
