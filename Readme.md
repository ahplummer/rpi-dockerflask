# What is this?

This is a simple boilerplate to get a Python flask running inside a Docker container on a Raspberry Pi. Optionally, you can have it restart when the Pi reboots.

## Requirements

* RaspberryPi
* Docker installed

## Building & Testing

Ensure all steps are done once logged into the Pi. NOTE: It is assumed that you have your `pi` user in the `dockergroup` as defined [here](https://docs.docker.com/engine/install/linux-postinstall/). Otherwise, you'll be in `sudo` hell.

* Build: `docker build -t flaskthing .`

* Run: `docker run -d -p 4444:4444 flaskthing:latest`. Note: change ports if you changed the server.py file. This also starts the container in detached mode.

* Test: `curl http://127.0.0.1:4444`

* Kill the container: `docker kill $(docker ps | awk '/flaskthing/ {print $1}')`

## Setting it to start upon reboot:

* Copy Flask.service over: `sudo cp Flask.service /etc/systemd/system/Flask.service`

* Enable/Restart: `sudo systemctl restart Flask.service`

