# Use the official PHP 8 image from Docker Hub
FROM php:8.0-apache

# Copy the local PHP files to the container
COPY index.php /var/www/html/

# Set the ServerName to suppress the warning
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Expose port 80 for Apache
EXPOSE 80
