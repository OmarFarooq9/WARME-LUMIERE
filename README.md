int led = 3;                // the pin that the LED is atteched to
int sensor = 8;              // the pin that the sensor is atteched to
int state = LOW;             // by default, no motion detected
int val = 0;                 // variable to store the sensor status (value)

void setup() {
  pinMode(led, OUTPUT);      // initalize LED as an output
  pinMode(sensor, INPUT);    // initialize sensor as an input
  Serial.begin(9600);        // initialize serial
}

void loop(){
  val = digitalRead(sensor);   // read sensor value
  if (val == HIGH) {           // check if the sensor is HIGH
    digitalWrite(led, LOW);   // turn LED ON
    delay(10);                // delay in milliseconds 
    
    if (state == LOW) {
      Serial.println("Motion stopped!"); 
      state = LOW;       // update variable state to HIGH
    }
  } 
  else {
      digitalWrite(led, HIGH); // turn LED OFF
      delay(5000);             // delay 5 seconds
      
      if (state == HIGH){
        Serial.println("Motion detected!");
        state = HIGH;       // update variable state to LOW
    }
  }
}
