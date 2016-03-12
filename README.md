Simply add the following to your Dockerfile:
```
RUN cd $(node -p "r=require;r('path').dirname(r.resolve('npm/package.json'))") && \
    npm install --save fs-extra && \
    sed -i -e s/graceful-fs/fs-extra/ -e s/fs\.move/fs.rename/ ./lib/utils/rename.js
```
