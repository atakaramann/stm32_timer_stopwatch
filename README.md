## STM32 TIM1 & SysTick Stopwatch

**Board:** STM32 Nucleo F413ZH  
**IDE:** STM32CubeIDE  
**Library:** HAL  

### What it does
Implements two parallel time-tracking systems:
- **TIM1** counts milliseconds, seconds and minutes via timer interrupt
- **SysTick** counts milliseconds and seconds via system tick handler

### Timer Configuration — TIM1
- Clock: 16MHz HSI
- Prescaler: 15
- Period: 999
- Output frequency: 1kHz (1ms period)

### Timer Configuration — SysTick
- Default HAL SysTick: 1ms tick
- ms and sec tracked inside SysTick_Handler

### Key concepts
- TIM1 base timer with interrupt
- SysTick handler override alongside HAL_IncTick()
- Volatile shared variables between main.c and stm32f4xx_it.c
- Extern variable declarations across source files
- Correct HAL initialization order (Start_IT after MX_TIM1_Init)
