## MBI5015 interface using STM32 timers with Nucleo-F401RE

### Overview
This STM32 Hal based source code is to generate several signals to interface with MBI5026 16-bit constant current LED sink driver.  
To control a MBI5016, STM32 MCU outputs four signals (CLK, SDI, LE and OE) with proper timing sync.  
By using two TIM timers it makes output signals with a proper timing.  
![MBI5026-timing_diagram](MBI5026-timing_diagram.png)

### Signal outputs
Output clock frequency is 1000kHz.  
A following signal capture picture shows 16 CLK for serial data input and one clock is for LE(Latch Enable)
and remain three periods for OE(Output Enable).  
![Clock and Latch Enable output signal capture](CLK_LE_output.png)
