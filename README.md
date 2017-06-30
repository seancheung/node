# Node:8-alpine

## Additional environment variables

* NPM_OPTIONS
  
  Passing npm options when installing(locally or globally)

* INSTALL_DIR

  Specify where the npm install command runs

* GLOBAL_INSTALLS

  Global packages to install; Separate them with `;`

* WORK_DIR

  Specify where the `command` runs

## Run

```bash
docker run -d -p 80:80 \
-v ./api:/var/www/api \
-e NPM_OPTIONS="--registry=https://registry.npm.taobao.org" \
-e INSTALL_DIR=/var/www/api \
-e TZ=Asia/Shanghai \
-e NODE_ENV=production \
-e WORK_DIR=/var/www/api \
-e DEBUG=*:* \
seancheung/node:8-alpine npm start
```

## Compose

```yml
 api:
  image: "seancheung/node:8-alpine"
  port: 
   - "80:80"
  volumes:
   - ./api:/var/www/api
  environment:
   - NPM_OPTIONS="--registry=https://registry.npm.taobao.org"
   - INSTALL_DIR=/var/www/api
   - TZ=Asia/Shanghai
   - NODE_ENV=production
   - WORK_DIR=/var/www/api
   - DEBUG=*:*
  command: npm start
```