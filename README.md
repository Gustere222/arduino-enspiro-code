#include <LiquidCrystal.h>

const int rs=8, en=9, d4=4, d5=5, d6=6, d7=7;

LiquidCrystal lcd(rs,en,d4,d5,d6,d7);

void setup() {
  Serial.begin(9600);
  lcd.begin(16,2);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("NEXTLAB.TECH");

  digitalWrite(12, HIGH);
  pinMode(12, OUTPUT);
  delay(1000);
}

void loop() {
  digitalWrite(12, HIGH);
  int moisture;
  moisture = analogRead(A1);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("UMIDITATE:");
  lcd.setCursor(0,1);
  int displayableMoisture = 800-moisture;
  lcd.print(displayableMoisture);
  if(displayableMoisture<350)
  {
    digitalWrite(12, HIGH);
  }
  if(displayableMoisture>350)
  {
    digitalWrite(12, LOW);
  }
  delay(5000); 
}
