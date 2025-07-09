# Real-Time Voice Encryption and Decryption using Simulink on Android/iOS Devices with Bluetooth Communication

This project demonstrates a real-time audio communication system between two mobile phones using MATLAB Simulink and Bluetooth, implementing two different encryption methods for audio signals. The project includes:

Voice recording on Phone A

Encryption using chosen method

Transmission over Bluetooth

Reception and decryption on Phone B

Playback of encrypted/decrypted audio


# Tools & Technologies
MATLAB & Simulink

Simulink Support Package for Android Devices

Bluetooth Communication Blocks

Android/iOS Smartphones

Signal Processing Toolbox

# Encryption Methods
Method 1: Spectrum Scrambling
The recorded audio signal is transformed to the frequency domain using FFT.

The spectral components are shuffled using a pseudorandom index permutation.

The scrambled signal is converted back to time domain using IFFT.

Resulting audio is unintelligible and secure.

# Method 2: Additive Noise Masking
Controlled noise signals (e.g., sine waves or white noise) are added to the original signal.

These mask the voice and make it unclear without knowing the exact noise to remove.

Noise signals are later removed in decryption using synchronized parameters.

# Application Flow
Phone A (Transmitter App)
Records real-time voice input

Encrypts using selected method (UI allows method selection)

Sends encrypted signal via Bluetooth

Phone B (Receiver App)
Receives the encrypted signal via Bluetooth

UI options:

Play Encrypted Audio

Play Decrypted Audio (Method 1)

Play Decrypted Audio (Method 2)

Decrypts using corresponding method and plays back

# Filter Design Explanation
For Method 2 (Noise Addition):
Bandpass Filters are used to isolate and remove added noise components.

Noise added as pure tones (e.g., 2 kHz, 3.5 kHz) is targeted using narrowband notch filters or inverse filters.

Filter designed using:

matlab
Copy code
d = designfilt('bandstopiir','FilterOrder',4, ...
               'HalfPowerFrequency1',1950, ...
               'HalfPowerFrequency2',2050, ...
               'DesignMethod','butter', ...
               'SampleRate',Fs);
# App UI Features
Phone A:
Record Button

Encryption Method Selection (Dropdown/Buttons)

Send via Bluetooth

Phone B:
Play Encrypted Audio

Play Decrypted Audio (Method 1)

Play Decrypted Audio (Method 2)

 # Video Demonstration

 # Click Here to Watch
[(https://www.youtube.com/watch?v=L1J6Nn4XBtY)]

# Simulink Files
PhoneA_Transmitter.slx

PhoneB_Receiver.slx

scramble_spectrum.m (helper function)

add_noise_signal.m (helper function)

# Setup Instructions
Install Simulink Support Package for Android Devices:
Simulink Android Support

Connect Android phones via USB and enable Developer Mode.

Open PhoneA_Transmitter.slx → Build & Deploy to Phone A

Open PhoneB_Receiver.slx → Build & Deploy to Phone B

Pair both devices via Bluetooth before running.




