/////Json
#include <ArduinoJson.h>
const int TAMANHO = 100;

int TermistorPin = A1;
int LuxPin = A0;

int Vo;
float R1 = 10000;
float logR2, R2, T, Tc, Tf, temp;
float c1 = 1.009249522e-03, c2 = 2.378405444e-04, c3 = 2.019202697e-07; //valores constante para calculo

volatile unsigned long cont = 0;
unsigned long tempo = 0;
unsigned long tempo2 = 0;
float v;

void setup() {
  Serial.begin(115200);
  pinMode(TermistorPin, INPUT);
  pinMode(LuxPin, INPUT);

  //  Configura o pino2 como interrupção externa do tipo Rising (borda de LOW para HIGH)
  pinMode(2,INPUT_PULLUP);
  attachInterrupt(digitalPinToInterrupt(2),interrupcaoPino2,RISING);  

}

void loop() {
  StaticJsonDocument<TAMANHO> json; //cria o objeto Json

  //Captacao dados temp
  float temp = readTemp(TermistorPin);
  
  //Captacao dados lux  
  float lux = readLux(LuxPin);

  //Captacao dados vel
  if((millis() - tempo) > 999){
    tempo = millis();
    v = (2*PI*cont*3.6*0.147)/60;
    cont = 0;
  }

  if((millis() - tempo2) > 2000){
    tempo2 = millis();
    //criacao json com dados q serao enviados
    json["vel"] = v;
    json["ValorLux"] = lux;
    json["temperatura"] = temp;

    serializeJson(json, Serial);
    Serial.println();
  }  
}

//funcão de interrupção do pino2, é executado quando o botao do pino2 pressionado
void interrupcaoPino2(){                    
  cont++;
}

//função que faz leitura da temperatura e retorna o valor em graus celcius
float readTemp(int ThermistorPin){  
  Vo = analogRead(ThermistorPin);
  R2 = R1 * (1023.0 / (float)Vo - 1.0); //calculo R2, demonstração no arquivo pdf da aula
  logR2 = log(R2);
  T = (1.0 / (c1 + c2*logR2 + c3*logR2*logR2*logR2));// Equação de Steinhart–Hart 
  Tc = T - 273.15; //temp em Graus celcius
  //Tf = (Tc * 9.0)/ 5.0 + 32.0; // temp em fahrenheit
  return Tc;
}
//função que faz leitura da intensidade luminosa e retorna o valor em lux
float readLux(int LuxPin) {
  float Rdark = 127410;
  float Vout = analogRead(LuxPin);
  float Rldr = 10000/ (1023/Vout-1);
  float L = pow(Rdark / Rldr, (1/0.8582));
  return L;
}
