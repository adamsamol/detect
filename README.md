import RPi.GPIO as GPIO
import picamera
import time
from email import *
camera = picamera.PiCamera()
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)
GPIO.setup(11, GPIO.IN)         #Czujnik Ruchu 
GPIO.setup(3, GPIO.OUT)         #Dioda LED
j=0;
 
while True:
       i = GPIO.input(11)
       if i == 0:                 #Gdy czujnik nie wykryje ruchu 
             print "Brak ruchu",i
             GPIO.output(3, 0)  #Turn OFF LED
             time.sleep(0.5)
       elif i == 1:               #Gdy czujnik wykryje ruch 
             print "Wykryto ruch",i
             GPIO.output(3, 1)  #Zapalanie diody LED 
             j=j+1
             camera.capture('image%03d.jpg'%j) #zrobienie zdjecia 
	     time.sleep(0.5)
       
tekst = """został wykryty ruch       
mail = str("adam.samol@onet.pl")
  if i == 1:
    smtplib(mail + tekst)
    
    


    
       
