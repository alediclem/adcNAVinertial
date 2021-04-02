# adcNAVinertial (current version v11_20)

## Project Summary
adcNAVinertial is a simple 4-layer PCB development board designed to fulfill several purposes:
- Evaluate sensors performance for applications in inertial navigation;
- Sensor modeling and calibration procedures;
- Real-time full-speed USB sensor data streaming;
- Implementation of sensor fusion algorithms on embedded ARM MCU and evaluation of code-generation capabilities of MATLAB/Simulink environment;
- Lay the foundation for a navigation computer board for small autonomous multirotors;

<p align="center">
<img src="/images/board_top.png" width="512">
</p>

## Board details
The main component of the board is a STM32F4 Arm Cortex-M4 microcontroller.
The board can mount a total of three sensor types which are connected to separate SPI peripherals of the processor. Some types of sensors have multiple footprint choices:
- The **inertial measurement unit** (**IMU**) sensor can be mounted on a LGA-14L or LGA-16 footprint;
- The **magnetometer** sensor can be mounted on a LGA-12 footprint;
- The **absolute pressure** and **temperature** sensor can be mounted on a HLGA-10L or LGA-10 footprint.

The MCU can be clocked by a 16MHz external crystal oscillator; a reset button and one status RGB LED may help debugging.

The board has a SWD connector for MCU debugging and programming, one  Micro-B USB connector with ESD diode clamping connected to the MCU full-speed peripheral, a 6-pin PicoBlade connector socket for external embedded devices, and one 2-pin PicoBlade connector for external power supply with reverse polarity and overcurrent protection. Spare pins of the microcontroller can be accessed via test points or through-hole pads.

## Assembly and test
A board prototype was easily assembled using reflow soldering; magnetometer IC was out of stock from distributors due to 2020 semiconductor shortage.

<p align="center">
<img src="/images/assembly.jpg" width="512">
</p>

C drivers for sensors and USB were written in order to stream data to a host computer using a virtual COM port. The following Simulink model can be used for real-time visualization and processing up to the maximum sensor sample rate of 6.6 kHz:

<p align="center">
<img src="/images/simulink_model_simple.png" width="512">
</p>

The following scope and spectrogram capture shows an example of the accelerometer output for a sample rate of 104 Hz:

<p align="center">
<img src="/images/accelerometer_g.png" width="512">
</p>

For the x axis:

<p align="center">
<img src="/images/spectrogram_simulink.png" width="512">
</p>

## Future versions
- Add ToF sensor;
- Remove unused footprints
