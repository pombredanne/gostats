# gostats
```
gostats -r fabric8io/fabric8
```

gostats will retrive useful statistics and metrics and optionally send them to ElasticSearch in order to perform powerful queries and visualisations with Kibana.

Currently it only supports getting the number of downloads a particular github release has had.  The project can be extended to retrieve anything that can be useful to send to ElasticSearch.

Ideally we'd expose a REST API so that a monitoring tool such as Prometheus can coe along and scrape any metrics instead of pushing to ElasticSearch here.  
## Getting started

### Install / Update & run

Get latest download URL from [gostats releases](https://github.com/fabric8io/gostats/releases)

```sh
sudo rm /tmp/gostats
sudo rm -rf /usr/bin/gostats
mkdir /tmp/gostats
curl --retry 999 --retry-max-time 0  -sSL [[ADD DOWNLOAD URL HERE]] | tar xzv -C /tmp/gostats
chmod +x /tmp/gostats/gostats
sudo mv /tmp/gostats/* /usr/bin/
```

### Usage

```
gostats is used to gather stats and metrics of various types and expose via rest to be scraped by a metrics tool
       								Find more information at http://fabric8.io.

Usage:
  gostats [flags]
  gostats [command]

Available Commands:
  gh-downloads retrives the number of downloads of a GitHub project release
  version      Display version & exit

Flags:
  -y, --yes   assume yes

Use "gostats [command] --help" for more information about a command.
```

## Development

### Prerequisites

Install [go version 1.4](https://golang.org/doc/install)


### Building

```sh
git clone git@github.com:fabric8io/gostats.git $GOPATH/src/github.com/fabric8io/gostats
./make
```

Make changes to *.go files, rerun `make` and run the generated binary..

e.g.

```sh
./build/gostats -r fabric8io/fabric8

```
