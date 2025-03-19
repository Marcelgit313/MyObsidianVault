Computer system is made up of various elements
- Input devices - text entry and pointing
- Output devices - display, digital paper
- Virtual Reality - special interaction and display devices
- Physical interaction - e.g. sound and haptic
- Paper - as output (print) and input (scan)
- Memory - RAM & permanent media, capacity and access
- Processing - speed of processing, networks
## Display Devices
In HCI displays have the largest effect
Displays determine
- Physical size of the viewport
- Range of effective field-of-view
- Possible resolution
- Types of feasible interaction modalities (Touch, no touch?)
Three primary purposes
- General purpose displays
- Electronic paper displays
- Volumetric (3D) displays
### General Purpose Displays
- High resolution
- Fast response times
- Vivid colors
Different technologies
- [[The Computer#Cathode Ray Tube (CRT)|CRT (Cathode Ray Tube)]]
- [[The Computer#Liquid Crystal Display (LCD)|LCD (Liquid Crystal Display)]]
- OLED (Organic LED)
- DLP (Digital Light Processing)
- PDP (Plasma Display Panel)
Different shapes and different configurations
Three size scales:
![[displays_sizes.png]]
### Bitmap Displays
Screen is vast number of colored dots
Term **"resolution"** used (inconsistently) for
- Number of pixels on screen (width x height; SVGA 1024 x 768)
- Density of pixels (in pixels or dots per inch - dpi), typically between 72 and 96 dpi
**Aspect ratio**
- Ratio between width and height
- 4:3 = "standard" screens; 16:9 = wide-screen
**Color depth**
- Black/White
- Grayscale
- Red/Green/Blue 8 bits each = 16.7 million of colors 
### Cathode Ray Tube (CRT)
![[displays_crt.png]]
### Liquid Crystal Display (LCD)
![[displays_lcd.png]]
- Pixel = 3x1 matrix (subpixels: red, green or blue color filter)
![[displays_lcd_pixel_filter.png]]
### Large Displays
Used for meeting, lectures, etc.
Technology
- Projected - RGB lights or LCD projector
- Video walls - lots of small screens together 
### Situated Displays
Displays in "public" places
- Display only
- Interactive
$\implies$ Location matters, information or interaction related to location
### Electronic Paper
- Black/White
- No fast update rates
- Higher resolution is needed (Ideal acuity to recognize a written character = ~229 pixels/cm at reading ditance 57cm)
- Color less important
- Mostly used for reading
### 3D Display Devices
**Head-Mounted Display**
- Two small displays embedded in helmet or eye-glasses
	- Together: 3D impression
- Single user system
- Immersive, but low-resolution
**PowerWall**
- Two well calibrated projectors with polarization filters
- Polarizing eyeglasses
**Cave Automated Virtuale Environment**
- Projection-based VR system
- Stereoscopic shell display device
**Autostereoscopic Displays**
- No glasses or other equipment required
- Limitations for complexity of objects and surface
- Limited resolution
- Only one person, sweet spot needed $\to$ No head movement
**Virtual Reality (VR) Motion Sickness**
- **Time delay:** Conflict: head movement vs. what eyes see
- **Depth perception:** Conflict: eye angle vs. focus
### Consequences
- Size and type of display (as well as computer system) dictate feasible interactions
- Limits in pixel/voxel density affect the needed precision of pointing devices
- Display size matters
$\implies$ Different devices, need the interface to support all different styles of interaction
## Entry Devices
### Text Entry Devices
#### Keyboards
- most common text input device
- Allows rapid entry of text by experienced users
- Layout: QWERTY / QWERTZ
#### Phone Pad
- Numeric keys with multiple presses

| 2 - a b c | 6 - m n o   |
| --------- | ----------- |
| 3 - d e f | 7 - p q r s |
| 4 - g h i | 8 - t u v   |
| 5 - j k l | 9 - w x y z |
- surprisingly fast
#### T9 Predictive Entry
- One Key = One Letter (Example: hello = 43556)
- Dictionary to "guess" right word (Example: 26 = "am"/"an")
	- $\to$ menu selection needed
#### Numeric Keypads
For entering numbers quickly
- Different Layout
#### Handwriting Recognition
Text can be input into the computer, using pen and interactive display
- Natural interaction
Technical problems
- Interpreting individual letters
- Coping with different styles of handwriting
#### Speech Recognition
Most successful with
- Single user and initial training
- Limited vocabulary systems
Problems with
- External noise interfering
- Imprecision of pronunciation
- Large vocabularies
- Different speakers
### Positioning, Pointing, Drawing
#### Cursor Keys
- Four keys
- Only basic motion tasks
- No standardized layout, inverted "T" most common
#### Mouse
Common, easy handheld pointing device
Located on Desktop
- Requires physical space
- Relative movement only
#### Touchpad, Trackpad
- Small, touch sensitive tablets
- "Stroke" to move pointer
- Good "acceleration" settings needed
#### Joystick
- Indirect: Pressure of stick = velocity of movement
- Buttons for selction
- Often used in computer games
#### Touchscreen
Electronic visual display that can detect presence and location of touch within display area
- Stylus and/or finger (Stylus = Higher resolution)
- Interact directly with displayed objects
- No extra device needed
- High popularity due to smartphones
- Ideal for small devices $\to$ not scaling efficiently to large displays
	- $\implies$ Vision-based  approaches
Two types of displays:
**Resistive Technique:**
Two thin, transparent electrically-resistive layers, with thin gap between them
- press on outer surface $\to$ layers touch $\to$ position can be calculated 

| Pros                                        | Cons                                  |
| ------------------------------------------- | ------------------------------------- |
| Low cost                                    | Risk of damage                        |
| High resistance to liquids and contaminants | Poor contrast, caused by extra layers |
|                                             | No multitouch                         |
**Capacitive Technique:**
Insulator (e.g. glass), coated with transparent conductor
- Human body is also electrical conductor $\to$ touching surface $\to$ distortion of screen's electrostatic field $\to$ measurable change
- Not usable with gloves / pens
#### Eyegaze
- Control interface by eye gaze direction
- Uses Laserbeam reflected off retina
- Good accuracy requires Headset
- Potential hands-free control
Problem: Human's visual system is used for in- and output at the same time
#### 3D Interaction
- Mouse extended to 6DOF (= six-degrees of freedom: x, y, z + roll, pitch, yaw)
- Stationary usage, alternative wanda device, cubic mouse but tracking is needed
### Tacking devices
Tack the position and gestures of the user
Device can be rate trough following values
- Jitter
- Update rates
- Latency
- Drift
- Accuracy
![[devices_tracking_devices_values.png]]
**Mechanical:** Position and orientation of user is calculated relative to a reference point using kinematics properties of devices
**Magnetic:** Tracking position of receiver via magnetic field
**Ultrasonic:** Speed of sound through air is used to calculate distance between transmitter and receiver
**Optical:** Usage of optical sensors to determine the position and the orientation of an object
**Inertial:**  Usage of gyroscopes and accelerometers 
**Hybird:** Combination of multiple tracking technologies often: internal + magnetic or internal + optical (Wii)
![[devices_tracking_devices_comparison.png]]
### Other Interface Devices
**Gesture Interfaces:** Positions or poses are compared to a stored set of defined gestures
**Haptics:** Human haptic sense consists of two modalities Kinesthetic sense (force and motion) and Tactile sense (tact and touch)
**Audio Interfaces:** 3D sound output, sound input/speech recognition
