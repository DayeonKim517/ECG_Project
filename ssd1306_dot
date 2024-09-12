// bit를 세팅해 주는 매크로
#ifndef cbi
#define cbi(sfr, bit) (_SFR_BYTE(sfr) &= ~_BV(bit))
#endif
#ifndef sbi
#define sbi(sfr, bit) (_SFR_BYTE(sfr) |= _BV(bit))
#endif

#include <SPI.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128 // OLED display width, in pixels
#define SCREEN_HEIGHT 64 // OLED display height, in pixels


#define OLED_RESET         -1 // Reset pin # (or -1 if sharing Arduino reset pin)
#define SCREEN_ADDRESS   0x3C ///< See datasheet for Address; 0x3D for 128x64, 0x3C for 128x32
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

#define NUMFLAKES     10 // Number of snowflakes in the animation example

void setup() {
  Serial.begin(115200);
  pinMode(8,OUTPUT);
  pinMode(9,OUTPUT);

  sbi(ADCSRA,ADPS2) ;
  cbi(ADCSRA,ADPS1) ;
  sbi(ADCSRA,ADPS0) ;

  // SSD1306_SWITCHCAPVCC = generate display voltage from 3.3V internally
  if(!display.begin(SSD1306_SWITCHCAPVCC, SCREEN_ADDRESS)) {
    Serial.println(F("SSD1306 allocation failed"));
    for(;;); // Don't proceed, loop forever
  }

  // Show initial display buffer contents on the screen --
  // the library initializes this with an Adafruit splash screen.
  //display.display();
  //delay(2000); // Pause for 2 seconds


  display.clearDisplay();

  // Draw a single pixel in white
  display.drawPixel(0, 0, SSD1306_WHITE);

  // Show the display buffer on the screen. You MUST call display() after
  // drawing commands to make them visible on screen!
  display.display();
  delay(1000);
  // display.display() is NOT necessary after every single drawing command,
  // unless that's what you want...rather, you can batch up a bunch of
  // drawing operations and then update the screen all at once by calling
  // display.display(). These examples demonstrate both approaches...

  display.clearDisplay();
  for(int x=0;x<128;x+=16){
    for(int z=0;z<64;z+=16){
      display.drawPixel(x, z, SSD1306_WHITE);
      display.display();
    }
  }
  delay(1000);
  // 문자표시하기
  display.clearDisplay();

  display.setTextSize(1);
  display.setTextColor(WHITE);
  display.setCursor(0,0);//(x,z)
  display.println("Hello world!");

  display.setTextSize(2);
  display.setTextColor(WHITE);
  display.setCursor(0,10);//(x,z)
  display.println("Hello!");

  display.setTextSize(3);
  display.setTextColor(WHITE);
  display.setCursor(0,27);//(x,z)
  display.println("Hello!");

  display.display();
  delay(1000);

}



void loop() {
     
  display.clearDisplay();
  for(int x=0;x<128;x+=16){
    for(int z=0;z<64;z+=16){
      display.drawPixel(x, z, SSD1306_WHITE);
      display.display();
    }
  }

  display.setTextSize(1);
  display.setTextColor(WHITE);
  display.setCursor(31,31);//(x,z)
  display.println("(32,32)");
  display.display();
  delay(1000);
  display.clearDisplay();
  delay(200);

}

