# 加速度センサーを使用する

MStack5 Gray には 6 軸 IMU ユニット

## スケッチ例 1 : 

````C
// (1) MSTACK_MPU6886 の定義
#define M5STACK_MPU6886
#include <M5Stack.h>

void setup() {
  M5.begin();
  M5.Power.begin();

  M5.IMU.Init(); // (2) センサーの初期化

  M5.Lcd.fillScreen(BLACK);
  M5.Lcd.setTextSize(3);
}

void loop() {

  // (3) x, y, z方向の加速度の取得
  float accX, accY, accZ;
  M5.IMU.getAccelData(&accX,&accY,&accZ);

  Serial.printf("%6.3f, %6.3f, %6.3f\n",accX, accY, accZ);
  delay(100);
}

````

