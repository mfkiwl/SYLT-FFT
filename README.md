SYLT-FFT
========
DEVSOUND (I)FFT(R) LIBRARY
-------------------------------------
<sup>And some other funky fixed-point maths like gray-coding and pow(2, f)</sup>

**Optimized (C-level) for Keil C Compiler and GCC on Cortex-M4.**

**Authors:**
* D. Taylor 2014 (gmail: senseitg)

**License:**
* MHG (GPL compatible) - see LICENSE

**Features:**
* FFT (Fast Fourier Transform) and IFFT (Inverse FFT)
* Fixed-point 32-bit, Radix-2
*	Complex or real data (with conversion overhead)
* No plan construction required before (I)FFT

**Options (config.h):**
* DIT (decimation-in-time) or DIF (decimation-in-frequency)
* Rounding on divide (-speed, +accuracy)
* Saturating math (-speed, +stability)
* Table size vs. max. FFT length

**Resource requirements:**
* Minimal memory requirements (in-place)
* Minimal stack use (non-recursive)
* Minimal twiddle tables (512 bytes for max N=512 FFT)

**Notes:**
* Designed for optimal performance, not optimal accuracy

**Caveats:**
* Care must be taken with input data to ensure no overflows
* Requires C99 (-std=c99 for GCC)

**Performance:**
* Comparing against: CMSIS DSP arm_cortexM4I_math.lib(1.4.2)
* Platform: Freescale Kinetis K20 (Cortex-M4/ARMv7E-M)
* KEIL = Keil C Compiler 5.01 -O3
* GCC  = GNU Tools for ARM Embedded Processors 4.8.4 -O3

```
Comparisons are of speed, +N% = faster than CMSIS, -N% = slower.
Please verify and do additional tests to add to the list.

  CMSIS-DSP             SYLT-FFT      N     KEIL     GCC
* arm_cfft_radix2_q31   fft_inverse   256   +25.6%   +15.1%
```