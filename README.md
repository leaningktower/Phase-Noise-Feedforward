<br><img width="977" alt="Pasted Graphic 3" src="https://github.com/user-attachments/assets/668d199b-efe7-48f4-b6ce-d251193f35d3">   
<br>The picture above shows the prototype board built for the first time implementation of laser phase noise feedforward [1] for Pound–Drever–Hall (PDH) locking technology [2]. The board converts the beat signal between cavity transmission and noisy stabilised laser to the real-time phase noise as a voltage output. The output can be sent into an EOM to implement the realtime correction of laser phase noise.   
<br>The original design is already detailly described in [1], since then I receive several requests for the PCB design but doesn’t have time to work on it. Recently we are working on a second phase noise feedforward system and that gives me a chance to optimise the design and draw a PCB board for it.   
<br>The new design is shown below.   
<br><img width="793" alt="Pasted Graphic 6" src="https://github.com/user-attachments/assets/b000f404-a94a-49c5-8b72-6ae320a8549a">   
<br>Most of the parts are similar to the old design and the main difference is the U5, which is used for the differential amplifier after the phase detector U4. At very beginning of this design, it is believed that a ~6 MHz bandwidth should be enough for any servo bump of sub MHz level. But the feedforward operation has a higher requirement since any feedforward gain error will significantly affect the canceling of noise. At -3 dB bandwidth, a gain error of 30% will limit the maximum phase noise cancellation to only -3 dB.   
<br>In the new design, the small signal gain is estimated about 40 MHz. This is tested with the response of the circuit to a Phase-shift keying (PSK) rf signal, we can find the rising time is decreased from ~100 ns to less than 10 ns:    
<br><img width="1090" alt="Pasted Graphic 8" src="https://github.com/user-attachments/assets/7fa32a9d-d422-4c2a-8328-99514f32b8ee">    
<br>The left panel is the response of old design and the right panel shows the response of the new design. It should be noted that the measurement on right has a 20 MHz bandwidth limit the get rid of the non-ideal isolation of the rf signal in phase detector and the actual rising time could be a bit higher. This rf leakage is well filtered by the free-space EOM amplifier that has a ~20 MHz bandwidth limit.    
<br>Except the bandwidth improvement, the design has a BPF-200 band pass filter and LNA at input. The band pass filter is need for the offset PDH locking, where there is an offset frequency between the laser to be locked and the cavity transmission. Since the offset frequency can be arbitrary frequency between 0 and 0.5 FSR of the optical cavity (usually hundreds of MHz), a mixer is used to down (up) convert the offset frequency to 200 MHz used in this circuit. For the case that the offset frequency is relatively close to 200 MHz, for example, a 260 MHz tone could easily leak through the mixer cause the abnormal working of the phase detector. If the offset frequency is pretty far away from 200 MHz, lower order bandpass filter can be used to decrease the group delay of the electronics.    
<br>Examples of the implementation of real-time phase noise feedforward:    
<br><img width="765" alt="Pasted Graphic 9" src="https://github.com/user-attachments/assets/96a203cd-775f-4fc4-8b31-28d22db1a820">    
______________________________________________________________________________________________________________
References:

[1] Li, Lintao, et al. "Active cancellation of servo-induced noise on stabilized lasers via feedforward." Physical Review Applied 18.6 (2022): 064005.

[2] Drever, Ronald WP, et al. "Laser phase and frequency stabilization using an optical resonator." Applied Physics B 31 (1983): 97-105.










