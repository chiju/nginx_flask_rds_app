# Use the official Nginx image as the base image
FROM nginx:latest

# Copy the HTML file into the default Nginx web root directory
COPY index.html /usr/share/nginx/html/

# Expose port 80 for incoming web traffic
EXPOSE 80

# Start Nginx when the container runs
CMD ["nginx", "-g", "daemon off;"]
