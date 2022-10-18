## BUILD PHASE
# Base image
FROM node:16-alpine as builder

# Switch workdir to '/usr/app'
WORKDIR '/usr/app'

# Copy package.json into the container
COPY package.json .

# Install all the deps
RUN npm install

# Copy the rest of the files into the container
COPY . .

# Build the production files meaning compiles the application into a folder called 'build'
RUN npm run build    

## RUN PHASE
# Base image
FROM nginx:1.23.1-alpine

# Copy over the production files to the nginx webroot
COPY --from=builder /usr/app/build /usr/share/nginx/html