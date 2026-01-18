# My low-level STM32 Handbook

## GPIO
You first need to enable the GPIOx peripheral before using it, otherwise it become useless no matter what you configure it to be.
```c
RCC->AHB1ENR = RCC_AHB1ENR_GPIOxEN;
```
Though check your STM32 datasheet to confirm of your GPIO is inside AHB1 or else.

--------------------------
### Configuration register
|    Register    |                    Controls                   |
|----------------|-----------------------------------------------|
| `GPIOx_MODER`  | **[1:0]** Pin mode (input/output/AF/analog)   |
| `GPIOx_OTYPER` | Push-pull or open-drain                       |
| `GPIOx_OSPEEDR`| **[1:0]** Output speed (low/mid/fast/high)    |
| `GPIOx_PUPDR`  | **[1:0]** Pull-up / pull-down                 |
| `GPIOx_IDR`    | Read input                                    |
| `GPIOx_ODR`    | Write output                                  |
| `GPIOx_BSRR`   | Atomic set/reset                              |
| `GPIOx_AFRL`   | **[3:0]** Alternate function (lower portion)  |
| `GPIOx_AFRH`   | **[3:0]** Alternate function (higher portion) |

***...TO BE CONTINUED...***