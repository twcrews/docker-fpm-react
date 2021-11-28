FROM node:16-alpine3.13 as build
WORKDIR /app
COPY . .
RUN npm install -g react-scripts; \
	npm ci; \
	npm run build; \
	rm -r node_modules
FROM nginx:1.21.4
COPY --from=build /app/build/ /usr/share/nginx/html/
RUN mkdir -p /usr/share/nginx/html/api; \
	rm /etc/nginx/nginx.conf
