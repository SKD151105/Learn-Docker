FROM ubuntu
# This is only experimentation, hence base is not chosen as node:18. 
# This is to show how to install node in ubuntu base image.

RUN apt-get update
RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get upgrade -y
RUN apt-get install -y nodejs

WORKDIR /app

# COPY package.json /app/package.json
# COPY package-lock.json /app/package-lock.json
COPY package.json package.json
COPY package-lock.json package-lock.json

# WORKDIR /app
# Since we want to run npm install in the /app directory, we set the working directory to /app.

RUN npm install
# Running the npm install layer before copying the index.js file to leverage docker cache.

COPY index.js index.js
# COPY .. 
# This allows us to copy all the files from the parent directory to the container.
# dockerignore file is used to ignore the node_modules folder from being copied to the container.

ENTRYPOINT ["node", "index.js"]