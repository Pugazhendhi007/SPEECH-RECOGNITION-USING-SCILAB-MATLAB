# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 
```
//  SPEECH RECOGNITION USING SCILAB
clc;
clear;
close;

disp("Loading audio files...");

// Read reference and test voice files
[y1, fs1] = wavread("C:\Users\acer\OneDrive\Attachments\good-morning-242169.mp3";
[y2, fs2] = wavread("C:\Users\acer\OneDrive\Attachments\intro-noise-131718 (1).mp3");

// Check sampling rates
if fs1 <> fs2 then
    error("Sampling rates must match!");
end

// Convert stereo to mono (if needed)
if size(y1,2) == 2 then
    y1 = mean(y1, 2);
end
if size(y2,2) == 2 then
    y2 = mean(y2, 2);
end

// Make both signals same length
n = min(length(y1), length(y2));
y1 = y1(1:n);
y2 = y2(1:n);

// Compute Euclidean distance
dist = sqrt(sum((y1 - y2).^2));

disp("Euclidean distance (reference vs test): " + string(dist));

// Decision based on threshold
if dist < 0.5 then
    disp("Matching with reference (same word)");
else
    disp("Not matching with reference (different word)");
end

// Plot both signals
figure(0);
subplot(2,1,1);
plot(y1);
title("REFERENCE VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

subplot(2,1,2);
plot(y2);
title("TEST VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

// Comparison plot
figure(1);
plot(y1, 'b');
plot(y2, 'r');
title("Original (Blue) vs Test (Red) Signal");
xlabel("Samples");
ylabel("Amplitude");
legend(["Reference", "Test"]);

disp("Waveforms plotted successfully. Close the graph window manually to finish.");

```

## OUTPUT: 
<img width="751" height="607" alt="dtsp" src="https://github.com/user-attachments/assets/9886df8c-ad19-4fad-b17f-c5fc663d01e9" />
<img width="682" height="571" alt="Screenshot 2025-11-21 233617" src="https://github.com/user-attachments/assets/85f2d2c8-1ef0-4ab5-8757-3d2ea0f68153" />




## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
