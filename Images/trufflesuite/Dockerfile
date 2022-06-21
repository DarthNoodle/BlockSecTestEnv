#Author
# https://www.joshfinnie.com/blog/getting-truffle-and-ganache-working-with-docker/


FROM node:16-bullseye-slim as base

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
        build-essential \
        python3 && \
    rm -fr /var/lib/apt/lists/* && \
    rm -rf /etc/apt/sources.list.d/*

RUN npm install --global --quiet npm truffle ganache-cli

#FROM base as truffle
#
#RUN mkdir -p /home/app
#WORKDIR /home/app
#
#COPY package.json /home/app
#COPY package-lock.json /home/app

#RUN npm install --quiet
#
#COPY truffle-config.js /home/app
#COPY contracts /home/app/contracts
#COPY migrations /home/app/migrations/
#COPY test /home/app/test/
#
#CMD ["truffle", "version"]

FROM base as ganache

RUN mkdir -p /home
WORKDIR /home
ENV NMEMONIC ''

EXPOSE 8545

ENTRYPOINT ["bash", "-c", "ganache-cli -m '${NMEMONIC}'"]

# Spin up the container but jump to a bash shell (good for debugging and messing around) 
# docker run --rm -it --entrypoint bash noodleware/ganache

# Spin up a new/fresh network with a specific nmemonic
# docker run -d -e NMEMONIC="sick item plug chalk sock viable grief keen daughter tank mix april" noodleware/ganache