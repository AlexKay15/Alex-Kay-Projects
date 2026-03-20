This semester, our project will be to utilize our STM32F429i-DISC1 board and its gyro, LCD, RNG, LEDs and
button to implement an advanced version to train the next generation of ground observation drone drivers.
While the wooden version shows the expected path, our walls and holes will be randomly generated, and
so our science lab has augmented our design with a quantum disruptor, which when activated by the user
button has two simultaneous effects: it will allow our eye-on-the-ground to move unimpeded through a wall,
or to move over a hole for a brief period of time.
We will use the 2D angle of our board “from being flat” to tip our virtual labyrinth—you could alterna-
tively think of this as the input to your drone’s “drive motor”. The more you angle away from vertical, the
more the drone will power itself in that direction. We will follow physics equations for a board tipped in a
gravity field, regardless of how you like to think about it.
The drone will be lost into a trap if the center of the drone is above any part of a trap when the Disruptor is
inactive.
