# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set the working directory in the container
WORKDIR /app

# Install necessary system packages
RUN apt update && apt install -y nginx

# Copy the current directory contents into the container
COPY . /app

# Install any required Python packages
RUN pip install --no-cache-dir -r requirements.txt

# Copy Nginx configuration (we’ll create this in the next step)
COPY nginx.conf /etc/nginx/nginx.conf

# Start Nginx and Uvicorn
CMD service nginx start && uvicorn main:app --host 0.0.0.0 --port 8000
