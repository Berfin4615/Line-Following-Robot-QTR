#include <QTRSensors.h>

QTRSensors qtr;

const uint8_t SensorCount = 6;
uint16_t sensorValues[SensorCount];

void setup()
{
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(5, OUTPUT);

  Serial.begin(9600);
  // configure the sensors
  qtr.setTypeAnalog();
  qtr.setSensorPins((const uint8_t[]){A0, A1, A2, A3, A6, A7}, SensorCount);


  delay(500);
  Serial.println("Calibrating..."); 
  for (int i = 0; i < 200; i++)
  {
    qtr.calibrate();
  }

  delay(1000);
}

void loop()
{
  int position = qtr.readLineBlack(sensorValues);


  /for (int i = 0; i < SensorCount; i++)
  {
    Serial.print(sensorValues[i]);
    Serial.print(" ");
  }/
  int hata = position - 2500;
  motorSur(-0.07 * hata, 0.07 * hata);

}

void motorSur(int hiz1, int hiz2)
{
  if(hiz1 < 0)
  {
    digitalWrite(8, HIGH);
    digitalWrite(7, LOW);
    analogWrite(6, abs(hiz1));
  }
  else
  {
    digitalWrite(8, LOW);
    digitalWrite(7, HIGH);
    analogWrite(6, hiz1);

  }

  if(hiz2 < 0)
  {
    digitalWrite(9, HIGH);
    digitalWrite(11, LOW);
    analogWrite(10, abs(hiz2));
  }
  else
  {
    digitalWrite(9, LOW);
    digitalWrite(11, HIGH);
    analogWrite(10, hiz2);

  }
} 
