Arduino Workshop Blueprint
==========================
Prepared by Zhang Yiwen

### DIY 1 - Blink LED
##### Code
```

/*  Blink  Turns on an LED on for one second, then off for one second, repeatedly.   This example code is in the public domain. */ 

// Pin 13 has an LED connected on most Arduino boards.
// give it a name:

int led = 13;

// the setup routine runs once when you press reset:
void setup() {                  
	// initialize the digital pin as an output.  
	pinMode(led, OUTPUT);     
}

// the loop routine runs over and over again forever:
void loop() {  
	digitalWrite(led, HIGH);  		// turn the LED on (HIGH is the voltage level)  
	delay(1000);               		// wait for a second  
	digitalWrite(led, LOW);   	 	// turn the LED off by making the voltage LOW  
	delay(1000);              		// wait for a second
}

```

##### Circuit

### DIY 2 - Led dimming with potentiometer
##### Code
```

const int pot= A0;
const int led = 9;

int sensorValue = 0; 
int outputValue = 0; 

void setup() {     
	 // initialize serial communications at 9600 bps:           
	Serial.begin(9600);   
}

void loop() {
    	int sensorValue = analogRead(pot); 
	float outputValue = sensorValue/1023.0 *255.0;
  	//int outputValue = map(pot, 0, 1023, 0, 255); 
	analogWrite(led, outputValue);	
	delay(2); 
}

```

##### Circuit

### DIY 3 - Servo Control
##### Code
···

/*  Blink  Turns on an LED on for one second, then off for one second, repeatedly.   This example code is in the public domain. */ 

// Pin 13 has an LED connected on most Arduino boards.
// give it a name:
#include <Servo.h> 

Servo myservo;  
int potpin = A0;  // analog pin used to connect the potentiometer
int val;    // variable to read the value from the analog pin 
 
void setup() 
{ 
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object 
} 
 
void loop() 
{ 
  val = analogRead(potpin);            // reads the value of the potentiometer (value between 0 and 1023) 
  val = map(val, 0, 1023, 0, 179);     // scale it to use it with the servo (value between 0 and 180) 

  //float pos = val/1023.0 *255.0;
  //myservo.write(pos);

  // sets the servo position according to the scaled value   
  myservo.write(val);
  
  delay(60);                           // waits for the servo to get there 
}

···
##### Circuit

### DIY 4 - Photo Resistor
##### Code
···

#include <Servo.h>

Servo myservo;

int pos = 0;

void setup()
{
  myservo.attach(9);
  pinMode(A3, INPUT);
}

void loop()
{
  pos = analogRead(A3);
  pos = map(pos, 0, 1023, 0, 360 );
  myservo.write(pos);
  delay(15);
}

···
##### Circuit
