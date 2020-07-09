# jjvison

## gpio pin map
```
cd/ tmp


### Git Hub Use
 git - Repository down lOAD
  ```
  git clone https://github.com/<user name>/<repository name>
  ```
  
  ### vim editor setting
  ```
  set nu  // Line number
  set cindent //C language indent
  set ts=4  //tab size 4
  if has("syntax")  // syntax on
    syntax on
   end if
   ```
```
   #vim pir.py

    #!/usr/bin/python
  2
  3 import time
  4 import RPi.GPIO as GPIO
  5
  6 print GPIO.VERSION
  7 GPIO.setmode(GPIO.BCM)
  8 GPIO.setup(4, GPIO.IN)
  9
 10 def interrupt_fired(channel):
 11     print("interrupt Fired")
 12     print(channel)
 13
 14 GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 15
 16 while(True):
 17     time.sleep(1)
 18     print("timer fired")
 
 ```
 ###
 ```
 pi@raspberrypi:~ $ cd jjvison/
-bash: cd: jjvison/: No such file or directory
pi@raspberrypi:~ $ ls
Adafruit_Python_DHT  Desktop    Downloads  Music     pir.py  Templates  work
Bookshelf            Documents  jjvision   Pictures  Public  Videos
pi@raspberrypi:~ $ cd jjvision
pi@raspberrypi:~/jjvision $ ls
datasheet  libjffi-1.2.so  README.md  simpletest.py
pi@raspberrypi:~/jjvision $ cp /home/pi/work
cp: missing destination file operand after '/home/pi/work'
Try 'cp --help' for more information.
pi@raspberrypi:~/jjvision $ cp /home/pi/work/pir.py
cp: missing destination file operand after '/home/pi/work/pir.py'
Try 'cp --help' for more information.
pi@rhiaspberrypi:~/jjvision $ cp /home/pi/work/pir.py .
cp: cannot stat '/home/pi/work/pir.py': No such file or directory
pi@raspberrypi:~/jjvision $ cp /home/pi/work/pir.py.
cp: missing destination file operand after '/home/pi/work/pir.py.'
Try 'cp --help' for more information.
pi@raspberrypi:~/jjvision $ add .
-bash: add: command not found
```
```
###
```
#!/usr/bin/python

 import time
 import RPi.GPIO as GPIO
 
  print GPIO.VERSION
  GPIO.setmode(GPIO.BCM)
  GPIO.setup(4, GPIO.IN)

def interrupt_fired(channel):
 print("interrupt Fired")
 a=1
 print(a)
 GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 
 while(True):
   time.sleep(1)
   a = 0
   print("timer fired")
   print(a)
   `````
   
   ##
   #!/usr/bin/python
  2
  3 import time
  4 import RPi.GPIO as GPIO
  5 import requests,vo json
  6 from influxdb import InfluxDBClient as influxdb
  7
  8 GPIO.setmode(GPIO.BCM)
  9 GPIO.setup(4, GPIO.IN)
 10
 11 def interrupt_fired(channel):
 12     print("interrupt Fired")
 13     a = 1
 14     print(a)
 15 GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 16
 17 while(True):
 18     time.sleep(1)
 19     a = 0
 20     data = [{
 21         'measurement' : 'pir',
 22         ' tags':{
 23             'visonUni':'2410',
 24             } ,
 25         'fields':{
 26             'pir' : a,
 27              }
 28         }]
 29     client = None
 30     try:
 31         client.white_points(data)
 32     except Exception as e:
 33         print "Exception write" + str(e)
 34     if client is not None:
 35         try:
 36             client.write_points(data)
 37         except Exception as e:
 38             print "Exception write" + str(e)
 39                 finally:
 40                     clent.close()
 41         print("running influxdb OK")


#grafena 들어가기
 sudo service grafana-server start

