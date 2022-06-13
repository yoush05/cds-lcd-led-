#include <Wire.h>
#include <LiquidCrystal_I2C.h>
라이브러리를 다운받아야 한다. 이름은 LiquidCrystal I2C 이다. 

LiquidCrystal_I2C lcd(0x27,16,2);  // set the LCD address to 0x27 for a 16 chars and 2 line display

int cds = A1;//
int cdsValue = 0;//값초기화 0으로 세팅   
int led1 = 12;            
void setup(){
    lcd.init();            
  lcd.backlight();
  백라이트를 켠다
  lcd.setCursor(0,0);
  맨위 맨 왼쪽부터 출력한다. 
  lcd.print("abcde");
  
  pinMode(led1, OUTPUT);
  Serial.begin(9600);//시리얼창을 열겠다 속도는 9600             
}
void loop(){
   cdsValue = analogRead(cds);
  Serial.print("sensor = ");
  Serial.println(cdsValue);
    lcd.setCursor(0,1);
  lcd.print("cdsValue = ");
   lcd.setCursor(12,1);
  lcd.print(cdsValue);
  if (cdsValue >= 700) 
{ digitalWrite(led1, LOW);  } 
else 
{ digitalWrite(led1, HIGH); } 
  delay(300);
}
//어두워지면자동으로불이들어오는시스템+lcd에 조도센서값을 표시하는 프로그램 
