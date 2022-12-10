// акселерометр
// пины подключения x,y,z
const int pinX=A0;
const int pinY=A1;
const int pinZ=A2;
// переменные для хранения значений
unsigned int x, y, z;
void setup() {
   // запуск последовательного порта
   Serial.begin(9600);
}
void loop() {
   // получение данных
   x = analogRead(pinX);
   y = analogRead(pinY);
   z = analogRead(pinZ);
   // вывод в последовательный порт
   Serial.print(x);
   Serial.print("  ");
   Serial.print(y);
   Serial.print("  ");
   Serial.print(z);
   Serial.println();
   // пауза
   delay(300);
}
