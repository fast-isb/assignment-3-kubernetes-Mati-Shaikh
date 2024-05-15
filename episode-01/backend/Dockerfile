# Use a base image with Node.js installed
FROM node:14-alpine

# Set the working directory inside the container
WORKDIR /app/backend

# Copy package.json and package-lock.json files
COPY backend/package.json backend/package-lock.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the backend source code
COPY backend .

# Expose the port on which the backend server will run
EXPOSE 5000

# Command to run the backend server
CMD ["npm", "start"]
