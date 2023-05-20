# Очки - навигатор
## Актуальность
В мире много сделано для незрячих людей, но мы предлагаем наш прибор для упрощения их повседневной жизни.

## Задачи
1) Проанализировать рынок.
2) Разработать прибор помогающий слепым ориентироваться в пространстве.
3) Сделать прогнозы (что будет после изобретение нашего устройства)

## Цель

Создать прибор который поможет слепым ориентироваться в пространстве. 


## Инструкция к запуску.

Преред запуском программ  *artifical intelligance*, *face recognition*, *voice assistant* мы использовали следующие библиотеки.
1) opencv
2) numpy
3) PyAudio
4) SpeechRecognition
5) gTTS

Для установки вам необходимо скачать PIP.

## Запуск нашего прибора.
Для запуска устройства подключите повербанк. Поверните устройство гладкой поверхности к себе, справа внизу вставьте провод от паввербанка. 
Если расстояние меньше 150 см, то пищалки будет издавать щелчки. До тех пор пока расстояние не будет больше 150 см.
Примечание: прибор не будет работать, если перед вами заркальная поверхность.

##программа.
```
#include <Arduino.h>
int trigPin = 7; // пин от датчик расстояния 
int echoPin = 6; // пин от датчик расстояния 
int buzzerPin = 8; // пин от пищалки
void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzerPin, OUTPUT); 
}
void loop() {
  int duration, cm;
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  cm = duration / 58;
  Serial.print(cm);
  Serial.println(" cm");
  if (cm < 150) { // если расстояние меньше 150 см, то начинает работать пищалка
    digitalWrite(buzzerPin, HIGH); // включить пищалку
    delay(100); // задержка для создания эффекта писка
    digitalWrite(buzzerPin, LOW); // выключить пищалку
    delay(100); // задержка между писками
  } else {
    digitalWrite(buzzerPin, LOW); // выключить пищалку
  }
  delay(1000);
}```
