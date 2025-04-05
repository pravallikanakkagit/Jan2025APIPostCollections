# Use the official Node.js 20 image as the base image
FROM node:20

# Set the working directory in the container
WORKDIR /app

# Install Newman and reporters globally in a single RUN command
RUN npm install -g newman newman-reporter-html newman-reporter-htmlextra

# Copy Postman collection and environment files
COPY DataDrivernAPIs.json .
COPY GoRestEnv.json .
COPY myuser.csv .

# Set the command to run Newman and execute the Postman collection
CMD ["newman", "run", "DataDrivernAPIs.json", "-e", "GoRestEnv.json", "-d", "myuser.csv", "-r", "cli,json,html,htmlextra"]