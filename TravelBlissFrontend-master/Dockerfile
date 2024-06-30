# Stage 1: Build the React app
FROM node:14-alpine as build

# Set working directory inside the container
WORKDIR /TravelBlissFrontend-master

# Copy package.json and package-lock.json to install dependencies
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy all files from the host to the container
COPY . .

# Build the React app for production
RUN npm run build

# Stage 2: Serve the React app with Nginx
FROM nginx:alpine

# Copy the build output from the first stage to Nginx's default directory
COPY --from=build /TravelBlissFrontend-master/build /usr/share/nginx/html

# Expose port 80 to the outside world
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
