FROM node:22-alpine AS development
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]

FROM node:18-alpine AS production
RUN addgroup -S app && adduser -S -G app app
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev && npm cache clean --force
COPY . .
RUN chown -R app:app /app
USER app
CMD ["npm", "run", "start"]