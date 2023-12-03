# jvm-slim

Amazon Corretto based Docker images with a minimal footprint.

## Supported tags and respective `Dockerfile` links

- [`11` (_11/Dockerfile_)](jre-11/Dockerfile)
- [`17` (_17/Dockerfile_)](jre-17/Dockerfile)
- [`21` (_21/Dockerfile_)](jre-21/Dockerfile)

## How it works

The images are based on the [Amazon Corretto](https://aws.amazon.com/corretto/) Docker images as build images. Then, using JLink the images are stripped down to the bare minimum required to run a JVM application.

## Details

This image works with [Micronaut](https://micronaut.io/) basic applications.
