#i21-1216 haadiya sajid

# Use an official Node.js runtime as a parent image
FROM node:14 as build

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install any needed packages specified in package.json
RUN npm install

# Bundle the source code inside the Docker image
COPY . .

# Build the app
RUN npm run build

# Start a new stage from scratch
FROM node:14

# Install serve
RUN npm install -g serve

# Set the working directory in the container to /app
WORKDIR /app

# Copy the build output from the previous stage
COPY --from=build /app/build .

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define the command to run the app
CMD [ "serve", "-s", ".", "-l", "5000" ]