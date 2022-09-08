import RPi.GPIO as GPIO
import numpy as np
import cv2
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
            print("Brak ruchu",i)
            GPIO.output(3, 0)  #Turn OFF LED
            time.sleep(0.5)
      elif i == 1:               #Gdy czujnik wykryje ruch 
            print("Wykryto ruch",i)
            GPIO.output(3, 1)  #Zapalanie diody LED 
            j=j+1
            camera.capture('image%03d.jpg'%j) #zrobienie zdjecia 
	    time.sleep(0.5)
       
tekst = """został wykryty ruch       
mail = str("adam.samol@onet.pl")
  if i == 1:
    smtplib(mail + tekst)
   
face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_alt2.xml')
 
cap = cv2.VideoCapture(0)
 
while(True):
    ret, img = cap.read()
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(gray, scaleFactor=1.05, minNeighbors=5)
 
    for (x,y,w,h) in faces:
        cv2.rectangle(img,(x,y),(x+w,y+h),(190,0,0),2)
 
    cv2.imshow('img',img)
    if cv2.waitKey(30) & 0xFF == ord('q'): 
    # uwaga! jeśli w kodzie widzisz "amp;" po znaku and to usuń ten kawałek.
        break
	
tekst = """został wykryty ruch       
mail = str("adam.samol@onet.pl")
  if i == 1:
    smtplib(mail + tekst, cab)	
 
cap.release()
cv2.destroyAllWindows()



    


    
       
