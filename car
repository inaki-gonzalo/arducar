/*
 modified 15 Sep 2014
 by Inaki Gonzalo
 based on Tom Igoe's example
 
 
 */
#include <SoftwareSerial.h>

int pinI1=8;//define I1 interface
int pinI2=11;//define I2 interface 
int speedpinA=9;//enable motor A
int pinI3=12;//define I3 interface 
int pinI4=13;//define I4 interface 
int speedpinB=10;//enable motor B
int pwmspeed =100;//define the spead of motor
boolean forward=true;

SoftwareSerial mySerial(6,7); // RX, TX
int power =4;
int ground=5;
int response;
void setup()  
{
  pinMode(pinI1,OUTPUT);
  pinMode(pinI2,OUTPUT);
  pinMode(speedpinA,OUTPUT);
  pinMode(pinI3,OUTPUT);
  pinMode(pinI4,OUTPUT);
  pinMode(speedpinB,OUTPUT); 
  // Open serial communications and wait for port to open:
  Serial.begin(9600);
  //while (!Serial) {
   // ; // wait for serial port to connect. Needed for Leonardo only
  //}
  pinMode(power, OUTPUT);   // digital sensor is on digital pin 2
    digitalWrite(power, HIGH);
pinMode(ground, OUTPUT);   // digital sensor is on digital pin 2
    digitalWrite(ground, LOW);

  Serial.println("Goodnight moon!");

  // set the data rate for the SoftwareSerial port
  mySerial.begin(9600);
  mySerial.println("Hello, world?");
}
void turnoff(){
   digitalWrite(speedpinA,LOW);// Unenble the pin, to stop the motor. this should be done to avid damaging the motor. 
     digitalWrite(speedpinB,LOW);
     digitalWrite(pinI4,LOW);//turn DC Motor B move clockwise
     digitalWrite(pinI3,LOW);
     digitalWrite(pinI2,LOW);//turn DC Motor A move anticlockwise
     digitalWrite(pinI1,LOW);
  
}
void stop1(){
    
     delay(1000000);
    
  }
void accelerate(int time,int spead){
    
      
     digitalWrite(pinI4,HIGH);//turn DC Motor B move clockwise
     digitalWrite(pinI3,LOW);
     digitalWrite(pinI2,LOW);//turn DC Motor A move anticlockwise
     digitalWrite(pinI1,LOW); 
     //analogWrite(speedpinA,spead+10);//input a simulation value to set the speed
     analogWrite(speedpinB,spead);
      delay(time);
      turnoff();
  }
  void reverse(int time,int spead){
     digitalWrite(pinI4,LOW);//turn DC Motor B move clockwise
     digitalWrite(pinI3,HIGH);
     digitalWrite(pinI2,LOW);//turn DC Motor A move anticlockwise
     digitalWrite(pinI1,LOW); 
      analogWrite(speedpinB,spead);
     delay(time);
      turnoff();
  }
  void turnLeft(int time,int spead){
     if (forward){ 
       digitalWrite(pinI4,HIGH);//turn DC Motor B move clockwise
       digitalWrite(pinI3,LOW);
     }
     else{
         digitalWrite(pinI4,LOW);//turn DC Motor B move clockwise
       digitalWrite(pinI3,HIGH);
     }
     digitalWrite(pinI2,HIGH);//turn DC Motor A move anticlockwise
     digitalWrite(pinI1,LOW); 
     analogWrite(speedpinA,255);//input a simulation value to set the speed
     analogWrite(speedpinB,spead);
   delay(time);
      turnoff();
    
  }
  void turnRight(int time,int spead  ){
   
       if (forward){ 
       digitalWrite(pinI4,HIGH);//turn DC Motor B move clockwise
       digitalWrite(pinI3,LOW);
     }
     else{
         digitalWrite(pinI4,LOW);//turn DC Motor B move clockwise
       digitalWrite(pinI3,HIGH);
     }
      digitalWrite(pinI2,LOW);//turn DC Motor A move anticlockwise
      digitalWrite(pinI1,HIGH); 
      analogWrite(speedpinA,255);//input a simulation value to set the speed
      analogWrite(speedpinB,spead);
    delay(time);
      turnoff();
  }
  void exit(){
Serial.println("Exiting..."); 
while(1) {
 delay(100000000);
  }

}

void loop() // run over and over
{
  if (mySerial.available()){
    response=mySerial.read();
    Serial.println(response);
   // if (response== "ü"){Serial.println("Accelerating");}
     switch (response) {
          case 252:    // your hand is on the sensor
            Serial.println("Accelerating");
           accelerate(30,pwmspeed);
            forward=true;
            break;
          case 248:    // your hand is close to the sensor
            Serial.println("Reverse");
           reverse(30,pwmspeed);
           forward=false;
            break;
          case 254:    // your hand is a few inches from the sensor
           Serial.println("Right");
           turnRight(30,pwmspeed-10);
           
           
            break;
          case 255:    // your hand is nowhere near the sensor
          Serial.println("Left");
           turnLeft(30,pwmspeed-10);
            
            break;
             case 244:    // your hand is nowhere near the sensor
            Serial.println("increasing spead");
            pwmspeed++;
            break;
             case 236:    // your hand is nowhere near the sensor
            Serial.println("decreasing spead");
            pwmspeed--;
            break;
          case 240:    // your hand is nowhere near the sensor
            Serial.println("stop");
            //stop1();
           // exit();
            break;
          } 

	
    
  }
  
}

