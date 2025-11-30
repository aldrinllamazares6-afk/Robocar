int infared1=10;
int infared2=12;
int sensorValue1;
int sensorValue2;

void setup() {
  pinMode(7, OUTPUT); //LEFT GO
  pinMode(5, OUTPUT);//LEFT BACK
  pinMode(2, OUTPUT); //RIGHT GO
  pinMode(4, OUTPUT); //RIGHT BACK
  pinMode(6, OUTPUT); //ENA
  pinMode(9, OUTPUT); //ENB
  pinMode(infared1,INPUT);
  pinMode(infared2,INPUT);

  Serial.begin(9600);
  Serial.println("Robot Car Moving...");
  delay(5000);
}

void loop() {
 sensorValue1=digitalRead(infared1);
 sensorValue2=digitalRead(infared2);

 Serial.println("LEFT: ");
 Serial.print(sensorValue1);
 Serial.println("RIGHT: ");
 Serial.println(sensorValue2); 


 if((sensorValue1==1)&&(sensorValue2==1)) {
 //move forward
 Serial.println("Moving Forward...");
 digitalWrite(7, HIGH);
 digitalWrite(5, LOW);
 analogWrite(6, 100);

 digitalWrite(2, HIGH);
 digitalWrite(4, LOW);
 analogWrite(9, 100);
 }
 
 if((sensorValue1==0)&&(sensorValue2==0)) {
  //move backward
  Serial.println("Moving Backward...");
  digitalWrite(7, LOW);
  digitalWrite(5, HIGH);
  analogWrite(6, 100);

  digitalWrite(2, LOW);
  digitalWrite(4, HIGH);
  analogWrite(9, 100);
 }
  
  if((sensorValue1==1)&&(sensorValue2==0)) {
  //turn left
  Serial.println("Turning Left...");
  digitalWrite(7, LOW); 
  digitalWrite(5, HIGH);
  analogWrite(6, 150);

  digitalWrite(2, HIGH);
  digitalWrite(4, LOW);
  analogWrite(9, 190);
  }

  if((sensorValue1==0)&&(sensorValue2==1)) {
  //turn right
  Serial.println("Turning Right...");
  digitalWrite(7, HIGH); 
  digitalWrite(5, LOW);
  analogWrite(6, 190);

  digitalWrite(2, LOW);
  digitalWrite(4, HIGH);
  analogWrite(9, 150);
  }
}
