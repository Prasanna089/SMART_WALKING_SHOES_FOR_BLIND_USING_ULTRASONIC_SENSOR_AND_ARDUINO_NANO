# SMART_WALKING_SHOES_FOR_BLIND_USING_ULTRASONIC_SENSOR_AND_ARDUINO_NANO
int trigPin1 = 7; //Trig - purple Jumper trigger pin of forward sensor
 int echoPin1 = 8; //Echo - blue Jumper echo pin of forward sensor
 int trigPin2 = 12; //Trig - pink Jumper trigger pin of sideward sensor
 int echoPin2 = 13; // echo-yellow echo pin of sideward sensor
 int forwardmotor=3; // forward vibrating motor
 int sidewardmotor=4; //sideward vibrating motor
 int a=A0; // voltage acroos 470ohm resistor of water sensor
int buzzer=9; // piezo buzzer 
long 
duration1,duration2,dcm1,dcm2,voltaged,voltage; 
void setup() { 
//Serial Port begin 
Serial.begin (9600);
 //Define inputs and outputs
 pinMode(trigPin1, OUTPUT); 
pinMode(trigPin2, OUTPUT);
 pinMode(echoPin1, INPUT);
 pinMode(echoPin2, INPUT);
 pinMode(forwardmotor,OUTPUT);
 pinMode(sidewardmotor,OUTPUT);
 pinMode(a,INPUT);
 pinMode(buzzer,OUTPUT); }
 void loop() {
 // The sensor is triggered by a HIGH pulse of 10 or more microseconds.
 // Give a short LOW pulse beforehand to ensure a clean HIGH pulse:
 digitalWrite(trigPin1, LOW);
 digitalWrite(trigPin2, LOW); 
delayMicroseconds(5);
 digitalWrite(trigPin1, HIGH); 
digitalWrite(trigPin2, HIGH); 
delayMicroseconds(10); 
digitalWrite(trigPin1, LOW);
 digitalWrite(trigPin2, LOW);
 duration1 = pulseIn(echoPin1, HIGH);
 duration2 = pulseIn(echoPin2, HIGH);
 // convert the time into a distance dcm1 = (duration1/2) / 29.1;
 dcm2 = (duration2/2) / 29.1;
 if (dcm1< 60) { digitalWrite(sidewardmotor,HIGH); }
 else{ digitalWrite(sidewardmotor,LOW); }
 voltaged=analogRead(a);
 // voltage in digital voltage=(voltaged*5)/1023;
 // voltage in corresponding analog
if (voltage>0.7||voltage<=1.2)
{ analogWrite(buzzer,150);}
 //buzzer with moderate sound if (voltage>1.2)
{ analogWrite(buzzer,255);}
 // buzzer with sharp sound else{ analogWrite(buzzer,0);}
 delay(250); }
