# Using the Docker image

The recommended way to use `JuniDB` is via the [docker] image.

## Installing the image

```bash
# Pull the image from Docker Hub
$ docker pull andskur/juni-db:latest
```

The image comes with binary. The `substrate` binary does not have our [offchain-ipfs]
pallets to interact with the IPFS node, instead you can connect to it through its multiaddr.

The image exposes ports `9944` for WebSockets, `9933` for RPC, `30333` for p2p, and `9615` for
Prometheus.

## Running the image

The default command for the image is:

`node-template --ws-external --rpc-external --base-path=/offchain-ipfs --dev`

Run the default with **dev** chain like so:

```bash
docker run -p 9944:9944 \
  -p 9933:9933 \
  -p 30333:30333 \
  -p 9615:9615 \
  -it \
  --rm \
  --name node-template \
  andskur/juni-db:latest
```

This will work with any arguments you'd normally pass to `substrate`

### Persistent Storage

To run with persistent storage volume between containers, first create a volume:

```bash
docker volume create junidb-vol
```

Then add `-v junidb-vol:/junidb` to the docker run commands above.


[docker]: https://hub.docker.com/repository/docker/andskur/juni-db
[offchain-ipfs]: https://github.com/uddugteam/substrate/tree/offchain-ipfs-v0.3