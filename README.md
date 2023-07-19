# WÄRME LUMIÈRE
WÄRME LUMIÈRE is a concept by which we aim to conserve power and energy. It consists of an infrared sensor, connected to a light [ which is at a distance around 100- 500 meters ]. We aim to place our sensor in an isolated region where street lights remain ON the entire night but the passersby are none to any. In such cases, we aim to use our project that whenever there is no population the light will be turned OFF, and if a person, vehicle, etc comes in range of our sensor [infrared sensor], it will detect them by their body heat or engine heat and the light ahead [ at a distance around 100-500 meters] will be turned ON and they will be turned OFF when the person or vehicle has passed and is out of sensors range. This will help us to save electricity which in future will benefit everyone. it will be for the greater good of the nation and its people.
This code sets up a basic motion detection system using an Arduino board and a motion sensor. The system uses an LED to indicate the presence of motion detected by the sensor. Here's a detailed explanation of the code:
1. Variable and Pin Declarations:
   - `int led = 3;`: This declares an integer variable `led` and assigns it the value 3. This variable represents the pin number to which the LED is connected.
   - `int sensor = 8;`: This declares an integer variable `sensor` and assigns it the value 8. This variable represents the pin number to which the motion sensor is connected.
   - `int state = LOW;`: This declares an integer variable `state` and initializes it to `LOW`. This variable keeps track of the current state of motion detection (whether motion is detected or not).
   - `int val = 0;`: This declares an integer variable `val` and initializes it to 0. This variable is used to store the current status (value) of the motion sensor.

2. `setup()` Function:
   - `pinMode(led, OUTPUT);`: This sets the LED pin (`led`) as an output, allowing it to be used to control the LED.
   - `pinMode(sensor, INPUT);`: This sets the motion sensor pin (`sensor`) as an input, enabling the Arduino to read the sensor's status.
   - `Serial.begin(9600);`: This initializes the serial communication with a baud rate of 9600, which allows the Arduino to communicate with a computer over a serial connection.

3. `loop()` Function:
   This is the main loop that continuously runs while the Arduino is powered on.

   - `val = digitalRead(sensor);`: This reads the current state (HIGH or LOW) of the motion sensor and stores it in the `val` variable.

   - `if (val == HIGH) { ... } else { ... }`: This checks if the sensor's status is HIGH (motion detected) or LOW (no motion detected).

     - If motion is detected (`val == HIGH`):
       - `digitalWrite(led, LOW);`: Turns ON the LED (connected to `led` pin) to indicate motion.
       - `delay(10);`: A small delay of 10 milliseconds to avoid rapid fluctuations in motion detection.

       - `if (state == LOW) { ... }`: This checks if the previous state was LOW (no motion detected) before the current motion was detected.
         - `Serial.println("Motion stopped!");`: Prints "Motion stopped!" to the serial monitor (connected to the computer) to indicate that the motion has stopped.
         - `state = LOW;`: Updates the `state` variable to `LOW`, indicating that no motion is currently detected.

     - If no motion is detected (`val == LOW`):
       - `digitalWrite(led, HIGH);`: Turns OFF the LED to indicate no motion.
       - `delay(5000);`: A delay of 5000 milliseconds (5 seconds) to prevent rapid changes in motion detection.

       - `if (state == HIGH){ ... }`: This checks if the previous state was HIGH (motion detected) before the current state with no motion.
         - `Serial.println("Motion detected!");`: Prints "Motion detected!" to the serial monitor to indicate that motion has been detected.
         - `state = HIGH;`: Updates the `state` variable to `HIGH`, indicating that motion is currently detected.

The code continuously reads the motion sensor's status, updates the LED state based on motion detection, and prints messages to the serial monitor indicating motion events.
