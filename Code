const int trigFront = 5;
const int echoFront = 4;
const int buzzerFront = 9;

const int trigLeft = 6;
const int echoLeft = 7;
const int buzzerLeft = 10;

const int trigRight = 8;
const int echoRight = 3;
const int buzzerRight = 11;

const int dangerDistance = 50;

void setup() {
  Serial.begin(9600);

  pinMode(trigFront, OUTPUT);
  pinMode(echoFront, INPUT);
  pinMode(trigLeft, OUTPUT);
  pinMode(echoLeft, INPUT);
  pinMode(trigRight, OUTPUT);
  pinMode(echoRight, INPUT);

  pinMode(buzzerFront, OUTPUT);
  pinMode(buzzerLeft, OUTPUT);
  pinMode(buzzerRight, OUTPUT);
}

long getDistance(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  long distance = duration * 0.0343 / 2; // Speed of sound = 343 m/s
  return distance;
}

void loop() {
  long distFront = getDistance(trigFront, echoFront);
  long distLeft = getDistance(trigLeft, echoLeft);
  long distRight = getDistance(trigRight, echoRight);

  Serial.print("Front: ");
  Serial.print(distFront);
  Serial.print(" cm, Left: ");
  Serial.print(distLeft);
  Serial.print(" cm, Right: ");
  Serial.print(distRight);
  Serial.println(" cm");


  if (distFront < dangerDistance) {
    tone(buzzerFront, 1000);  
  } else {
    noTone(buzzerFront);
  }

  if (distLeft < dangerDistance) {
    tone(buzzerLeft, 1200, 100);  
    delay(150);                   
  } else {
    noTone(buzzerLeft);
  }

  if (distRight < dangerDistance) {
    tone(buzzerRight, 800, 300);  
    delay(350);                   
  } else {
    noTone(buzzerRight);
  }

  delay(100); 
}
