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

# Expose internal port 80
EXPOSE 80

# Container runs this code
CMD [ "node", "server.js" ]