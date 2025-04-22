
Name: BHARGAV GORIVALE

Company: My Equation Education

Domain : E-Drive : A Industrial Training Program On EV’s and software simulation

Duration : Feb 2025

Mentor : Abinash Kumar Panda

# **Overview of the Project**

## **Project :  Design-Of-An-Electric-Vehicle-Using-MATLAB-Simulink**

### **Objective**
This project aims to develop a simple and efficient electric vehicle (EV) model in MATLAB Simulink using individual component models to analyze key performance parameters such as speed, SOC (State of Charge), and current under various drive cycles. The model allows for flexible adjustments to motor power, vehicle body properties (rolling resistance, air drag, and weight), and battery configurations to match real-world EV performance.

### **Key Activities**
1. Model Development: Building an EV model in MATLAB Simulink using modular (individual) components.

2. Performance Analysis: Analyzing speed, State of Charge (SoC), and current behavior during simulation. Evaluating the system response under various drive cycles (e.g., FTP-75, NEDC).

3. Parameter Customization: Tuning motor power, vehicle dynamics (rolling resistance, air drag, and weight). Modifying battery configuration (voltage, capacity, number of cells).

4. Drive Cycle Simulation: Running standard or custom drive cycles to assess real-world performance.

5. Real-world Performance Matching: Adjusting the model to reflect real EV behavior for practical insights or prototyping.

### **Technologies Used**

1. MATLAB Simulink:
    - For system modeling, simulation, and visualization.

    - Component libraries (Simscape, Simscape Electrical).
      
  
### **Results :**

1. EV Model Current Graph:
   ![EV_MODEL_Current_GRAPH](https://github.com/user-attachments/assets/b6392ac1-7a82-4e01-bd24-9584c1652690)


   
2. Key Detection:
    - The program uses specific addresses to directly interact with the STM32 GPIO registers. These addresses are defined in the code as follows:

             uint32_t volatile *const pGPIODModeReg  = (uint32_t*)(0x40020C00);     // GPIO Mode Register
             uint32_t volatile *const pInPutDataReg  = (uint32_t*)(0x40020C00 + 0x10); // GPIO Input Data Register
             uint32_t volatile *const pOutPutDataReg = (uint32_t*)(0x40020C00 + 0x14); // GPIO Output Data Register
             uint32_t volatile *const pClockCtrlReg  = (uint32_t*)(0x40023800 + 0x30); // Clock Control Register
             uint32_t volatile *const pPullupDownReg = (uint32_t*)(0x40020C00 + 0x0C); // Pull-up/Pull-down Register

    - These registers control the configuration and behavior of the GPIO pins for Port D on the STM32F407. The base address for GPIOD is 0x40020C00.
      
3. Clock Signal:
   
    - Before interacting with GPIO pins, the peripheral clock for GPIOD must be enabled.

            *pClockCtrlReg |= (1 << 3);

4. GPIO Pin Configuration :

   a. Configuring PD0-PD3 as Output (Rows)

        *pGPIODModeReg &= ~(0xFF); // Clear mode bits for PD0-PD3
        *pGPIODModeReg |= 0x55;   // Set PD0-PD3 as output (01 for each pin)

    - The GPIO mode register configures the behavior of each pin.
      
    - &= ~(0xFF) clears the mode bits for pins PD0 to PD3.
      
    - |= 0x55 sets these pins as outputs by configuring 2 bits for each pin as 01 (which corresponds to output mode in STM32).

   b. Configuring PD8-PD11 as Input (Columns)

        *pGPIODModeReg &= ~(0xFF << 16);
   
     - The same mode register is modified to configure PD8-PD11 as input pins by clearing their mode bits. No need to set them, as the reset value for these bits corresponds to input mode (00).

5. Pull-up Resistors for Columns:

       *pPullupDownReg &= ~(0xFF << 16);  // Clear
       *pPullupDownReg |=  (0x55 << 16);  // Enable pull-up resistors for PD8-PD11

     - The Pull-up/Pull-down register enables internal pull-up resistors for the input pins PD8-PD11.
       
     - This prevents floating inputs when no button is pressed, ensuring stable high readings when no key is pressed.
       



### **Keypad Layout Corresponding to the Program:**
![KeypadInterfacing](https://github.com/user-attachments/assets/9f43bada-9755-48a8-b3ac-e141686fe3cd)
