# deno-dev
[Deno](https://github.com/denoland/deno) development container based on latest [node alpine](https://github.com/nodejs/docker-node/tree/18ed56ea9ba03c16f48372927f5eb2553033e8de) container for testing puproses. [Denon](https://github.com/denosaurs/denon) is installed by default.

Make sure to make the following directories in your CWD:
*  persistent
    *  Store persistent files here, which are not part of the application or not suitable to commit to a repo (like config files, tokens, databases ...etc)
*  app
    * Store your app here. Could be a git repository as well.
*  deno
    * This is where Deno will store it's cache and installed packages, so you don't have to download them over and over again.

Bring it up with this simple ```docker-compose.yaml``` file:
```yaml
version: "3.7"
services:
    deno-dev:
        image: "pho3nixhun/deno-dev:latest"
        container_name: deno-dev
        ports:
            - "3000"
        volumes:
            - "./persistent:/srv/persistent"
            - "./app:/srv/app"
            - "./deno:/srv/deno"
        stdin_open: true
        tty: true
```
```docker-compose up -d```

Attach to the console like this:
```docker exec -ti deno-dev sh```
