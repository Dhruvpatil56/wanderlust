# ------------------------ STAGE 1 -----------------------------------
FROM node:lts-alpine3.20 AS build1

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package.json package-lock.json ./

# Install backend dependencies
RUN npm install

# Now copy the rest of the application files
COPY . .

# ------------------------ STAGE 2--------------------------------------

FROM node:lts-alpine3.20

# Set the working directory
WORKDIR /app

# Copy the above stage as compressed
COPY --from=build1 /app .

# Copy the environment variable file
COPY .env.sample .env

# Expose the port that the backend will run on
EXPOSE 5000

# Start the backend application
CMD ["npm", "start"]

