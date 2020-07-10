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
  
  import time
import RPi.GPIO as GPIO
 
 print GPIO.VERSION
  GPIO.setmode(GPIO.BCM)
 GPIO.setup(4, GPIO.IN)

 def interrupt_fired(channel):
     print("interrupt Fired")
    print(channel)

GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 
while(True):
  time.sleep(1)
     print("timer fired")
 
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
   ```
   ###
   ```
   #!/usr/bin/python
  
 import time
import RPi.GPIO as GPIO
 import requests,vo json
  from influxdb import InfluxDBClient as influxdb
 
 GPIO.setmode(GPIO.BCM)
 GPIO.setup(4, GPIO.IN)

 def interrupt_fired(channel):
     print("interrupt Fired")
     a = 1
   print(a)
  GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 
  while(True):
    time.sleep(1)
     a = 0
      data = [{
         'measurement' : 'pir',
        ' tags':{
            'visonUni':'2410',
             } ,
         'fields':{
            'pir' : a,
            }
         }]
     client = None
     try:
         client.white_points(data)
    except Exception as e:
          print "Exception write" + str(e)
    if client is not None:
         try:
             client.write_points(data)
        except Exception as e:
            print "Exception write" + str(e)
               finally:                   
 clent.close()
 print("running influxdb OK")


#grafena 들어가기
 sudo service grafana-server start
 
 ```
 ### 
 bt ->  블루투스 끄기

