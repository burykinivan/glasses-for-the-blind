# Очки - навигатор

## Оглавление
Актуальность
## Актуальность
В мире много сделано для незрячих людей, но мы предлагаем наш прибор для упрощения их повседневной жизни.

## Задачи
1) Проанализировать рынок.
2) Разработать прибор помогающий слепым ориентироваться в пространстве.
3) Сделать прогнозы (что будет после изобретение нашего устройства)

## Цель

Создать прибор который поможет слепым ориентироваться в пространстве. 


## Инструкция к запуску.

Преред запуском программ  *artifical intelligance*, *voice assistant* мы использовали следующие библиотеки.
1) opencv
2) PyAudio
3) SpeechRecognition
4) gTTS

Для установки вам необходимо скачать PIP. После чего открываете python. В терминале вводите:
1) pip install SpeechRecognition
2) pip install gTTS
3) pip install PyAudio

После чего устанавливаете opencv.

## Запуск нашего прибора.
Для запуска устройства подключите повербанк. Поверните устройство гладкой поверхности к себе, справа внизу вставьте провод от паввербанка. 
Если расстояние меньше 150 см, то пищалки будет издавать щелчки. До тех пор пока расстояние не будет больше 150 см.
Примечание: прибор не будет работать, если перед вами заркальная поверхность.

##программа.
```c++
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
}
```
Этот код предназначен для ультразвукового датчика, который измеряет расстояние и запускает зуммер, если расстояние меньше 150 см. 
TrigPin и echoPin используются для отправки и приема ультразвуковых волн. Длительность волны вычисляется с помощью функции pulseIn(), которая измеряет время, за которое волна отражается обратно. Расстояние в сантиметрах затем вычисляется путем деления длительности на 58.
Если расстояние меньше 150 см, зуммер включается с помощью функции analogWrite() со значением 255 (максимальное). Если расстояние больше или равно 150 см, зуммер выключается, установив значение analogWrite() на 0.
Переменная buzzerOn используется для отслеживания того, включен ли зуммер в данный момент или выключен. Если он включен, он не будет включаться снова, пока расстояние не превысит 150 см. Если он выключен, он не будет выключаться снова, пока расстояние не опустится ниже 150 см.
Задержка delay(1000) в конце функции loop() используется для ожидания 1 секунды перед следующим измерением.
