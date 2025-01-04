# Step 1: Use an official Node.js runtime as a parent image
FROM node:16-alpine

# Step 2: Set the working directory
WORKDIR /usr/src/app

# Step 3: Install dependencies and build the app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Step 4: Install a lightweight web server (e.g., Nginx)
FROM nginx:alpine

# Step 5: Copy build folder to the Nginx html folder
COPY --from=0 /usr/src/app/build /usr/share/nginx/html

# Step 6: Expose port 80
EXPOSE 80

# Step 7: Start Nginx server
CMD ["nginx", "-g", "daemon off;"]

