# install node if need 
# install npm
npm install 
# Run this project 
 node index.js

# make Docker image
# Use official Node.js base image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app
COPY . .

# Expose the port the app listens on
EXPOSE 3000

# Start the app
CMD ["node", "index.js"]

# Build docker 
docker build -t chat-app 

# Run Docker image 
docker run -d -p 3000:3000 --name my-chat-app chat-app

# push Docker Hub
docker tag chat-app ashraful90/chat-app:latest <br>
docker login <br>
docker push ashraful90/chat-app:latest


