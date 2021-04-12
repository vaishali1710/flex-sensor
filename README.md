# flex-sensor
interfacing of flex and arduino
int flexPin=A0;
float VCC=5;
float R=47000;   //resistor for voltage divvider cicuit (fixed resistor usually taken as 47000ohm)
float nobendResistance=25000;   //resistance when bend angle is 0 degree
float bendResistance=100000;   //resistance when bend angle is 90 degree
void setup()
{
  Serial.begin(9600);
  pinMode(flexPin,INPUT);
}

void loop()
{
  int ADCflex=analogRead(flexPin);   
  float Vflex=ADCflex*VCC/1023.0;
  float Rflex=R*(VCC/Vflex-1.0);   //resistance of flex sensor calculated using voltage divider formula
  Serial.println("Resistance:"+String(Rflex)+"ohms");

  float angle=map(Rflex,nobendResistance,bendResistance,0,90.0);   //map function converts the resistance of the sensor to bend angle of the sensor nobendresistance mapped to 0 degree and bendresistance mapped to 90 degree
  Serial.println("Bend:"+String(angle)+"degrees");
  Serial.println();
  delay(1000);
}
