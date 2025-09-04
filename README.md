#include <Sparki.h>

#define NOTE_A   440
#define NOTE_A5  880
#define NOTE_F   349
#define NOTE_F5  698
#define NOTE_C5  523
#define NOTE_E   659
#define NOTE_GS  415

void playImperialMarch() {
  sparki.beep(NOTE_A, 500); delay(100);
  sparki.beep(NOTE_A, 500); delay(100);
  sparki.beep(NOTE_F, 350); delay(50);
  sparki.beep(NOTE_C5, 150); delay(100);
  sparki.beep(NOTE_A, 500); delay(100);
  sparki.beep(NOTE_F, 350); delay(50);
  sparki.beep(NOTE_C5, 150); delay(100);
  sparki.beep(NOTE_A, 1000); delay(250);
  sparki.beep(NOTE_E, 500); delay(100);
  sparki.beep(NOTE_E, 500); delay(100);
  sparki.beep(NOTE_E, 500); delay(100);
  sparki.beep(NOTE_F, 350); delay(50);
  sparki.beep(NOTE_C5, 150); delay(100);
  sparki.beep(NOTE_GS, 500); delay(100);
  sparki.beep(NOTE_F, 350); delay(50);
  sparki.beep(NOTE_C5, 150); delay(100);
  sparki.beep(NOTE_A, 1000);
}

void drawEyes(bool blink) {
  sparki.clearLCD();
  sparki.drawCircle(30, 24, 8);
  sparki.drawCircle(30, 24, 3);
  if (blink) {
    sparki.drawLine(70, 20, 90, 20);
  } else {
    sparki.drawCircle(80, 24, 8);
    sparki.drawCircle(80, 24, 3);
  }
  sparki.updateLCD();
}

void setup() {
  sparki.clearLCD();
  sparki.print("Sparki Show!");
  sparki.updateLCD();
  delay(1000);
  playImperialMarch();
}

void loop() {
  sparki.moveForward(30);
  delay(1000);
  sparki.moveBackward(30);
  delay(1000);
  sparki.moveRight(90);
  sparki.moveForward(20);
  delay(1000);
  sparki.moveLeft(180);
  delay(1000);

  drawEyes(false);
  delay(2000);
  drawEyes(true);
  delay(500);
  drawEyes(false);
  delay(2000);

  sparki.servo(SERVO_CENTER);
  delay(500);
  sparki.servo(SERVO_RIGHT);
  delay(1000);
  sparki.servo(SERVO_CENTER);

  for (int i = 0; i < 3; i++) {
    sparki.RGB(RGB_RED);
    delay(300);
    sparki.RGB(RGB_GREEN);
    delay(300);
    sparki.RGB(RGB_BLUE);
    delay(300);
    sparki.RGB(RGB_OFF);
  }

  sparki.clearLCD();
  sparki.print("Tchau!");
  sparki.updateLCD();
  sparki.beep();
  delay(3000);
}