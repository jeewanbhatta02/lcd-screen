#include<LiquidCrystal.h>
LiquidCrystal lcd(13,12,6,4,3,2);
const int temperature =A0;
const int D=8;
void setup()
 
{
  lcd.begin(16,2);
  Serial.begin (9600);
  pinMode(D,OUTPUT);
}
void loop()
{
  digitalWrite(D,LOW);
  int Temp=analogRead(temperature);
  float volts=(Temp/965.0)*5;
  float celcious=(volts-0.5)*100;
  float fahrenheit=(celcious*9/5+32);
  Serial.println(fahrenheit);
  lcd.setCursor(5,0);
  lcd.print(fahrenheit);
  delay(2000);
}
