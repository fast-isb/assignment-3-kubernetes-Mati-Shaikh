# Use a base image with Node.js installed
FROM node:14-alpine as build

# Set the working directory inside the container
WORKDIR /app/frontend

# Copy package.json and package-lock.json files
COPY front-end/package.json front-end/package-lock.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the frontend source code
COPY front-end .

# Build the frontend application
RUN npm run build

# Use a lightweight Nginx image to serve the frontend
FROM nginx:alpine

# Copy the built frontend files to the Nginx web server directory
COPY --from=build /app/frontend/build /usr/share/nginx/html

# Expose port 80 to allow incoming traffic to the Nginx server
EXPOSE 80

# Command to start the Nginx server
CMD ["nginx", "-g", "daemon off;"]
