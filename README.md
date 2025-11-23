# Design-of-FIR-Filters-using-hanning-window

 # DESIGN OF FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```asm
// =============================================================
// LOW-PASS FIR FILTER USING HANNING WINDOW
// =============================================================

// --- Filter specifications ---
fs = 1000;          // Sampling frequency (Hz)
fc = 100;           // Cutoff frequency (Hz)
N  = 51;            // Filter length (odd number preferred)

// --- Compute the ideal impulse response ---
n = 0:N-1;          
alpha = (N-1)/2;    
m = n - alpha;      

// Ideal lowpass impulse response (sinc function)
h_ideal = (2*fc/fs) * sinc(2*fc*m/fs);

// --- Apply Hanning window ---
w = 0.5 - 0.5*cos(2*%pi*n/(N-1));  
h = h_ideal .* w;  // Windowed filter coefficients

// --- Plot the impulse response ---
scf(0);
plot(n, h);
xlabel("Sample index (n)");
ylabel("Amplitude");
xtitle("Impulse Response of Hanning-windowed Low-pass FIR Filter");

// --- Frequency response ---
[H, f] = frmag(h, 512, fs);
scf(1);
plot(f, 20*log10(H));
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
xtitle("Frequency Response of FIR Low-pass Filter");
xgrid();

// =============================================================
// TEST SIGNAL: a mixture of low and high frequencies
// =============================================================
t = 0:1/fs:1;   // 1 second of data
x = sin(2*%pi*50*t) + 0.5*sin(2*%pi*200*t);  // 50 Hz + 200 Hz components

// --- Apply the filter ---
y = conv(x, h, "same");

// --- Plot signals ---
scf(2);
subplot(2,1,1);
plot(t, x);
xlabel("Time (s)");
ylabel("Amplitude");
xtitle("Original Signal (50Hz + 200Hz)");

subplot(2,1,2);
plot(t, y);
xlabel("Time (s)");
ylabel("Amplitude");
xtitle("Filtered Signal (Low-pass output)");
xgrid();

// =============================================================
// END OF SCRIPT
// =============================================================
```

# OUTPUT
<img width="758" height="710" alt="505963842-21aa3f9e-1ed8-4048-a687-0b95610731a2" src="https://github.com/user-attachments/assets/c551b99d-88e8-49fc-9858-32adc68143da" />
<img width="757" height="713" alt="505963925-0f249c02-e4f3-41da-b437-8abc4f890dab" src="https://github.com/user-attachments/assets/314091f4-3884-4145-b1c0-39b83b04ceec" />
<img width="753" height="714" alt="505964095-32a18653-e7d6-410d-aa85-d645a0798a88" src="https://github.com/user-attachments/assets/0b75690e-bd4f-471b-b6ba-311594366d9a" />


# RESULT
LOW PASS FIR FILTER USING HANNING WINDOW IN SCILAB IS DESIGNED.
