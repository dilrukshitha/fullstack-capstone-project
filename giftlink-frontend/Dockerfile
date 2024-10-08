# Base image for building the React app
FROM node:14 as build

# Set the working directory
WORKDIR /app

# Copy the package.json and install dependencies
COPY package.json package-lock.json ./
RUN npm install

# Copy the entire frontend code
COPY . .

# Build the frontend for production
RUN npm run build

# Serve the frontend using nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose the port nginx will run on
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
