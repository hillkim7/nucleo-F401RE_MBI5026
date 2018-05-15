## MBI5015 interface using STM32 timers with Nucleo-F401RE

### Overview
This STM32 Hal based source code is to generate several signals to interface with MBI5026 16-bit constant current LED sink driver.  
To control a MBI5016, STM32 MCU outputs four signals (CLK, SDI, LE and OE) with proper timing sync.  
By using two TIM timers it makes output signals with a proper timing.  
![MBI5026-timing_diagram](MBI5026-timing_diagram.png)

