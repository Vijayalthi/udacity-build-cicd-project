FROM public.ecr.aws/docker/library/node:18.14.2-alpine3.17

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

RUN if [ -z "$REACT_APP_MOVIE_API_URL" ]; then \
      echo "DOCKER API URL IS EMPTY"; \
    else \
      echo "DOCKER API URL IS SET"; \
    fi

RUN npm run build

EXPOSE 3000

CMD ["npm", "run", "serve"]
