# Stage 1: Frontend Build
FROM node:23 AS frontend-builder
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . .

# Stage 2: Final Image
FROM node:23
WORKDIR /app

# Copy built assets from the frontend-builder stage
COPY --from=frontend-builder /app .

# Copy environment configuration
COPY .env.sample .env.local

# Expose port 5173
EXPOSE 5173

CMD ["npm", "start"]

#Define the default command to run the application in development
CMD ["npm" ,"run", "dev","--","--host"]
