const int LM35 = 0; // saída sensor na entrada A0 - Analógica
float temperatura = 0; // variável tipo float que armazena a temperatura ambiente
int ADClido = 0; // variável inteira que captura o valor lido pelo sensor
const int Buzzer = 12; // buzzer conectado na entrada 12 - digital
const int Led10 = 10; // LED conectado na entrada 10 - digital
 
void setup(){
analogReference(INTERNAL); //No Mega, use INTERNAL1V1, no Leonardo remova essa linha
pinMode(Buzzer, OUTPUT); //seta o buzzer como saída
pinMode(Led10, OUTPUT); //seta o LED como saída
}
 
void loop(){
ADClido = analogRead(LM35); // a variável corresponde ao valor captado pelo sensor de temperatura
temperatura = ADClido * 0.1075268817204301; //multiplicador para que o valor lido seja convertido para decimal
   
if(temperatura > 50){ // valor de referência configurado como 50ºC
digitalWrite(Buzzer, HIGH); // aciona o buzzer
digitalWrite(Led10, HIGH);  // aciona o LED
}
else{      // caso a temperatura ambiente esteja abaixo do valor de referência
digitalWrite(Buzzer, LOW); // desativa o buzzer
digitalWrite(Led10, LOW);  // desativa o LED
}
}
