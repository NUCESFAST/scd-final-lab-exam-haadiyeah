#i21-1216 haadiya sajid
# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install any needed packages specified in package.json
RUN npm install

# Bundle the source code inside the Docker image
COPY . .

# Make port 4000 available to the world outside this container 
EXPOSE 4000

# Define the command to run the app
CMD [ "node", "index.js" ]