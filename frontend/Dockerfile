# -------- Build Stage --------
FROM node:18-alpine AS builder

WORKDIR /app

# Copy package files first
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy rest of the code
COPY . .

# Build Next.js app
RUN npm run build


# -------- Production Stage --------
FROM node:18-alpine

WORKDIR /app

# Copy only necessary files from builder
COPY --from=builder /app ./

# Expose port
EXPOSE 3000

# Start Next.js production server
CMD ["npm", "run", "start"]
