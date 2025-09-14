# Stage 1: Builder
FROM alpine:3.19 AS builder

# Install any tools you need to build static assets
RUN apk add --no-cache curl

# Example: generate a simple HTML file dynamically
RUN echo "<!DOCTYPE html><html><head><title>Multi-stage Apache</title></head><body><h1>Hello from Apache (Multi-stage Docker build)!</h1></body></html>" > /index.html

# Stage 2: Final image with Apache
FROM httpd:2.4

# Copy only the built artifacts from the builder stage
COPY --from=builder /index.html /usr/local/apache2/htdocs/

# Expose Apache port
EXPOSE 80
