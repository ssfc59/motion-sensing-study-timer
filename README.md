# motion sensing study timer
![timer2](https://user-images.githubusercontent.com/114293506/213210966-9c3a5c37-0bbb-428c-b178-318841d1eebd.jpeg)

Developed by Francesco Cirillo in the late 1980s (Cirillo, 2022), the Pomodoro technique has become one of the most well known productivity techniques. Its structure of:
1. Defining a goal
2. Working on that goal for 25 minutes
3. Taking a 5 minute break 
4. Taking a longer break for every 4 Pomodoros completed
is familiar to anybody who has investigated ways to increase their productivity while optimising results. As someone who has has utilised the Pomodoro technique throughout my studies, I was curious if I could create a physical device based on this technique that would not only make my study sessions more productive, but also more enjoyable.

My research questions are as follows:
How can I monitor my work/study environment with this device?
How can this device foster a more productive and inspiring study environment?
Following that, I created a Pomodoro timer device,  with an added function that will display an encouraging message for the user when they are likely not working.

**Build Components:**
1. Arduino Uno
2. HC-SR501 PIR sensor
3. Adafruit Neopixel Stick
4. 16x2 LCD screen

This study timer follows the Pomodoro technique, blocking out a 25 minute work portion followed by a 5 minute break portion. The Neopixel stick on the top provides a basic visual representation of the amount of time elapsed, while the LCD screen displays the time elapsed in an analog format. This timing format creates a study routine to keep the user on track, while the PIR sensor tracks one’s patterns of movement as they study: if the user is in motion, aka typing, writing, or sketching something, it is more likely that they are at work. In constrast, if the user is not moving, they are more likely to not be at work. Following that logic, whenever the PIR sensor does not detect any motion, the LCD screen will display a random encouraging message out of 10 to motivate the user to continue working. With these functionalities, this study timer can foster more productive and enjoyable study sessions.

**HC-SR501 PIR sensor:**
This sensor will trigger and send a digital high pulse when it detects motion within its range, and send a digital low pulse when no motion is detected. It can detect motion from about 120 degrees around it and from up to 7 metres away.

**PIR sensor Customisations:**
Users can adjust the amount of times the PIR sensor triggers, its sensitivity, and its time delay between signals by adjusting the jumper and the 2 potentiometers on its back. Out of 2 possible trigger modes, I set my PIR sensor to multiple trigger (H) mode instead of single trigger (L) mode by putting the jumper on the top two pins so it could trigger multiple times to detect changes in a person’s study patterns.

The 2 potentiometers on the back of the sensor are the sensitivity adjust potentiometer and the time delay potentiometer, which determine its range of detection , and the time interval of the high output sent before the output goes low again respectively. These figures can be increased or decreased by turning the potentiometer clockwise or counterclockwise respectively.
I turned the “sensitivity” potentiometer to its lowest range to suit the usually compact area of an individual’s study environment, and set its “time delay” potentiometer to its second lowest setting for precise feedback of motion detected during one’s study process.

![IMG_4495](https://user-images.githubusercontent.com/114293506/213215527-46dff6f4-c1fe-436b-805e-b572c5631032.jpg)
My adjusted PIR sensor

**Adafruit Neopixel Stick:**
 My project only lights up 5 of the 8 LEDs: during the work portion of the Pomodoro, an additional light will turn red for every five minutes that passes. 
 
![Screenshot_20230118_124427](https://user-images.githubusercontent.com/114293506/213213133-c2759277-c956-47df-af47-d00855279915.png)

Once 5 lights on the LED strip have turned red, it signifies that 25 minutes of the study portion has passed, and prompts the beginning of the 5-minute break. 

During the break portion, an additional light will turn green for every 1 minute that passes during this break. Once 5 lights on the LED strip have turned green, it means that the 5-minute break has passed, and a new Pomodoro round has begun.

**16x2 LCD screen:**
This component is a Liquid Crystal Display screen that can display 2 rows of 16 characters. In this project, it displays the amount of time elapsed in analog format, number of Pomodoros completed in this session, and different messages depending on PIR sensor input on the top row.

![954E3BED-A67F-4306-8658-B14ED09E93C8](https://user-images.githubusercontent.com/114293506/213214540-39e808aa-0f4b-44d3-97e3-411cbcb7e017.jpg)

The LCD screen while PIR reading is high

![IMG_4485](https://user-images.githubusercontent.com/114293506/213214956-aea1dc80-f227-442c-9fb2-b12382783bcb.jpg)

The LCD screen offering encouragement while the PIR reading is low

**Code:**
To account for the different time intervals in between updates to the Neopixel strip and LCD screen, I coded with nested loops, whereupon the “inner loop” would execute a set amount of times for each iteration of the “outer loop” to update the LCD screen a proportionate number of times for the lighting up of each additional Neopixel during both the Pomodoro and the break. I explain this more in detail in the code comments.

![61C23B6E-8471-4B83-83FB-DE630541C4E1](https://user-images.githubusercontent.com/114293506/213215887-9f95f5c9-a8de-48c3-994a-4ef4a7a5d4f7.jpg)

**Demonstration video of Motion Sensing Pomodoro Timer:**
https://youtube.com/shorts/T6F4kPXfHqc







