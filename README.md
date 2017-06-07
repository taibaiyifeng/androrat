 功能

获取联系人信息
获取通话信息
获取短信信息
GPS/网络定位
实时监控接收短信息
实时获取手机状态
拍照
响铃
录视频
发短信
打电话
打开浏览器访问URL
手机震动
使用方法其实蛮简单，只要把src里面的Androrat和AndroratServer这两个工程编译出来就行了。其中Androrat是安卓程序，AndroratServer是java程序。编译Androrat后会在Androrat目录下的bin目录下生成LauncherActivity.apk这个安卓程序，安装到别人手机上就行了，打开程序会让你配置服务端IP和端口然后后开启服务和停止服务两个按钮。当然可以把ip直接做到程序中隐藏窗口。具体可以在LauncherActivity.java这个文件中修改。然后就是AndroratServer了，编译的时候可以导出为jar包，执行java -jar 包名.jar就行了。执行后会出现一个软件界面列出当前已监控的手机列表。然后可以得到手机里面一切信息。包括控制手机等……
androrat
========

Remote Administration Tool for Android

Androrat is a client/server application developed in Java Android for the client side and in Java/Swing for the Server.

> The name Androrat is a mix of Android and RAT (Remote Access Tool).

It has been developed in a team of 4 for a university project. It has been realised in one month. The goal of the application is to give the control of the android system remotely and retrieve informations from it.

# Technical matters

* The android application is the client for the server which receive all the connections. 
* The android application run as a service(not an activity) that is started during the boot. So the user does not need to interact with the service (Even though there is a debug activity that allow to configure the IP and the port to connect to). 
* The connection to the server can be triggered by a SMS or a call (this can be configured)

### All the available functionalities are

* Get contacts (and all theirs informations) 
* Get call logs 
* Get all messages 
* Location by GPS/Network 
* Monitoring received messages in live 
* Monitoring phone state in live (call received, call sent, call missed..) 
* Take a picture from the camera 
* Stream sound from microphone (or other sources..) 
* Streaming video (for activity based client only) 
* Do a toast 
* Send a text message 
* Give call 
* Open an URL in the default browser 
* Do vibrate the phone

# Folders

The project contains the following folders:

* doc: Will soonly contain all the documentation about the project
* Experiment: Contain an *experimental* version of the client articulated around an activity wish allow by the way to stream video
* src/Androrat: Contain the source code of the client that should be put on the android plateform
* src/AndroratServer: Contain the sources of the Java/Swing server that can be run on any plateform
* src/api: Contain all the different api used in the project (JMapViewer for the map, forms for swing, and vlcj for video streaming)
* src/InOut: Contain the code of the content common for the client and the server which is basically the protocol implementation

# Screenshots

## Main GUI

This is the main GUI where all the clients connected appears. The list is dynamically updated when a new client connects or is disconnected. Moreover a log of all connections and global informations are showed in the log panel at the bottom of the window. A simple double-click on a client open his window to interact with him.

![Main GUI](https://raw.github.com/RobinDavid/androrat/master/doc/main.png)

## Client Panel

All the actions with client can be made in the client window which is articulated around tabs. The default tab is called Home and provide various functionalities. First as we can see in the left scrollview all the informations about the client like sim infos, battery infos, network infos, sensors infos etc. On the right there is the options which allow remotely to change the configuration of the client like the ip and port to connect to, either or not wait a trigger to intent server connection etc. Finally quick actions can be perfomed in this tab like a toast message, do vibrate the phone or open an URL.

![Client Panel](https://raw.github.com/RobinDavid/androrat/master/doc/homepanel.png)

## Other tabs

The two screenshots below shows two others tabs for two functionalities which are respectively get contacts and geolocation. As you can see on the get contacts panel the list on the left show all contacts the name, the phone number and the picture if available. Morevover on the right three buttons allow to get more information about the selected contact send him a sms or call him. For Geolocation we can choose our provider either GPS either network that use google to locate. Then the streaming can be started and the map will be updated as soon as data has been received.

![Contacts](https://raw.github.com/RobinDavid/androrat/master/doc/contact.png)

![GPS tab](https://raw.github.com/RobinDavid/androrat/master/doc/gps.png)
