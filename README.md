# tiddlywiki docker

Run TiddlyWiki 5 via docker.

## Acknowledgment
Original forked from https://github.com/djmaze/tiddlywiki-docker

## Prerequisites

Install docker. Follow instryuctions on docker site

## Quickstart

 ```bash
    git clone git clone -b  addons https://github.com/maldun/tiddlywiki-docker.git
    docker build -t tiddlywiki:5 .
	docker run -d -p 8082:8082 tiddlywiki:5
  ```

Now TiddlyWiki should be running on [http://localhost:8082](http://localhost:8082).

## Keeping the data

The container uses a Docker volume to save the wiki data. In order not
to lose sight of that, I recommend using a local folder for the volume.

    sudo docker run -d -p 8082:8082 -v $(pwd)/.tiddlywiki:/var/lib/tiddlywiki -t tiddlywiki:5

In this example, the folder `$(pwd)/.tiddlywiki` is used for the data.

# Auth

Default auth is `user` / `wiki`

Simply provide the USERNAME and PASSWORD env variables to customise.

# Other settings

If you are in a memory-constrained environment, you can provide the 
`NODE_MEM` environment variable to specify the memory ceiling (in MB)

To serve the tiddlywiki at a [non-root prefix path](https://tiddlywiki.com/static/Using%2520a%2520custom%2520path%2520prefix%2520with%2520the%2520client-server%2520edition.html) set the `SERVE_URI` environment variable: this variable ''must'' start with a forward slash character. The tiddlywiki will be served by the container at http://<IP>/${SERVE_URI} - the container initialization script takes care of setting the required host configuration tiddler.
