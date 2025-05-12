# Smoke-Detector-System
#define smoke  A0  
#define buzzer  2  
#define led  3 
#define fan 4
float data ;
int flag = 400 ;

void setup() {
  Serial.begin(9600);
  pinMode(smoke, INPUT);
  pinMode(led, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(fan, OUTPUT);
  digitalWrite(fan, LOW);
  digitalWrite(led, LOW);
  digitalWrite(buzzer, LOW);

}

void loop() {
  data = analogRead(A0);
  if(data < flag){
    digitalWrite(buzzer, LOW);
    digitalWrite(led, LOW);
    digitalWrite(fan, LOW);
  }
   else if(data >= flag){
    digitalWrite(buzzer, HIGH);
    delay(200);
    digitalWrite(led, HIGH);
    delay(200);
    digitalWrite(buzzer, LOW);
    delay(200);
    digitalWrite(led, LOW);
    delay(200);
    

    
  }
  
}
