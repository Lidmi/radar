#include <Adafruit_NeoPixel.h>
#include <Servo.h>
#include <NewPing.h>

#define RING_PIN 10
#define TRIG 5
#define ECHO 8
#define MAX_DIST 20
#define THRESHOD 8

NewPing sonar=NewPing(TRIG,ECHO,MAX_DIST); # датчик
Servo servo; # 
Adafruit_NeoPixel ring=Adafruit_NeoPixel(16,RING_PIN,NEO_GRB+NEO_KHZ800); # кольцо

void setup() {
  Serial.begin(9600);
  servo.attach(3);
  ring.begin();
  ring.setBrightness(30);
  ring.show();
}

void loop() {
  for(int i=0;i<=180;i++){
    servo.write(i);
    int dist=sonar.ping_cm();
    light_up(dist,i);
    delay(30);
    }
   for(int i=180;i>=0;i--){
    servo.write(i);
    int dist=sonar.ping_cm();
    light_up(dist,i);
    delay(30);
    }
    
}

void light_up(int dist,int degree){
  int led_number=int(degree/22.5);
  if (dist<=THRESHOD && dist>0){
       Serial.print(led_number);
       Serial.print(" ");
       Serial.println(dist);
      ring.setPixelColor(led_number,ring.Color(255,0,0));
      ring.show();
    }else{
      ring.setPixelColor(led_number,ring.Color(0,0,0));
      ring.show();
      }
  }
