# Useful Data team tools

## Pre-reqs

* Install brew for MacOS: https://brew.sh/

## Python & Conda

```bash
# Python 3
brew install python

# Conda 3
brew install conda
```

## AWS CLI

```bash
# AWS CLI
brew install awscli

# List S3 buckets
aws s3 ls
```

## Docker

```bash
# Docker
brew install docker

# Docker compose
brew install docker-compose
```

Docker cheat sheet: https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf

## Kubectl

Follow instructions from [infra-iam-sso](https://github.com/skillz/infra-iam-sso).

```bash
# Kubectl
brew install kubernetes-cli

# List contexts
kubectl config get-contexts

# List pods in qa namespace
kubectl -n qa get pods
```

## Minikube

```bash
# VirtualBox is a pre-rep for Minikube on MacOS
brew cask install virtualbox

# Minikube
brew install minikube

# Start Minikube
minikube start --vm-driver=virtualbox

# Build local docker image with Minikube Docker daemon
eval $(minikube docker-env)
docker build -t my-image-name .
```

## Helmfile

```bash
# Helmfile
brew install helmfile

# Apply helm chart
helmfile apply

# Destroy stack
helmfile destroy
```

## Kafka tools

Download Confluent Platform: https://www.confluent.io/get-started/
```bash

#Set environment variable
export CONFLUENT_HOME=<confluent path>

# Confluent CLI requires Java 8 or 11
#Start Confluent services
bin/confluent local services start

#Stop Confluent services
bin/confluent local services stop

# List topics
bin/kafka-topics \
  --bootstrap-server b-1.data-sdp-dev.m7lfm8.c2.kafka.us-west-2.amazonaws.com:9092 \
  --list

# Consume from beginning
bin/kafka-console-consumer \
  --from-beginning \
  --bootstrap-server b-1.data-sdp-dev.m7lfm8.c2.kafka.us-west-2.amazonaws.com:9092 \
  --topic segmented_user

# Consume in Avro from beginning
bin/kafka-avro-console-consumer \
  --from-beginning \
  --bootstrap-server b-1.data-sdp-dev.m7lfm8.c2.kafka.us-west-2.amazonaws.com:9092 \
  --property schema.registry.url=http://data-rts-schema-registry.dev.cloud.skillz.com/ \
  --topic segmented_user
```
