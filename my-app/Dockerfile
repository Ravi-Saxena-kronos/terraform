# ---------- Stage 1: Builder ----------
FROM node:20 AS builder

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy source
COPY . .

# ---------- Stage 2: Runtime ----------
FROM node:20-slim

WORKDIR /app

# Copy only necessary files
COPY --from=builder /app /app

# Expose port
EXPOSE 5000

# Env variables for RDS (ECS injects them)
ENV DB_HOST="" \
    DB_USER="" \
    DB_PASS="" \
    DB_NAME=""

# Start the app
CMD ["node", "server.js"]
