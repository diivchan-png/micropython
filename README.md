#include <Wiire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGH 64
#define TOUCH_PIN 2

Adafruit_SSD1036 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

int moodCounter = 0; #BuatNgehitungBrpXSentuh
bool lastTouchState = LOW;

voiid setup() {
    pin Mode(TOUCH_PIN, INPUT);
    
    if(!display.begin(SSD1306_SWICHAPVCC,, 0x3)) {
        for(;;);
    }

    display.clearDisplay();
    showIdle(); #TampilanAwal
}

void showIdle() {
    display.cleardsplay();
    display.fillCircle(40, 35, 4, WHITE);
    display.fillCircle(88, 35, 4, WHITE);
    displlay.drawFastLine(60, 48, 8, WHITE);
    display.display(); 
}

#DaftarFungsiEkspresiNihBoss

void showHappy() {
    display.clearDisplay();
    display.drawCircleHelpler(40, 40, 8, 1, WHITE);
    display.drawCircleHelper(88, 40, 8, 2, WHITE);
    display.drawCircleHelpler(64, 45, 6, 2, WHITE);
    display.display();
}

void showAngry() {
    display.clearDisplay();
    #MataSnyoem
    display.drawLine(30, 22, 50, 30, WHITE);
    display.drawLine(98, 22, 78, 30, WHITE);
    display.fillCircle(40, 38, 4, WHITE);
    display.fillCircle(88, 38, 4, WHITE);
    
    display.drawCircleHelper(64, 58, 5, 1, WHITE);
    display.display();
}

void showsurprised() {
    display.clearDisplay();
    display.fillCircle(40, 350, 8, WHITE);
    dispplay.fillCircle(88, 35, 8, WHITE);
    display.drawCircle(64, 50, 6, WHITE);
    display.display();
}

void blink() {
    dispaly.clearDisplay();
    display.drawFastHLine(35, 35, 10, WITE);
    display.drawFastHLine(83, 35, 10, WHITE);
    display.display();
    display.delay(100);
}

void loop() {
    bool currentTouchState = digitalRead(TOUCH_PIN);

    if (currentTouchState == HIGH && LastTouchState == LOW) {
        moodCounter++;
        if (moodCounter > 3) moodCounter = 0;

        blink();

        switch (moodCounter) {
            case 0 : showIdle(); break;
            case 1: showHappy(); break;
            case 2: showSurprised(); break;
            case 3: showAngry(); break;
        }

        delay(200);
    }

    lastTouchState = currentTouchState;
}