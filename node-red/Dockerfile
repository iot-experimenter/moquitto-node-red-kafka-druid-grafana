# *******************************************************************************
# docker build --build-arg UID=$(id -u) --build-arg GID=$(id -g) -t noderedjohan1 .
# *******************************************************************************
#ARG NODE_VERSION=6
#FROM node:${NODE_VERSION}

# Home directory for Node-RED application source code.
#RUN mkdir -p /usr/src/node-red

# User data directory, contains flows, config and nodes.
#RUN mkdir /data

#WORKDIR /usr/src/node-red

# Add node-red user so we aren't running as root.
#RUN useradd --home-dir /usr/src/node-red --no-create-home node-red \
#    && chown -R node-red:node-red /data \
#&& chown -R node-red:node-red /usr/src/node-red

# Add core user so we aren't running as root.
#
# We don't run as node-red because we want to mount EFS,
# and the node-red user does not exist there.
# Use the core UID.
#RUN adduser -h /usr/src/node-red -D -H -u 500 core \
#    && chown -R core:core /data \
#    && chown -R core:core /usr/src/node-red
#USER core
#USER node-red

# package.json contains Node-RED NPM module and node dependencies
#COPY package.json /usr/src/node-red/
#RUN npm install latest-version

# User configuration directory volume
#VOLUME ["/data"]
#EXPOSE 1880
# Environment variable holding file path for flows configuration
#ENV FLOWS=flows.json
#ENV NODE_PATH=/usr/src/node-red/node_modules:/data/node_modules

#CMD ["npm", "start", "--", "--userDir", "/data"]





FROM nodered/node-red-docker
USER root
RUN chmod 777 /usr/local/lib/node_modules	
RUN export npm_config_prefix=/home/node/.npm-global
USER node-red

#*********************************************************************************
#ENV NPM_CONFIG_PREFIX=/root/.node-red
#ARG UNAME=johan
#ARG UID=1000
#ARG GID=1000
#RUN groupadd -g $GID -o $UNAME
#RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME
#USER $UNAME
# **** allow sudo usage ***
#RUN apt-get install aptitude
#RUN aptitude install sudo -y 
#RUN adduser -u 1000 -g 1000 johan && \
#    echo "user ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/johan && \
#    chmod 0440 /etc/sudoers.d/johan
#****************************************************************************
#USER johan
#*****************************************************
#FROM node:0.12-slim
# add git
#RUN apt-get update
#RUN apt-get install -y git
# ***** update nodejs **********
#RUN npm cache clean -f
#RUN npm install -g n latest
#RUN n stable
# download latest stable node-red
#RUN npm install -g node-red
#******************************************************

# add some useful nodes
RUN npm uninstall node-red-contrib-ui
#RUN npm audit fix
RUN npm install node-red/node-red-dashboard
#RUN npm install -g node-red-contrib-kafka-node-fix
#RUN npm install -g node-red-node-random
#RUN npm install -g node-red-contrib-graphs
#RUN npm install -g node-red-contrib-influxdb
#RUN npm install -g node-red-contrib-cloudera
#RUN npm install -g node-red-contrib-iiot-jwt
#RUN npm install -g node-red-contrib-csvtojson
#RUN npm install -g node-red-contrib-combine
#RUN npm install -g node-red-contrib-fast-csv
#RUN npm install -g node-red-contrib-excel
#RUN npm install -g node-red-contrib-json
#RUN npm install -g node-red-contrib-mqtt-json
#RUN npm install -g node-red-contrib-smartmeter
#RUN npm install -g node-red-contrib-convert

#RUN npm install -g node-red-contrib-kafka-node-fix
#RUN npm install -g minimatch@3.0.2
#RUN npm install -g node-red-contrib-kafka-producer
#RUN npm install -g node-red-contrib-rdkafka
# use external storage for the user directory
# VOLUME /root/.node-red
#VOLUME /home/johan/node-red-data

# expose port
EXPOSE 1880

# Set the default command to execute
# when creating a new container
# CMD /usr/local/bin/node-red -v





