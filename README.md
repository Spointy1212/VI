#include <Adafruit_NeoPixel.h>
#define  sensorPin  6
#define PIN 2  /*定义了控制LED的引脚，6表示Microduino的D6引脚，可通过Hub转接出来，用户可以更改 */
#define PIN_NUM 2 //定义允许接的led灯的个数

Adafruit_NeoPixel strip = Adafruit_NeoPixel(PIN_NUM, PIN, NEO_GRB + NEO_KHZ800);
int state;

void setup()
{
  pinMode(sensorPin, INPUT);
  Serial.begin(9600);
}
void loop()
{
  state = digitalRead(sensorPin);
 if (state == 1)
    {Serial.println("Somebody is in this area!");
    strip.begin();
  strip.setPixelColor(0, strip.Color(255, 0, 0));//红
  strip.show(); 
  delay(1000);
  strip.setPixelColor(0, strip.Color(0, 255, 0));//绿
  strip.show();
  delay(1000);
  strip.setPixelColor(0, strip.Color(0, 0, 255));//蓝
  strip.show();
  delay(1000);
  strip.setPixelColor(0, strip.Color(0, 0, 0));//灭
  strip.show();
  delay(1000);
 }
  else{
    Serial.println("No one!");}
  delay(2000);
}
