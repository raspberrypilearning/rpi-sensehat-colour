## Sense HAT colour sensor

The version 2 Sense HAT includes an onboard colour sensor that can be used to measure the amount of light that is hitting the sensor, and detect the quantities of red, green and blue light.

The following code will output values for red, green and blue light that is detected, as well as the total amount of light that is incident of the sensor.

--- code ---
---
language: python
filename: main.py
line_numbers: true
line_number_start: 
highlight_lines: 
---
from sense_hat import SenseHat
from time import sleep

sense = SenseHat()
sense.color.gain = 60
sense.color.integration_cycles = 64

while True:
    sleep(2 * sense.colour.integration_time)
    red, green, blue, clear = sense.colour.colour # readings scaled to 0-256
    print(f"R: {red}, G: {green}, B: {blue}, C: {clear}")
--- /code ---

**Gain** is simply the sensitivity of the sensor. It can have values of `1`, `4`, `16` or `60`.

**Integration cycles** are the time that the the sensor takes between measuring the light. Each integration cycle is 2.4 milliseconds long, and the number of integration cycles can be any number between `1` and `256`.
