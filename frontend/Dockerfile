# Use an official Node runtime as the base image
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json first, for efficient caching
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the current directory contents into the container
COPY . .

# Build the project for production
RUN npm run build

# Expose the app on port 8080
EXPOSE 8080

# Command to run the application
CMD [ "npm", "run", "serve" ]
