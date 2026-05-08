# Step 1: Use a lightweight production server
FROM nginx:alpine

# Step 2: Copy all your frontend assets (index.html, style.css, script.js)
# This assumes they are in the same folder as the Dockerfile
COPY . /usr/share/nginx/html

# Step 3: Support for Cloud Run dynamic port mapping
# Cloud Run sets a $PORT environment variable. Nginx defaults to 80.
# This small hack ensures Nginx listens to the port Cloud Run assigns.
CMD ["sh", "-c", "sed -i 's/listen  80;/listen '\"${PORT:-80}\"';/' /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'"]
