import RPi.GPIO as GPIO
import time
import keyboard

#gpio pini 18 yaptim tamamen google den aldığım bilgilerle 
SERVO_PIN = 18
GPIO.setmode(GPIO.BCM)
GPIO.setup(SERVO_PIN, GPIO.OUT)

# servo motor
pwm = GPIO.PWM(SERVO_PIN, 50)  
pwm.start(0)  

def set_servo_angle(angle):
    duty_cycle = (angle / 18) + 2
    GPIO.output(SERVO_PIN, True)
    pwm.ChangeDutyCycle(duty_cycle)
    time.sleep(0.5)
    GPIO.output(SERVO_PIN, False)
    pwm.ChangeDutyCycle(0)
   
  try:
    angle = 90  # baslangıç acısı
    set_servo_angle(angle)
    print("Klavye kontrol")
    
  while True:
        if keyboard.is_pressed('a'):  #A tuşuna tanımlıyom ismimin baş harfi die değiştirirsiniz olmazsa
            angle = min(angle + 20, 180)  #doru yönde mi dönüyo bilmiyom
            set_servo_angle(angle)
            print(f"Açı: {angle}°") #bekleme süresi eklemedim eklesem mi
except KeyboardInterrupt:
    print("progrum sonlandırıldı")
finally:
    pwm.stop()
    GPIO.cleanup()
