# Arduino-DCmotor-with-ultraSonic-sensor


# Code Below:
```cpp
byte redLED = 2;
byte trig = 4;
byte echo = 3;
byte buzzer = 8;
byte enable = 10;
byte input1 = 11;
byte input2 = 12;

int distance;
unsigned long travelTime;

void setup() {
  Serial.begin(9600);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(enable, OUTPUT);
  pinMode(input1, OUTPUT);
  pinMode(input2, OUTPUT);
  pinMode(redLED, OUTPUT);
}

void loop() {
  digitalWrite(trig, LOW);
  delayMicroseconds(5);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  travelTime = pulseIn(echo, HIGH);

  distance = (travelTime / 2) * 0.0343;

  if (distance < 25) {
   digitalWrite(input1, LOW);
    digitalWrite(input2, LOW);
    analogWrite(enable, 0);
    digitalWrite(redLED, HIGH);
    digitalWrite(buzzer, HIGH);
  }


  Serial.println(distance);

  delay(200);
}

```
