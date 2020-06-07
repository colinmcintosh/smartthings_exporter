# smarthings_exporter [![Build Status](https://travis-ci.org/kadaan/smartthings_exporter.svg?branch=master)](https://travis-ci.org/kadaan/smartthings_exporter) [![Coverage Status](https://img.shields.io/coveralls/github/kadaan/smartthings_exporter/master.svg)](https://coveralls.io/github/kadaan/smartthings_exporter) [![Go Report Card](https://goreportcard.com/badge/github.com/kadaan/smartthings_exporter)](https://goreportcard.com/report/github.com/kadaan/smartthings_exporter)

smartthings_exporter is a command line tool to export information about your SmartThings
sensors in a format that can be scraped by [Prometheus](http://prometheus.io). The tool uses 
the [GoSmart](http://github.com/kadaan/gosmart) library to talk to SmartThings and collect 
sensor data and exposed the metrics over http.

## Installation

The installation instructions assume a properly installed and configured Go
development environment. The very first step is to download and build
smartthings_exporter (this step will also download and compile the GoSmart library):


```
$ go get -u github.com/kadaan/smartthings_exporter
```

### SmartThings Setup

Before you can use smartthings_exporter, you need to register it with SmartThings.  

The first step is to setup the API that smartthings_exporter uses to communicate with SmartThings.  Follow the 
[GoSmart SmartThings API setup](https://github.com/kadaan/gosmart#smartthings-api-setup) steps.

Take note of the `client_id` and `client_secret` of your SmartThings app that you just created.

### smartthings_exporter configuration

We now need to register smartthings_exporter to with your SmartThings app.

Run:

```
$ smartthings_exporter register --smartthings.oauth-client=<client_id> --smartthings.oauth-secret=<client_secret> > .st_token
```

Follow the prompts to authorize the app.

## Running

Now we can start smartthings_exporter by running:

```
$ smartthings_exporter --smartthings.oauth-client=<client_id> --smartthings.oauth-token.file=.st_token
```