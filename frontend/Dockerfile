FROM node:20-alpine

# Optional: Add bash for clarity
RUN apk add --no-cache bash

WORKDIR /app

# Install deps
COPY package.json package-lock.json ./
RUN npm install

# Copy source code
COPY . .

# Ensure vite binary is resolvable
ENV PATH="/app/node_modules/.bin:$PATH"

EXPOSE 5173

CMD ["npm", "run", "dev"]
