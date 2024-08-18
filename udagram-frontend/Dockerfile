### Build
FROM beevelop/ionic:latest AS ionic

# Set the environment variable for Node.js to use the legacy OpenSSL provider
ENV NODE_OPTIONS=--openssl-legacy-provider

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./
RUN npm ci --force

# Bundle app source
COPY . .
RUN ionic build

### Run
FROM nginx:alpine
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
