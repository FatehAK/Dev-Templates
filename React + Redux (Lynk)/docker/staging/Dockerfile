FROM mhart/alpine-node:12 AS builder
WORKDIR /app
COPY . .
RUN yarn global add react-scripts
RUN yarn
RUN yarn run build:staging

FROM mhart/alpine-node
RUN yarn global add serve
WORKDIR /app
COPY --from=builder /app/build .
CMD ["serve", "-p", "3000", "-s", "."]
EXPOSE 3000
