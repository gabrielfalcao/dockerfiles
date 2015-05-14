# nodejs dockerfile


`docker pull gabrielfalcao/nodejs`

This is the base image for `gabrielfalcao/bower-grunt` because it provides a custom compiled nodejs 0.12.2.


Basic usage:


```Dockerfile
FROM gabrielfalcao/nodejs

RUN npm install -g bower grunt-cli

CMD ["bash"]
```
