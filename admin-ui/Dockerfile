FROM node:17.9.0-slim
LABEL maintainer="madhu"
RUN useradd adminui
WORKDIR /app
RUN chown adminui /app /home
COPY . .
# Set registry + retry configs to avoid timeouts
RUN npm config set registry https://registry.npmjs.org/ \
 && npm config set fetch-retries 5 \
 && npm config set fetch-retry-mintimeout 20000 \
 && npm config set fetch-retry-maxtimeout 120000 \
 && npm config set timeout 600000 \
 && npm install
EXPOSE 3000
USER adminui
CMD ["npm","start"]
