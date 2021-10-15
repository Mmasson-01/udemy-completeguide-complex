FROM node:alpine as builder

# Prepare application work directory
WORKDIR /app

# Copy package.json
COPY package*.json .

# Install dependencies
RUN npm install

# Copy application files
COPY . .

# Production build
RUN npm run build


FROM nginx as production
EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
