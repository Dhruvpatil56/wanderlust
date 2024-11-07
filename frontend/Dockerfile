# ------------------------------ STAGE 1---------------------------------------
FROM node:lts-alpine3.20 AS build1

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json first to leverage Docker caching
COPY package.json package-lock.json ./

# Install dependencies (including devDependencies)
RUN npm install

# Now copy the rest of your application files
COPY . .

# ------------------------------ STAGE 2----------------------------------------
FROM node:lts-alpine3.20

# Set the working directory
WORKDIR /app

# Copy the above part as compressed
Copy --from=build1 /app .

# Copy environment variables if needed
COPY .env.sample .env.local

# Build production-ready assets
RUN npm run build

# Expose the port that Vite will run on (default is 5173)
EXPOSE 4173

# Start the app in production mode
CMD ["npm", "run", "preview", "--", "--host"]

