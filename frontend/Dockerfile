FROM node:20-alpine

WORKDIR /app

# Copy package files first
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Now copy the rest of the app
COPY . .

# Add vite to PATH (from node_modules)
ENV PATH /app/node_modules/.bin:$PATH

EXPOSE 5173

CMD ["npm", "run", "dev"]
