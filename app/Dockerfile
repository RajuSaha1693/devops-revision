# Build stage
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Runtime stage
FROM node:18-slim
WORKDIR /app
COPY --from=build /app .
RUN npm install --omit=dev

# Add user
RUN groupadd -r app && useradd -r -g app app
USER app

CMD ["node","index.js"]
