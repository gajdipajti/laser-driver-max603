# Circuit Parameters

## MAX603 voltage divider for the SET pin

I've measured the Laser Diode current (I\_LD) and voltage (U\_LD) to calculate the substitute resistance (R\_LD). Then I added the 10 Ohm current sense resistance to calculate the output voltage (U\_out) for the MAX603. Then I calculated the required R1/R2 ratio. Finally by keeping the R2 value fixed I calculated the R1+P1 value.

| I\_LD \[mA\] | U\_LD \[mV\] | R\_LD \[Ohm\] | R\_cs + R\_LD \[Ohm\] | U\_out \[mV\] | R1 + P1/R2 | R2 \[Ohm\] | R1+P1 | P1 \[Ohm\] |
| ----------- | ----------- | ------------ | ---------------- | --------- | -------- | ---------- | ----- | ---------- |
| 10          | 2030        | 203,00       | 213,00           | 2130      | 0,775    | 4,7        | 3,64  | 1,29       |  |
| 21          | 2130        | 101,43       | 111,43           | 2340      | 0,950    | 4,7        | 4,46  | 2,11       |  |
| 25          | 2170        | 86,80        | 96,80            | 2420      | 1,017    | 4,7        | 4,78  | 2,43       |  |
| 34          | 2230        | 65,59        | 75,59            | 2570      | 1,142    | 4,7        | 5,37  | 3,02       |  |
| 38          | 2270        | 59,74        | 69,74            | 2650      | 1,208    | 4,7        | 5,68  | 3,33       |  |
| 46          | 2330        | 50,65        | 60,65            | 2790      | 1,325    | 4,7        | 6,23  | 3,88       |  |
| 57          | 2400        | 42,11        | 52,11            | 2970      | 1,475    | 4,7        | 6,93  | 4,58       |  |
| 70          | 2500        | 35,71        | 45,71            | 3200      | 1,667    | 4,7        | 7,83  | 5,48       |  |
| 80          | 2560        | 32,00        | 42,00            | 3360      | 1,800    | 4,7        | 8,46  | 6,11       |  |
| 90          | 2620        | 29,11        | 39,11            | 3520      | 1,933    | 4,7        | 9,09  | 6,74       |  |
| 100         | 2690        | 26,90        | 36,90            | 3690      | 2,075    | 4,7        | 9,75  | 7,40       |  |
| 110         | 2760        | 25,09        | 35,09            | 3860      | 2,217    | 4,7        | 10,42 | 8,07       |  |
| 120         | 2820        | 23,50        | 33,50            | 4020      | 2,350    | 4,7        | 11,05 | 8,70       |  |
| 130         | 2890        | 22,23        | 32,23            | 4190      | 2,492    | 4,7        | 11,71 | 9,36       |  |
| 140         | 2930        | 20,93        | 30,93            | 4330      | 2,608    | 4,7        | 12,26 | 9,91       |  |
| 150         | 2970        | 19,80        | 29,80            | 4470      | 2,725    | 4,7        | 12,81 | 10,46      |  |

## Current sense circuit

The current sense resistor (R\_cs) is made up from two 20 Ohm resistors in parallel resulting in 10 Ohm resistance. If we would measure the voltage drop on the resistor we would get the following equation I\_LD = U\_cs/10. For example: 100 mV -> 10 mA.

To measure the voltage drop a 1x differential operational amplifier is used. The output is fed into a comparator circuit and into the LM3914 both with 1250 mV reference voltage.

## LM3914 resistor values

I used a circuit tutorial from [Peter J. Vis](https://www.petervis.com/Education/lm3914/lm3914-circuit-tutorial.html).

### R1 value - how much current we want to give to the bar?

*I used skipped this question by using a 10k potentiometer on the Ref\_OUT pin (PIN7). This would result in 1,25 mA-25 mA range. But don't test the higher range.*
[Calculator](https://www.petervis.com/Education/lm3914/lm3914-resistor-r1-calculator.html)

### R2 value - maximum input signal

*As I liked the 1.25V reference, I simply shorted the R1 and Ref\_ADJ pin (PIN8) to the ground.* [Calculator](https://www.petervis.com/Education/lm3914/lm3914-resistor-r2-calculator.html)

### Mode selection - bar or dot?

*5V on PIN 9 would set it to bar.*
