# Stage 1: Build the React application
FROM node:14 as build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the entire application code to the working directory
COPY . .

# Build the React application
RUN npm run build

# Stage 2: Serve the React application with a lightweight HTTP server
FROM nginx:alpine

# Copy the built React app from the build stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 (default port for HTTP traffic)
EXPOSE 80

# Start nginx to serve the built app
CMD ["nginx", "-g", "daemon off;"]
