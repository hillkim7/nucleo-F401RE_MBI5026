## Interfacing MBI5026 using STM32 timers with Nucleo-F401RE

### Overview
This STM32 Hal based source code is to generate several signals to interface with MBI5026 16-bit constant current LED sink driver.  
The MBI5026 is kind of serial-in and parallel out IC. To talk with this IC a MCU has to output signals with proper timing.  
<br>
![MBI5026 timing diagram](MBI5026-timing_diagram.png)

### Build & Run environment
* Nucleo-F401RE
* STM32CubeMX Version 4.25.0
* Keil MDK-ARM 5.24.1

### Implementing timing diagram
The timing domain consists of CLK, SDI, LE and OE pulses. To make it simple CLK, SDI and LE pulses are grouped together with a same clock width.
The range of remain OE pulse is treated as three clock width of SDI so that total number of clocks are 20.  
![timing diagram design](timing_diagram_design.png)

There are two frequencies in the diagram:  
  - T1: data shift frequency  
  - T2: parallel output frequency (T1 * 20)

Two TIM timers make these ferquencies respectively.  
A TIM1 is in charge of T1 pulse. A TIM1 triggers a Update Event to TIM2 at each 20 cycles with the Repetition Count (RCR) 19.  
The _Slave Mode_ of TIM2 is _Reset Mode_ that restarts the timer count then activates the PWM output channel1.

### Signal outputs
Output clock frequency is 1000kHz.  
A following signal capture picture shows 16 CLK clocks for serial data input and one clock for LE(Latch Enable)
and three periods for OE(Output Enable) which is period of no clock.  
![Clock and Latch Enable output signal capture](CLK_LE_output.png)

---
  By Hill Kim
