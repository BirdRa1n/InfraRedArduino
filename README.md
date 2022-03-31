
# INFRAVERMELHO ARDUINO

O projeto a seguir recebe códigos de controles utilizando infra vermelho.




![App Screenshot](https://thumbs2.imgbox.com/6a/8b/sucfZwsT_t.png)


## IR.INO 

```c++

#include <IRremote.h>
int RECV_PIN = 9; // porta digital que será definida para receber os dados do Arduino.
IRrecv irrecv(RECV_PIN);
decode_results results;

void setup()
{
  Serial.begin(9600);
  irrecv.enableIRIn(); // habilitar o infra vermelho.
  
}
void loop()
{

  if (irrecv.decode(&results))
  {
    Serial.println(" ");
    Serial.print("Código: ");
    //Serial.println(results.value); mostra o código ao ser precionado um botão do controle
    const int ALL_ON_CODE = results.value;
    
    Serial.println(ALL_ON_CODE); // vai conter o código que será usado nas condições
    Serial.println(" ");
  }

  irrecv.resume(); // reseta o estado do ISR

}
```

