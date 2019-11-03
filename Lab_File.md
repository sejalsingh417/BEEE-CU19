# Experiment4 – LED Controlled By Smart Phone


## Aim:
To design a Smart Phone controlled LED such that when we push the ON button on our Smart Phone APP, the LED starts glowing and when we push the OFF button, the LED stops glowing.

## Apparatus:
Arduino Board, LED, Resistance - 220ohm, Breadboard, Wires, Bluetooth Module.

## Circuit Diagram:
![Exp4](https://user-images.githubusercontent.com/54620652/67159391-95ac8700-f361-11e9-9c36-94dd2e045554.png)
## Theory:
**Concepts Used -**\
***LEDs:***\
An LED is a small light (it stands for "light emitting diode") that works with relatively little power. The Arduino board has one built-in on digital pin 13.
An external LED can also be used by specifying the pin number it is using on the Arduino.
In electronics, polarity indicates whether a circuit component is symmetric or not. LEDs, being diodes, will only allow current to flow in one direction. And when there’s no current-flow, there’s no light.
The positive side of the LED is called the “anode” and is marked by having a longer “lead,” or leg. The other, negative side of the LED is called the “cathode.” Current flows from the anode to the cathode and never the opposite direction. A reversed LED can keep an entire circuit from operating properly by blocking current flow. So don’t freak out if adding an LED breaks your circuit. Try flipping it around.\
***Bluetooth - HC5:***\
=> For the communication between mobile and microcontroller, Bluetooth module (HC-5) is used.\
=> Low Power 1.8V operation, 1.8 to 3.6V InputOutput.\
=> Serial port Bluetooth module have a Bluetooth 2.0+EDR (Enhanced Data Rate), 3Mbps modulation with complete 2.4GHz radio transceiver and baseband.\
=> Using Bluetooth profile and android platform architecture different type of Bluetooth applications can be developed.\


**Learning and Observations -**
1. We can recognize the positive and negative terminals of an LED even without using a Multimeter. The longer leg of the LED is the positive terminal (or the anode) and the smaller leg is the negative terminal (or the cathode).
2. Another way of finding the positive and negative terminals of an LED is to see the parts inside the LED. The larger part is the negative side (i.e. the cathode) and the smaller part is the positive side (i.e. the anode).

## Problems and Troubleshooting:
1. The first problem that we faced was due to the cable of the Arduino which was not working properly. This problem was solved by using another cable.
2. The proper port of the Arduino was not selected. After it was selected the Arduino worked perfectly.
3. The code had some errors like proper pin was not mentioned, etc. But after modifying the code, everything worked perfectly fine.

## Precautions:
1. The Arduino and its cable should be working properly.
2. Proper port of the Arduino should be selected.
3. The connections should be made neat and clean.
4. Desired resistance should be used.
5. Bluetooth Module Should be working properly.

## Arduino Code:
```
//LED_SMART_PHONE
char junk;
String inputString="";
void setup(){
 Serial.begin(9600);
 pinMode(13, OUTPUT);
}
void loop(){
  if(Serial.available()){
  while(Serial.available()){
      char inChar = (char)Serial.read();
      inputString += inChar;   
    }
    Serial.println(inputString);
    while (Serial.available() > 0){ 
    junk = Serial.read() ; }
    if(inputString == "a"){ 
      digitalWrite(13, HIGH);  
    }else if(inputString == "b"){  
      digitalWrite(13, LOW);
    }
    inputString = "";
  }
}


## Result:
Glowing of LED by pressing the ON button in the Smart Phone APP was verified after uploading the program.
