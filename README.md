# Drone Detection System with STM32

This project integrates AI capabilities for drone detection using an STM32 board, along with a camera module and radar system.

## Hardware Requirements

- STM32F4 Discovery board (or any compatible STM32 board)
- Arducam 5MP Plus OV5642 Mini Module Camera Shield
- Drone detection module
- Radar system (connected via UART or SPI)
- Necessary connecting wires

## Software Requirements

- STM32CubeMX
- STM32CubeIDE or any compatible IDE
- STM32CUBE.AI tool inside the STM32CUBEIDE 
- TensorFlow Lite for Microcontrollers
- HAL Library

## Camera Module Integration (Arducam OV5642)

### Hardware Setup

1. **Connect Arducam Camera Module**:
   - **SPI Interface**:
     - MOSI to STM32 MOSI pin
     - MISO to STM32 MISO pin
     - SCK to STM32 SPI clock pin
     - CS to a GPIO pin on STM32 (e.g., PA10)
     - GND to STM32 ground (GND)
     - VCC to STM32 power supply (e.g., 3.3V or 5V)

### Steps to Integrate Camera Module

1. **Configure STM32CubeMX**:
   - Set up SPI1 interface for Arducam communication.
   - Configure GPIO pins (e.g., PA10 for CS).

2. **Implement Camera Driver**:
   - Implement `camera_driver.c/h` for SPI initialization, GPIO setup, and image capture.

3. **Update Main Application**:
   - Include `camera_driver.h` in `main.c`.
   - Initialize the camera module and capture images in your main application loop.

## Steps to Build and Run the Project

1. **Setup STM32CubeMX**:
   - Open STM32CubeMX and create a new project for your STM32 board.
   - Configure SPI1 for Arducam communication and GPIO pins.
   - Generate the initialization code and open it in STM32CubeIDE.

2. **Write the Embedded Code**:
   - Implement camera initialization and image capture in `camera_driver.c`.
   - Update the main application logic in `main.c` to handle camera captures and integrate with AI inference.

3. **Compile and Upload the Code**:
   - Compile the project in STM32CubeIDE.
   - Connect your STM32 board to your PC and upload the code.

4. **Run the System**:
   - Power up the STM32 board.
   - The board will initialize peripherals, capture images from Arducam, and process data for drone detection.

## Troubleshooting

- Ensure all connections (SPI, GPIO) are correctly configured and securely connected.
- Verify the SPI communication settings (clock polarity, phase, baud rate) match between STM32 and Arducam.
- Check camera driver implementation (`camera_driver.c/h`) for correct SPI commands and data handling.

## License

This project is licensed under the MIT License.
