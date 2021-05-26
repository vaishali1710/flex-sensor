**flex_sensor**
int flexPin = A0;      // Pin connected to voltage divider output

float VCC = 5;      // voltage at Ardunio 5V line
float R_DIV = 47000.0;  // resistor used to create a voltage divider
float flatResistance = 25000.0; // resistance when flat
float bendResistance = 100000.0;  // resistance at 90 deg

void setup() {
  Serial.begin(9600);
  pinMode(flexPin, INPUT);
}

void loop() {
  // Read the ADC, and calculate voltage and resistance from it
  int ADCflex = analogRead(flexPin);
  float Vflex = ADCflex * VCC / 1023.0;
    Serial.print("output voltage:");
    Serial.println(String(Vflex) + "volt");
  delay(1000);
}
