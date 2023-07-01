# STM32F103C8T6_DAC_TriangularWave
## Author: Harry Nguyen (Created 07/01/2023)

This is a very interesting project that approximate the function of a DAC circuit using the PWM module on STM32F103C8T6 Blue Pill kit. During this project, I dedicate to generate triangular waveform using STM32F103C8T6, an MCU without built-in DAC module.

Component:
- STM32F103C8T6 Blue Pill kit
- Resistor 330 ohm
- Capacitor 1uF

As the PWM module can only generate square wave pulse, which in the frequency domain is the combination of multiple different sinusoidal waves, accroding to the Fourier transform. Therefore, to generate our dedicated waveform, we must get rid of most of these AC harmonic from the output signal and maintain only the DC component, which is the job of the low pass filter.

### To design the specific DAC circuit, we must following these steps:
- Define the DAC resolution.
- Define the maximum possible PWM frequency.
- Define the frequency of the output wave, and check if that frequency is valis due to the Nyquist criteria.
- Determine the number of sampling point on the waveform and generate a look up table using MATLAB code.
- Design the low pass filter with desired cut-off frequency.

There are multiple way to fetch the wave amplitude values from the look up table to the PWM register, however, using TIMER to trigger the DMA module is absolutely the best option as it prevent the main CPU from overloading.

## References:
1. Khaled Magdy, STM32 ARM tutorial series, https://deepbluembedded.com/stm32-change-pwm-duty-cycle-with-dma-for-sine-wave-generation/.

