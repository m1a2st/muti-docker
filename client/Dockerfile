FROM node:16-alpine as builder
 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# 出現第二個FROM語法，代表上一個FROM下面的事情都做完，即表示一個新的模塊
FROM nginx:stable
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# --from 代表複製其他工作階段的內容
COPY --from=builder /app/build /usr/share/nginx/html