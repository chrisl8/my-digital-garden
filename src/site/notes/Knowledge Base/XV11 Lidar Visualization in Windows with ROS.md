---
{"created":"2024-12-28","time":"Saturday, December 28th, 2024 @ 2:42:40pm","tags":["KnowledgeBase"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/knowledge-base/xv-11-lidar-visualization-in-windows-with-ros/","dgPassFrontmatter":true}
---


I come up with real nonsense requirements at times. I have an XV11 Neato Vacuum Lidar that I want to visualize on Windows, so here goes:

# Install ROS2 on Windows:
https://docs.ros.org/en/jazzy/Installation/Windows-Install-Binary.html  
### Dependencies.  
ROS2 for windows is accomplished via a large download along with a lot of dependency installs.  
  
Note that ROS2 is **very** picky about the Python version. It is hardcoded in a lot of the ROS2 files.  
  
```  
choco install -y python --version 3.8.3  
choco install -y vcredist2013 vcredist140 cmake  
```  
I'm skipping OpenSSL for now, hoping I can use what I already have installed.  
#### VS Code Community Link
https://aka.ms/vs/16/release/vs_community.exe  
#### Qt5  
Qt5 is very difficult to find and install, this seems to be the correct installer download location:  
https://download.qt.io/archive/qt/5.12/5.12.12/  
[[attachments/a6c218788806ce79a0bff27895a34207_MD5.jpeg|Open: Pasted image 20241228150833.png]]
![attachments/a6c218788806ce79a0bff27895a34207_MD5.jpeg](/img/user/attachments/a6c218788806ce79a0bff27895a34207_MD5.jpeg)
  
As admin run:  
```  
setx /m Qt5_DIR C:\Qt\Qt5.12.12\5.12.12\msvc2017_64  
setx /m QT_QPA_PLATFORM_PLUGIN_PATH C:\Qt\Qt5.12.12\5.12.12\msvc2017_64\plugins\platforms  
```  
### Binary Pacakge  
I renamed the extracted folder to `rso2-jazzy` and placed it in `D:\`  
  
### Environment setup  
  You must do this in any terminal/window before attempting to run any `ros2` commands.
`D:\ros2-jazzy\ros2-windows\local_setup.ps1`  
Using the path based on wherever you put it.  
  
### Testing Windows Environment  
This should work:  
`ros2 run turtlesim turtlesim_node`  
  
As should the other tutorials, which you can use for testing your knowledge, your Windows install and your robot install:    
https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html

# Install dependencies
`pip install pyserial`
# Build ROS2 Packages on Windows (Colcon)
https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html
```
pip install -U colcon-common-extensions
md \dev\ros2_ws\src
cd \dev\ros2_ws\src
gh repo clone n1kn4x/xv11_lidar_python
cd ..
colcon build --symlink-install --merge-install
colcon test --merge-install
```
# COM Port
I couldn't make the CLI argument work, so instead find out what the COM port is in Windows Device Mangager and edit `xv11_lidar_publisher.ph` replacing:
`self.declare_parameter("port", "/dev/ttyXV11")`
with
`self.declare_parameter("port", "COM5")`
"COM5" being whatever port it is.

# Start the Lidar
```
cd \dev\ros2_ws
install\setup.ps1
ros2 run xv11_lidar_python xv11_lidar
```
Hopefully you will see output like this and then nothing. Also the Lidar should be spinning now if it wasn't already (it may or may not spin as long it is plugged into USB):
```
[INFO] [1735419171.252725000] [xv11_lidar]: Initializing XV11 Lidar Node.
[INFO] [1735419171.295768700] [xv11_lidar]: COM5 connected!
```
Leave that running in its own terminal/window.

# Make sure it is dumping data
In another 
```
D:\ros2-jazzy\ros2-windows\local_setup.ps1
ros2 topic echo /scan
```
This should start spewing out a lot of data. Mostly floating point numbers.

# Get the "Frame ID"
RVIZ needs a "Frame" to "fix" on. It knows what these Frames are because it will not allow you to use one that doesn't exist, but it won't tell you what they are.
There are two ways to find the Frame ID:
1. In the `ros2 topic echo /scan` output, scroll up and find a line like this: `frame_id: xv11_lidar` "xv11_lidar" is the Frame ID.
    1. In the source code file `xv11_lidar_publisher.ph` find the line like `self.declare_parameter("frame_id", "xv11_lidar")` and again, "xv11_lidar" is the Frame ID.

# Visualize in Rviz
Hopefully Rviz installed back when you installed ROS2.
You can kill the Scan output winow and use it again, but don't kill the window where `ros2 run xv11_lidar_python xv11_lidar` is running, because that is what Rvix will listen to.

```
D:\ros2-jazzy\ros2-windows\local_setup.ps1
ros2 run rviz2 rviz2
```
Change the "Global Options"->"Fixed Frame" from "map" to "xv11_lidar"
[[attachments/8d6d858b0c057ab2943642edef1d70b8_MD5.jpeg|Open: Pasted image 20241228150006.png]]
![attachments/8d6d858b0c057ab2943642edef1d70b8_MD5.jpeg](/img/user/attachments/8d6d858b0c057ab2943642edef1d70b8_MD5.jpeg)
Just type/paste it in, the drop-down won't work.

Click on "Add" and add a Laserscan topic
[[attachments/1164717474df4e96ba8e703a89ba2812_MD5.jpeg|Open: Pasted image 20241228150126.png]]
![attachments/1164717474df4e96ba8e703a89ba2812_MD5.jpeg](/img/user/attachments/1164717474df4e96ba8e703a89ba2812_MD5.jpeg)
![attachments/2b54d2c050ab18749fa58517473518c7_MD5.jpeg](/img/user/attachments/2b54d2c050ab18749fa58517473518c7_MD5.jpeg)

Expand the LaserScan topic and pick the "/scan" Topic as the source
[[attachments/d8bb6c2f8576b56c8877cd6eb273e95d_MD5.jpeg|Open: Pasted image 20241228150220.png]]
![attachments/d8bb6c2f8576b56c8877cd6eb273e95d_MD5.jpeg](/img/user/attachments/d8bb6c2f8576b56c8877cd6eb273e95d_MD5.jpeg)
You'll need to "click away" from the Topic input to get it to "take."

Then you should see some colored dots in the display in the middle.
[[attachments/04e4d5a7db8b4558bf42fe5bb38b92d3_MD5.jpeg|Open: Pasted image 20241228150312.png]]
![attachments/04e4d5a7db8b4558bf42fe5bb38b92d3_MD5.jpeg](/img/user/attachments/04e4d5a7db8b4558bf42fe5bb38b92d3_MD5.jpeg)

You can rotate the veiw around and/or change it to "Top Down"
[[attachments/70facb11d3a804093df1a36e0104ae8a_MD5.jpeg|Open: Pasted image 20241228150428.png]]
![attachments/70facb11d3a804093df1a36e0104ae8a_MD5.jpeg](/img/user/attachments/70facb11d3a804093df1a36e0104ae8a_MD5.jpeg)

This Lidar is pretty low resolution so there are a lot of gaps, but the range is pretty good so it should show dots even in a big room, although outdoors it may be blank.

*And that is all. Installing ROS just to visualize the output of a cheap Lidar is a bit silly, but it worked.*
In theory one could find a simpler way to dump the output and maybe use a script to do something else with it.
