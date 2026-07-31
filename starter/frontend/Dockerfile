FROM  public.ecr.aws/docker/library/node:18.14.2-alpine3.17

WORKDIR /app

# Copy dependdency files
COPY package*.json ./

# Install packages
RUN npm ci

# Copy code
COPY . .

# Déclarer l'argument pour l'URL du backend AWS
ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=$REACT_APP_MOVIE_API_URL

# Build the app
RUN npm run build

# install serve tool
RUN npm install -g serve

# Expose the port used by the React app
EXPOSE 3000

# Start serve on build directory
CMD ["serve", "-s", "build", "-l", "3000"]