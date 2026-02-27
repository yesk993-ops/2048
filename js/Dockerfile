# Stage 1 — Build (optional for static)
# We use alpine with build tools in case you ever add preprocessing
FROM node:18-alpine AS build

WORKDIR /app

# Copy source
COPY . .

# (no build steps needed for static, but keeping stage for future)
RUN echo "No build needed for pure static content"

# Stage 2 — Serve
FROM nginx:stable-alpine

LABEL maintainer="you@example.com"

# Remove default nginx static
RUN rm -rf /usr/share/nginx/html/*

# Copy static built files from build stage
COPY --from=build /app /usr/share/nginx/html

# Expose
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
