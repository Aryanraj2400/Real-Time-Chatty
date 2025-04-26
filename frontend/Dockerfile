# Build phase
FROM node:18 as builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

# Production phase
FROM nginx:stable-alpine

# Clean default nginx static files
RUN rm -rf /usr/share/nginx/html/*

# Copy from Vite's dist folder
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
