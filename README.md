# flex-sensor
int flexPin = A0;

void setup() 
{
 Serial.begin(9600); 
}

void loop()
{
 int flexVal;
 flexVal = analogRead(flexPin);
 Serial.print("flex resistance:");
 Serial.println(flexVal);
 delay(1000);  //providing delay of 1ms 

}
