# Final stage
FROM node:16-alpine

# Set node environment to production
ENV NODE_ENV production

# Update the system
RUN apk --no-cache -U upgrade

# Prepare destination directory and ensure user node owns it
RUN mkdir -p /home/node/app

RUN touch /logs/app.log

# Set CWD
WORKDIR /home/node/app

# Install PM2
RUN npm i -g pm2

# Copy package.json and package-lock.json
COPY package*.json ./

# Install production dependencies
RUN npm ci

# Copy the rest of your app
COPY . .

# Start the app using PM2 directly without process.yml
ENTRYPOINT ["pm2-runtime", "index.js"]
