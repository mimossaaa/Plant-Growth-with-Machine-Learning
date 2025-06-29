System Architecture Overview
 - Sensors: Soil moisture, Light, Temp, Humidity sensors connected to RPi GPIO/I2C/Analog pins. Camera connected via CSI.
 - Data Acquisition: A Python script reads sensor values at regular intervals.
 - Data Logging: Sensor readings (excluding images) are appended to a CSV file.
 - CV Module: Periodically captures images, processes them (potentially using the AI accelerator if a neural network is used) to generate a health score.
 - RL Agent:
   - Reads the latest sensor data from the CSV or directly.
   - Optionally incorporates the CV health score into its state or reward calculation. This measures the amount of vegitaton by calculating the amount of green pixels in the FOV.
   - Uses a trained policy (running inference on the AI accelerator via TFLite) to decide on an action.
   - Actuators: The RL agent's chosen action triggers the corresponding actuator (e.g., turns the water pump on/off via RPi GPIO).
   - Feedback Loop: The environment changes (plant grows, soil dries), sensors detect this, feeding new data back into the system.



## Sensors used
- [ ] Soil moisture sensor
- [ ] Humidity sensor
- [ ] Temperature sensor
- [ ] light intensity sensor
- [ ] UV light strip
- [ ] Oled screen
 
      
## Goals
 - A machine learning model can properly grow a plant by manipulating the soul moisture and light intensity, while it tracks the soil moisture, light intensity, temperature, and humidity.


