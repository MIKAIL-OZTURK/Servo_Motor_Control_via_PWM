# STM32F4 - Servo Motor Control via PWM

This project demonstrates how to control a servo motor using PWM (Pulse Width Modulation) with the STM32F407VG Discovery Board. It uses TIM4 in PWM mode to generate signals that rotate the servo between 0° and 180°.

## 🔧 Hardware

- **Microcontroller**: STM32F407VG (Discovery Board)
- **Servo Motor**: SG90
- **Power Supply**: 5V
- **Connections**:
  - Servo Signal → `PD12` (TIM4 Channel 1)
  - Servo VCC → 5V
  - Servo GND → GND

## 🧰 Tools & Environment

- **IDE**: STM32CubeIDE 1.16.1
- **HAL Library**: STM32Cube HAL (auto-generated via CubeMX)
- **Language**: C
- **Clock Configuration**:
  - SYSCLK: 84 MHz (HSI + PLL)
  - TIM4: 50Hz PWM (Prescaler: 83, Period: 19999)

## 📐 PWM Details

Servo motors typically expect:
- 1 ms pulse for 0°
- 1.5 ms for 90°
- 2 ms for 180°
  
With a 20 ms PWM period (50 Hz), these values are generated using:
```c
pulse_width = ((angle * 1000) / 180) + 1000;
```


## 🚀 Features
- Generates 50 Hz PWM signal using TIM4 Channel 1
- Controls servo angle from 0° to 180° and back in 10° increments
- Smooth delay-based transitions
- Modular Servo_Set_Angle() function

## 📸 Preview


https://github.com/user-attachments/assets/d7112c1d-6cd2-4e07-9ad9-d462cce528f6



## 📦 Future Improvements
- Control angle via UART (e.g., serial terminal)
- Read angle input via ADC (e.g., potentiometer)
- Use interrupts or timer-based scheduling instead of HAL_Delay()


## 📄 License
MIT License. See LICENSE file for details.
