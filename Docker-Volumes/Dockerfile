# Base image pulled from DockerHub
FROM node:14

# Set working directory
WORKDIR /app

# Copy the dependencies from package.json into the working directory
COPY package.json .

# Install all the dependencies from package.json
RUN npm install

# Copy over all the remaining files into /app
COPY . .

# Build-time argument
# This variable is not available anywhere else except this Dockerfile
# The ENV variable, however, is available throughout all code
ARG DEFAULT_PORT=80

# Add the global environment variable; can also be added on the CLI
# No need for hardcoding
# Important to not to store senstive data in the environment variables;
# It is baked into the image, and then everyone can read these values
ENV PORT $DEFAULT_PORT

# Expose internal port 80
EXPOSE $PORT

# The container will map to the working directory's path
# This is an anonymous volume
# Anonymous volumes do not survive container shutdown; named volumes do
# VOLUME [ "/app/feedback" ]

# Container runs this code
# Uses NPM to use the start command which then uses the nodemon devDependency
# Nodemon reflects changes in the server.js file in realtime
CMD [ "npm", "start" ]