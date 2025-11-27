# Frequency-Division-Multiplexing

# AIM
To implement Frequency Division Multiplexing (FDM) for six different message signals using Scilab, generate the multiplexed signal, and perform demultiplexing to recover all the original message signals. The experiment also includes plotting the message signals, multiplexed signal, and demultiplexed signals.

# APPARATUS REQUIRED
Computer System

Scilab Software

# ALGORITHM
Set sampling frequency, time duration, and time vector.

Generate six message signals with different frequencies.

Assign six different carrier frequencies.

Perform DSB-SC modulation by multiplying each message with its carrier.

Add all modulated signals to form the multiplexed FDM signal.

For each channel, multiply the multiplexed signal with the same carrier (demodulation).

Apply a low-pass filter to extract the recovered message.

Plot message signals, multiplexed signal, and recovered s ignals.

# THEORY
Frequency Division Multiplexing (FDM) is a technique in which multiple message signals are transmitted simultaneously over a single communication channel by assigning each signal a different carrier frequency. 

Each message modulates its own carrier, and all modulated signals are added to form the multiplexed signal. Since the carrier frequencies are well separated, the signals do not overlap in the frequency domain.

At the receiver, each signal is recovered by multiplying the multiplexed signal with the corresponding carrier (coherent demodulation) and passing it through a low-pass filter to extract the original baseband 
message. FDM is widely used in radio broadcasting, telephone systems, and cable TV.

# PROGRAM
clc;

clear;

close;

fs = 70000;                 

t = 0:1/fs:0.04;            

m1 = 3.0 * sin(2*%pi*120*t);

m2 = 3.3 * sin(2*%pi*140*t);

m3 = 3.5 * sin(2*%pi*160*t);

m4 = 3.7 * sin(2*%pi*180*t);

m5 = 3.9 * sin(2*%pi*200*t);

m6 = 4.1 * sin(2*%pi*220*t);

c1 = cos(2*%pi*3000*t);

c2 = cos(2*%pi*5000*t);

c3 = cos(2*%pi*7000*t);

c4 = cos(2*%pi*9000*t);

c5 = cos(2*%pi*11000*t);

c6 = cos(2*%pi*13000*t);

s1 = m1 .* c1;

s2 = m2 .* c2;

s3 = m3 .* c3;

s4 = m4 .* c4;

s5 = m5 .* c5;

s6 = m6 .* c6;

fdm = s1 + s2 + s3 + s4 + s5 + s6;

r1 = fdm .* c1;

r2 = fdm .* c2;

r3 = fdm .* c3;

r4 = fdm .* c4;

r5 = fdm .* c5;

r6 = fdm .* c6;

cutoff_hz = 450;                     

norm_cutoff = cutoff_hz / (fs/2);

M = 121;                             

[h, w] = wfir("lp", M, [norm_cutoff, 0], "hm", 0);


d1 = conv(r1, h, "same");

d2 = conv(r2, h, "same");

d3 = conv(r3, h, "same");

d4 = conv(r4, h, "same");

d5 = conv(r5, h, "same");

d6 = conv(r6, h, "same");

d1 = 2*d1;

d2 = 2*d2;

d3 = 2*d3;

d4 = 2*d4;

d5 = 2*d5;

d6 = 2*d6;

figure(1);

subplot(3,2,1); plot(t,m1); title("Message 1");

subplot(3,2,2); plot(t,m2); title("Message 2");

subplot(3,2,3); plot(t,m3); title("Message 3");

subplot(3,2,4); plot(t,m4); title("Message 4");

subplot(3,2,5); plot(t,m5); title("Message 5");

subplot(3,2,6); plot(t,m6); title("Message 6");

figure(2);

plot(t,fdm);

title("FDM Multiplexed Signal");

figure(3);

subplot(3,2,1); plot(t,d1); title("Demod 1");

subplot(3,2,2); plot(t,d2); title("Demod 2");

subplot(3,2,3); plot(t,d3); title("Demod 3");

subplot(3,2,4); plot(t,d4); title("Demod 4");

subplot(3,2,5); plot(t,d5); title("Demod 5");

subplot(3,2,6); plot(t,d6); title("Demod 6");

# OUTPUT WAVEFORM

![WhatsApp Image 2025-11-27 at 21 09 36_298d0477](https://github.com/user-attachments/assets/81604a48-da9d-4cec-9005-a534c3ea566e)

![WhatsApp Image 2025-11-27 at 21 10 08_89944c9c](https://github.com/user-attachments/assets/e4040fc1-b1d3-4263-95f3-d673348c20b3)

![WhatsApp Image 2025-11-27 at 21 09 34_8ed717cb](https://github.com/user-attachments/assets/99d0d099-e143-4ca0-865d-87a13ecb183d)

# CALCULATION
![WhatsApp Image 2025-11-27 at 20 33 28_f3145a8d](https://github.com/user-attachments/assets/328e0b8a-f714-4185-bd72-02b3f980fe54)

![WhatsApp Image 2025-11-27 at 20 33 45_cbed54a5](https://github.com/user-attachments/assets/0b868ff0-acee-45a9-9f74-a0c3c66d4cdb)

# RESULT
Six different message signals were generated and modulated using FDM. All modulated signals were added to form a multiplexed FDM signal. Each message was successfully recovered using coherent demodulation followed by low-pass filtering. The plots confirmed accurate multiplexing and demultiplexing.
