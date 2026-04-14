# Stage 1: Build React (Vite) app
FROM node:18-alpine AS build
WORKDIR /Sales-Savvy
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build     # builds static files in /dist (Vite default)

# Stage 2: Serve with Nginx
FROM nginx:alpine
# Copy build output from previous stage to Nginx html folder
COPY --from=build /Sales-Savvy/dist /usr/share/nginx/html

# Expose the port Nginx will serve
EXPOSE 80

# Run Nginx in foreground
CMD ["nginx", "-g", "daemon off;"]