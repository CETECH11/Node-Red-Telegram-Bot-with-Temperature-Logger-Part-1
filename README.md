# Node-Red-Telegram-Bot-with-Temperature-Logger-Part-1

![alt text](https://hackster.imgix.net/uploads/attachments/1629226/_WvSFb9YUP4.blob?auto=compress%2Cformat&w=900&h=675&fit=min)

Node-RED is a powerful tool for creating and connecting IoT applications with a graphical interface. It allows you to drag and drop nodes that can perform various functions, such as reading sensors, sending messages, storing data, and more. One of the nodes that Node-RED supports is the Telegram bot node, which enables you to communicate with your IoT devices using the popular messaging platform Telegram.

In this article, I will show you how to use Node-RED and Telegram bot to send temperature data from a DHT11 sensor connected to a Raspberry Pi. You will be able to ask your Telegram bot for the current temperature and receive a reply with the sensor reading. You will also be able to set up a notification system that will alert you when the temperature exceeds a certain threshold.

To follow this tutorial, you will need the following components:

A Raspberry Pi with Node-RED installed (you can follow this guide to install Node-RED on your Raspberry Pi)
A DHT11 temperature and humidity sensor
A Telegram account and a Telegram bot token (you can follow this guide to create a Telegram bot and get its token)

![alt text](https://hackster.imgix.net/uploads/attachments/1629235/image_TaVEFkDdmH.png?auto=compress%2Cformat&w=740&h=555&fit=max)

The first step is to connect the DHT11 sensor to the Raspberry Pi using the breadboard and the jumper wires. The DHT11 sensor has four pins: VCC, Data, NC (not connected), and GND. Connect the VCC pin to the 3.3V pin of the Raspberry Pi, the GND pin to the GND pin of the Raspberry Pi, and the Data pin to the GPIO 4 of the Raspberry Pi.

To read data from the DHT11 sensor, we will use a Node-RED node called node-red-contrib-dht-sensor. To install this node, open a terminal on your Raspberry Pi and run the following command:

npm install node-red-contrib-dht-sensor

Then restart Node-RED by running:

node-red-stop
node-red-start
Then add the DHT11 node and open the properties then choose your DHT11 pin.

Go to Google Play or App Store, download, and install Telegram. In my case, I'm using telegram web. First, search for “botfather” and click the BotFather as shown below.

Next, start the BotFather, and use /newbot to create a new bot.

Next, name your bot.

Then, mention the username.

Finally, it will show you the api key.

![alt text](https://hackster.imgix.net/uploads/attachments/1629233/image_5NqHSeYmhe.png?auto=compress%2Cformat&w=740&h=555&fit=max)

Anyone that knows your bot username can interact with it. To make sure that we ignore messages that are not from our Telegram account (or any authorized users), you can get your Telegram User ID.

In your Telegram account, search for “IDBot”

Start a conversation with that bot and type /getid. You will get a reply with your user ID. Save that user ID because you’ll need it later in this tutorial. 
To communicate with the Telegram bot, we will use a Node-RED node called node-red-contrib-telegrambot. To install this node, open a terminal on your Raspberry Pi and run the following command:

npm install node-red-contrib-telegrambot
Then restart Node-RED by running:

node-red-stop
node-red-start
Then open your Node-RED editor in your browser (usually http://raspberrypi:1880) and drag a Telegram receiver node and a Telegram sender node from the palette to the workspace. Double-click on the Telegram receiver node and click on the pencil icon next to Bot configuration.

Enter your bot name and token that you obtained from BotFather in step 1. Then click on Add and Done.

To request temperature readings from the DHT11 sensor, we will create a simple flow that consists of three nodes: a Telegram receiver node, a DHT11 sensor node, and a Telegram sender node.

In this flow, if you trigger the node, it will send you the temp and humi data to the Telegram bot.

![alt text](https://hackster.imgix.net/uploads/attachments/1518136/8_tJuwoRM3dI.JPG?auto=compress%2Cformat&w=740&h=555&fit=max)

You must check out [PCBWAY](https://www.pcbway.com/) for ordering PCBs online for cheap!

You get 10 good-quality PCBs manufactured and shipped to your doorstep for cheap. You will also get a discount on shipping on your first order. Upload your Gerber files onto PCBWAY to get them manufactured with good quality and quick turnaround time. [PCBWay](https://www.pcbway.com/) now could provide a complete product solution, from design to enclosure production. Check out their online Gerber viewer function. With reward points, you can get free stuff from their gift shop.Also, check out this useful blog on PCBWay Plugin for KiCad from [here](https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html). Using this plugin, you can directly order PCBs in just one click after completing your design in KiCad.
