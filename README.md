# vue-pwa

Following the guide here: https://www.blog.plint-sites.nl/progressive-web-app-using-vue-cli-3/<br>

Send a simple notification to user when they enable notifications by clicking a button.

Demo:
<br>
<img src="./demo.gif" width="480" style="border: 1px solid #ddd; border-radius: 8px">


## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Compiles and hot-reloads for production
To test service worker, you have to run the production package. Use the following command to build production package, and serve it off http-server.
```
yarn run serve-build
```

## Continuous Delivery

Using Docker
```
docker build -t dockerize-vue-pwa .
docker run -it -p 8080:8080 --rm --name dockerize-vue-pwa-1 dockerize-vue-pwa
```

Using Netlify

[![Netlify Status](https://api.netlify.com/api/v1/badges/aa7e2016-d031-4d81-8c68-a4d912269502/deploy-status)](https://app.netlify.com/sites/experiments-pulkit-01/deploys)

