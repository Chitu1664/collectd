<h1 align="center">collectd-docker</h1>

<p align="center">
  <a href="https://github.com/revett/collectd-docker/releases" target="_blank"><img 
</p>

Simple [CollectD](https://github.com/collectd/collectd) instance running within a [Docker](https://github.com/docker/docker) container, with support to send statistics to  [Graphite](https://github.com/graphite-project).

**Note** - also accepts traffic from [StatsD](https://github.com/etsy/statsd/) clients on `localhost:8125`.

## Setup

1. [Install Docker](http://docs.docker.com/installation/mac/).
2. Pull the latest image from the Docker [registry](https://registry.hub.docker.com/u/revett/collectd/):

```
docker pull akumar261089/collectd
```

## Usage

Start the container:

```
docker run -d  -e EP_HOST=example.com -e EP_PORT=2003 akumar261089/collectd
```

### Environment Variables

You **must** replace the required environment variables within the `docker run` command shown above:

**Required**:

* `EP_HOST`
  - IP or hostname for the endpoint.
* `EP_PORT`
  - Default: `2003`
  - Port for the endpoint.

**Optional**:

* `HOST_NAME`
  - Default: `collectd-docker`
  - Used to create the namespace.
* `PREFIX`
  - Default: `local.debug`
  - Used to create the namespace.
  - **Graphite** only.

### Namespace

When viewing the metrics within [Grafana](http://grafana.org/) via Graphite for example, they will come under the following namespace:

```
{{PREFIX}}.{{HOST_NAME}}.cpu-*
```

