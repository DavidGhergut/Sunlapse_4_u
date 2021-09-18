# Sunlapse_4_u

### Requireed hardware:

* Raspberry Pi
* Picamera 
* SDcard (for Raspbian and storage purposes)

![Requirements](https://github.com/DavidGhergut/Sunlapse_4_u/blob/main/Requirements.png)
## How to set up the program:

#### 1. Make sure you have installed Raspbian. If not, here are the steps to do that: https://www.raspberrypi.org/software/.

#### 2. Set up your Picamera: https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/2.

#### 3. Clone this repository in the /usr/local/bin directory
```
git clone https://github.com/DavidGhergut/Sunlapse_4_u.git
``` 

#### 4. Downloading sunwait: https://www.m4pi.it/2017/12/28/astronomic-time-with-raspberry/#google_vignette.
* After clicking on the website, go here and download sunwait:
  ![Instructions](https://github.com/DavidGhergut/Sunlapse_4_u/blob/main/Downloading_sunwait.png)

And then follow these instructions in your Terminal 🖥:

```
cd Downloads/
tar -xvzf sunwait-20041208.tar.gz
cd sunwait-20041208/
make sunwait
sudo cp sunwait /usr/local/bin/
```
 

#### 5. We set up crontab for the first time:
```
crontab -e
``` 
Something like this will show up:

![Terminal_message](https://github.com/DavidGhergut/Sunlapse_4_u/blob/main/Terminal_message.png)

#### 6. Search for the location of your residence (latitude and longitude)

##### 😁 Helpful suggestion 😌

* Access this website in order to find your desired location's coordinates: https://www.maps.ie/coordinates.html.

#### 7. Write the following commands in the crontab with the correct information:

```
# m h  dom mon dow   command
 * *   *   *   *   /usr/local/bin/sunwait sun up -5:00 [insert latitude] [insert longitude]; python3 /usr/local/bin/Sunlapse_4_u/main.py
 * *   *   *   *   /usr/local/bin/sunwait sun down -5:00 [insert latitude] [insert longitude]; python3 /usr/local/bin/Sunlapse_4_u/main.py 
``` 
Now, the Raspberry Pi will know to wait until 5 minutes before the sunrise and the sunset to run the program. 

## ⚠️ Make sure you do not have your raspberry pi on sleep if you want to run this project! The crontab may disappear once the computer is shut down and you will need to redo step 7 of the setup. ⚠️

### ‼️ Acknowledgment ‼️

This project is an automated version of the [project made by Caroline Dunn](https://github.com/carolinedunn/timelapse).

### ✅ Special thanks and sites that may answer to possible questions 👏:
* https://scruss.com/blog/2013/02/06/hey-its-the-sun-heyu-and-sunwait-and-cron-on-the-raspberry-pi/
* https://www.m4pi.it/2017/12/28/astronomic-time-with-raspberry/#google_vignette
