# Use an official Node runtime as base image
FROM node:16-alpine3.14

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json for using cached node_modules
COPY package*.json ./

# Install CRA and dependencies
RUN npm install -g create-react-app \
    && npm install

# Copy the current directory contents into the container at /app
COPY . .

# Make port 3000 available to the world outside this container
EXPOSE 3000

# Define environment variable for Create React App
ENV NODE_ENV production

# Run app when the container launches
CMD ["npm", "start"]
