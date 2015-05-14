# bower-grunt dockerfile


`docker pull gabrielfalcao/bower-grunt`

This image gives you a brand new docker image containing nodejs 0.12.2
+ grunt-cli and bower.

With this you can build your own frontend docker images based on grunt


Basic usage:


```Dockerfile
FROM gabrielfalcao/bower-grunt

ADD . /frontend

WORKDIR /frontend

RUN npm install
RUN bower install --allow-root

EXPOSE 9000

# Define default command.
CMD ["grunt"]
```
