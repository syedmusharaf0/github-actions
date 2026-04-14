# =========================
# Stage 1: Build stage
# =========================
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# 🔥 Debug + Build
RUN npm run build && ls -la /app && ls -la /app/dist

# =========================
# Stage 2: Production stage
# =========================
FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]