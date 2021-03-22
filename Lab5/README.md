# Lesson 5: Crossbar.io and Paho

* [MQTT](https://en.wikipedia.org/wiki/MQTT)
* [MQTT AWS DEVELOPER GUIDE](https://docs.aws.amazon.com/iot/latest/developerguide/mqtt.html)

## Lab 5A: Crossbar.io

### Ran Crossbar.io router on Terminal 1 and navigated to 127.0.0.1:8080/info
$ git clone https://github.com/crossbario/crossbar-examples
$ docker pull crossbario/crossbar-armhf
$ docker run -v $PWD:/node -u 0 --rm --name=crossbar -it -p 8080:8080 crossbario/crossbar-armhf

![image](https://user-images.githubusercontent.com/32800667/111930272-ebbdb680-8a8e-11eb-9ce8-63d3f809f9f5.png)

### Ran publish-client on Terminal 2 and subscribe-client on Terminal 3
-- Terminal 2 --
$ sudo pip3 install -U autobahn[twisted,encryption,serialization,xbr]
$ cd crossbar-examples/getting-started
$ cd .crossbar
cd 1.hello-world
$ python3 client_component_publish.py

![image](https://user-images.githubusercontent.com/32800667/111930491-756d8400-8a8f-11eb-8552-74003226c83d.png)

-- Terminal 3 --
$cd crossbar-examples/getting-started/1.hello-world/
$ python3 client_component_subscribe.py

![image](https://user-images.githubusercontent.com/32800667/111930695-e2811980-8a8f-11eb-9a8f-645fa8f7bbc5.png)

## Lab 5B: Eclipse Mosquitto and Eclipse Paho

### Ran Mosquitto
$ sudo apt install mosquitto mosquitto-clients
$ mosquitto_sub -h localhost -v -t "\$SYS/#"

![image](https://user-images.githubusercontent.com/32800667/111930815-283de200-8a90-11eb-8127-0ce8fb14ad01.png)

#### Things to note: Mosquitto subscribed on one terminal and published to another. We published to SYS, a common terminal, so there was data from other users present.

### Test sneding "Hello" with two local terminals

In Terminal 1:
$ mosquitto_sub -h localhost -v -t test/topic &

In Terminal 2:
$ mosquitto_pub -h localhost -t test/topic -m "Hello"

#### Terminal 1 yields:

![image](https://user-images.githubusercontent.com/32800667/111931165-08f38480-8a91-11eb-8bbb-8af532ea500f.png)


## Paho

$ sudo pip3 install -U paho-mqtt
$ git clone https://github.com/eclipse/paho.mqtt.python.git
$ cd ~/iot/lesson5
$ python3 client.py

### subscribe code on one terminal and publish with another:

#### Terminal 1
$ python3 sub.py

#### Terminal 2
$ python3 pub.py

**This allows the message "Hello" to be published:**

![image](https://user-images.githubusercontent.com/32800667/111931389-7f908200-8a91-11eb-8046-45df9ce65e6c.png)

#### Terminal 1
$ python3 sub-multiple.py

#### Terminal 2
$ python3 pub-multiple.py

![image](https://user-images.githubusercontent.com/32800667/111931506-b9618880-8a91-11eb-8f5e-d8efcfcab5c8.png)


