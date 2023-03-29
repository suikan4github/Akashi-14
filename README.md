# Akashi-14
Compatct Flash board for Nucleo H735ZI.

# Details

This board connect the compact flash to the NucleoH735ZI FMC as the 8bit true IDE mode. The connection is depicted below :

| Compact Flash | H735ZI Pin | H735ZI Functionality |
|---------------|------------|----------------------|
| nCS0          | PC8        | FMC_NE2              |
| IORD          | PD4        | FMC_NOE              |
| IOWR          | PD5        | FMC_NWE              |
| nWAIT         | PD6        | FMC_NWAIT            |
| IRQ           | PD2        | EXTI2 ( active H)    |

# STM32H735ZI configuration
The CF interface of the STM32H735ZI must be configured as : 
- One of the FMC SRAM memory space must be assigned to the NE2. The CF is assigned to this memory space.
- That memory space must be 8bt and must have asynchronous wait. 
- If the IRQ is needed, assign PD2 as EXTI2. This is active H signal. 

Also, the Nucleo has to be modify :
- Cut SB19 to assign PD8 to FMC_D13
- Cut SB12 to assign PD9 to FMC_D14
- Short SB9 to assign PB6 to STLINK ( LPUART1_TX )
- Short SB34 to assign PB7 to STLINK ( LPUART1_RX )

Thus, the PB6 and PB7 should be assigned to LPUART1 async configuration. 



# License
This project is licensed under [MIT License](LICENSE).