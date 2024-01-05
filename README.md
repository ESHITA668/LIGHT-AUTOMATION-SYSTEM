# LIGHT-AUTOMATION-SYSTEM
c++
define ldr A0
int thrs = 100;
int green = 2;
int red = 3;
int Delay = 1000; // delay in ms
int relay = 4;
int ir1 = 5;
int ir2 = 6;
void setup() {
 pinMode(green, OUTPUT);
 pinMode(red, OUTPUT);
 pinMode(relay, OUTPUT);
 pinMode(ir1, INPUT);
 pinMode(ir2, INPUT);
 Serial.begin(9600);
}
void loop() {
 static int count = 0;
 if(digitalRead(ir1) == 0){
 digitalWrite(green, HIGH);
 delay(Delay);
 digitalWrite(green, LOW);
 count++; }
 if(digitalRead(ir2) == 0){
 digitalWrite(red, HIGH);
 delay(Delay);
 digitalWrite(red, LOW);
 count--;
 }
 int lux = analogRead(ldr);
 Serial.print("No of People in room : ");
 Serial.println(count);
 Serial.print("Lux : ");
 Serial.println(lux);
 if((count>0) && (lux<thrs)){
 digitalWrite(relay, HIGH);
}
 else{
 digitalWrite(relay, LOW); }
}
