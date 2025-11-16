# Use a lightweight Node.js base image
FROM node:24-alpine

LABEL name=localapp

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to leverage Docker layer caching
# This allows npm install to be cached if dependencies haven't changed
COPY package*.json ./
COPY main.js .
COPY public public
COPY views views


# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port your Node.js application listens on
ENV APP_PORT=5000
EXPOSE ${APP_PORT}

# Define the command to run your application
#CMD [ "npm", "start" ]
ENTRYPOINT node main.js
#ENTRYPOINT node main.js ${APP_PORT}