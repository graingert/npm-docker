This repo contains a patch with the differences from:
https://github.com/DIREKTSPEED-LTD/npm so that you can use that fix on any npm
rather than just npm:master, or relying on DIREKTSPEED-LTD to merge
npm:master.

Simply add the following to your Dockerfile:
```
RUN apt-get update && apt-get install -y curl patch
RUN cd $("r=require,d=r('path').dirname;d(d(r.resolve('npm/package.json')))") && \
    curl https://raw.githubusercontent.com/graingert/npm-docker/master/npm-docker.patch | patch -s -p0
```
