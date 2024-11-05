# Use a specific Node.js version
FROM node:lts-alpine3.20

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package.json package-lock.json ./

# Install backend dependencies
RUN npm install

# Now copy the rest of the application files
COPY . .

# Copy the environment variable file
COPY .env.sample .env

# Expose the port that the backend will run on
EXPOSE 5000

# Start the backend application
CMD ["npm", "start"]

